---
title: "How to set NIC priority?"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by kynov on 2010-09-08
Hey all,

I have two nic's in my work PC running 10.04 32-bit desktop.  Eth0 and eth1 are both connected to the same LAN using static IPs.  Now, this works fine until I use eth1 for its intended purpose which is using it to monitor the network.  The port on the switch it is connected to is setup as a Cisco SPAN port.  Everytime the SPAN session is setup, I lose connectivity to the LAN as it appears to be prioritizing traffic to eth1.  I tried the only command I could find about setting the metric of the iface which is--

sudo ifconfig eth1 inet metric 10

When I run that, I get an error stating SIOCSIFMETRIC: Operation not supported. 

Anyone know what I am missing???

Thanks!

---

