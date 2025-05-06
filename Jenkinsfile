pipeline {
    agent any
    tools {
        maven "apache-maven-3.9.9"
    }
    stages {
        stage('Git Checkout') {
            steps {
                script {
                    git branch: 'master',
                        credentialsId: 'jenkins_credentails',
                        url: 'https://github.com/vijayaperuboinaEFX/simple-java-maven-app.git'
                }
            }
        }
        stage('Build maven Project')
        {
            steps {
                sh 'mvn install -Dskiptest'
            }
        }
        stage('Test Maven -Junit') {
            steps {
	                sh "mvn test"
                    }
                post{
                    always {
		                    junit 'target/surefire-reports/*.xml'
                        }
	            }
            }
        post {
        success {
                echo 'I will always say Hello again!'
                }
            }
            
    }
}
