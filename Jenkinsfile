pipeline {
agent any
environment {
        PROJECT_DIR = '/apps/farmfrontend/'
        TEST_REPORT = 'test-reports/farmfrontend_report.xml'
    }
    stages {
        stage ('Build') {
            steps {
                sh """
                #!/bin/bash

                echo "Build..."
                # 1. Update dependencies & create optimised build in Jenkins workspace
                npm install
                npm run build

                """
            }
        }
        stage("Deploy") {
            steps {
                sh """
                #!/bin/bash

                echo "Deploy..."
                # 1.  Copy project from jenkins workspace to project directory on server
                rm -rf "${PROJECT_DIR}"
                cp -R $WORKSPACE/build "${PROJECT_DIR}"

                """
            }
        }
    }
}