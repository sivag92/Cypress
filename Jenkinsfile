pipeline {
    agent any

    parameters{
        string defaultValue: 'cypress/e2e/test/**', description: 'Enter the Spec name', name: 'Spec', trim: true
        choice choices: ['Chrome', 'Edge', 'FIrefox'], description: 'Enter the browser you want the scripts to run', name: 'Browser'
    }

    options{
        ansiColor('xterm')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                bat "npm i"
                bat "npx cypress run --browser ${Browser} --spec ${Spec}"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
        stage('Release') {
            steps {
                echo 'Releasing...'
            }
        }
    }

    post{
        always{
            publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'cypress/reports', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
        }
    }
}
