---
title: "&quot;Spoof&quot; ping response time?"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by seikoxyz on 2010-08-12
I have an Ubuntu 10.04 box that is connected directly to my cable modem as a router/firewall for my LAN.
 
The LAN is 192.168.0.X. The Ubuntu gateway is operating as 192.168.0.1.
 
I am using pptp on the Ubuntu gateway to connect to my University's VPN.
 
I am trying to use Xbox 360's systemlink to join open games on the University's LAN, however I am not showing any activate sessions. Researching the issue, I have found that Xbox 360 automatically filters out any LAN games where the host's ping response is greater than 30ms, presumably to prevent people from playing games over the internet without Xbox Live.
 
I'm thinking there must be a way using iptables to see a ping request from the XBOX 360 (192.168.0.5) to one of the remove VPN addresses (say any 10.1.2.X address) and return an immediate response from the Ubuntu box, which of course would be much less than 30ms.
 
Any thoughts? All help is appreciated in advance.

---

