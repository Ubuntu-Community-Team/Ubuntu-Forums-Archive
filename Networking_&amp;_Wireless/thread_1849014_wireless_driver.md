---
title: "wireless driver?"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by bozicso on 2011-09-23
I have this problem:

[IMG]http://www.dodaj.rs/f/2B/6W/1CxKOWdZ/screenshot.png[/IMG]

[IMG]http://www.dodaj.rs/f/2P/ib/2KVgSlZL/1/screenshot.png[/IMG]

```
lspci -knn|grep work -A 5
sudo lshw -C network
``````
04:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e021]
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0139]
    Kernel driver in use: tg3
    Kernel modules: tg3


 *-network UNCLAIMED
       description: Network controller
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:54600000-54603fff
  *-network
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 1c:75:08:2d:bd:c1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=sb ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 memory:53500000-5350ffff
```

---

### Post by chili555 on 2011-09-23
> 0280]: Broadcom Corporation BCM43225 802.11b/g/n [[COLOR="Red"]14e4:4357[/COLOR]] (rev 01)bcmwl-kernel-source is not correct for this device. The correct driver is brcm80211 which is included in the latest kernel version:> $ modinfo brcm80211
filename:       /lib/modules/[COLOR="Red"]2.6.38-11[/COLOR]-generic/kernel/drivers/staging/brcm80211/brcm80211.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     0039D58F094F7B0F75BAA6B
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]4357[/COLOR]sv*sd*bc*sc*i*
depends:        mac80211,cfg80211
staging:        Y
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
parm:           msglevel:int
parm:           phymsglevel:int
What kernel version are you running? Please run and post:```
uname -r
```

---

### Post by bozicso on 2011-09-23
```
2.6.35-28-generic
```

---

### Post by chili555 on 2011-09-23
Please see: [http://ubuntuforums.org/showthread.php?t=1617380](http://ubuntuforums.org/showthread.php?t=1617380)

---

