---
title: "Ubuntu 11.04 server with 2 network cards"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by leliofa on 2011-09-22
All, I have set up a proxy server using a Ubuntu server 64bit ver. 11.04 and everything now works like a charm. There is still one little thing that i would like to solve to be able to tell myself I have done a good job.
When I boot the server it isn't able to go on internet directly. First I have to delete one route that is default on eth1. Leaving only the default on eth0 (eth0 is directly connected to Internet) everything starts working fine. To delete the route at each boot I have added a rule in /etc/network/interfaces that say "up route delete default eth1".
Question: what the hell is that automatically add that route each time the box boot? How can I directly prevent it from doing so?.
P.s. both the cards are configured with DHCP (eth0 gets the address from the provider and eth1 from the lan router). 

Thank you very much in advance for the support!
Lelio

---

