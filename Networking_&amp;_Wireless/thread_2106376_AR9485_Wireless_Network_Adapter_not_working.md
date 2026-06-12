---
title: "AR9485 Wireless Network Adapter not working"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by arun_a on 2013-01-18
Hi..

I purchased a new HP Laptop (HP 2000 series). I have installed Kubuntu 12.10 ,but I am unable to use wifi. After pressing F12(wifi switch) ,I got the following info   from sudo rfkill list all:


0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
1: hp-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
2: hp-bluetooth: Bluetooth
        Soft blocked: yes
        Hard blocked: no

The information showed by sudo lshw -class network command is:
  
  *-network DISABLED
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:e5:43:b9:10:69
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-17-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:92500000-9257ffff memory:7eb00000-7eb0ffff

After pressing the wifi switch, It still shows red on the keyboard. Kindly help. Thank you.

---

### Post by praseodym on 2013-01-19
Try

```
sudo rfkill unblock all
```
If its not working, try a reset of the BIOS to default settings.

---

### Post by arun_a on 2013-01-22
Thanks a lot.. :) .. It worked .:D

---

