---
title: "Wired and Wireless connection problem with hp Pavilion dv2000"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by Dkambei on 2010-06-06
My laptop is an hp pavilion entertainment pc dv2000 the specific model is dv2415nr i recently installed the new ubuntu 10.04 but neither my wired or wireless connection seem to work. I'm new at using ubuntu in fact I've never used ubuntu before so a really detailed explanation would be very useful, thank you :p

---

### Post by ajgreeny on 2010-06-06
Open a terminal (Applications - Accessories - Terminal) and type ```
sudo lshw -C network
``` and report back here the output.  That will tell us the actual make of network cards and chipset used, which should help get them running.

---

### Post by Dkambei on 2010-06-07
Ok here is the whole report i get:

   *-network               
         description: Network controller
         product: BCM4311 802.11b/g WLAN
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:01:00.0
         version: 02
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: driver=b43-pci-bridge latency=0
         resources: irq:19 memory:b3000000-b3003fff
    *-network DISABLED
         description: Wireless interface
         physical id: 2
         logical name: wlan0
         serial: 00:1a:73:64:6d:99
         capabilities: ethernet physical wireless
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by AfefTech on 2010-09-06
This is not solved.  Many people have this same issue and it has yet to have resolution

---

