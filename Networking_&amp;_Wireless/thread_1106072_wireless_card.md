---
title: "wireless card"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by spedax on 2009-03-25
how do I see what wireless card I have ? and what drivers ubuntu uses.

Thanks

---

### Post by chili555 on 2009-03-25
Open a terminal and do:```
sudo lshw -C network
```It will show details about both ethernet and wireless. Here, for example, is my wireless:>   *-network
       description: Wireless interface
       product: [COLOR="Red"]PRO/Wireless 3945ABG [Golan] Network Connection[/COLOR]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:c2:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR] ip=192.168.1.108 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

---

### Post by spedax on 2009-03-25
works ! thanks allot :)

---

