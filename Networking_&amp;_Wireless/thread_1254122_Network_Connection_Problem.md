---
title: "Network Connection Problem"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by zzasha978 on 2009-08-31
Hi
 
I tried to connect internet to two desktops using a router. One runs XP and the other runs Ubuntu 9.04 (Jaunty). The machine installed XP is connected internet but not the machine for Ubuntu. I checked 'ipaddress' for Ubuntu machine and its inet address (assume to be ipaddress) is 127.0.0.1. I think that its ipaddress is conflicted.
 
I connected a modem to a router so cable line from modem to lan in router then, port 1 and 2 were connected into each desktop. I tried to reset modem with turning off the power for 20 minutes to reset with router and two pcs. Then, power were back on in order of the modem, the router, and pcs.
 
Could you please guide me how to resolve ipconflict issue on the Ubuntu machine in order to connect internet ?
 
Thanks so much for your inputs in advance.
 
James

---

### Post by creeddd on 2009-08-31
maybe you should set them manually instead of letting the router assign them to your machine. then try yo ping the router. ( i wonder if that helps) [http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Networking](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Networking) this could also help.

---

### Post by zzasha978 on 2009-08-31
Thanks so much for your help. I changed IPv4 setting to automatic DHCP.

---

