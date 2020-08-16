## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagram:https://github.com/roland2020-rc/ProjectElkServe/blob/master/Diagram%20of%20the%20cloud.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the file may be used to install only certain pieces of it, such as Filebeat.

Playbook files

-https://github.com/roland2020-rc/ProjectElkServe/blob/master/Configuration/yml%20files/filebeat_configuration.txt
-https://github.com/roland2020-rc/ProjectElkServe/blob/master/Configuration/yml%20files/filebeat_playbook_yml.txt
-https://github.com/roland2020-rc/ProjectElkServe/blob/master/Configuration/yml%20files/host_yml.txt
-https://github.com/roland2020-rc/ProjectElkServe/blob/master/Configuration/yml%20files/install_elk_playbook.txt

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box? The load balancer protects against DDOS attacks or overloaded servers crashing.
The advantage of a jump box is to limit the attack surface for bad actors and limitng different methods from getting into the system

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system file.
- _TODO: What does Filebeat watch for? The filebeat watches any changes to files, logs and sends them to the correct person/place
- _TODO: What does Metricbeat record? The metricbeat record server system metrics for docker and othe modules

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address   | Operating System |
|----------|----------|--------------|------------------|
| Jump Box | Gateway  |52.246.248.84 | Linux            |
| ElkSever | Logging  |52.143.119.223| Linux            |
| DVWA-VM1 | test envi|52.223.79.138 | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-73.73.247.210

Machines within the network can only be accessed by Jump Box.
- Jumpbox: 52.246.248.84 and my IP address:73.73.247.210

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 |   73.73.247.210      |
| ElkSever | No                  |   10.0.0.8           |
| DVWA-VM1 | No                  |   10.0.0.5           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible? The advanatage of automate configuration with ansible are accuracy, speed, easy, and automates a web developer jobs.

The playbook implements the following tasks:
- Download and install docker
- Download and Install python-pip
- Download and Install Docker module
- Incrase Virtual memory
- Download and launch a docker elk container with image:sebp/elk
- Ports that Elk runs on 5601:5601, 9200:9200, 5044:5044


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/roland2020-rc/ProjectElkServe/blob/master/Screenshots/starting_the_elk_server_in_the_elk_vm.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- DVWA-VM1 

We have installed the following Beats on these machines:
- ElkServer, Jumpbox, and the DVWA-VM1

These Beats allow us to collect the following information from each machine:
- File and metric beat are modeule thatcollect, parsing, and visualizing information from data sources likewise the cloud platform, containers and systems. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible container.
- Update the playbook file to include the correct configuration
- Run the playbook, and navigate to ansible hosts to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? install_elk_playbook and filebeat_playbook. and its in the /etc/ansible/
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? The ansible host file with the specify by private IP address.
- _Which URL do you navigate to in order to check that the ELK server is running? 52.143.119.223:5601

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._