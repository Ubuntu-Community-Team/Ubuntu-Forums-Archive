---
title: "Ubuntu Server 12.04.2 LTS. Internet sharing with three network cards !"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by heming on 2013-06-15
Hello from Bulgaria. Excuse me for my bad English. I am a novice with Ubuntu. Before that time I used Slackware. Here's my question:
Ubuntu Server 12.04.2 LTS + with three network card + twisted pair cables 
I want to share my internet (Eth0) to the other two cards **(eth1)** **(eth2)** connected to two machines **(Windows7,WindowsXP)**


**eth0** (ISP Internet network) 
IP: 10.34.2.115
Netmask: 255.255.255.0
Gateway: 10.34.2.1
DNS: 10.34.2.1


**eth1**
IP: 192.168.1.1
Netmask: 255.255.255.0


**eth2**
IP: 192.168.2.1
Netmask: 255.255.255.0


In Slackware using the following command in rc.loca:
```
iptables -t nat -A POSTROUTING -s 192.168.1.2 -j MASQUERADE
iptables -t nat -A POSTROUTING -s 192.168.2.2 -j MASQUERADE
``` 


Result, the two (Windows) machines have internet at the following addresses:
**(windows7)**
IP: 192.168.1.2
Netmask: 255.255.255.0
Gateway: 192.168.1.1
DNS: 192.168.1.1


**(windowsXP)**
IP: 192.168.2.2
Netmask: 255.255.255.0
Gateway: 192.168.2.1
DNS: 192.168.2.1


**How can I do this with ubuntu server ?**

---

### Post by Cheesemill on 2013-06-15
The iptables commands you posted are the same for Ubuntu as they are for Slackware.

You also need to enable forwarding in the kernel by editing the /etc/sysctl.conf file and uncommenting the **[COLOR=#ff0000]net.ipv4.ip_forward=1[/COLOR]** line.

This setting requires a reboot before it takes effect, if you want to make the change effective without a reboot then run the command...
```
sudo sysctl -w net.ipv4.ip_forward=1
```

---

### Post by heming on 2013-06-15
I do not remember if it's done right. I tried exceedingly. I'll try again.
Thanks.

---

