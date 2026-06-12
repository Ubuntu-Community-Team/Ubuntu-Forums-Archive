---
title: "Cannot Conect to WPA Network? or wirless card not working..."
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by blackzmage on 2009-03-15
Hi guys, this is my 3rd post here regarding the same topic. I cannot access my wireless internet connection on Ubuntu 8.10 Intrepid, installed via Wubi on a separate drive from windows. 

I have the : **_Linksys Wireless-G PCI Adapter with Speedbooster, Model NO. WMP54GS version 1.4_** for my desktop. I ran [FONT="Fixedsys"]lspci[/FONT] and it gave me this:

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:08.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:09.0 USB Controller: Agere Systems USS-344S USB Controller (rev 11)
00:09.1 USB Controller: Agere Systems USS-344S USB Controller (rev 11)
00:09.2 USB Controller: Agere Systems USS-344S USB Controller (rev 11)
00:09.3 USB Controller: Agere Systems USS-344S USB Controller (rev 11)
00:0a.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
00:0b.0 Token ring network controller: IBM 16/4 Token ring UTP/STP controller (rev 66)
00:0c.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
```

I am assuming that the chipset is BCM4318. I have installed the driver via ndiswrapper, but i cannot connect to my WPA Personal etwork or a unsecured network. 


If anybody can help me that will be great.

---

### Post by kevdog on 2009-03-15
Is this a usb device?  A usb device is listed with lsusb rather than on the pci bus with lspci.  Are you sure of the chipset #?  I do see the bcm4318, which I believe you can use without ndiswrapper but rather with the newer b43 driver or the open source openfwwf driver.  Do you have a working internet connection like a wired connection?

---

