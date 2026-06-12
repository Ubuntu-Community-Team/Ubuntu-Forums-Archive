---
title: "eth0 refusing the link up after update (sky2)"
date: 2012-01-21
forum: Networking &amp; Wireless
---

### Post by okt on 2012-01-21
I recently updated and rebooted the machine to see that eth0 (wired adapter) is refusing the link up. I get no status lights on the laptop or the router. The cable works just fine linking up my other box the the router. 

ifconfig eth0
```
eth0      Link encap:Ethernet  HWaddr 00:21:9b:e7:74:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 
```

dmesg | grep eth0
```
[    1.089969] sky2 eth0: addr 00:21:9b:e7:74:cc
[   12.182265] sky2 eth0: enabling interface
[   12.182391] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

sudo ethtool eth0
```
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  Not reported
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: No
        Speed: Unknown!
        Duplex: Unknown! (255)
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: no
```

ethtool -i eth0
```
driver: sky2
version: 1.25
firmware-version: N/A
bus-info: 0000:09:00.0
```

sudo lshw -C network
```
*-network              
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e7:74:cc
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f9ffc000-f9ffffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 03
       serial: 00:22:69:4b:dd:e1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.201 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f9efc000-f9efffff memory:f0000000-f00fffff(prefetchable)
```

lsb_release -a; uname -a
```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:        10.04
Codename:       lucid
Linux XPS 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux
```

Not sure what step to take, I've tried to disable and re-enable the adapter via the BIOS-setup, when it was disabled it certainly didn't show up via ifconfig. 

Wireless is working just fine, I'm just in need of getting the wired port up because I route a bunch of traffic down the wired for media streaming.

---

### Post by okt on 2012-01-22
Fixed with

sudo modrobe -r sky2; sleep 2; sudo modprobe sky2

---

