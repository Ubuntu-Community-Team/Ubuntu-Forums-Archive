---
title: "broadcom wireless driver problem"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by Abu Noor-Eddin on 2009-09-11
Hello all,

I did a fresh install of Ubuntu 8.04 and everything went fine. I tried to connect to my wireless network but it never connects (it keeps asking me for the password). 

I tired millions of websites, tutorials, and blogs but with it did not work. I installed several things, uninstall several things, enable/disable several things but it cannot work!

Would you please help me before I go insane?

Thanks in advance.

---

### Post by Crafty Kisses on 2009-09-11
What are the results of the following?
```
lspci
lsusb
lshw -C network
```

---

### Post by Abu Noor-Eddin on 2009-09-11
> **Codename said:**
> What are the results of the following?
```
lspci
lsusb
lshw -C network
```

this is the result 
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

```
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

```

```

  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:cf:62:75
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:95:8b:f5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.2.18 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

```

---

### Post by Abu Noor-Eddin on 2009-09-12
Any help please!

---

### Post by Ayuthia on 2009-09-12
If you already have a working connection in Ubuntu, have you tried using the b43 driver instead of the Broadcom STA?  If I recall correctly the Broadcom STA module did not work too great in 8.04.

---

### Post by Abu Noor-Eddin on 2009-09-12
> **Ayuthia said:**
> If you already have a working connection in Ubuntu, have you tried using the b43 driver instead of the Broadcom STA?  If I recall correctly the Broadcom STA module did not work too great in 8.04.

I think I tried it before switching to STA, but it was not working also.

---

### Post by AZinOH on 2009-09-12
I have a BCM4318 operating perfectly in 9.04. After installing Jaunty, I clicked on System>Administration>Hardware Drivers and enabled the b43 driver and I was good to go. In fact...it works better in Ubuntu than it does in Vista. If you don't have a necessary attachment to 8.04, I'd consider upgrading to 9.04.

---

### Post by Abu Noor-Eddin on 2009-09-12
> **AZinOH said:**
> I have a BCM4318 operating perfectly in 9.04. After installing Jaunty, I clicked on System>Administration>Hardware Drivers and enabled the b43 driver and I was good to go. In fact...it works better in Ubuntu than it does in Vista. If you don't have a necessary attachment to 8.04, I'd consider upgrading to 9.04.

If there is no solution, I will upgrade. I am waiting for any ideas that may help.

---

### Post by Abu Noor-Eddin on 2009-09-12
> **AZinOH said:**
> I have a BCM4318 operating perfectly in 9.04. After installing Jaunty, I clicked on System>Administration>Hardware Drivers and enabled the b43 driver and I was good to go. In fact...it works better in Ubuntu than it does in Vista. If you don't have a necessary attachment to 8.04, I'd consider upgrading to 9.04.

You know, it was working fine before I switched to fedora but it is not when I am back to Ubuntu.

---

### Post by GlennW on 2009-09-12
Hey everyone! I've recently been given a Dell Inspiron 2200. It was running XP and was a complete mess! So, I've installed 9.04 and overwritten it all. Nice...

I've got a couple of issues, albeit related ones. First, the ethernet port is loose so I assume that's why I can't establish a wired connection. Second, I have the Broadcom B43 Wireless Driver (shows up in the Hardware Driver selections) but it says that this driver is not activated. I attempt to activate it and it attempts to download and install but not having an active internet connection, nothing happens.

Referring to some of the above posts, here are my outputs:
(I've copied the terminal outputs over to my desktop via a USB stick)

Lspci

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) 
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) 
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03) 
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) 
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03) 
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller 
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03) 

Lsusb

Bus 001 Device 003: ID 090c:1000 Feiya Technology Corp. Memory Bar 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

lshw -C network

WARNING: you should run this program as super-user. 
  *-network:0             
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 3 
       bus info: pci@0000:02:03.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network:1 
       description: Ethernet interface 
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:02:08.0 
       logical name: eth0 
       version: 03 
       serial: 00:12:3f:0e:bd:af 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes 
  *-network:0 DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 7a:eb:df:85:95:07 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 
  *-network:1 DISABLED 
       description: Wireless interface 
       physical id: 3 
       logical name: wlan0 
       serial: 00:14:a5:00:e6:4e 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 

Thanks for your help. Please keep in mind that I'm still a bit of a Linux noob. The adage KISS certainly applies...

---

### Post by Abu Noor-Eddin on 2009-09-12
so so disappointing !!!

---

### Post by GlennW on 2009-09-12
Anyone?

---

### Post by m_duck on 2009-09-12
I have basically no experience with broadcom wireless cards apart from helping a friend with one the other day. He had a similar problem, and though it could "see" his router via gnome-network-manager, he could not connect. Oddly *iwlist scanning* gave no scan results. However, for some reason installing WICD (thus uninstalling gnome-network-manager) to manage the wireless connection seemed to work.
 
This will need an internet connection for package downloads but is possible from another computer.
 
Also, I don't think his chipset was a BCM4311 but I am unsure as to how much the broadcom chips differ.
 
Hope this is of some use!

---

