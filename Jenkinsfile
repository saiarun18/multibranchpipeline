pipeline
{
    agent any
    stages
        {
            stage(ContinuousDownload)
            {
                steps
                {
                 script
                    {
                    try
                    {
                        git 'https://github.com/intelliqittrainings/maven.git'
                    }
                    catch(Exception e)
                    {
                        
                    }
                    
                    }
                }
            }
            stage(ContinuousBuild)
            {
                steps
                {
                    sh 'mvn package'
                }
            }
            stage(ContinuousDeployment)
            {
                steps
                {
                    deploy adapters: [tomcat9(credentialsId: 'c105f7f0-5a5e-40df-9a3f-699a30a466b3', path: '', url: 'http://172.31.19.113:8080')], contextPath: 'testapp', war: '**/*.war'
                }
            }
            stage(ContinuousTesting)
            {
                steps
                {
                      git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                      sh 'java -jar /home/ubuntu/.jenkins/workspace/DeclarativePipeline/testing.jar'
                }
            }
}}
