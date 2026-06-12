---
title: "Wireless doesn't work on Compaq Presario V5000 with Ubuntu 8.10 on a USB drive"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by PwnCakes193 on 2008-12-05
I have ubuntu 8.10 on a flash drive, and im using a Compaq presario v5000 as the machine that runs it. Everything works perfectly except the wireless.
I clicked the network box in the top right and the connect to wireless box is grayed out, as is the enable ethernet. I tried entering manual settings, but still no luck.

I am a complete noob about this stuff and the simplest explanation would be the greatest thing ever. Thank you so much in advance.

---

### Post by Ayuthia on 2008-12-05
> **PwnCakes193 said:**
> I have ubuntu 8.10 on a flash drive, and im using a Compaq presario v5000 as the machine that runs it. Everything works perfectly except the wireless.
I clicked the network box in the top right and the connect to wireless box is grayed out, as is the enable ethernet. I tried entering manual settings, but still no luck.

I am a complete noob about this stuff and the simplest explanation would be the greatest thing ever. Thank you so much in advance.

Can you go into the Terminal and post the results of;
```
lspci -nn
```
It will help identify your wireless card and then we can help point you in the right direction.

---

### Post by PwnCakes193 on 2008-12-05
ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)



is this all that you need?

---

### Post by Ayuthia on 2008-12-06
The 4311 card has three options for wireless.  You can use NDISwrapper along with a Windows wireless driver, the b43 open source driver, or you can use Broadcom's proprietary driver.  The easiest one to try first is the Broadcom proprietary driver.  Have you gone into System->Administration->Hardware Drivers and activated the Broadcom STA driver?  If not, you might want to try that first.  It does not require any downloading.

---

### Post by PwnCakes193 on 2008-12-06
I went there and I activated the option that requires no downloading. It went green and the wireless didn't work. I connected to ethernet and downloaded and installed the other one, and it does work. Thanks man! I would've hated to have no wireless on such a great operating system.

---

