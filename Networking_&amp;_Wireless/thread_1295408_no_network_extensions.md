---
title: "no network extensions?"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by dvdljns on 2009-10-19
Need help troubleshooting this..

lshw output::  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@00:0c.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=64
       resources: iomemory:f4030000-f403ffff iomemory:f4020000-f402ffff irq:9


ifconfig output::lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3292 (3.2 KiB)  TX bytes:3292 (3.2 KiB)

Does anyone know why iwconfig shows lo  no wireless extensions.

I have ubuntu 7.04 with a wg311v3 card setup by ndiswrapper.

Looked on rhe web and forums and did not find this problem anywhere. Do not know how to troubleshoot this problem.

---

### Post by Iowan on 2009-10-19
> **dvdljns said:**
> 
        oes anyone know why iwconfig shows lo  no wireless extensions.The loopback device (lo) doesn't show wireless extensions on any of my systems.  I suspect it's a driver issue - but I don't have a suggestion what to try on 7.04. **ndiswrapper** would have been a suggestion - if you hadn't already tried it...

---

### Post by dvdljns on 2009-10-19
The driver seems to be installed right. on this card the only way you can install it is with ndiswrapper. I know the card works. I have to take it from that comp and use it in this one. so the card and driver works in windows. never heard of this problem before. It is on the list of cards that users claim is tested with 7.04. As for as I can tell no ones had this problem with any card. The only thing I can think of is reinstalling everything.:confused:

---

