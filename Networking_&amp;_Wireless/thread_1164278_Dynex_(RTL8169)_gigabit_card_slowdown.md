---
title: "Dynex (RTL8169) gigabit card slowdown"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by Wyldfire on 2009-05-19
I have installed a new gigabit network in the house, cat-6, with a linksys gigabit router.  The connection works at full gigabit speeds.  I installed a Dynex DX-PCIGB NIC in my ubuntu box.  It will only connect at 100Mbs speed.  I do have a second NIC on board, but it is currently unused.  

I have tried 

sudo ethtool --change eth1 speed 1000 duplex full

but it just loses connection for a moment, then reverts to 100Mbs.

Can anyone help me get up to speed? (pun intended)

Info:

sudo lshw -C Network
```
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: 10
       serial: 00:21:27:f3:81:58
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.108 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:19:db:ac:ad:3f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s

```

---

### Post by Wyldfire on 2009-05-19
Bump for assistance... anyone?

---

### Post by brendanpiater on 2009-05-21
Hi There,

I had the same issue (running at 100 mbps) but running:

$ sudo ethtool --change eth1 speed 1000 duplex full

...set eth0 to 1000 mbps for me. I did see some stuff when searching previously that the driver is little buggy for realtec cards, perhaps your card is is one of the cards experencing these issues.

$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:38:89:be
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=MII speed=1GB/s

Cheers
Brendan

---

### Post by Wyldfire on 2009-05-21
Tried that.  It simply reset to 100Mbps as soon as it came back up.  Anyone got any other ideas?  Or, as a last resort, do you know what card I can get that will work out of the box?

---

### Post by brendanpiater on 2009-05-21
For sure, I only meant that it worked for me so it may be related spefically to the card chip version/driver.

Good luck!

Cheers
B

---

