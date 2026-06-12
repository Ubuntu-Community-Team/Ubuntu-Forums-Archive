---
title: "Firewall Builder - using inbound NAT rules from INSIDE"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by swb_mct on 2009-11-25
I am new to Linux and Firewall builder, but not new to commercial firewalls. I have set up an Ubunto internet gateway with Firewall Builder and everything works except . . Firewall Builder is setup to let us access Microsoft Outlook Web Access (inbound 443) on an internal Exchange server from the internet. This works fine. . . We also need to use Outlook Web Access from workstations within the internal network and need to use the same URL because of the SSL certificate. So from the inside we have always used [https://owa.xyz.com/owa](https://owa.xyz.com/owa) but this does not work with my FWBuilder configuration.  
 
Inbound NAT rules work from the LAN with the default port forwarding rules on most all other firewalls.   
 
looking at the Policy and NAT configuration that makes it work from outside seems like it should also work from the LAN because we have "original source = Any". 
 
How can I make inbound rules to internal servers work from internal workstations with Firewall Builder ? 
 
 
Please remember that am in the dark with IP Tables and Linux even though setting up the firewall with Firewall Builder was easy.

---

