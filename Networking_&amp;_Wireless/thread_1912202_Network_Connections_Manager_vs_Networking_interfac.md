---
title: "Network Connections Manager vs Networking interfaces file"
date: 2012-01-20
forum: Networking &amp; Wireless
---

### Post by shayno90 on 2012-01-20
I have question regarding ubuntu network connections.

If I add a static IP to :
/etc/networking/interfaces
and then restart it:
/etc/init.d/networking restart

The changes do not seem to take effect.

However if I add a manual static address, gateway and netmask to Network Connections applet manager in the taskbar the change takes immediate effect. In some cases, will then read the network information previously added to
/etc/networking/interfaces

I assume both are independent of each other thus does network manager applet have to be disabled in order for the interfaces file to work?

---

