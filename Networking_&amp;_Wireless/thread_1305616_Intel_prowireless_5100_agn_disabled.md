---
title: "Intel pro/wireless 5100 agn disabled"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by magicskyer on 2009-10-30
I am using 9.10 and the wireless is disabled.
I can not check the wireless by click on the network manager.
I don't know how to enable it

```
magicskyer@magicskyer-laptop:~$ sudo lshw -c network
[sudo] password for magicskyer: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:0b:be:e6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v3.04 ip=203.188.81.157 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:d5500000-d550ffff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fa:7e:60:24
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:d4500000-d4501fff

```

---

### Post by magicskyer on 2009-10-30
Is there anyone can help me solve this problem?

---

### Post by toopi on 2009-11-30
> **magicskyer said:**
> Is there anyone can help me solve this problem?

Is there like a physical switch to turn on?  Some laptops nowadays have it.

---

### Post by avacado on 2009-12-27
try code 
sudo rfkill list
and make sure the wifi is enabled in bios
try turning the physical switch to 'off' this worked for me!

---

