---
title: "Networking and VM firewalls"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by dlegatt on 2010-08-11
I'm not certain if this belongs here or in the server forum.
I have a small server that is running vmware server on top of ubuntu server 10.04.
On a virtual machine, I am running m0n0wall with two virtual NICs bridged to the two physical NICs installed on my server. 
I am a bit confused as to how to manage the physical NIC on the server so that the only WAN port that can be seen from outside the network is the virtual one that is managed by m0n0wall.  
Right now, the physical NIC is receiving an ip address of 192.168.1.103 from my linksys router that is managing my network until I get my m0n0wall working.  The m0n0wall nic is getting an ip of 192.168.1.106.  How can I make it so the physical NIC is invisible and only the virtual NIC can be seen?

---

