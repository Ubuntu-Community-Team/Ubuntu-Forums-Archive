---
title: "Changed modem/router config, now cannot set static ip address"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by misterspider on 2010-11-17
I have Xubuntu 10.04 installed, and have been using a Billion 5210s modem in conjunction with a Linksys wrt54gl router. My PC was connected via a wired connection to the linksys (dhcp server enabled), the linksys WAN port was connected to the Billion LAN, and I ran the Billion in bridge mode (dhcp server disabled).

Through the Network Manager I had specified a manual ip address, and this has been working fine. The problem with this setup was that every time the power goes off (switch of power point etc), once it gets turned back on the internet connection was lost and I had to re-configure the modem and router. This always took far too long! 

So I now have changed things so that the billion modem has the dhcp server enabled and the linksys has it disabled, and I am using the router as a wireless access point. I connect the modem LAN to the router LAN.

This is much better except that now the manual settings in Network Manager don't work. I have specified an ip address, subnet mask, default gateway, and two DNS servers.

To get it to work, I simply type 
$sudo dhclient 
but this gives me the first available ip (not the one manually entered). I'm guessing there is something simple in the modem web interface that will solve this, what should I look for?

---

