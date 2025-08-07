pipeline {
    agent any
    stages {
        stage("unit-test") {
            steps {
                echo 'UNIT TEST EXECUTION STARTED'
            }
        }
        stage("functional-test") {
            steps {
                echo 'FUNCTIONAL TEST EXECUTION STARTED'
            }
        }
        stage("black-duck-security-scan") {
           steps {
               echo 'BLACK DUCK SECURITY SCAN STARTED'
               script {
                   // security_scan product: "blackducksca"
                   security_scan product: "polaris", polaris_application_name: 'E2E-Integration-Ap', polaris_project_name: 'TestProject',
                       polaris_assessment_types: 'SCA', polaris_branch_name: 'master'
                }
            }           
        }
        stage("build") {
            steps {
                echo 'BUILD EXECUTION STARTED'
                echo 'Pulling...' + env.BRANCH_NAME
            }
        }
    }
    // post {
    //     always {
    //         cleanWs()
    //     }
    // }
}
