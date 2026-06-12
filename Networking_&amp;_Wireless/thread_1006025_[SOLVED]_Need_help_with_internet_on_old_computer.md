---
title: "[SOLVED] Need help with internet on old computer"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by kslinux on 2008-12-08
I am new to linux.

I am trying to get the internet to work on an old desktop computer - Dell Dimension 4500. I am using kubuntu 8.04.1 which uses KDE 3.5.9.

I am currently using a Windows XP laptop for my internet. I'd like to get the desktop working to try it out as well on the internet. It would be great to be able to download Linux applications directly onto the desktop computer rather than using a flashdrive to transfer data from one computer to another.  I have a wireless network at home.

I have plugged a Linksys WUSB54GSC wireless card into one of the desktop's USB connections. It would be ideal to get the wireless running if at all posible.

I've been reading on the forum what information is required. I am posting the results from the common commands (i.e., lspci, iwconfig, ifconfig). I have also posted the results from "lsusb". This does show that the Linksys card is there. Note also that "lsusb" shows an external hard drive and mouse installed. Both of these work.

Thank you for your help.


Results from “lspci”:

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
02:01.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
02:02.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)


Results from “iwconfig”:
lo no wireless extensions.

eth0 no wireless extensions.


Results from “ifconfig”:
eth0 Link encap:Ethernet HWaddr 00:08:a1:0d:53:8c
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:19 Base address:0xd800

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


Results from “lsusb”:
Bus 004 Device 004: ID 1058:1100 Western Digital Technologies, Inc.
Bus 004 Device 002: ID 13b1:0026 Linksys
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000

---

### Post by albinootje on 2008-12-08
In this link there are two links mentioned to a Howto with Ndiswrapper for this card. [http://www.linux.com/forums/topic/941](http://www.linux.com/forums/topic/941)

And this link claims that the card works without Ndiswrapper in Intrepid :
[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)

---

### Post by kslinux on 2008-12-11
Thank you.  I have loaded Intrepid and the wireless internet connection is working.  In fact, I am using this old desktop to write this reply.

:D

---

### Post by superprash2003 on 2008-12-11
please mark this thread as SOLVED.

---

### Post by kslinux on 2008-12-11
> please mark this thread as SOLVED.

done

---

