pipeline {
    agent any
//
    environment {
        JAVA_HOME = "C:\\Program Files\\Java\\jdk-17" // change if needed
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/rahul-revanth-reddy-gali/user-management-jenkins.git'
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                sh './mvnw test'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Build and test succeeded!'
        }
        failure {
            echo '❌ Build failed!'
        }
      //  always {
        //    cleanWs()
       // }
    }
}
