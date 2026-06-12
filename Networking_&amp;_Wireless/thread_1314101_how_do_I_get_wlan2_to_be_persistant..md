---
title: "how do I get wlan2 to be persistant."
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by dvdljns on 2009-11-04
I have been trying to set up a netgear wg311v3. I was having no luck so I got a a usb that uses a rtl8087l chip. ubuntu 8.04 has the driver built into the kernel for that card. While I was trying to get connected with that card my netgear card started working but even though ndiswrapper wrote wlan0 as elias for my netgear card. ubuntu sees my wg311 card as wlan2. I do not know whats going on but I have 2 problems if I turn off are reboot my comp. I have to plug in the usb card before wlan2 will show up. after I get connected I can unplug the usb card. but I need to get get wlan2 to stay after a reboot since I need the usb card in another comp. besides plugging in the usb and unplugging it is getting to be a pain. how do I resolve this.

```


  *-network:0
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: wlan2
       version: 03
       serial: 00:22:3f:e7:07:80
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg311v3 driverversion=1.52+NETGEAR,02/22/2005,3.1.1.7 ip=192.168.1.103 latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:19:21:04:bb:9d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s


```

---

### Post by oldrocker99 on 2009-11-05
I'm running Karmic, and I had to use ndiswrapper and the XP driver to get it working. Still, I have to run

sudo modprobe ndiswrapper

at bootup to get it online. Grrr.

---

### Post by dvdljns on 2009-11-06
> **oldrocker99 said:**
> I'm running Karmic, and I had to use ndiswrapper and the XP driver to get it working. Still, I have to run

sudo modprobe ndiswrapper

at bootup to get it online. Grrr.

Look around in the posts here. there is a file you sometimes have to add modprobe to by hand sometimes. also make sure you do ndiswrapper -m

here is what my problem was.

[http://ubuntuforums.org/showthread.php?t=1315441&highlight=answer](http://ubuntuforums.org/showthread.php?t=1315441&highlight=answer)

---

