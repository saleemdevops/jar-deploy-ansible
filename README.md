# War file Deployment using nginx

This template shows an example of ansible playbook how to build and deploy a war file
This also takes care of installing all required software stack if its a fresh new machine

## Setup
Perform the following steps in order to setup ansible machine

Step | Command                    | Description
:--: | -------------------------- | ---------------
1.   | OS                         | CentOS 7
2.   | Download EPEL Repository   | wget http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-8.noarch.rpm
3.   | Enable rpm of EPEL         | rpm -ivh epel-release-7-8.noarch.rpm
4.   | Install Ansible            | sudo yum install ansible -y
5.   | Test Version               | ansible --version  (Tested with : 2.2.0.0)

## Configurations
Clone the deployment repository and do the following changes before running the ansible-playbook

    git clone https://github.com/naggappan/jar-deploy.git

## Environment: Production run
    
    vim production/group_vars/all/vars_file.yml   --> modify domain name / Load balancer's IP and required parms
    vim production/group_vars/all/vars_credentials.yml   --> DB password and jwt key "if required you can use ansible vault to encrypt / decrypt"
    vim production/inventory --> provide IP address of all servers

## RUN
Following command is used to start the deployment process, This will install all required dependencies.
    
    cd jar-deploy
    ansible-playbook -i production webservers.yml -vv 
