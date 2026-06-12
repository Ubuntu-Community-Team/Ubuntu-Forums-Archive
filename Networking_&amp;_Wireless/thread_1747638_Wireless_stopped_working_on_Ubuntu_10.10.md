---
title: "Wireless stopped working on Ubuntu 10.10"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by hiralrajani on 2011-05-02
My wireless was just working fine, untill last night. But doesnt any more. I have a hp machine and a Broadcom wireless lan driver. In the active driver it shows that the Broadcom STA driver is active, but still shows that the wireless is disabled. What is going on ?

Output of lspci command:
01:00.0 Netowrk Controller : Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

Output of sudo lshw -C network:
*-network DISABLED
description: Wireless interface
product: BCM4312 802.11a/b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:01:00.0
logical name: eth1
version: 02
serial: 00:1a:73:83:90:c2
width: 64 bits
clock: 33 Mhz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=w10 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11a
resources: irq:19 memory:b3000000-b3003fff

---

### Post by hiralrajani on 2011-05-02
Sorry for not having searched the forum thoroughly.. I did a rfkill unblock all to get the driver enabled..
Can someone mark this post as solved.. I dont seem to find a way to do it.

Ubuntu Rocks!!

---

