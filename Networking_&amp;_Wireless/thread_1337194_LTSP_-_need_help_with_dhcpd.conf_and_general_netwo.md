---
title: "LTSP - need help with dhcpd.conf and general network confusion."
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by youbuntu on 2009-11-25
Hi people. I have got my 9.10 Ubuntu LTSP up and running... but it uses *two* ethernet interfaces, and I only want it to use one, so that machines can boot off it *anywhere* on my home network.

Here is my current config (attached)

I want to know - in n00b terms please - what I need to do to have a *single* NIC LTSP server running, and what I edit in dhcpd.conf to implement this. I need the server attached to the main home network, *NOT* split across two NICs as it is now.

My home network has three routers - one is an ADSL modem + router, and has a DHCP server running, and it's IP is: 192.168.1.254. The other two routers which are daisy-chained off it, have *FIXED* IP addresses of: 192.168.1.250 & 192.168.1.240. The subnet mask for the whole network is the default: 255.255.255.0

I am *extremely* confused about dhcpd.conf - I mean, what on earth is a DNS server?... doesn't my existing main router do the DNS stuff?. What is a broadcast address?? arrgh!! help please!!

Thanks guys.


[COLOR=Red][EDIT] noone? :([/COLOR]

---

### Post by youbuntu on 2009-11-25
Wow, it would seem I have *stumped* the Ubuntu community! ;)

---

