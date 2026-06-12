---
title: "network manager disappears, forces me to reboot"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by grimslider75 on 2010-03-27
out of the box everything was working great, it was only after i installed kubuntu then removed it that i started having problems with the wireless connection. 

once the network manager stops working, the terminal stops as well. In the system monitor is says that "terminal" is "uninterruptible" as well as the "nm-applet." 

this is what i get from sudo lshw -C network
```
*-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 0c:ee:e6:b4:ff:c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.2.13 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:d1100000-d110ffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:7b:0c:34
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:d1000000-d103ffff ioport:2000(size=128)

```

any suggestions? 

PS. I am not experienced with linux. I spend more time studying philosophy then i do on finding out how linux works.

---

