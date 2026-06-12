---
title: "Intermittent Wired Connection"
date: 2012-01-21
forum: Networking &amp; Wireless
---

### Post by AustenB on 2012-01-21
Hello,

I just installed Ubuntu 11.10 a couple days ago (I now dual-boot with windows 7).  The first issue I had after installation was that updates would quit in the middle of downloading all of them, and I'd have to restart the update again.  I finally got the updates now, but I now notice my internet connection intermittently drops out.

Here is some hardware information:

```
~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GF104 [GeForce GTX 460] (rev a1)
01:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation GF104 [GeForce GTX 460] (rev a1)
02:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)
04:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
06:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
07:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
09:00.0 IDE interface: Marvell Technology Group Ltd. Device 91a3 (rev 11)

```Here is some network information:

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:d3:48:21:15  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:d3ff:fe48:2115/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:258432 errors:0 dropped:258432 overruns:0 frame:258432
          TX packets:174860 errors:0 dropped:248 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:343963671 (343.9 MB)  TX bytes:14673279 (14.6 MB)
          Interrupt:50 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2713538 (2.7 MB)  TX bytes:2713538 (2.7 MB)

``````
~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0

```

Any help is greatly appreciated!

---

### Post by AustenB on 2012-01-23
bump.

---

### Post by AustenB on 2012-01-24
bump.

---

### Post by AustenB on 2012-01-26
bump.

---

### Post by AustenB on 2012-01-28
I managed to solve the issue after doing some googling.

The network card has bugs with ubuntu (Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller).

If you have the same card, here is a link that provides a fix.

[http://amk1.wordpress.com/2009/06/09/realtek-8168-module-issue/](http://amk1.wordpress.com/2009/06/09/realtek-8168-module-issue/)

A couple edits for this fix:

[LIST]
[*]_All_ commands require the prefix "sudo"
[*]After performing the command "sudo make clean modules && make install", type "sudo nautilus". Locate the folder for the driver you just extracted, and copy "r8168.ko" from its src folder.  Now navigate to "/lib/modules".  Open the folder for the latest module, and go to "~/kernel/drivers/net".  Paste "r8168.ko" into this folder.  Rename "r8169.ko" to "r8169.koold".  Exit the nautilus window.  Follow the rest of the directions; you shouldn't have to blacklist r8169.
[/LIST]

---

### Post by revoice on 2012-03-18
> **AustenB said:**
> I managed to solve the issue after doing some googling.

The network card has bugs with ubuntu (Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller).

If you have the same card, here is a link that provides a fix.

[http://amk1.wordpress.com/2009/06/09/realtek-8168-module-issue/](http://amk1.wordpress.com/2009/06/09/realtek-8168-module-issue/)

A couple edits for this fix:

[LIST]
[*]_All_ commands require the prefix "sudo"
[*]After performing the command "sudo make clean modules && make install", type "sudo nautilus". Locate the folder for the driver you just extracted, and copy "r8168.ko" from its src folder.  Now navigate to "/lib/modules".  Open the folder for the latest module, and go to "~/kernel/drivers/net".  Paste "r8168.ko" into this folder.  Rename "r8169.ko" to "r8169.koold".  Exit the nautilus window.  Follow the rest of the directions; you shouldn't have to blacklist r8169.
[/LIST]


You are abso-******-lutely amazing

thank you!! :guitar:

---

