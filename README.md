# SpringBootInMinikubeWithCofigMap
start minikube in windows
prerequisites
1. Install kubectl
2.Install Minikube
3.Install Docker 
4.Enable Hypro Visor in Bios and Search Turn Windows features on or off and  check Hyper-V


minikube start --vm-driver=hyperv  --v=7 --alsologtostderr
minikube dashboard  --v=7 --alsologtostderr


create one java code and create the image


set docker  repository for minikube cluster with the following commands otherwise we will not able to see the image  which referred in yaml file , repository will be different . Once you run the following command you can see the images from power shell  
 minikube docker-env 
 minikube docker-env | Invoke-Expression

Create the image now 
docker build . --tag=demo-front:latest --rm=true

 // create config map
  kubectl edit -f variable.yaml
 
 
deploy  yaml in minikube
  kubectl delete deployment demo-front
  kubectl delete service demo-front
  kubectl create -f frontend-deployment.yaml --v=7 --alsologtostderr
 


get the env variable list after deployment 

kubectl get pods

kubectl exec demo-front-855f5fcff9-7fpd7 -xsvnb env

