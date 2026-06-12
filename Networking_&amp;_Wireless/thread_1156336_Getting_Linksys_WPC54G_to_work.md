---
title: "Getting Linksys WPC54G to work"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by WRG on 2009-05-11
Ubuntu noob here who has recently started using 9.04.  I have a wireless that I am trying to get to work, Linksys WPC54G.  I figured out to install windows wireless drivers and I did.  I quess now I just need a driver my card wireless card.  Anyone know where to find one, and is there thing else you have to do to get it to work?


-Thanks

---

### Post by Peter09 on 2009-05-11
Can you post the output of the terminal commands

```
lshw -C network
```

and

```
ifconfig
```

---

### Post by pablolie on 2009-05-15
I have the same card and am trying to get it to work in 8.04 LTS, here is the output of that command

  *-network
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:9
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth2
       serial: 00:0c:41:a9:df:9c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by superprash2003 on 2009-05-15
please post ifconfig output as well and output of iwconfig from the terminal..

---

