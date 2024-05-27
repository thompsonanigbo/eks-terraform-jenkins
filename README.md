# eks-terraform-jenkins

PROJECT: using Terraform (IaC), Jenkins to deploy EKS cluster in AWS cloud and and connect to ECR for image push. Json image created and nginx docker image used for this project. Configuration files and codes are in GitHub repository. Jenkins used for the pipeline. 

This automates the deployment process end to end. 

 
Steps followed are: 

#1 From AWS console, create a user (named utom)and generate the access keys. This is used to access the console or command line to provision the infrastructure. 

Create and Ubuntu machine (named jenkins-server) also from the console. t2.medium instance type is used. This machine acts as. The host to run the Jenkins pipeline. As such some packages needs to be installed like Jenkins, AWS CLI, Kubernetes, and Terraform via the User data section of the EC2. The installation is accomplished automatically upon setup of the EC2.  

Grab the public ip of the newly created jenkins server and access the it via the browser at port 8080 (i.e 54.166.141.156:8080). 808ethen sign into the jenkins application using the passord retrieved from the server’s etc/... location. By this you need to connect (SSH) to the server. 

Now you can start using the jenkins. First is to create new item (or job). 

The credentials for the AWS environment can be stored as environmental variables in the credentials section of the jenkins. Here we store the access key, and secret key. 

Continue with the job and enter the required script, pointing the URL to the Git URL where the code files reside. 

The script for the Jenkinsfile has stages for each terraform command: terraform init, terraform validate, terraform plan and terraform apply. The apply and destroy commands are passed as choices in parameterised section of the build job. 

The job takes about 15mins to run, creating 62 resources that can be confirmed via the console. 

This automated approach to provisioning an EKS cluster using Jenkins pipeline makes it easy for teams to seamlessly build and deploy various orchestration environments while making changes to the containers, and images with code files versions controlled from GitHub. 

  
 
