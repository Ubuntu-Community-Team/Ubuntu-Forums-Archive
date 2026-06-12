---
title: "Secondary Static IP Address?"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by RMOP on 2009-08-15
eeePC Ubuntu 8.04

Not sure this is what I need, but my perusal of this forum suggests it *might* be.

Problem: If I connect to my DD-WRT WTR54GS Wireless Travel Router via CABLE, *I must use a static IP address when the router is in **Repeater Bridge Mode***. Normally, I want my eeePC to get an IP address dynamically (as happens when I connect to the same router wirelessly). But, when I need to make configuration changes to the router (say, to move it to AP Mode from Repeater Bridge Mode), I want a *wired* connection and a static IP address. But, if the same router is *already* in AP mode, a wired connection should assign an IP address to the eeePC dynamically. Hope I'm making clear sense.

Am I understanding things correctly in thinking I can configure a secondary (alias?) interface (eth1 or eth0:0) to which a fixed IP address and gateway have been assigned? I've only got one physical adapter, but I want to be able to have my eeePC connect via cable to this router independently of the router's configuration (i.e., Repeater Bridge or AP Mode). And I don't want to have to manually tell Ubuntu whether to use a static or dynamic IP.

Am I asking for too much? My question is based on ignorance, which I hope to reduce. Advice appreciated. Many thanks.

---

