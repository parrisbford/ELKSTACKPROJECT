# ELKSTACKPROJECT
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram] https://app.diagrams.net/#G1EMEX0-gtbxYJHh7IefmNrZ47zNCuDIAq

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  ### TODO: Enter the playbook file. 
  install-elk.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
### TODO: What aspect of security do load balancers protect? What is the advantage of a jump box? 
Defending against DDoS attacks, by restricting traffic. 
They provide network security to one specific location that must be connected to prior to launching any services. 


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the vulnerable VMS and system metrics.
### TODO: What does Filebeat watch for? 
It monitors log files.
### TODO: What does Metricbeat record?
Metrics from the server and OS.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| TODO     | SERVER   | 10.0.0.5   | Linux            |
| TODO     | SERVER   | 10.0.0.7   | Linux            |
| TODO     | SERVER   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jummpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 69.222.144.126-HOME IP 

Machines within the network can only be accessed by jumpbox provisioner.
### TODO: Which machine did you allow to access your ELK VM? What was its IP address?
The ansible container. 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |  Yes                | 69.222.144.126       |
| WEB1     |  NO                 | 10.0.0.4             |
| WEB2     |  NO                 | 10.0.0.4             |
| ELKVM    |  NO                 | 69.222.144.126, 10.0.0.4 |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
### TODO: What is the main advantage of automating configuration with Ansible? 
You can orchestrate the entire app environment no matter where it is deployed,using a single playbook. 



The playbook implements the following tasks:
### TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- install docker.io
- install python-pip
- install docker container
-launch docker contain: elk


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

AZUREUSER@ELKVM:~$ sudo docker ps


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
### TODO: List the IP addresses of the machines you are monitoring.
WEB1- 10.0.0.5
WEB2- 10.0.0.7


We have installed the following Beats on these machines:
### TODO: Specify which Beats you successfully installed. 
filebeat. 

These Beats allow us to collect the following information from each machine:
### TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
Filebeat monitors specified log files or locations, and forwards them to Elasticsearch for indexing.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to ansible folder.
- Update the host file to include:
[webservers]
#alpha.example.org
#beta.example.org
#192.168.1.100
#192.168.1.110
10.0.0.5 ansible_python_interpreter=/usr/bin/python3
10.0.0.7 ansible_python_interpreter=/usr/bin/python3

[elk]
10.1.0.4 ansible_python_interpreter=/usr/bin/python3


- Run the playbook, and navigate to ElkVm_ to check that the installation worked as expected.

### TODO: Answer the following questions to fill in the blanks:
- _Which file is the playbook? Where do you copy it? nano install-elk.yml, inside of the /etc/ansible folder. 
- _Which file do you update to make Ansible run the playbook on a specific machine? /etc/ansible/install-elk.yml. 
- How do I specify which machine to install the ELK server on versus which to install Filebeat on? Within the configuration file. 
- _Which URL do you navigate to in order to check that the ELK server is running? http://52.173.17.95:5601/app/kibana#/home/tutorial/systemLogs


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
ansible-playbook (your playbook name).yml

