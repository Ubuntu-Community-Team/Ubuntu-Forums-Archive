---
title: "Switching between ethernet ports"
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by technocp on 2012-04-12
I have two ehthernet ports on my system
But I have only one Lan cable which I connect to either of ports whenever needed.
I am using Ubuntu 10.04 SERVER edition
where network interfaces are driven by /etc/network/interfaces
I have configured both eth0 and eth1 to different static addresses
it works fine

But the problem is that when I disconnect my Lan cable from eth0 and connect it to eth1, I have to ifdown eth0. Only then I can connect to the network using eth1.

I have read about hotplug, 85-ifupdown.rules, but I am not able to convert it into a solution to my problem

I want either ifdown to take place automatically when ever the lan cable is disconnected from eth0/eth1. OR I want my system to easily recognise on which port the Lan cable is connected and start using my network resources through that port and interface.

Is it possible to work in that way. If yes can you guide me with steps to follow.

---

