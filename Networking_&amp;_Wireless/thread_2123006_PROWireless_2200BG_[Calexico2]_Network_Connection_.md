---
title: "PRO/Wireless 2200BG [Calexico2] Network Connection problems"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by andyn11 on 2013-03-06
i know its an old network card and needs drivers but iam new to linux and would love some help here



andy@andy-330:~$ sudo lshw -C network
  *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:7f:df:24
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:dfffc000-dfffcfff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth0
       version: 10
       serial: 00:14:2a:b7:27:2a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.50.104 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:17 ioport:d800(size=256) memory:dfffbc00-dfffbcff
andy@andy-330:~$

---

### Post by chili555 on 2013-03-06
It appears to have all the driver it needs. However, it also appears that there is another problem:> *-network:0 [COLOR="#FF0000"]DISABLED[/COLOR]
description: Wireless interface
product: PRO/Wireless 2200BG [Calexico2] Network Connection
vendor: Intel CorporationLet's have a look at:```
rfkill list all
dmesg | grep ipw
```Thanks.

---

### Post by andyn11 on 2013-03-06
andy@andy-330:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
andy@andy-330:~$ dmesg | grep ipw
[   25.142961] libipw: 802.11 data/management/control stack, git-1.1.13
[   25.142968] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   25.187072] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   25.187079] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   25.187293] ipw2200 0000:00:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   25.187333] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   25.805016] ipw2200: Radio Frequency Kill Switch is On:
[   25.823102] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   28.160018] ipw2200: Failed to send POWER_MODE: Command timed out.
[   32.824036] ipw2200: Failed to send POWER_MODE: Command timed out.
andy@andy-330:~$

---

### Post by chili555 on 2013-03-06
> 0: phy0: Wireless LAN
Soft blocked: no
[COLOR="#FF0000"]Hard blocked: yes[/COLOR]>  ipw2200: Radio Frequency Kill Switch is On:Find the wireless switch on your laptop, switch it and you'll be all set.

---

### Post by andyn11 on 2013-03-06
its not doing anything

---

### Post by chili555 on 2013-03-06
What is the make and model of laptop? Is there a physical switch or a key combination such a Fn+F5 or, as on my Lenovo, both?

Off for the evening. I'll see you tomorrow.

---

### Post by andyn11 on 2013-03-06
there is a button next to my power button with wifi sign on it maybe its broke ... will take it into my local pc repair shop

---

### Post by andyn11 on 2013-03-07
i have an old infinity 330 laptop

---

### Post by chili555 on 2013-03-07
I wonder if this may be helpful: [http://ubuntuforums.org/showthread.php?t=1538766](http://ubuntuforums.org/showthread.php?t=1538766)

---

### Post by thedreamer69 on 2013-04-29
Just to say many thanks to chili555. 
I've solved my wireless issue ("[COLOR=#000000] [/COLOR][COLOR=#417394]Failed[/COLOR][COLOR=#000000] to [/COLOR][COLOR=#417394]send[/COLOR][COLOR=#000000] [/COLOR][COLOR=#417394]POWER_MODE[/COLOR][COLOR=#000000]: Command timed out") reading his threads.
On Acer old laptop there is a wireless switch....
Best regards.
G[/COLOR]

---

