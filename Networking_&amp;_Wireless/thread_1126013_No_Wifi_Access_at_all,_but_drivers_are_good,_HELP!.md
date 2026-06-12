---
title: "No Wifi Access at all, but drivers are good, HELP!!!"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by Kilroyy on 2009-04-15
ok this is my first venture into a linux OS, and I can say so far I'm very pleased. 
    now on to my issue

I have a compaq presario C700 US running Ubuntu 8.10. 
using a ethernet cable I did all the updates and had everything running smoothly EXEPT the wifi. this particular pc has a button to turn on/off wifi, it does Nothing in ubuntu. just stays red. under system drivers it tells me the driver is active and in use, yet I have no access to any wifi. I've tried for HOURS and HOURS over the last two days to figure this out, running everything I could find from madwifi, ndiswap, and about a good 2 dozen other walkthroughs with no change .  

the wifi adapter is 
Atheros AR5007 802.11b/g WiFi Adapter

if ANYONE has any idea of how to help I would greatly appreciate it!

---

### Post by livid86 on 2009-04-15
How are you searching for networks?

---

### Post by Kilroyy on 2009-04-15
I've tried using the network manager but I get messages that no wifi adapter is present.

---

### Post by Kilroyy on 2009-04-15
went to terminal and typed lshw -C network it returned....

kilroy@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:78:bb:72
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.3 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f6:aa:ab:e5:cf:10
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


kilroy@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
kilroy@ubuntu:~$

---

### Post by Kilroyy on 2009-04-15
anyone???

---

### Post by t0mppa on 2009-04-15
You didn't disable the Hardware Drivers when you tried all those solutions? Should always do that, if you try to install a new set of drivers, after all only one set of drivers can function at one time. And if you had multiple drivers trying to vie for control, it's no wonder none of the solutions worked. Generally either the MadWifi or NDISwrapper work for these chips.

And the button for switching WiFi on/off on your computer most likely works just fine, it's just the led that isn't getting any feedback.

---

