---
title: "Kvm guest as default gw, host has no internet"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by druggo on 2012-06-17
Hi

I have a kvm host setup with precise and kvm.

The host has 2 nics. eth0 is setup as bridge br0 to guest for LAN access, the other nic i use pci passthrough for my guest firewall (pfsense) 

The setup works for my other lan clients, confirming the pci passthrough to be working, however i have no connectivity from my kvm host.

Tcpdump shows packets initiated from host travel out on the guests wan interface but i receive no resp for my SYN packet.

The weird part is that when i telnet [www.google.com](www.google.com) 80 from the host i get packets returned?! Google is the only site i've seen working? Really strange. No rules on the host/guest fw for this it should allow all traffic outbound.

 Could be some mac spoofing setting with my isp? I'm Grasping for ideas here... :( 

Im out of ideas here. Please help!

---

