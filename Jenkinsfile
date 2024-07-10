pipeline{
	agent any
	environment {
		DOCKERHUB_PASS = credentials('docker-pass')
	}
	stages{
		stage("Building the Student Survey Image"){
			steps{
				script{
					checkout scm
					sh 'echo ${BUILD_TIMESTAMP}'
					sh 'docker login -u charuvarthana -p Charu@1234'
					sh 'docker build -t charuvarthana/survey-2 .'
				}
			}
		}
		stage("Pushing image to docker"){
			steps{
				script{
					sh 'docker push charuvarthana/survey-2'
				}
			}
		}
		stage("Deploying to rancher"){
			steps{
				script{
					sh 'kubectl rollout restart deploy test'
				}
			}
		}
	}
}
