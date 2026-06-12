---
title: "Ports and Deluge"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by Jdogzz on 2011-10-28
I've been trying to configure torrenting in Ubuntu at all for a few weeks without success. I have tried both Transmission and Deluge but neither work. I followed this tutorial:
[http://ubuntuforums.org/showthread.php?t=1259923](http://ubuntuforums.org/showthread.php?t=1259923)
and configured port forwarding in my Netgear WNR3500v2 VCNA but it still says "connection refused" when I check the port on [http://canyouseeme.org](http://canyouseeme.org). (The port is 50650 btw) I don't use any firewalls, and my ISP is Comcast if that means anything. I have tried this also with a VPN but I get "connection timed out" on the port checker website. Can anyone help troubleshoot what's blocking me?

---

### Post by Jdogzz on 2011-10-30
Managed to fix it with this program:
[http://gufw.tuxfamily.org/](http://gufw.tuxfamily.org/)

I just added a premade exception for Deluge.

---

