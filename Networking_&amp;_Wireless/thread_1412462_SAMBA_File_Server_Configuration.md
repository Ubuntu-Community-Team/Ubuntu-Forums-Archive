---
title: "SAMBA File Server Configuration"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by wiztstar on 2010-02-21
[SIZE=4]   [/SIZE][SIZE=3] I have a PC set up with Ubuntu 9.10 and Samba.  I have 2 network cards installed in this machine and I need to configure it so that one network card serves files to one Gateway while the other serves to an other.  My goal is to use Ubuntu as a bridge/firewall to keep the internet from passing through.  One network card will be connected to internet pc's running windows while the other will be hooked to windows pc's that cannot get on the net (to protect from viruses in the outside network.  [/SIZE]
[SIZE=3]Example: eth0=192.168.1.1 and the private ip= 10.108.0.1[/SIZE]
[SIZE=3]Can anyone point to so some configuration examples for a newbie.  [EMAIL="acannon@nextmediagroup.net"]acannon@nextmediagroup.net[/EMAIL][/SIZE]

---

### Post by johnson.d on 2010-02-22
Samba, By default, listens on all the interfaces that are connected. Hence no additional configuration is needed for Samba service to listen on multiple interfaces.

After starting Samba you can use the following command to check the interfaces it is listening on

$ netstat -tapn | grep smbd |grep LISTEN

For configuring Ubuntu system as a gateway you can refer the following document:

[http://newbiedoc.sourceforge.net/networking/homegateway.html](http://newbiedoc.sourceforge.net/networking/homegateway.html)

---

