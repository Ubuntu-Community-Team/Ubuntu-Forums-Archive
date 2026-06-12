---
title: "HUGE problems with Acer Travelmate Wireless"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by redheadgiant on 2009-05-31
Hello all!

My name is Simeon and I'm new here. I've had trouble with my laptop's wireless for some time now. I've browsed this forum looking for help and stuff, but I've hit a wall.

I have an Acer Travelmate 2304LCi and it on-board wireless isn't working.

When I type in <lshw -C network> this is what the output reads: 

 *-network:1 UNCLAIMED
       description: Ethernet controller
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=32

The network card doesn't seem to work.

As far as my understanding goes, "UNCLAIMED" means that there is no driver, or the driver isn't recognized. I've run ndiswrapper, and the driver GUI says that the driver is installed properly and recognizes hardware is present. 

There is no logical id, and no MAC address that I can find, and so networking has become impossible](*,).

I beg for some help. Anything is welcome and greatly appreciated!

Cheers: Simeon

---

