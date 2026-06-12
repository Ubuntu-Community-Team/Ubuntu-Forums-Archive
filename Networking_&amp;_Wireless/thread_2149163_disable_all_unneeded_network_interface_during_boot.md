---
title: "disable all unneeded network interface during boot"
date: 2013-05-27
forum: Networking &amp; Wireless
---

### Post by icoming on 2013-05-27
Hello,

I run Ubuntu server 12.04 LTS in my Dell server. The server has 4 network interfaces and 2 of them connect to network, but only one of them are used by the OS. The other interface is used by an independent component in the Dell server called iDRAC.

I only set up one interface eth0 in /etc/network/interfaces in Ubuntu. But the problem is that the other interface (eth1) is set up automatically somehow after the system boots, assigned with a private IP address (10.*.*.*), and a default gateway of the private subnet is added to the routing table, which prevents me from sshing to the machine. I have no idea what process does it.

I tried to disable eth1 in /etc/rc.local, but it doesn't work. 
ifconfig eth1 0.0.0.0
ifconfig eth1 down

What is going on here? Can anyone help me?
Thanks,
Da

---

