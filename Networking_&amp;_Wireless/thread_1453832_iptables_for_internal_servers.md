---
title: "iptables for internal servers"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by joffre.yc on 2010-04-13
I have Ubuntu installed in my machine, CentOS as a guest in a virtual machine. CentOS and Ubuntu are in the local network 192.168.5.0/24, vmnet1 logical interface is used for Ubuntu for this purpose. On the other hand Ubuntu has internet connectivity throught physical interface eth0 with a public IP.

For academic purpose, I have set up some services, for example ssh server on centOS, it works locally.
Now I want outside connection requests to be accepted by Ubuntu in the eth0 and routed throught vmnet1 to centOS server, I want to do it with iptables on Ubuntu so I wonder if someone could help me with the iptables configuration.

Thanks for your help, and sorry for my english.

Joffre

---

