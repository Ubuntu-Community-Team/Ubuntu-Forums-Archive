---
title: "Problems with WICD and WPA2 on Karmic"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by MellowVids on 2009-11-09
I am using Karmic Koala on an AMD64 system, the Netgear wg311v3 adapter, and I followed instructions in other threads to finally get ndiswrapper to work.  

Anyway, I still cannot connect to my network, which is WPA2 encrypted.  Neither knetworkmanager nor wicd can connect to my router; however, both could scan for networks and could see the one I wanted to connect to.  

This leads me to suspect that the driver and ndiswrapper are working properly, but that my configuration is bad. 

Anyone have any ideas or suggestions?

---

### Post by lusitano on 2009-11-16
> **MellowVids said:**
> I am using Karmic Koala on an AMD64 system, the Netgear wg311v3 adapter, and I followed instructions in other threads to finally get ndiswrapper to work.  

Anyway, I still cannot connect to my network, which is WPA2 encrypted.  Neither knetworkmanager nor wicd can connect to my router; however, both could scan for networks and could see the one I wanted to connect to.  

This leads me to suspect that the driver and ndiswrapper are working properly, but that my configuration is bad. 

Anyone have any ideas or suggestions?

Is your network a hidden network?

If so, try enable broadcasting network.

---

