---
title: "Intel i810 video card"
date: 2009-06-07
forum: Multimedia Software
---

### Post by mihe on 2009-06-07
Hi,
I have a dell inspiron 6400 with 945 video card, see below. 

lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)


I  have used sudo dpkg-reconfigure -phigh xserver-xorg to update my xorg.conf. As I have understood in ubuntu 8.04 not much should be specified in the xorg.conf file. I try to run a cae software for displaying geometry and for finite element post processing. It involves displaying a lot of colored faces...

When I install the xserver-xorg-video-i810 diver with synaptic I can not get 1280x800 resolution. Also my keybord layout get mixed up. However the cae software work quite ok.

When I unistall i810 and install xserver-xorg-video-intel I get 1280x800, the keyboard is ok (characters as ^&* and so on are on the right keyes). However the cae software does not look that pretty. It does not seem to know what should be in the background and what should be in front. All faces get displayed even though some should be behind others. Also drop down menues and input boxes get behind the background.

Any help appreciated, how can I get 1280x800 and a video card driver that work ok with my cae software?

Regards,
Micke

---

### Post by mihe on 2009-06-07
I guess a god thing about forums is that when specifying the problem you might even resolve it yourself;). This is how I did:

I use the i810 driver
Install the 915resolution package
I change the USA keyboard layout to the proper one in preferences + keyboard.

Just a curious question. How could using the i810 driver mix up my keyboard (to USA)?

/Micke

---

