pipeline {
    agent {
        node {
            label 'nodejs'
        }
    }
    stages {
         stage('Run Test'){
             parallel {
                 stage('Backend Tests') {
                     steps {
                         sh 'node ./backend/test.js'
                     }
                 }         
                 stage('Frontend Tests') {
                     steps {
                         sh 'node ./frontend/test.js'
                     }
                 }
             }
         } 
         stage('Deploy') {
             when {
                expression { env.GIT_BRANCH == 'origin/main' }
                beforeInput true
             }
             input {
                    message 'Deploy the application?'
             }
             steps {
                 echo 'Deploying....' 

             }
         }

    }
}
