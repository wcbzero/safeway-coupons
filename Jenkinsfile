pipeline {
    agent any
    triggers { cron('H 6 * * *') }
    stages {
        stage('Build') {
            steps {
                withCredentials([file(credentialsId: 'safeway-coupons-config', variable: 'SAFEWAY_COUPONS_CONFIG')]) {
                    sh '''
                    docker build -t safeway-coupons .

                    docker run -v "${SAFEWAY_COUPONS_CONFIG}":"/app/config.ini" safeway-coupons
                    '''
                }
            }
        }
    }
}