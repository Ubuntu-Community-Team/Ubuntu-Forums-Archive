---
title: "Ethernet card conflicts"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by thawkb on 2012-10-19
I installed a second ethernet card in my system using ubuntu 10.4 and I believe I am having some conflicts.  I need to have the address configured on one (eth0) as 10.1.3.100 netmask 255.255.252.0 
I have eth1 configured as an address of 10.1.0.98 with the same netmask.  I am not using a gateway for eth1 as I am planned on connecting directly to the redhat cpu.

I cannot access the internet or log in remotely to the machine (ubuntu)without having both ethernet ports occupied such as through a switch.  If I only have eth0 connected I cannot get internet.  
I need the second ethernet card to interface to a different network.  Between that network and the 10.1.0.98 (eth1) I can ping back and forth but many times have it drop off for reasons unknown.  When my redhat system boots up I also had where it said there was an address conflict with another device on the network having that address and I don't see how this is possible.  If I boot the redhat system up without the internet connection to the switch I do not get this error. 

Thanks ahead of time and hope you can understand how I described my problem.  I am not a linux wizard

---

