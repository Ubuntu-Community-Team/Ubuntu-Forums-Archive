---
title: "8111C no gigabit (1000baseT-FD)"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by xxxlucasxxx on 2009-02-23
Hi all,

I've been banging my head trying to get gigabit speeds with my network card with no luck. I can only get 100 Mb/s.

I've tried lots of random things, but nothing has worked so far. My setup looks like this:

         
Ubuntu 8.10:RTL8111C ----- Netgear:GS105----Vista
                

The GS105 is a gigabit switch and Vista is connecting at 1 Gb/s.

When running **lshw -C network**
I get:
```
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:82:53:eb
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.010.00-NAPI duplex=full ip=192.168.1.47 latency=0 link=yes module=r8168 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       product: DGE-530T Gigabit Ethernet Adapter (rev 11)
       vendor: D-Link System Inc
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth1
       version: 11
       serial: 00:15:e9:3d:bb:f5
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=32 link=no maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5a:2c:92:a9:1d:4d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

The first section is what I'm trying to work with.

When I run **mii-tool -v** I get:
```
eth0: negotiated 100baseTx-FD, link ok
  product info: vendor 00:07:32, model 17 rev 2
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  link partner: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

```

The big thing I notice is that the advertising is less the 1000baseT options.

When I try **ethtool **I get:

```
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

```

I've tried **ethtool -s eth0 speed 1000 duplex full autoneg on** with no luck and
I've tried **autoneg off** yet it still says **Advertised auto-negotiation: Yes**.

And **ethtool -a eth0**
gives
```
Pause parameters for eth0:
Cannot get device pause settings: Operation not supported

```

Any suggestions?

---

### Post by xxxlucasxxx on 2009-03-08
ok, think I got this pain figured out. From my testing I think the cable is bad. Ha! Love it - all this work and a bad cable. I should know better in my old age.

Thanks for any thoughts of giving me a hand.

Lucas

---

