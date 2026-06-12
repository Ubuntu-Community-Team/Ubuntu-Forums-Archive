---
title: "lshw -C networking shows USB wifi disabled?"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by hattrickinc on 2010-03-03
Hey guys! 

New to the site, first post (thank you, thank you).. lol I hope to be here all the time helping as much as I can! 


Hopefully you can help me with my problem.. I was using my usb Alfa AWUS036H-v5 usb wifi card, and then after I rebooted, it randomly stopped working.. did some searching on the site, one idea was to do ```
sudo lshw -C networking 
``` , which I did, and it shows my internal wifi card (iwl3945) working fine, but says my wlan7 (Alfa usb) as:

network* Disabled

Also, in the upper right hand corner, the antenna is greyed out and says "Device Not Ready"

Any ideas? 

Thanks in advance =)

---

### Post by chili555 on 2010-03-03
I don't think lshw would show USB devices at all. lsusb shows USB devices. Also, the command is:```
sudo lshw -C network
```No [COLOR="Blue"]ing[/COLOR]. Any interesting reason you need two wireless devices working at the same time?

---

### Post by hattrickinc on 2010-03-03
I don't need two at the same time..the range on my internal one sucks, and the USB one picks up quite a few more. 

Sorry I put the ING- I was typing this on my phone lol
It still shows network* Disabled... any idea how to remove this? 

thank you for your help..

---

### Post by Enigmapond on 2010-03-03
well I would get rid of one wireless card as they may be competing/conflicting with each other and then right-click on the network manager icon and enable the network.....

---

### Post by chili555 on 2010-03-03
> It still shows network* Disabled... any idea how to remove this?As I said, USB devices do not show in lshw. Please post it for our inspection.

---

### Post by hattrickinc on 2010-03-03
Nick@MSIWind:~$ sudo lshw -C network
[sudo] password for Nick: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:55:69:9b
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:d000(size=256) memory:ffd10000-ffd10fff(prefetchable) memory:ffd00000-ffd0ffff(prefetchable) memory:dfd00000-dfd1ffff(prefetchable)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:01:8f:32
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.109 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:dfc00000-dfc00fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan6
       serial: 00:c0:ca:39:af:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by chili555 on 2010-03-03
> driver=iwl3945 ip=192.168.1.109Does Network Manager have it stopped because your internal network device is connected? Can you manipulate the switch or key combination to turn off the internal device?> *-network DISABLED
description: Wireless interface
physical id: 2
logical name: wlan6
serial: 00:c0:ca:39:af:fbI guess I learn something new every day.

---

