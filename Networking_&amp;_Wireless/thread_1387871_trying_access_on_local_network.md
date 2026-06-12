---
title: "trying access on local network"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by soropi on 2010-01-22
hello ,
I'm a new user of Xubuntu 9.10 on a PIII pc and trying to connect , using the same router, to other pc's which running both  Ubuntu 9.10 and Win XP.
Using Gigolo a can connect to other pc's but cannot open remote files because the Thynar-xfce manager doesn't work with it. I found some help here :[www.uvena.de/gigolo/help.html]("http://ubuntuforums.org/www.uvena.de/gigolo/help.html") 
but isn't clear if it works in Xubuntu.  Any ideas which applications should I use ? Thanks.

---

### Post by Dennis N on 2010-01-22
You can install Filezilla on the Xubuntu machine and log onto the other Linux machines with an SSH connection. This will allow you to easily transfer files to and from the other machines. All you need is the IP address of the other machines.

The machines you want to connect to must have the package openssh-server installed before you can connect.

---

### Post by soropi on 2010-01-25
Thank you for your response
Although I installed FileZilla on Xubuntu machine which worked ok and I can see everything on my Pc I didn't manage to connect with anything else.
I followed instructions about ssh connection but nothing.Perhaps I should have FileZilla also in other Pc's ?Could this method be ok in connecting with a Pc working on Windows?
Thanks in advance.

---

### Post by soropi on 2010-01-25
Some additional info if can be useful:
1) I can connect the Xubuntu pc to other using Ubuntu using the "Remote Desktop Viewer " Application on ssh protocol , but it's just like having a terminal on the remote pc.
2) Using "openssh server" other pc on Ubuntu can communicate with another Windows pc but is not possible to "see" the Xubuntu one.

---

