
pipeline {
    agent {
        label 'local'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                dir('C:\\Users\\Raj\\Desktop\\jenkins-sc') {
                    bat 'docker build -t flask-app:latest .'
                }
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                    docker run -d --name flask-app -p 5000:5000 flask-app:latest
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                bat 'curl.exe --fail --retry 5 --retry-delay 2 http://localhost:5000/health'
            }
        }
    }
}
