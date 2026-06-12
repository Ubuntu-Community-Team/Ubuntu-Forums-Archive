---
title: "Dancing NAT addresses"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by jimwill on 2012-01-22
Ok, it's an older Kubuntu. 8.04 Hardy. 
I have a Comtrend CT-5363 router, Desktop with Hardy (also have Oneiric installed but waiting to get Audacity working before switching for good) and an older laptop with Hardy. I have the laptop setup as a server to develop some stuff on Wordpress. The desktop came up 192.168.1.2 and the laptop 192.168.1.3. So that is how I set up the router, to forward port 80 to 192.168.1.3.
However, if I shut the desktop down over night the next morning the desktop comes up as the .3 and the laptop is now .2 !!
The laptop was originally using wireless but I have since removed the wireless pcmcia and installed a pcmcia nic card. Now it wants to come up as 192.168.1.4!!!!!

I have tried using KNetworkManager, that just crashes any connection. I've tried setting a static ip in the etc/network/interfaces file, on both computers, but to no avail. 
The only way to get the correct ip's is to shut everything down, including the router, then power up the router, then the desktop, then the laptop!

Any other suggestions?
(the laptop is an older dell and only allows 512 megs of memory so I can't upgrade from Hardy)

---

