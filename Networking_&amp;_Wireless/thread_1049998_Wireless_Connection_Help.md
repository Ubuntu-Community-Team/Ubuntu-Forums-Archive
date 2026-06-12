---
title: "Wireless Connection Help"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by Dombie on 2009-01-25
I'm completely new to Linux but I was told to start with Ubuntu, so I got hold of the 32bit disc and dual booted with Windows xp professional (32 bit as well).
I put the disc in and let it do all its work setting it up, doing what was needed when prompted. Once it was done i followed a guide to connect to the internet (wireless) and the first bit it said was "system>administration>network" but i cannot find "network".

I'm on wireless and using NETGEAR as my connection point to my hub downstairs. Any help on how to get connected would be really appreciated!

Thanks in advance!

---

### Post by Kevbert on 2009-01-25
Welcome to Ubuntu.
It's likely that you need to install some firmware drivers for your wireless adapter. In order to do this, we first need to find out what chipset your wireless is based upon.  In order to do this go to Applications-Accessories-Terminal and type in
```
lspci
iwconfig
ifconfig
```
It may just be that wireless is not switched on. If you go to the two-display icon in the top righthand corner of the display and right-click on it with the mouse, make sure Enable wireless and Enable network is ticked (if you can't do this you need the drivers). If you can, by left-clicking on the same icon, you should get a display of all the available networks.

---

### Post by Dombie on 2009-01-25
> **Kevbert said:**
> Welcome to Ubuntu.
It's likely that you need to install some firmware drivers for your wireless adapter. In order to do this, we first need to find out what chipset your wireless is based upon.  In order to do this go to Applications-Accessories-Terminal and type in
```
lspci
iwconfig
ifconfig
```
It may just be that wireless is not switched on. If you go to the two-display icon in the top righthand corner of the display and right-click on it with the mouse, make sure Enable wireless and Enable network is ticked (if you can't do this you need the drivers). If you can, by left-clicking on the same icon, you should get a display of all the available networks.

Ok i went into the terminal and typed in what you said (terminal is so much better than windows control pannel!).
What bit should i be looking at?

Oh and thanks of the fast reply!

---

### Post by VirtualEdgar on 2009-01-25
Hi Dombie,

The Terminal (Applications/Accessories/Terminal) is like a command prompt in your Windows. Type the commands that are given to you in there then post the result back in here. :)

Good luck!

---

### Post by Dombie on 2009-01-25
scott@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
scott@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

scott@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:83:8e:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2362418518 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:222 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)

scott@ubuntu:~$

---

### Post by Kevbert on 2009-01-25
The response from those commands suggest that wireless hasn't been found at all. Do you have a switch for turning on the wireless ? If so, please press it once and then try
```
lspci 
```
again. Are you using a USB device ? If so, post the output of
```
lsusb
```
If none of these options work, please state the make and model of PC and the wireless adapter make and model (if known).

---

### Post by Dombie on 2009-01-25
> **Kevbert said:**
> The response from those commands suggest that wireless hasn't been found at all. Do you have a switch for turning on the wireless ? If so, please press it once and then try
```
lspci 
```
again. Are you using a USB device ? If so, post the output of
```
lsusb
```
If none of these options work, please state the make and model of PC and the wireless adapter make and model (if known).


scott@ubuntu:~$ lsusb

Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 004: ID 0846:7100 NetGear, Inc. WN121T Wireless Adapter

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 004: ID 05b8:3106 Agiler, Inc. 

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 003: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



My wireless is called NETGEAR (you can see it above

---

### Post by Kevbert on 2009-01-25
You'll need to install the firmware via ndiswrapper (to install the windows drivers).  You can install ndiswrapper and ndisgtk via the installation CD. Pop the Cd in the drive and browse to /pool/main/n in there you'll find folder for ndiswrapper and ndisgtk. In each of these you'll find a .deb file, double click on each of the .deb files to install them.
Now you need the windows drivers which you can get from [[COLOR="Red"]here[/COLOR]]("http://www.freewebs.com/duckles/netgearwn121tdriver.htm"). Copy the WN121T.inf and WN121TXP.sys files to your home folder by right clicking on them and selecting Save Link As. 
Now go to System-Administration-Windows Wireless Drivers (this is ndisgtk).
Click on Install New Driver and point it to your downloaded WN121T.inf file that you've just saved.
It should now be possible to turn on and use wireless (I'm not sure if you need to perform a reboot first).

---

### Post by Dombie on 2009-01-25
> **Kevbert said:**
> You'll need to install the firmware via ndiswrapper (to install the windows drivers).  You can install ndiswrapper and ndisgtk via the installation CD. Pop the Cd in the drive and browse to /pool/main/n in there you'll find folder for ndiswrapper and ndisgtk. In each of these you'll find a .deb file, double click on each of the .deb files to install them.
Now you need the windows drivers which you can get from [[COLOR="Red"]here[/COLOR]]("http://www.freewebs.com/duckles/netgearwn121tdriver.htm"). Copy the WN121T.inf and WN121TXP.sys files to your home folder by right clicking on them and selecting Save Link As. 
Now go to System-Administration-Windows Wireless Drivers (this is ndisgtk).
Click on Install New Driver and point it to your downloaded WN121T.inf file that you've just saved.
It should now be possible to turn on and use wireless (I'm not sure if you need to perform a reboot first).

Thank you so much!
I'll give that a go when I go back on Ubuntu tomorrow!
Hopefully it will work :)

---

