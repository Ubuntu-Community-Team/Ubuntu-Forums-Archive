---
title: "BCM4306 (rev 02) 14e4:4324 on b43legacy unavailable"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by wolfgentleman on 2013-01-27
I am running Linux Mint 13 Maya KDE and the wifi card shows the connection state as unavailable and does not scan. It says the the current drivers are b43legacy. I tried installing b43 drivers and it stopped even seeing my wifi card. I had to reinstall the OS to get it to see the card again. This is an old laptop, Gateway M275.

---

### Post by praseodym on 2013-01-27
Did you install the firmware via '''linux-firmware-nonfree'''?

---

### Post by wolfgentleman on 2013-01-27
When I installed the b43 firmware I used the b43-fwcutter to install it using the instructions from wireless.kernal.org that used the archive file. However when I first installed Linux Mint it already had b43legacy drivers being used.

---

### Post by wolfgentleman on 2013-01-28
bump

---

### Post by wolfgentleman on 2013-01-28
```
sudo lspci -vvnn | grep 14e4
``` Produces:```

02:04.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 02)
        Subsystem: Broadcom Corporation Device [14e4:0421]
```

---

### Post by wolfgentleman on 2013-01-28
```
sudo lshw -C network
```Produces:```

  *-network:0             
       description: Network controller
       product: BCM4306 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:10 memory:e0200000-e0201fff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:6d:4e:f6
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.50 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:e0204000-e0204fff ioport:4000(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:8b:59:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43legacy driverversion=3.2.0-23-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```

---

### Post by praseodym on 2013-01-28
Try this firmware package:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
From here:

[http://forum.ubuntuusers.de/topic/netzwerkkarte-nach-deaktivierung-im-autostart/#post-2480236](http://forum.ubuntuusers.de/topic/netzwerkkarte-nach-deaktivierung-im-autostart/#post-2480236)

---

### Post by wolfgentleman on 2013-01-28
A MILLION THANKS!!!! My wifi is working like a charm!

---

