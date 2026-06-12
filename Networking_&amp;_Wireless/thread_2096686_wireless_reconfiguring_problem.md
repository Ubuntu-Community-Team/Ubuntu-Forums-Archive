---
title: "wireless reconfiguring problem"
date: 2012-12-20
forum: Networking &amp; Wireless
---

### Post by bawasingh on 2012-12-20
[FONT=monospace]Sir i have a HCL ME icon 54 laptop , i have installed ubuntu 12.04 . i am not set my wifi only i have to use wired connection.
pl reconfigure my network.
 

amankpanwar@amankpanwar-HCL-Notebook:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f050ffff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 70:71:bc:44:98:e3
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.0.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:f0400000-f043ffff ioport:d000(size=128)

[/FONT]

---

### Post by overdrank on 2012-12-20
Hi and welcome, please do not create multiple threads on the same issue. Duplicate [_here_]("http://ubuntuforums.org/showthread.php?p=12414308#post12414308"). Thread closed

---

