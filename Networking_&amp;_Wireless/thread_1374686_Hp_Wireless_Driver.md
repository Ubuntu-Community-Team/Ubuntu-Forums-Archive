---
title: "Hp Wireless Driver"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by donamin on 2010-01-07
Hi. I Have a hp Pavilion DV3 2005ee Notebook by vista default OS.
recently, i installed linux on my system. but wireless doesn't seem to be working.
can you help me? 
thanks

---

### Post by H3LlIoN on 2010-01-07
They are gonna need more info.  For starters, run terminal and type following commands:

lspci -nn
lshw -C Network 
then copy/paste results here.  They are also going to need to know what version of Ubuntu you are running.

Good luck

---

### Post by donamin on 2010-01-07
i'm using ubuntu 9.1...

lspci -nn


00:00.0 Host bridge [0600]: 
Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)

00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)

00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)

00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G98M [GeForce G 105M] [10de:06ec] (rev a1)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)



lshw -C Network


WARNING: you should run this program as super-user.
  *-network               

       description: Network controller
       product: BCM4312 802.11b/g

       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       
version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list

       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:dc000000-dc003fff

  *-network
       description: Ethernet interface
       
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       
vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       
bus info: pci@0000:05:00.0
       logical name: eth0
       version: 03
       serial: 00:23:5a:44:a2:69

---

### Post by bkratz on 2010-01-07
The BCM4312 is supposedly covered by this

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by PauGNU on 2010-01-07
Basically, you need to connect your pc via ethernet (just for a while) and go to: System > Administration > Hardware drivers. There you'll see this driver related to broadcom. Install it and reboot your computer. Now you'll be able to see wireless networks.

---

