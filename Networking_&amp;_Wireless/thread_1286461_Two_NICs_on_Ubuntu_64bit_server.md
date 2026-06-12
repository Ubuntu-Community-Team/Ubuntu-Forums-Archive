---
title: "Two NICs on Ubuntu 64bit server"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by brukutu on 2009-10-09
Hi.
This isnt really ubuntu specific but i need to know if lets says i got two NICs on my server namely eth0 and eth1. Here are the settings
eth0 ip 192.168.1.1
eth1 ip 192.168.100.1


I got one big network, now i have specific devices on that network (running of a differnt ip range) that i dont want to be avaiable to the other users of the network who get the IP from a DHCP server runing on a router, like 192.168.1.x

Now my question is. 
Can i connected both of those NICs into the same switch?

---

### Post by houstonbofh on 2009-10-09
Yes.  It is called multinetting.  It can impact performance significantly and it is not very secure.

Get a v-lan switch, and it gets much better.

---

