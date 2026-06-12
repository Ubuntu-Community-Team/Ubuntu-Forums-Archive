---
title: "pci nic"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by maziar_bijari on 2010-11-02
[SIZE=5]hi ,i install ubuntu server 10 with one onboard nic and one pci dlink nic ,now i check and eth0 (onboard) is oky ,but i set ip in eth1 but i cant ping out of computer and also i cant ping my ubuntu from another computer ,i install ethtool with sudo apt-get install ethtool[/SIZE]
[SIZE=5]ethtool eth1 :it show ip with rx :86 packet ,it say link is up but i cant use this nic ,anyone can help me plz(im new in linux world)[/SIZE]

---

### Post by maziar_bijari on 2010-11-02
im still wating for help

---

### Post by grahammechanical on 2010-11-02
I am not sure that I understand what you are asking for. Do you want to use eth1 but you are not able to? I use the desktop edition of 10.10 not the server edition. I am hoping that I am hoping that the main difference between the two is that you have server type programs installed and I do not.

The message from ethtool is that eth1 is UP. It needs to also say RUNNING. Try right clicking on the network manager icon and selecting Edit Connections. Select Eth1, it might say Auto eth1, and click Edit. Then tick the box that says Connect automatically. 

Regards

---

