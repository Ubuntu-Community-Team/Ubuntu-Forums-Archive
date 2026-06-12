---
title: "Realteak RTL8101 continuous disruption"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by Illuminatus- on 2010-07-26
Hello, 

While i manage to connect to my router, the connection cannot take place if i am a bit far from the router. 
i.e. from where i work, i can connect to my router only if i am under windows. From this same place, ubuntu detects the network but is almost 101% of time unable to connect.
I hope the problem is clear.

I am on ubuntu 10.04, 64bit

I will post information on my card below:

1) Machine Brand and Model: Toshiba satellite L500-10x
2) No output for: lspci
3) lshw -C network:
```
-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:44:17:3a
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:30 ioport:4000(size=256) memory:f2010000-f2010fff(prefetchable) memory:f2000000-f200ffff(prefetchable) memory:f2020000-f203ffff(prefetchable)
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:26:b6:1a:84:60
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.16.2 multicast=yes wireless=IEEE 802.11bg
```

---

