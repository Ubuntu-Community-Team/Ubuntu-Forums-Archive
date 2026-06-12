---
title: "switching DNS"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by Eklod on 2010-11-06
Hello: 

A few days ago, I upgraded from Hardy to Lucid 10.04.LTS, mainly because I was not able to connect via broadband using a ZTE668 usb stick. This task is so much easier under Lucid, which recognized the device and is now working fine, except for two things.  

1 - When I boot and connect, it picks up my ISP (Rogers) DNS.  If I disconnet and reconnect broadband without restarting, my DNS are set to OpenDSN.  My settings under Network Broadband is currently set to use default dns provided by ISP.  I wonder where the configuration to use OpenDNS resides, and how to stop this unstable behavior.      

2- By default, I keep wireless disabled as I rarely use it.  This setting does not stick it is re-enabled every time I reboot or connect and reconnect.   While trying to get the ZTE working under Hardy, I tried all the tricks described in this and other forums.  I likely edited a config file somewhere, which sometimes superceeds settings under networking and which was not erased when I upgraded to Lucid?  

-I otherwise really really like Lucid!         

Any suggestions to  stabilise networking?

---

### Post by SeijiSensei on 2010-11-08
You probably edited /etc/dhcp3/dhclient.conf.  Take a look at that, particularly the prepend directives.

---

