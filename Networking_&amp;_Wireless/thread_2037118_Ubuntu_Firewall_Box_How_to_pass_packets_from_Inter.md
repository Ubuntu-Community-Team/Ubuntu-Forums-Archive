---
title: "Ubuntu Firewall Box: How to pass packets from Internal Interface to External Interfac"
date: 2012-08-03
forum: Networking &amp; Wireless
---

### Post by duplex50 on 2012-08-03
Hello Again,

Everyone was extremely helpful on my last posts, so I am back again!
 
My Ubuntu 12 server has eth0 attached to dsl model and eth1 is attached to internal network via a switch.  I can now successfully talk internally through eth1 and externally to the internet via eth0.

I would like to know how I can start using eth1 as the default gateway for clients on my network.

eth0 is configured as 192.168.254.2 and eth1 is configured as 192.168.1.23.

I assume that packets are passed from 192.168.1.0 network to 192.168.254.0 network via IPTABLES.  I plan on using fwbuilder as my front-end for IPTABLES.  Before I start using this front end, I would like to make simple IPTABLES entries via command line so I can point my workstation to 192.168.1.23 as the gateway and connect out to the internet.  Once again, I just want to test connecting to the internet from my workstation (192.168.1.246) through eth1 on my server (192.168.1.23) out through eth0 (192.168.254.2) to the internet before implementing the front-end.
 
So:
Workstation (192.168.1.246) requesting [www.google.com]("http://www.google.com") -->via--> Firewall eth1 (192.168.1.23) -->via--> eth0 (192.168.254.2) -->via--> DSL modem (192.168.254.254).
 
What do I have to do to access the internet from my workstation through the Firewall?
 
Please let me now if any Output would assist.

Thank you all very much again!

---

### Post by duplex50 on 2012-08-03
I also want to set this up manually without using front-end GUI for learning purposes as well.  I want to understand what all is going no regarding the networking setup.
 
Thanks.

---

