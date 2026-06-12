---
title: "wireless device found during installation but not after"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by sailingboarder on 2009-07-06
I recently installed ubuntu server on an old laptop(IBM thinkpad 2628-VSU from 2001). During the installation, it detected eth0 as a wireless interface and eth1 as ethernet. However, after installation, I cannot find any mention of eth0 or a wireless device at all. I've tried lspci, iwconfig, and lshw, but can't find it. How is it that the installation cd could detect it, but I can't detect it now?

---

### Post by superprash2003 on 2009-07-06
could you post outptu of **lshw -C network** from the terminal.ensure that your wifi switch is on , most cards have a ON/OFF switch

---

### Post by sailingboarder on 2009-07-06
```

sailingboarder@pirate:~$lshw -C network
 *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth1
       version: 0c
       serial: 00:03:47:91:ae:09
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A ip=137.165.214.95 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes

```

---

