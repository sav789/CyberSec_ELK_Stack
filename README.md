## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/diagram_filename.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-playbook.yml
  - metricbeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure, in addition to restricting access to the network.
- Load balancers protects the system from DDoS attacks by shifting attack traffic. 
- The advantage of a jump box is to give access to the user from a single node that can be secured and monitored 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- Filebeat watches for any information in the file system which has been changed and when it has.
- Metricbeat takes the metrics and statistics that collects and ships them to the output you specify
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Server   | 10.0.0.7   | Linux            |
| Web-2    | Server   | 10.0.0.6   | Linux            |
| Elk-VM   | Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Public IP address from home

Machines within the network can only be accessed by _____.
- Jump Box VM: IP 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Home IP              |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| Elk-VM   | No                  | 10.0.0.4             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Advantage is that you can put commands into multiple servers from a single playbook

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install: docker.io
  Install: python-pip
  Install: docker
  Command: sysctl -w vm.max_map_count=262144
  Launch docker container: elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/project_1_firstDay_screenshot.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 IP: 10.0.0.7
- Web-2 IP: 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat and metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
	-Metricbeat monitors servers by collecting metrics like CPU or memory or data related to services running on a server. Filebeat monitors the log files or locations specified, and collecting log events for indexing. ex: use the metricbeat dashboard to see what kind of Operating systems or the systems country location that are accessessing a server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
	- /etc/ansible/file/filebeat-configuration.yml

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
	- edit the /etc/ansible/host file to add webserver/elkserver ip addresses

- _Which URL do you navigate to in order to check that the ELK server is running?
	- www.publicip:5601 (Kibana)
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._