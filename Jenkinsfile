pipeline {
	agent any
	tools {
        maven 'maven3.6.1'
		jdk 'jdk1.8.0_211'
    }
    stages {
        stage('Build') {
            steps {
				sh 'echo $PATH'
				sh 'echo $JAVA_HOME'
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
