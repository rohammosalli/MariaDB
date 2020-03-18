###### Deploy MariaDB with Ansible with Automated backup with bash
=========

An Ansible playbook to privision MariaDB on CentOS distros.

Requirements
------------

- Python installed -> ` yum install python -y `
- Proper Internet acess to install packages and repositories
- An admin access (sudo) to the server.
- copy you ssh-public-key to the server for sure 

##### values
if you want to change values you have to decrypt with a password and again please encrypt with ansible-vault the test password is ```amiramir```

--------------
```bash
ansible-vault encrypt mariadb/vars/private.yml

ansible-vault decrypt mariadb/vars/private.yml
```
or you want to view the file just use this 

```bash
ansible-vault view mariadb/vars/private.yml
```

for the edit use this one
```bash
ansible-vault edit mariadb/vars/private.yml
```
----------------


##### deploy 

if you wand to just deploy it please use this 

```bash
ansible-playbook -i host.ini -b  main.yml --ask-vault-pass -K 
```

to tun in dry-run pelase use this option --check

use -K if you are sudoer user and if you use root user it's not erequired 

and if you want to select you database name on backup script please chage this variable DATABASE_NAME on this path ```files/backup.sh```