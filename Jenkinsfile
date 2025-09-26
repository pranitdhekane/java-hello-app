pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/pranitdhekane/java-hello-app.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t java-hello-app .'
            }
        }

        stage('Docker Run') {
            steps {
                sh 'docker run -d -p 8080:8080 --name java-hello-app java-hello-app'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}

