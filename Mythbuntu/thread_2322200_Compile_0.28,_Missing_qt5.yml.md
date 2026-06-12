---
title: "Compile 0.28, Missing qt5.yml?"
date: 2016-04-26
forum: Mythbuntu
---

### Post by gga96 on 2016-04-26
I am trying to download and compile 0.28.
Running ansible fails, because I think file qt5.yml is missing from my system.

Setup:    MythBuntu 14.04
    Qt 5.6.0
    Mythtv .27
    Using Reference [https://www.mythtv.org/wiki/Build_from_Source](https://www.mythtv.org/wiki/Build_from_Source)  version 0.28"    

For installing dependencies I am using the ansible option.

This is what I did:
> 
glen@backend1:~$ git clone [https://github.com/MythTV/ansible](https://github.com/MythTV/ansible)
Cloning into 'ansible'...
remote: Counting objects: 316, done.
remote: Total 316 (delta 0), reused 0 (delta 0), pack-reused 316
Receiving objects: 100% (316/316), 36.93 KiB | 0 bytes/s, done.
Resolving deltas: 100% (151/151), done.
Checking connectivity... done.

> 
glen@backend1:~$ sudo apt-get install ansible
[sudo] password for glen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libyaml-0-2 python-jinja2 python-markupsafe python-yaml
Suggested packages:
  ansible-doc sshpass python-jinja2-doc
The following NEW packages will be installed:
  ansible libyaml-0-2 python-jinja2 python-markupsafe python-yaml
0 upgraded, 5 newly installed, 0 to remove and 1 not upgraded.
Need to get 743 kB of archives.
After this operation, 4,487 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libyaml-0-2 amd64 0.1.4-3ubuntu3.1 [48.1 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main python-yaml amd64 3.10-4ubuntu0.1 [102 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main python-markupsafe amd64 0.18-1build2 [14.3 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main python-jinja2 all 2.7.2-2 [161 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe ansible all 1.5.4+dfsg-1 [418 kB]
Fetched 743 kB in 13s (54.7 kB/s)                                              
Selecting previously unselected package libyaml-0-2:amd64.
(Reading database ... 404006 files and directories currently installed.)
Preparing to unpack .../libyaml-0-2_0.1.4-3ubuntu3.1_amd64.deb ...
Unpacking libyaml-0-2:amd64 (0.1.4-3ubuntu3.1) ...
Selecting previously unselected package python-yaml.
Preparing to unpack .../python-yaml_3.10-4ubuntu0.1_amd64.deb ...
Unpacking python-yaml (3.10-4ubuntu0.1) ...
Selecting previously unselected package python-markupsafe.
Preparing to unpack .../python-markupsafe_0.18-1build2_amd64.deb ...
Unpacking python-markupsafe (0.18-1build2) ...
Selecting previously unselected package python-jinja2.
Preparing to unpack .../python-jinja2_2.7.2-2_all.deb ...
Unpacking python-jinja2 (2.7.2-2) ...
Selecting previously unselected package ansible.
Preparing to unpack .../ansible_1.5.4+dfsg-1_all.deb ...
Unpacking ansible (1.5.4+dfsg-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libyaml-0-2:amd64 (0.1.4-3ubuntu3.1) ...
Setting up python-yaml (3.10-4ubuntu0.1) ...
Setting up python-markupsafe (0.18-1build2) ...
Setting up python-jinja2 (2.7.2-2) ...
Setting up ansible (1.5.4+dfsg-1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...

And then:
> 
glen@backend1:~$ ansible-playbook -i hosts qt5.yml
ERROR: Unable to find an inventory file, specify one with -i ?


The qt5.yml file is not on my system?

What have I done wrong?
How do I fix the problem?

Thanks for your help.

Cheers 
Glen

---

### Post by clueo8 on 2016-04-28
It appears you are running this command from your home directory (~) but you should cd into the ansible directory and then try running the ansible-playbook command.  The qt5.yml file should be in the ~/ansible directory.

---

### Post by gga96 on 2016-04-28
Yes I was in my home directory.
> 
glen@backend1:~$ cd ~/ansible
glen@backend1:~/ansible$ ansible-playbook -i hosts qt5.yml
ERROR: dnf is not a legal parameter in an Ansible task or handler

This seems an odd error. The following is a copy of ~/ansible/qt5.yml and appears to agree with the GitHub file.
> 
# Master playbook

- hosts:        localhost
  roles:
    - { role: mythtv-deb, when:  ansible_pkg_mgr == "apt" }
    - { role: mythtv-rpm, when:  ansible_pkg_mgr == "yum" }
    - { role: mythtv-dnf, when:  ansible_pkg_mgr == "dnf" }
    - { role: mythtv-freebsd, when: ansible_pkg_mgr == "pkgng" }
    - role: qt5

Any thoughts

---

### Post by clueo8 on 2016-04-28
I got that error before too and read somewhere (cant find where) to just remove any references to 'dnf' in this file as well as any other files that are used as you just need to use 'apt' to install the dependencies.

---

