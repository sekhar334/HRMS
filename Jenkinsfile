pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout source code from Git
                git 'https://github.com/sekhar334/HRMS.git'
            }
        }
        stage('Setup') {
            steps {
                // Set up virtual environment
                sh 'python3 -m venv venv'
                sh 'source venv/bin/activate && pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                // Run Django tests
                sh 'source venv/bin/activate && python manage.py test'
            }
        }
        stage('Deploy') {
            steps {
                // Handle migrations
                sh 'source venv/bin/activate && python manage.py migrate'
                // Collect static files
                sh 'source venv/bin/activate && python manage.py collectstatic --no-input'
                // Perform deployment actions (e.g., copy files to server)
                // Add deployment scripts or commands here
            }
        }
    }
}
