---
title: "wireless doesn't work"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by Mina Fouad on 2010-07-28
Hi all,
after I installed Ubuntu, the WLAN doesn't work and I think It needs a drive to work on Ubuntu.
the problem I didn't find the appropriate drive
my laptop: Fujitsu Siemens Amilo li 1818
any help will be appreciated.

---

### Post by displayaway on 2010-07-28
The first step is to share the output of these commands. They should point to your next step.

lspci
lshw -class network

---

### Post by Mina Fouad on 2010-07-28
```

lspci

```

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


```


```
lshw -class network
```
```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:60:fc:11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.32 latency=32 maxlatency=64 mingnt=32 multicast=yes

```

---

### Post by bkratz on 2010-07-28
since there doesn't seem to be an entry for "network controller" in the lspci listing, you might also want to post the output of lsusb in case it is on an internal usb bus.  Also, check the bios and make sure there is no way to accidentally turn it off.

---

### Post by Mina Fouad on 2010-07-28
> **bkratz said:**
> since there doesn't seem to be an entry for "network controller" in the lspci listing, you might also want to post the output of lsusb in case it is on an internal usb bus.  Also, check the bios and make sure there is no way to accidentally turn it off.
please be more clear am new to ubuntu.

---

### Post by bkratz on 2010-07-28
> **Mina Fouad said:**
> please be more clear am new to ubuntu.

Normally with lspci you would see something like

```
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
```


The one labeled Network controller is the wireless card in this case a BCM4318.  lsusb (LSUSB in lowercase )gives a similar output for usb devices, which may be where your wireless card is "hiding".

---

### Post by Mina Fouad on 2010-07-29
so, what should I do ???

---

### Post by Mina Fouad on 2010-07-30
please, any one can help do>>>>>

---

### Post by DEVIL DOG on 2010-07-30
I'm no expert, but have you tried going to System>Administration>Hardware Drivers using your wired connection?

---

### Post by bkratz on 2010-07-30
> **Mina Fouad said:**
> so, what should I do ???

A quick googlubuntu of Amilo li 1818 shows a number of theads all of which show it is a usb device. You need to verify this by using the terminal and typing in lsusb (LSUSB in lowercase) and posting it here.  Here is the typical line I found in one of the threads.

Bus 001 Device 002: ID 0bf8:100f Fujitsu Siemens Computer,

 yours of course may vary.

Here is the link showing a search for the ID number. 0bf8:100f. All of the threads seem to be a few years old, but they all reflect the use of ndiswrapper and the XP (Windows) version of the drivers.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&cof=FORID:9&ie=UTF-8&q=0bf8:100f&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&cof=FORID:9&ie=UTF-8&q=0bf8:100f&as_qdr=all&sa=Google+Search&lang=en)


After you check lsusb we can proceed.

---

### Post by Mina Fouad on 2010-07-30
> **DEVIL DOG said:**
> I'm no expert, but have you tried going to System>Administration>Hardware Drivers using your wired connection?
yes I tried but noway

---

### Post by Mina Fouad on 2010-07-30
> **bkratz said:**
> A quick googlubuntu of Amilo li 1818 shows a number of theads all of which show it is a usb device. You need to verify this by using the terminal and typing in lsusb (LSUSB in lowercase) and posting it here.  Here is the typical line I found in one of the threads.

Bus 001 Device 002: ID 0bf8:100f Fujitsu Siemens Computer,

 yours of course may vary.

Here is the link showing a search for the ID number. 0bf8:100f. All of the threads seem to be a few years old, but they all reflect the use of ndiswrapper and the XP (Windows) version of the drivers.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&cof=FORID:9&ie=UTF-8&q=0bf8:100f&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&cof=FORID:9&ie=UTF-8&q=0bf8:100f&as_qdr=all&sa=Google+Search&lang=en)


After you check lsusb we can proceed.

I checked lsusb and this is the result:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bf8:100f Fujitsu Siemens Computers 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
I followed the instructions that included in [this link]("https://wiki.ubuntu.com/LaptopTestingTeam/Old/FujitsuAmiloLi1818") but I didn't find xp sis163u ??? !!

---

### Post by bkratz on 2010-07-30
> **Mina Fouad said:**
> I checked lsusb and this is the result:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bf8:100f Fujitsu Siemens Computers 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
I followed the instructions that included in [this link]("https://wiki.ubuntu.com/LaptopTestingTeam/Old/FujitsuAmiloLi1818") but I didn't find xp sis163u ??? !!




Found this link

[http://ubuntuforums.org/archive/index.php/t-446024.html](http://ubuntuforums.org/archive/index.php/t-446024.html)

the post from user welshlion  give a link to the source file for SIS163u. Downloaded the file, extracted it and found the following files in it ( In the setupxp2000>> win98>>usb>>winxp folder)

sis163u.inf and sis163u.inf ( the two files you are supposed to need!)


the link was

[http://www.tp-link.com/support/download.asp?a=1&m=TL%2DWN320G](http://www.tp-link.com/support/download.asp?a=1&m=TL%2DWN320G)

---

### Post by bkratz on 2010-07-30
Made a mistake remove the win98 folder from the string mentioned. Sorry!

---

