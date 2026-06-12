---
title: "Broadcom BCM4311 not recognized by Ununtu 12.04"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by Gweg421 on 2013-02-06
i just installed ubuntu 12.04 and it wont recognise my home wifi network let alone connect. If i plug it in it works just fine. Im using; *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:17 memory:d6000000-d6003fff
Any help is greatly appreciated

---

### Post by scatteredstones on 2013-02-07
Have you tried any of the solutions found here?  [https://help.ubuntu.com/community/Wi...Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

### Post by mörgæs on 2013-02-07
Hi, welcome to the fora.

I have renamed your thread and moved it to a better forum. Please take a look around here; there are many threads dealing with your card (or see the page mentioned above).

---

### Post by wildmanne39 on 2013-02-07
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install linux-firmware-nonfree
```
Reboot
Thanks

---

