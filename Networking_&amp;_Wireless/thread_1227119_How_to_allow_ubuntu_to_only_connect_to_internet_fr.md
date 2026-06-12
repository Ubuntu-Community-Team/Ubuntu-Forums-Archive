---
title: "How to allow ubuntu to only connect to internet from eth0"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by kameelperdza on 2009-07-30
I have 2 nic's in my ubuntu server. My interface file looks like this
 
[SIZE=1]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.53
netmask 255.255.255.0
gateway 192.168.0.2
auto eth0:1 
iface eth0:1 inet static
address 192.168.0.54
netmask 255.255.255.0
gateway 192.168.0.2
auto eth1
iface eth1 inet static
address 192.168.8.16
netmask 255.255.255.0
gateway 192.168.8.1
auto eth1:1 
iface eth1:1 inet static
address 192.168.8.17
netmask 255.255.255.0
gateway 192.168.8.1
 
When i try to update my ubuntu by pressing apt-get update then ubuntu tries to look on 192.168.8.17, and if 192.168.0.17 is unavailable then  the update fail.
 
But when the i type apt-get upgrade the it use 192.168.0.54 to upgrade.
What i want to do is allow only eth0(192.168.0.54 & 192.168.0.53) to connect to the  internet. eth1 is only used for local. 
 
Can someone tell me what to do?
 
 
[/SIZE]

---

