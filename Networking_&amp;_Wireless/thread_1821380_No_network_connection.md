---
title: "No network connection"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by pepribal on 2011-08-09
Hi,

I've got a broadband connection that uses the Vodafone HG556a router. The problem is that Ubuntu (11.04) doesn't connect: it keeps trying for a while (like a minute or so), and then gives up.

On the other hand, wifi connections work perfectly well, it's just tha cable connection. I've tried with different cables, with the same result.

I've deleted and reconfigured the wired connection many times. I usually go for the auto eth connection, with the default parms. Nothing seems to work.

Any ideas?

Thx.

---

### Post by garvinrick4 on 2011-08-09
Network manager basically sets itself up. What is the driver, that is the culprit maybe.
Unusual mostly wired works and wifi does not.
Open a terminal and copy and paste these commands.
```
sudo lshw -C network
``````
lspci -k
```Show us just the network cards in the lspci -k

---

### Post by pepribal on 2011-08-09
The **lspci** command yields:

```
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Wistron Corp. Device 1053
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
```While the **lshw** yields:

```
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth0
       version: 10
       serial: 00:00:e2:a0:bd:43
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 ioport:2000(size=256) memory:ec005000-ec0050ff memory:90020000-9002ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:21:91:84:31:e9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.38-10-generic firmware=1.7 link=no multicast=yes wireless=IEEE 802.11bg
```Any clue?

---

### Post by garvinrick4 on 2011-08-09
Does not look to be a problem but I have read 20 articles on the 2 drivers listed though 8139too and 8139cp. 8139too is the correct one. I will bump this to the front there has got to be Many users who have this card been around forever. I believe a user name chili555 has a box with this card and if no one gives you a solution I will ask him to help you out.
I would have blacklisted 8139cp but that does not seem to do it in Forums I have searched.
Someone give this user a hand please.

---

