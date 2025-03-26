## How to Set Up Essential DevOps Tools on Ubuntu/Linux: A Complete Guide

DevOps tools are crucial for automating software development, deployment, and infrastructure management. Below is a step-by-step guide on how to install some of the most essential DevOps tools on Ubuntu/Linux.

Learn how to set up essential DevOps tools on Ubuntu/Linux for automation, CI/CD, and cloud management. This guide covers installing Docker, Kubernetes, Terraform, Ansible, AWS CLI, Prometheus, Grafana, and more to streamline development and deployment workflows. Perfect for DevOps engineers looking to optimize their infrastructure and software delivery. 🚀


## Prerequisites
1. A system running Ubuntu 20.04 or later.
2. A user with sudo privileges.
3. Basic knowledge of the Linux command line.
4. Internet connectivity.

### Update System Packages
Before installing any tools, ensure your system is up-to-date:
```bash
sudo apt update && sudo apt upgrade -y
```

## 1. Install AWS CLI
The AWS Command Line Interface (CLI) allows you to interact with AWS services directly from your terminal, enabling automation and scripting for cloud resource management.

Steps:
1. Download the AWS CLI installer:
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

2. Install unzip if not already installed :
```bash
sudo apt install -y unzip
```

3. Unzip the installer:
```bash
unzip awscliv2.zip
```

4. Run the installer:
```bash
sudo ./aws/install
```

5. Verify the installation:
```bash
aws --version
```

6. Configure AWS CLI:
```bash
aws configure
```
Enter the following details:
- AWS Access Key ID
- AWS Secret Access Key
- Default region
- Default output format (e.g., JSON)

### Steps to Retrieve AWS Access Key ID and Secret Access Key
To use the AWS CLI, you need an Access Key ID and Secret Access Key. Follow these steps to retrieve them:

#### 1. Step 1: Sign in to AWS Management Console
  - Go to the AWS Management Console:
    👉 https://aws.amazon.com/console/
  - Sign in with your root or IAM user credentials.

#### 2. Step 2: Navigate to IAM (Identity and Access Management)
- In the AWS Console, search for IAM in the search bar.
- Click on IAM to open the Identity and Access Management service.

#### 3. Step 3: Create or Retrieve Access Keys
For an Existing IAM User:
- In the IAM Dashboard, click Users (on the left sidebar).
- Select the username for which you need access keys.
- Go to the Security credentials tab.
- Scroll down to the Access keys section.
- If you already have an access key, you can use it. If not, click Create access key.

#### For a New IAM User (If No User Exists):
- Go to Users → Click Add users.
- Enter a username and select Access key - Programmatic access.
- Assign appropriate permissions (e.g., AdministratorAccess or custom policies).
- Click Next, then Create user.
- After creation, download the .csv file with the Access Key ID and Secret Access Key.

#### 4. Step 4: Store the Access Keys Securely
- Copy the Access Key ID and Secret Access Key.
- You won't be able to view the Secret Access Key again after this step.
- Store them in a secure location like AWS Secrets Manager or a password manager.



## 2. Install Jenkins
Jenkins is a CI/CD automation server.

1. First Install JAVA on instance using :
```bash
sudo apt install openjdk-17-jdk
```

2. To test if Java has been installed successfully, run this command:
```bash
java -version
```

3. Install dependencies:
```bash
sudo sudo apt-get update
```

4. Add the Jenkins repository key:
```bash
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
```

5. Add Jenkins to APT sources:
```bash
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
```

6. Install Jenkins:
```bash
sudo apt-get update sudo apt-get install jenkins -y
```

7. Enable Jenkins to start on boot:
```bash
sudo systemctl enable jenkins && sudo systemctl start jenkins
```

8. Verify Jenkins status:
```bash
sudo systemctl status jenkins
```

9. Access Jenkins: Open a browser and navigate to http://<your-ip>:8080. Use the password located in /var/lib/jenkins/secrets/initialAdminPassword.


## 3. Install Docker
Docker helps in containerization, making applications portable and scalable.

1. Update the package index:
```bash
sudo apt update && sudo apt upgrade -y
```

2. Install dependencies:
```bash
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```

3. Add Docker’s official GPG key:
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

4. Set up the Docker repository:
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

5. Install Docker:
```bash
sudo apt update sudo apt install -y docker-ce docker-ce-cli containerd.io
```

6. Verify the installation:
```bash
docker --version
```

