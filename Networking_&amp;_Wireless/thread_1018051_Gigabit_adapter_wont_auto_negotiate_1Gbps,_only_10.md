---
title: "Gigabit adapter wont auto negotiate 1Gbps, only 100mbps"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by ThaddeusW on 2008-12-21
Hello everyone, 

My Ubuntu 8.04 server has two on board Intel 82546EB gigabit adapters. I currently only use one and for some strange reason it does not want to auto negotiate 1Gbps. At first I checked the usual suspects: trying different Ethernet cables and changing the ports on the switch (Netgear GS105). Sometimes it *might* auto negotiate 1Gbps but most of the time its just 100Mbps which is too slow. My kernel is 2.6.24-18 generic. 

Any ideas? Even if I try and force 1Gbps using:

```
#ethtool -s eth0 speed 1000
```    

It will disconnect and just reconnect at 100 again. Its driving me nuts here.

---

### Post by ThaddeusW on 2008-12-22
No one has ever had this problem? I was playing with bridging and it amazingly connected at 1Gbps every time! but the bridge did not work so I deleted the bridge and bought eth0 back up. It stayed connected at 1Gbps! After I shut down the system and powered it back up it still will not negotiate 1Gbps. 

Is there a way to force 1Gbps? As in make 1000Mbps the only means in which the adapter will attempt to negotiate?

*UPDATE*

Well it might be my switch. Not 100% sure but I switched the ports before and it didnt help but I just switched the port now and it worked. My switch might be spazing out on me. But I still want to be able to force full duplex and 1000mbps. So if the link fails 1Gbps again I can swap ports and reboot the switch until I see a link.

---

