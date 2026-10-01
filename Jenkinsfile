pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/thirumalai004/react-jenkins-docker.git'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t react-jenkins-app:v1 .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker stop react-app || exit 0'
                bat 'docker rm react-app || exit 0'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 3001:80 --name react-app react-jenkins-app:v1'
            }
        }
    }
}