7. Enable Docker to start on boot:
```bash
sudo systemctl enable docker
```

8. Run Docker without sudo (optional):
```bash
sudo usermod -aG docker $USER newgrp docker 
or
sudo chown $USER /var/run/docker.sock
```

9. Test Docker Commands 
```bash
docker ps
```

## 4. Install Terraform
Terraform is an Infrastructure as Code (IaC) tool.

1. Download the Terraform binary:
```bash
sudo apt update && sudo apt install -y gnupg software-properties-common curl
curl -fsSL https://releases.hashicorp.com/terraform/1.5.7/terraform_1.5.7_linux_amd64.zip -o terraform.zip
```

2. Install the unzip tool (if not installed):
```bash
sudo apt install -y unzip
```

3. Extract and move the binary:
```bash
unzip terraform.zip sudo mv terraform /usr/local/bin/
```

4. Verify installation:
```bash
terraform --version
```

## 5. Install Ansible
Ansible automates configuration management.

1. Install Ansible using the package manager:
```bash
sudo apt update && sudo apt install -y ansible
```

2. Verify installation:
```bash
ansible --version
```

## 6. Install Kubernetes 
GOTO this Link
```bash
https://github.com/vinayakz/kubernetes
```

## 7. Install Prometheus
Prometheus is a monitoring and alerting toolkit.

1. Download Prometheus:
```bash
wget https://github.com/prometheus/prometheus/releases/download/v2.50.0/prometheus-2.50.0.linux-amd64.tar.gz
```

2. Extract the archive:
```bash
tar -xvzf prometheus-2.50.0.linux-amd64.tar.gz cd prometheus-2.50.0.linux-amd64
```

3. Move binaries to /usr/local/bin:
```bash
sudo mv prometheus promtool /usr/local/bin/
```

4. Create a Prometheus config directory:
```bash
sudo mkdir /etc/prometheus sudo mv prometheus.yml /etc/prometheus/
```

5. Verify Prometheus installation:
```bash
prometheus --version
```

6. Start Prometheus:
```bash
prometheus --config.file=/etc/prometheus/prometheus.yml
```

## 8 Install Grafana
Grafana visualizes data collected by Prometheus.

1. Add Grafana’s repository:
```bash
sudo apt update sudo apt install -y software-properties-common wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add - echo "deb https://packages.grafana.com/oss/deb stable main" | sudo tee /etc/apt/sources.list.d/grafana.list
```

2. Install Grafana:
```bash
sudo apt update sudo apt install -y grafana
```

3. Start and enable Grafana:
```bash
sudo systemctl start grafana-server sudo systemctl enable grafana-server
```

4. Access Grafana: Open a browser and navigate to http://<your-ip>:3000. Use
```bash
default credentials (admin/admin).
```

## 9 Install Helm

### Prerequisites:
1. Ensure Kubernetes is running.
2. Helm requires a Kubernetes cluster running version 1.18+.
3. Install Kubectl as well
4. Verify your Kubernetes setup by running:
5. Ensure the cluster is accessible and kubectl is configured correctly:

Helm is a package manager for Kubernetes that helps deploy and manage applications using Helm charts. Follow these steps to install Helm on Ubuntu/Linux.

1. Get the Helm shell file:
```bash
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
```

2. Change permission and run shell file:
```bash
chmod 700 get_helm.sh ./get_helm.sh
```

3. Verify installation:
```bash
helm version
```


## Install ArgoCD:

1. Create the ArgoCD Namespace:
```bash
kubectl create ns argocd
```

2. Install ArgoCD: Apply the ArgoCD manifests to install it:
```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

3. Verify ArgoCD Installation: Check the pods in the ```bash argocd ``` namespace to ensure they are running:
```bash
kubectl get pods -n argocd
```

4. Accessing the ArgoCD UI: By default, the ArgoCD server is exposed as a ```bash ClusterIP ``` service. To access the UI:
- Option 1: Port Forwarding Forward the port to your local machine:
```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
Access the UI at: https://localhost:8080

- Option 2: Change Service to NodePort
Update the ArgoCD server service to NodePort:
```bash
kubectl edit svc argocd-server -n argocd
```

- Change type: ClusterIP to type: NodePort.
- Access ArgoCD at: http://<node-ip>:<node-port>


## Conclusion

Following these steps, you now have the essential DevOps tools installed on Ubuntu/Linux, allowing you to manage infrastructure, automate workflows, monitor applications, and deploy containerized applications efficiently.
