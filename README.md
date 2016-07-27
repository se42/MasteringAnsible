# MasteringAnsible
Repository used during completion of Mastering Ansible course on Udemy

## Setup procedure for new fleet of Ubuntu 16.04 servers
### Adapted from: [Initial Server Setup with Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04)

1. as root:
  - apt-get update
  - apt-get upgrade
  - apt-get install software-properties-common
  - apt-add-repository ppa:ansible/ansible
  - apt-get update
  - apt-get install ansible
  - adduser ansible
  - usermod -aG sudo ansible
  - visudo and append 'ansible ALL=(ALL) NOPASSWD: ALL'
  - su - ansible
    - mkdir .ssh/
    - chmod 700 .ssh
    - nano .ssh/authorized_keys (TODO: add your MB_Pro .ssh/id_rsa.pub)
    - chmod 600 .ssh/authorized_keys
    - exit
  - nano /etc/ssh/sshd_config (TODO: PasswordAuthentication no)
  - systemctl reload sshd
  - test ssh login from local machine to ansible@ip
  - exit

1. as ansible:
  - mkdir ansible
  - cd ansible
  - git clone https://github.com/se42/MasteringAnsible.git .
  - TODO: develop playbook for further configuration of MA-CONTROL
  - TODO: develop playbook for creation of MA-<fleet> droplets with DO module (dynamic inventory?)
