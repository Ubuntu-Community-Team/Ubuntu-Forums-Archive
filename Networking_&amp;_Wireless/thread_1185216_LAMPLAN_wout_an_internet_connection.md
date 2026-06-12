---
title: "LAMP/LAN w/out an internet connection"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by Icky_Ev on 2009-06-12
Cheers, everyone. Hope you can help a girl totally out of element cobble something together. 

I need to set up a LAMP/LAN that will NOT have an internet connection. Will be an isolated group of computers hooked up to the server through a router. Internet access will be a different group of computers with a different router, and the two shall never meet.

I was able to successfully set up & install 9.0.4 and tweak all the files (interfaces, hosts, ect), could ping $host localhost and access the server through other computers on the network via localhost or it's IP. Which was all fine and good until I realized I had it plugged into the wrong router...

To make a long story short, I set up again with the server plugged into the appropriate router (no WWW connection) and cannot access the server remotly or even $host localhost ("no servers found") Resetting network/interfaces to static, pointing hosts ect- nadda. 

All the how-tos and docs I've found assume that there's an internet connection in play. Could someone shove me in the direction of a how-to for my purposes (if there is one?) or suggest what's going wrong? I'm sure I'm missing something very, very simple. :\

---

### Post by dmizer on 2009-06-12
Try disabling NAT on the isolated router. Then configure everything for static IP. That, or install dnsmasq on the LAMP server to provide both DNS and DHCP on your isolated LAN: [https://help.ubuntu.com/community/Internet/ConnectionSharing#DHCP/DNS%20server](https://help.ubuntu.com/community/Internet/ConnectionSharing#DHCP/DNS%20server)

PS
(Just to make sure) On your isolated LAN, there should not be any cables attached to the WAN port on the router.

---

### Post by Icky_Ev on 2009-06-12
Thank you for the suggestions, I'll try them out. :KS

---

