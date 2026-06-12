---
title: "wireless problem with laptop"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by TheRacerX on 2012-06-23
I have a Toshiba Tecra S4 laptop with a Broadcom 4311 chipset wireless adapter and i just installed Ubuntu 12.04 64bit, but for some reason when i activate the wireless driver it doesnt work, ive tried everything to get it working but nothing works, anyone have any ideas ive tried the lshw thing and it gave me this 

theracerx@Dante:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network 
description: Ethernet interface
product: 82573L Gigabit Ethernet Controller
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 00
serial: 00:15:b7:91:54:57
capacity: 1Gbit/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.5-1 latency=0 multicast=yes port=twisted pair
resources: irq:45 memory:ffce0000-ffcfffff ioport:cfe0(size=32)
*-network UNCLAIMED
description: Network controller
product: BCM4311 802.11b/g WLAN
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:05:00.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: memory:ffafc000-ffafffff
*-network
description: Wireless interface
physical id: 1
bus info: usb@1:7
logical name: wlan1
serial: 30:46:9a:2f:aa:85
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=ath9k_htc driverversion=3.2.0-26-generic firmware=1.3 ip=192.168.0.103 multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

the adapter shows up but it doesn't actually seem to be operational

---

### Post by praseodym on 2012-06-23
Install the package **linux-firmware-nonfree** and reboot.

---

### Post by TheRacerX on 2012-06-23
just tried that now it did nothing

---

### Post by praseodym on 2012-06-23
Check:

```
lspci -nnk | grep -iA2 net
rfkill list
iwconfig
lsmod
dmesg | grep b43
```

---

### Post by TheRacerX on 2012-06-23
i figured the problem out after i installed the firmware, i went into the additional drivers thing again and removed the Broadcom STA Wireless Driver then restarted the computer, now the wireless is working thanks for your help

---

