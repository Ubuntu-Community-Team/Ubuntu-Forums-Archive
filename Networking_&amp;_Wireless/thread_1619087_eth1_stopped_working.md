---
title: "eth1 stopped working"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by aerende on 2010-11-11
After a reboot, my eth1 no longer has a 192.168.0.? inet address and so I cannot connect to the Internet.  Instead it has "inet addr:10.0.0.6".

I am using Ubuntu within VMWare on a Mac and the Mac is connected to a router using DHCP to deliver IP addresses to the computers behind the router/firewall.  I've tried:

1)  "/etc/init.d/networking restart -now" and I get

     DHCPOFFER from 192.168.0.1
     DHCPREQUEST on eth1 to 255.255.255.255 port 67
     ip length 272 disagrees with bytes received 534

Could this length mismatch be the problem?

---

### Post by aerende on 2010-11-11
After doing

1)  ifdown eth1
2)  ifup eth1

a number of times, eth1 works now!  Hmm...   Oh, well.

---

