---
title: "Non-local network traffic not being ACKed?!?"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by john3exonets on 2011-06-16
I can't find anything about this in the archives..but then again, my google foo is low this week ;)

I have a number of Ubuntu 11.04 servers running inside a VMware ESX/i server.  They each have at least three different interfaces (eth0, eth1, eth2, etc.). Each interface is on a different subnet (192.168.1.0, 192.168.2.0, 192.168.3.0 ,etc.) I have a number of client PCs outside on a 192.168.4.0 subnet. The Ubuntu servers are each set with one gateway (192.168.1.1), and the external PCs all use that to talk to the VM servers for maintenance work.  

When I try to connect to the VM Ubuntu servers on any of the other two interfaces from the outside PCs, nothing comes back.  I have confirmed that the traffic *does* reach the servers on those other interfaces, but nothing ever gets responded to...no ACKs, no ICMP...nothing.  I can make connections from one VM Ubuntu server to another on these other interfaces just fine, but they are on the local subnet too. Its when it has to respond back to a pc that is not on the local subnet, where the route back is out another interface that it doesn't seem to respond.

Is there something I need to change so it will respond back??

Thanks!

---

