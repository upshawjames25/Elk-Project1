## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Elkstack Diagram](https://github.com/upshawjames25/Elk-Project1/blob/main/Diagrams/HW%20Diagram.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  -[Ansible Playbook] (https://github.com/upshawjames25/Elk-Project1/tree/main/Ansible)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- _TODO: What aspect of security do load balancers protect?
It helps prevent overloading servers as well as optimizes productivity and maximizes uptime.
It also adds resiliency by rerouting live traffic from one server to another causing it to eliminate single points of failure from attacks such as DDoS attack. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
- _TODO: What does Filebeat watch for?_Filebeat watches for any information in the file system which has been changed and when it has.
- _TODO: What does Metricbeat record?_It records metrics/statistics data and transports them to the output that you specifics thru Elasticsearch/Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
|ELKVM1    |server    | 10.0.0.4   | Linux            |
|Web-1     |server    | 10.0.0.5   | Linux            |
|Web-2     |server    | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_

Machines within the network can only be accessed by the Jump-Box-Provisioner.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
 Jump-Box-Provisioner/10.0.0.4
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.4 10.0.0.2    |
| ELKVM1   |  no                 | 10.0.0.4             |
| Web-1    |  no                 | 10.0.0.5             |
| Web-2    |  no                 | 10.0.0.6             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
One main advantage would be YAML Playbooks. It is the best alternative for configuration management/automation.
It is also able to automate complex multi-tier IT application environements.
The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
First I, SSH into the Jump-Box-Provisioner (ssh redadmin@40.117.224.154)
Start/Attached to the ansible docker (sudo docker start tender_morse)/(sudo docker attach tender_morse)
Went to /etc/ansible/roles directory and created the ELK playbook (Elk_Playbook.yml)
Ran the Elk_Playbook.yml in that same directory (ansible-playbook Elk_Playbook.yml)
Lastly, I SSH into the ELK-VM to verify the server is up and running.
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)
ELK-VM Docker PS
### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
Web-1 
Web-2 
We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the metricbeat-configuration.yml file to /etc/ansible/roles/files.
- Update the metricbeat-configuration.yml file to include include the ELK private IP in lines 62 and 96
- Run the playbook, and navigate to http://40.122.233.230:5601/ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? filebeat-playbook.yml Where do you copy it? /etc/ansible/roles
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?http: //40.122.233.230:5601/

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._