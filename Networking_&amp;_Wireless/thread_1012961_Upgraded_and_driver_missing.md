---
title: "Upgraded and driver missing"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by babujbf on 2008-12-16
So I did some updates on my hardy system, and my wireless restricted drivers disappeared and they no longer appear on the restricted driver manager. What can I do?

---

### Post by Joe2Shoe on 2008-12-16
Go into Synaptic Package Manager and add the restrictive repositories, then download them.

---

### Post by babujbf on 2008-12-16
all reps are enabled, download what the drivers? I don't remember the name of the driver. How can I find it?

---

### Post by babujbf on 2008-12-16
anyone?

---

### Post by Ayuthia on 2008-12-16
Please post the results of:
```
lspci -nn
lshw -C network
```
That will help us identify your wireless card and possibly point you in the right direction.

---

### Post by babujbf on 2008-12-16
Oh if you wanna know my wireless card, it is WDA-1320 but there are no linux drivers for it if thats what you are thinking about. Therefore I need the restricted driver I was using before. Here are the results anyways.

for lspci -nn

00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon Xpress 200 Host Bridge [1002:5a33] (rev 01)
00:02.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI-X Root Port [1002:5a34]
00:11.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:437a] (rev 80)
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 81)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] [1002:7142]
01:00.1 Display controller [0380]: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary) [1002:7162]
02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:03.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
02:04.0 Communication controller [0780]: Conexant HSF 56k Data/Fax Modem [14f1:2f20]

for lshw -C network

WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:16:76:dd:26:08
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.0.0.67 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=28 mingnt=10

---

### Post by Ayuthia on 2008-12-16
Have you checked to see if linux-backports-modules-intrepid-generic is installed?

---

### Post by babujbf on 2008-12-16
I have linux-backports-modules-2.6.24-16-generic intrepid does no appear on synaptic search, all repos are enabled...

Note: I am running Hardy

---

### Post by babujbf on 2008-12-16
any ideas?

---

### Post by theDaveTheRave on 2009-01-29
Babujbf

Have you been able to "fix" this problem??

I'm curious as i have exactly the same issue, I have a thread out there where previously I just removed the "offending" drivers, rebooted, reloaded them and then rebooted again (a bit long winded but it worked!), but on this occasion the wifi card will still not work.

Unfortunately I have now buggered around with modprobe so much I may well have broken the card untill I do a clean install.... I just need to find the instalation disk that I used to have!

Otherwise I am now hearing from friends that Intrepid is much better than it was 4 months ago.... it completely caned my system!

So maybee I need to do a clean upgrade....?

Have you checked to see if a live CD works for you? I would use one if I could find one!

When I used to install I didn't even need to hard wire into the net, it would just work straight off the wireless, no hassles at all.

But this seems to happen to me far too often, and seemingly to everyone else as well!

David

---

