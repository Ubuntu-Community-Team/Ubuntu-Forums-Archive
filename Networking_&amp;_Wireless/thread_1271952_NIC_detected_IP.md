---
title: "NIC detected IP"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by waltweb on 2009-09-21
I am in the process of setting up some snort boxes using the Ubuntu server. I had the box up and running in a test mode and decided to change the ip address and move it into production. The system has 2 nics with eth0 being a static ip address that I changed. Eth1 is in promiscous mode so has no ip address. I can remote into the box on eth0 using the new ip address but when I look at the logging for snort it shows that the detection ip address is the old address for eth0. I can not find anywhere to change what the system is reporting the ip address as. The ips are on 2 completely different subnets.
 
Thanks

---

