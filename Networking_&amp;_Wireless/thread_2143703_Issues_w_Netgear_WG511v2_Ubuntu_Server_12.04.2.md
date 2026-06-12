---
title: "Issues w/ Netgear WG511v2 Ubuntu Server 12.04.2"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by Me0wCat on 2013-05-09
Hello all. Please give me grace as this is my first post.

Ive been noobing around with an old Dell Inspirion 2650 and had Lubuntu 12.10 running on it. I had ordered a Netgear WG511v2 and had installed it using the instructions provided here: [http://forum1.netgear.com/showthread.php?t=35739](http://forum1.netgear.com/showthread.php?t=35739) and it worked perfectly. I then decided to wipe Lubuntu and install Ubuntu Server 12.04.2. I installed the netgear drivers using ndiswrapper in the same manner as before. All seemed well until i try and connect to a wireless network. i have no wireless extensions when i run iwconfig and there is no reference to wlan anywhere. Ive hunted around for a couple hours and have yet to find a solution. Help?

lspci, lshw -C network, ndiswrapper -l output:

```
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 05)00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 05)
00:1d.0 USB controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 Go] (rev b2)
02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)





  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 78
       serial: 00:08:74:3c:9d:aa
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=10.42.0.70 latency=80 maxlatency=10 mingnt=10 multicast=yes port=MII speed=100Mbit/s
       resources: irq:10 ioport:3000(size=128) memory:e8000000-e800007f memory:14000000-1401ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:1c000000-1c00ffff memory:1c010000-1c01ffff
















mrv8335 : driver installed
    device (11AB:1FAA) present
```

---

### Post by ahallubuntu on 2013-05-09
~

---

