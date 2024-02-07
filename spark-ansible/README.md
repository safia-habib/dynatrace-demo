# Dynatrace demo with Ansible to delete spark job through workflows
## 1. Deploy Minikube with AWX on Ec2 instance:

Use the guide [here](https://gist.github.com/dmccuk/93db22e9b30d1963b8fca0de96fc82f0) to setup a minikube environment with awx operator (Opensource ansible tower) 

## 2. Deploy Dynatrace on the Minikube cluster 
Use the official Dynatrace documentation to deploy Dynatrace Operator on the Minikube cluster 

## 3. Deploy Spark Operator on the Minikube Cluster
Follow the documentation [here](https://github.com/GoogleCloudPlatform/spark-on-k8s-operator) to create spark operator on the minikube cluster

## 4. Add the Playbook to Ansible 
Add Delete-Spark-Pod.yml to the AWX playbooks 

## 5. Create a Dynatrace workflow 
Trigger is Davis problem
Filter Query : event.name == "IllegalArgumentException-AWX-Remediation-Demo"
Action is to call the Ansible playbook (Create connection to the tower, add the Job ID from AWX console) 

## 6. Deploy the Spark resource that does not have enough resources 
Deploy the wrong-resource.yaml file on the minikube cluster using the following command: 

## 7. View the workflow in Dynatrace
On deployment of wrong resource file the Dynatrace workflow is executed which calls ansible and deploys the right resource. 


