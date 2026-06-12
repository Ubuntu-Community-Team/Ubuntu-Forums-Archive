---
title: "Wireless issue with ubuntu 9.10"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by Hawk666 on 2009-12-05
my wireless worked great on jaunty but now when i type

lshw -C network

i get this

WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 11
       serial: 00:10:a7:29:67:08
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.2.18 latency=32 maxlatency=255 mingnt=255 multicast=yes
       resources: irq:20 ioport:d400(size=256) memory:ec000000-ec0003ff memory:ef600000-ef61ffff(prefetchable)
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: d
       bus info: pci@0000:02:0d.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=28 mingnt=10
       resources: memory:eb800000-eb80ffff

the reason i'm creating a new thread for this is because all the other threads i've seen at least have some kind of driver, from what i can see i don't:

configuration: latency=32 maxlatency=28 mingnt=10

---

### Post by Hawk666 on 2009-12-06
problem solved, thanks anyway, in case anyone is watching this thread for a solution, I ran through the process given under "Wireless troubleshooting" in Ubuntu help

---

