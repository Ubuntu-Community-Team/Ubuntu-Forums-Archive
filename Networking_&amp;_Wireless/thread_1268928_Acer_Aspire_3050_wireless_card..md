---
title: "Acer Aspire 3050 wireless card."
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by Renegade II on 2009-09-17
After formatting my HD and installing Ubuntu my wireless card does not work no more and I can not seem to be able to ind any drivers for it.

A search on this forum lead me to the following topic: [http://ubuntuforums.org/showthread.php?t=511458](http://ubuntuforums.org/showthread.php?t=511458)

So, having done that I hope there is someone on here that can help me out.

Here is the output hope it will help:
> renegade@renegade-laptop:~$ sudo lshw -C network
[sudo] password for renegade: 
  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 40
       serial: 08:00:27:8d:cf:71
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=pcnet32 driverversion=1.35 duplex=full ip=10.0.2.15 latency=64 link=yes maxlatency=255 mingnt=6 module=pcnet32 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:f5:09:27:29:63
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

