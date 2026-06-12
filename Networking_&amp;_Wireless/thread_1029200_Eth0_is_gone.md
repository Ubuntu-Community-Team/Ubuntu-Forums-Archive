---
title: "Eth0 is gone"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by Jappsta on 2009-01-03
Hi all,
I'm running ubuntu 8.10 on my laptop (hp 8510w) dual booting with windows. Only problem is, my wired network connection isn't working. It works fine with windows but somehow eth0 doesn't show up in ifconfig. dmesg gives me this entry:

[    2.103947] libata version 3.00 loaded.
[    2.106286] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    2.106287] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.106334] e1000e 0000:00:19.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.106344] e1000e 0000:00:19.0: setting latency timer to 64

I tried modprobe e1000 but nothing seems to happen.
I'm completely stumped, does anyone have an idea what might solve this?
Thanks in advance,
Hidde

Edit:
Just found another clue in dmesg,

[    2.165984] e1000e 0000:00:19.0: PCI INT A disabled
[    2.166008] e1000e: probe of 0000:00:19.0 failed with error -5

Edit2:

lshw:
*-network UNCLAIMED
   description: Ethernet controller
   product: 82566DC Gigabit Network Connection
   vendor: Intel Corporation
   physical id: 19
   bus info: pci@0000:00:19.0
   version: 04
   width: 32 bits
   clock: 33MHz
   capabilities: cap_list
   configuration: latency=0
*-network DISABLED
   description: Ethernet interface
   physical id: 1
   logical name: pan0
   serial: fe:b1:18:36:ab:30
   capabilities: ethernet physical
   configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Jappsta on 2009-01-05
I'm completely stumped and my problem persists, any help would be greatly appreciated.

Thanks,
Hidde

---

