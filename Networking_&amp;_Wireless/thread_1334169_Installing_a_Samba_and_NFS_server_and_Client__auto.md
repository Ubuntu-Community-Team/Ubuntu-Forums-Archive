---
title: "Installing a Samba and NFS server and Client : automatic installers !"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by frenchn00b on 2009-11-22
Hey, 

you would like to forget all those nano and complicated things about Linux for installations:

You may use my [installer]("http://yellowprotoss.ye.funpic.org/website/ubuntuinstallers/ubuntu_server_logins.jpg") : 
Here guys I made what I want for the logins / password, as example (not instlling ldap), for samba and nfs:

```
  cd /tmp 
wget http://yellowprotoss.ye.funpic.org/website/ubuntuinstallers/ubuntu-samba-nfs-installer.sh
cat ubuntu-samba-nfs-installer.sh  
# in case: sudo apt-get install xdialog
sudo su 
sh ubuntu-samba-nfs-installer.sh  
```
 
 --
edit:
It is a beta version, and you have no warranties
The /etc/exports has to be verified by a geek. And if we are very lucky, he'll improve the scripts.

---

