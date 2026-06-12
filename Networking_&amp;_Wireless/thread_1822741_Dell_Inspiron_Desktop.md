---
title: "Dell Inspiron Desktop"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by Justinba1010 on 2011-08-10
I can't get the wireless card to connect but it finds the network. Help please. I tried before but too much information so let me try again with less. I can't get into the network but it searches and finds it.

---

### Post by garvinrick4 on 2011-08-10
Usually just need to get right driver. what is your card:
```
sudo lshw -C network
```
Post it back here.

---

### Post by Justinba1010 on 2011-08-10
I am in the middle of disk check but I will write it here asap.

---

### Post by Justinba1010 on 2011-08-11
Disk Check had no errors but I have to write word by word for this.
ONCE AGAIN THIS IS HAND WRITTEN SORRY FOR ALL MISTAKES IF THERE ARE ANY.
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semi conductor Co., Ltd.
physical id: 0
bus info: PCI@000: 02: 00. 0
logical name: eth0
version: 02
serial: 00: 25: 64: // I think this is my security codes
size: 10Mbits/s
capacity: 100Mbits/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pci express msix vdp bus_master cap_list rom ethernet physical tp mi i 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiation on=on broadcast=yes driver=8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MI speed=10Mbits/s 
resources: irq: 42 i oport:e800(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:febe0000-febfffff
*-networ
description: Wireless interface
physical id: 1
bus info: firwir@1
logical name: wlan0
serial: //once again
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=usb driverversion=2.6.38-10-generic firmware=N/ A link=no multicast=yes wireless=I EEE 802.11bgn

I hope this helps

---

### Post by Justinba1010 on 2011-08-11
Well if it helps as I will be going to sleep. M?y card is a netgear WNA1100 so if that helps please tell me that magical sudo command lol.

---

