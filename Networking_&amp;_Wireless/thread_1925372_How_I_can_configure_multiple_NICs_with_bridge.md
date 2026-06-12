---
title: "How I can configure multiple NICs with bridge"
date: 2012-02-14
forum: Networking &amp; Wireless
---

### Post by YesGood on 2012-02-14
Hello everybody!!

Please, Help me.:(

I need configure the host machine with two network interface eth0 and eth1. I use the bridge for both interfaces, but for some reason, is not worked.  This is my  archive /etc/network/interfaces

auto eth1 
iface eth1 inet manual 

auto br1  
iface br1 inet static 
address 192.168.1.17 
network 192.168.1.0 
netmask 255.255.255.0 
broadcast 192.168.1.255 
bridge_ports eth1 
bridge_stp off 
bridge_fd 0 
bridge_maxwait 0 

auto eth0 
iface eth0 inet manual 

auto br0  
iface br0 inet static 
address 192.168.1.16 
network 192.168.1.0 
netmask 255.255.255.0 
broadcast 192.168.1.255 
gateway 192.168.1.1 
bridge_ports eth0 
bridge_stp off 
bridge_fd 0 
bridge_maxwait 0 

With this configuration do not connect to the internet

---

### Post by drdos2006 on 2012-02-14
Check these threads out, they may help.

[http://ubuntuforums.org/showthread.php?t=1719190](http://ubuntuforums.org/showthread.php?t=1719190)
[http://ubuntuforums.org/showthread.php?p=11320085#post11320085](http://ubuntuforums.org/showthread.php?p=11320085#post11320085)

regards

---

### Post by YesGood on 2012-02-14
Thanks for answers.

I visit the links you post me.
But I do not have the similar enviroment.

I have configuring two interfaces eth0-> br0 , eth1-> br1 and in the NetworkManager only appear eth1, and the eth0 do not appear. 

So I dont have access in the internet.

How I see if the firewall is the problem? or What is my error?

---

