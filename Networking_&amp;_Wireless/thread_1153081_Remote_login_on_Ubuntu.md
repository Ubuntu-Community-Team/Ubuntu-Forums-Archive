---
title: "Remote login on Ubuntu"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by linuxus95 on 2009-05-08
Hello and thanks for any support. I am currently running Jaunty on two computers joined together in a home network. I was wondering if there was a way to login as a remote user to one of my computers. Basically if i had an account called john on one of the computers, would there be a way to login remotely as john on the other one? Is there something like \\computer1\john which i could type in the username box and login remotely? Thanks for any help.

---

### Post by milton1 on 2009-05-08
The easiest, best way to do this is through the command line with ssh. you will need the ssh server running on the machine you want to log into.

```
sudo apt-get install openssh-server 
```
once this is done, you can log in to the computer with:
```
 ssh <username>@<remote_address> 
```
Adding the -X flag to the above command will give you the option of running graphical apps remaotely, as well.

---

### Post by superprash2003 on 2009-05-08
\\computer1\john - used for accessing files.. do you want to remote control the pc or access its files?

---

### Post by linuxus95 on 2009-05-09
Thanks for your help, mililtion. Although this works great, my idea is to login remotely from the login screen, meaning just type the username and password of a remote user into the login screen and basically login as him, just from a different computer. I was thinking of an equivalent of "Roaming Profiles" in a Windows environment. I apologize for my bad linux vocabulary, as I am used to the Windows environment and have only been running Ubuntu for a week or so.

---

### Post by superprash2003 on 2009-05-09
you could use system->pref->remote desktop to share.. and applications->internet->remote desktop viewer to view

---

