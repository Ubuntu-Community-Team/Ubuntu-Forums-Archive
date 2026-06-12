---
title: "Problems with Atheros L1E card on P5QL-PRO mb"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by knopper67 on 2009-08-26
I just built a new system using an ASUS P5Ql-PRO motherboard. Everything works except for the Atheros Card. Whenever I plug in the ethernet cable to the back, two led's light up. The orange and Yellow ones to be exact.

I guess that indicates that there's SOME type of connection.

I did a "sudo lshw -C Network" to find out if anythings wrong, but to me it doesn't say much.

```
*-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:7b:82:13
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 36:25:42:86:36:60
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

It has the drivers loaded and everything, but I still can't access the internet.

Also, just so you know. I tried installing a copy of XP to see if that would help, but It still wouldn't connect either.

That leaves me to assume that this craptastic card is incompatible with my modem. If that's even possible.

Could anyone lend a hand to find out what's wrong? I can provide config files if necessary.

---

### Post by knopper67 on 2009-08-28
Okay, solved the problem. Turns out I need to unplug the modem for a couple minutes. Then it started working. Silly me.

---

