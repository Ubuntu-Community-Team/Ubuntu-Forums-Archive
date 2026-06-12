---
title: "I installed my wireless USB adapter's driver with ndiswrapper, now what?"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by Hexifford on 2009-03-01
I got the inf file for my D-Link WUA-2340 wireless adapter installed with ndiswrapper and it says the device is present when I sudo ndiswrapper -l, but in network manager it still only has the eth0 thing. The light on my adapter isn't turning on either. I'm guessing that I've still got a lot of messing around to do with netowork manager... can someone help me please?

Kubuntu Intrepid

---

### Post by ibutho on 2009-03-01
Can you check the chipset being used by the wireless card. To do that, enter the commands below and post back the output
```
sudo lspci | grep -i net
```
```
lshw -C network
```
and
```
lsusb
```

---

### Post by Hexifford on 2009-03-01
This is what I got when I put in sudo lspci | grep -i net:
```
04:07.0 Broadcom Corporation BCM4401-B0 100Base-1X (rev 02)
```
This is what I got from putting in lshw -C network:
```
*-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: eth0
       version: 02
       serial: 00:13:72:30:1e:b7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:43:02:bb:94:f0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```
This is what I got from putting in lsusb:
```
 Bus 002 Device 004: ID 07d1:3a08 D-Link System predator Bootloader Download
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 045e:00f9 Microsoft Corp.
Bus 001 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

The Broadcom thing that I got from sudo lspci | grep -i net is the built in thing that came with my computer for a wired internet connection. But since I'm using a wireless network now, I can't use that anymore. I need to get the D-Link USB adapter working.

---

### Post by ibutho on 2009-03-01
To me, it appears that the system is not correctly identifing the wireless card. There is a [guide]("https://help.ubuntu.com/community/WifiDocs/Device/D-Link_WUA-2340") that may help you get that card working on your system. Hope that helps.

---

