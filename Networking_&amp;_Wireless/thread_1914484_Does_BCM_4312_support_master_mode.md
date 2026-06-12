---
title: "Does BCM 4312 support master mode"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by anyone2009 on 2012-01-24
I'm trying to use my laptop wireless car as an access point using ubuntu 10.10 & madwifi . 

So I'm just wondering if my wireless card support master mode or not 

when I type this command to the terminal I get this info 

```
sudo lshw -C network 
```


description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4d:65:3a:d9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.104 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fe7fc000-fe7fffff



thanks

---

