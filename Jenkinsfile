pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch:'main', url: 'https://github.com/vigneshbhatn/Calculator-Java.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy with Ansible') {
            steps {
                sh 'ansible-playbook -i inventory.ini deploy.yml'
    }
}

    }

    post {
        success {
            echo "✅ Build and tests successful!"
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
        failure {
            echo "❌ Build or tests failed!"
        }
    }
}
