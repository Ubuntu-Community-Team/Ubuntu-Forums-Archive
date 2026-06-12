---
title: "Find subnetworks"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by Ubentoo on 2010-08-27
Hello,  given my computer is in a network consisting of multiple subnetworks, i.e. there are groups of computers: {192.168.1.1, 192.168.1.2, 192.168.1.3 etc.}, {192.168.2.1, 192.168.2.2, 192.168.2.3 etc.},..., {192.168.254.1, 192.168.254.2, 192.168.254.3 etc.}. My computer is 192.168.1.1. So I can communicate with 192.168.1.2, 192.168.1.3 etc. To communicate with other people I have manually switch to the proper subnetwork and take a new ip, e.g. 192.168.2.1. My question is: Is there any way to be member of all groups and communicate simultaneously with ALL computers? And if not, is there a way to find out (without manually changing the ip address) if computers of other subnetworks are online, so one does not have to change the ip and then look for other computers in the new subnetwork?  Many thanks, Ubentoo

---

### Post by sikander3786 on 2010-08-27
Not possible I believe unless your PC is part of that subnet. Add multiple NICs for multiple networks.

---

### Post by Iowan on 2010-08-27
You should be able to alias your interface (eg. eth0:1 gets address 192.168.1.1, eth0:2 gets 192.168.2.1, eth0:3 gets 192.168.3.15, etc). [This]("https://help.ubuntu.com/community/NetworkConfigurationCommandLine") help page might be useful.

---

### Post by Sabir_101 on 2010-08-27
This link [http://www.firewall.cx/ip-subnetting-routing.php](http://www.firewall.cx/ip-subnetting-routing.php) has some good information on how to route between subnets...

---

