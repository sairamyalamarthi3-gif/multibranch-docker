pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image2 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image2 sairamyalamarthi3/paytm:buses'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push sairamyalamarthi3/paytm:buses'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -d --name bus-app -p 2222:80 sairamyalamarthi3/paytm:buses'
            }
        }
    }
}
