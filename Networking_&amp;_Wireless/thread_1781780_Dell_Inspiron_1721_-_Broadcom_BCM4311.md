---
title: "Dell Inspiron 1721 - Broadcom BCM4311"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by dematerialize on 2011-06-14
I just installed the 64-bit Kubuntu 11.04 and i've been having some issues getting the wifi to work. At first I went to additional drivers and activated the STA driver and restarted. After restarting when I went into the network manager and any option for wireless was disabled. I was wondering which method would be most effective in fixing this issue. Thanks. 

lspci -nn | grep 'Broadcom'

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

sudo lshw -C network 

  *-network                                                                                        
       description: Network controller                                                             
       product: BCM4311 802.11a/b/g                                                                
       vendor: Broadcom Corporation                                                                
       physical id: 0                                                                              
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:89:77:0b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.0.0.9 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:21 memory:fe5fe000-fe5fffff

---

### Post by bkratz on 2011-06-14
You might try this link and the link within to change to the b43 driver--it seems to work correctly for your card in 11.04.

[http://ubuntuforums.org/showthread.php?t=1759568](http://ubuntuforums.org/showthread.php?t=1759568)

you need to be careful since you have a broadcom Ethernet interface and the STA driver sometimes tries to blacklist ssb which is needed for the b44 driver that the BCM4401-B0 100Base-TX also uses. b43 also used ssb so it is a win win.

---

