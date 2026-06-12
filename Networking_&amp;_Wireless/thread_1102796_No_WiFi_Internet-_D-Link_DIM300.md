---
title: "No WiFi Internet- D-Link DIM300"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by dealcorn on 2009-03-22
WiFi does not work on the Ubuntu 8.04 side of my dual boot machine (Intel D945GCLF2 motherboard, D-Link DIR300 router and Ralink USB adapter).  I can connect to and administer the router using its access point so the problem may be limited to Internet connectivity.  After reading other posts, I ran lsusb, lspci, dmesg | grep eth0,lsmod | grep ndiswrapper,  and  route with the results listed below.  Curiosly, internet access used to work and then stopped.  I have a similar situation on my other dual boot machine which uses a D-Link usb dongle (used to work then stopped at about the same time).

dea@u8:~$ lsusb
[INDENT]Bus 005 Device 002: ID 148f:2573 Ralink Technology, Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 [/INDENT] 
dea@u8:~$ lspci
[INDENT]00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)[/INDENT]
dea@u8:~$ dmesg | grep eth0
[INDENT][   31.477276] eth0: RTL8168c/8111c at 0xf8828000, 00:1c:c0:a8:f6:a7, XID 3c4000c0 IRQ 220
[   49.254229] r8169: eth0: link down
[   49.255725] ADDRCONF(NETDEV_UP): eth0: link is not ready[/INDENT]
dea@u8:~$lsmod | grep ndiswrapper
[INDENT]search dim2400 DIM2400
nameserver 192.168.0.1[/INDENT]dea@u8:~$ route
[INDENT]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0[/INDENT]
dea@u8:~$

---

### Post by dealcorn on 2009-03-22
Upon reflection I should correct an error and try some other stuff before posting this question.  I will repost with more accurate information if need arises.  Consider this thread dead.

---

