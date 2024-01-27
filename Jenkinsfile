pipeline {
	agent any

	stages {
		stage('Clone') {
			steps {
				git 'https://github.com/salihonder/maven-project-sample.git'
			}
		}
		stage('Compile') {
			steps {
				sh 'mvn compile'
			}
		}
		stage('CodeReview') {
            steps {
                sh 'mvn pmd:pmd -P metrics'
            }
						post {
							success {
								recordIssues(tools: [pmdParser(pattern: '**/pmd.xml')])
							}

			      }
    }
	}
}
