---
title: "getting ad hoc wireless going"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by bu2971x on 2009-04-10
here is my info...............

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

what do I need to do to get wireless going in 8.04.?
I use eth0 ok but lo is idle and doesnt do anything.I want to get wireless going first and then set up an ad hoc direct wireless connection
between my Laptop and an HP officejet printer that has wireless built in.
Model J4680 .The printer works perfectly in Ubu 8.04.
It says it can be done but the usual way is through a driver they supply for XP and Mac.
Any info much appreciated.

---

### Post by superprash2003 on 2009-04-11
post output of the following
1)iwlist scanning
2)lshw -C network
3)iwconfig

---

### Post by bu2971x on 2009-04-11
lo        no wireless extensions.

eth0      no wireless extensions.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

the other one is too big to paste.
by the way, is the new 9.04 better and maybe its best to just dump 8.04
and upgrade..??   what do you think?? it would have all the wireless and ethernet ready to go..no???

---

### Post by superprash2003 on 2009-04-13
9.04 hasnt officially been launched.. being a new OS , could have a lot of bugs .. it would not be as stable as 8.10 .. you can give it a try on vmware or a spare machine.. you would need to post all outputs if you wish to diagnose the problem..

---

### Post by bu2971x on 2009-04-13
description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:54:3e:40
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=70.41.234.118 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes

here is the rest....  what am I  missing..??

---

### Post by superprash2003 on 2009-04-14
output of
1)iwconfig
2)ifconfig

---

### Post by bu2971x on 2009-04-14
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:54:3e:40  
          inet addr:72.4.56  Bcast:72.173..255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:255965 (249.9 KB)  TX bytes:25559 (24.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1176 (1.1 KB)  TX bytes:1176 (1.1 KB)

lo no wireless extensions.

eth0 no wireless extensions.

---

### Post by superprash2003 on 2009-04-16
look at this [http://www.linuxquestions.org/questions/linux-newbie-8/wlan-issue-intel-corporation-prowireless-3945abg-network-connection-674952/](http://www.linuxquestions.org/questions/linux-newbie-8/wlan-issue-intel-corporation-prowireless-3945abg-network-connection-674952/)

---

### Post by bu2971x on 2009-04-16
I did the backport thing and it doesnt work. I would think the Intel
card is the most common amd any problems with it would have been fixed a long time ago. Apparently not. For christs sake fix it in 9.04...

---

