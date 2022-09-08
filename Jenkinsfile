pipeline {
  //agent any
  agent any
  tools {
      maven '3.8.6'
  }
  stages {
    stage('deploy-to-exchange') {
      steps {
        // deploys the same binary zip file exchange
        // mvn clean deploy works fine, 
        // it will rebuilt an equivalent binary zip file
        sh "mvn clean deploy -X"
      }
    }
    stage('deploy-to-rtf') {
      steps {
        // deploy from Exchange to RTF runtime.
        //sh "mvn clean package deploy -Pbuild -Dpackaging=mule-application -DmuleDeploy -Dmule.version=4.4.0 -Denv=sandbox -Dusername=stigadimanutan -Dpassword=Remember\\*8 -Drtf.app.name=demo-rtf-cicd-muleapp -Ddeployment.target=migmnik-mule-rtf -Dbusiness.group.id=496ac21f-ecc4-4296-bbb7-cbb1ebcb7923 -DplatformClientId=fbc2345f4c174a059b749e7dbf8b8dee -DplatformClientSecret=15F7bB0B42eb4801a2eF62f573B099d4 -DplatformEnv=Sandbox -Dreplicas=1 -DingressUrl=rtfapi.sandbox.manutan.corp -DdeploymentName=demo-rtf-cicd-muleapp"
        sh "mvn clean package deploy -DmuleDeploy -Dmule.version=4.4.0 -Dusername=tigadidt -Dpassword=Remember*8 -Drtf.app.name=demo-rtf-cicd-muleapp -Ddeployment.target=rtf-gke-sidd Dbusiness.group.id=b6430f15-51c3-4480-8ed3-917175ef77af -DplatformClientId=eb98819200324dcf86c3405e5e699b0a -DplatformClientSecret=91486e20c81843A5bF596552Aa376f10 -DplatformEnv=dev -Dreplicas=1 -DingressUrl=rtfapi.dev.devoteam.corp -DdeploymentName=demo-rtf-cicd-muleapp -X"
        
      }
      post {
        success {
          sh 'echo RTF CICD all done!  '
        }
      }
    }
  }
}
