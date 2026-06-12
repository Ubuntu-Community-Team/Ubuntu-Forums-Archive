---
title: "Dual Nic Setup"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by boreese on 2011-11-08
I have a system with 2 seperate network cards
The 2 networks must remain seperate (no bridge).
 
Nic #1
10.1.1.2
255.255.255.0
10.1.1.2
All devices on the 10 network only answer to IP.... setup by design
 
Nic #2
192.168.190.247
255.255.255.0
192.168.190.243
DNS: 192.168.190.253
 
The problem I am having is that the 192 network is a global connection to multiple sites.
When the 10 network is plugged in, I can access only local systems in the 192 network.
 
dns.chi.XXX.com works
dns.dal.XXX.com does not
dns.atl.XXX.com does not
 
If I disconnect from the 10 network, I can get to all the other sites.
I have tried a different network card and the results are the same.
 
Firewall has been turned off.
 
Anyone know what is happening? I have tried everything I can think of.
Thanks for the time......

---

