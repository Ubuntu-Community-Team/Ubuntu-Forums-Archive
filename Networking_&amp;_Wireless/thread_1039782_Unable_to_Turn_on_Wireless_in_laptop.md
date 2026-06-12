---
title: "Unable to Turn on Wireless in laptop"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by crazeepingu on 2009-01-14
I am new to ubuntu and i installed 8.10 on my HP Pavilion zv6000. It has broadcom wireless card and i could install windows driver using ndis-gtk. The hardware is detected but i am unable to turn the wireless device ON. I ran following commands and have following results. I would appreciate if someone can help me use wireless with ubuntu.

sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bd:2d:26
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:6a:60:fe
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 86:4e:04:75:b8:cc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by skern03 on 2009-01-14
> **crazeepingu said:**
> I am new to ubuntu and i installed 8.10 on my HP Pavilion zv6000. It has broadcom wireless card and i could install windows driver using ndis-gtk. The hardware is detected but i am unable to turn the wireless device ON. I ran following commands and have following results. I would appreciate if someone can help me use wireless with ubuntu.


I'm running Ubuntu 8.10 on an old Dell laptop with a virtually identical card and Broadcom chipset (wireless 802.11 b/g), and did not need to install the windows driver. There's a proprietary driver installed on my system named "Broadcom B43 wireless driver."

You can find this under Systemn, Administration, Hardware Drivers. See if you can add that driver to your system, and ditch the windows driver.

Also, check System, Preferences, Network. It's a GUI into the net config. See what wireless networks are available and configured (it's the second tab from the left). 

Are you sure you set the network up correctly, i.e., DHCP or preset IP address?

---

### Post by crazeepingu on 2009-01-15
I cant find the proprietary driver that you mentioned. I checked under Systemn, Administration, Hardware Drivers but it does not list drivers for the wireless card. 

Also i cant see any wireless network. I think as i mentioned earlier the problem is to turn on the wireless card. the out put of "sudo lshw -C network" command shows 

*-network:0 DISABLED
description: Wireless interface

In the help under wireless troubleshooting it says 
"Disabled - see Section 3.3.1 &#8213; Check that the device is on." So if you can please help me to turn on the device. I did click the device turn on/off switch but that does not help

---

### Post by crazeepingu on 2009-01-15
I used wired connection to connect to the internet and updated ubuntu. After the update when i restarted my computer i was surprised to see that it detected wireless card and it was turned ON. I simple had to configure my network and it all worked. Now i am so happy to use wirless with Ubuntu.:guitar:

---

### Post by skern03 on 2009-01-15
> **crazeepingu said:**
> I used wired connection to connect to the internet and updated ubuntu. After the update when i restarted my computer i was surprised to see that it detected wireless card and it was turned ON. I simple had to configure my network and it all worked. Now i am so happy to use wirless with Ubuntu.:guitar:

Great! Now that I think about it, that's what I did as well - connected through a wired connection first with the card inserted. Glad you got it working!

Please mark the thread solved. Go to Thread Tools at the top of this thread, and click it, select Mark as Solved. That way others will benefit from this!

---

