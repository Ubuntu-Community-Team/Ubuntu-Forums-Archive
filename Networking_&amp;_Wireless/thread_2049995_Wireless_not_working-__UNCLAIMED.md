---
title: "Wireless not working-  UNCLAIMED"
date: 2012-08-29
forum: Networking &amp; Wireless
---

### Post by hectorescallon on 2012-08-29
i just upgraded my laptop from ubuntu 10.04 to whatever latest version 12.04 i think..  and the wireless is not working... 
on terminal i went to lshw -C network
and this is what i got, can anybody help me find the driver or any suggestions 


 *-network UNCLAIMED    
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:b3200000-b3203fff

---

### Post by nativehound on 2012-08-29
It looks like you need the drivers. 

More info here

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

