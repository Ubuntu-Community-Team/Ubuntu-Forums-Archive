---
title: "bcm43xx: hardware present: no"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by tacobeans1234 on 2010-09-27
Hey guys,


So I just recently moved my new computer over to Lucid from windows XP. I know little about ubuntu, I've only used it for about a year. I have a WMP54G PCI card and I did some research and found that the bcm43xx is the correct driver for said device. So I tried using ndisgtk and I'm getting the "Hardware Present: No" thing. Rather frustrating. 

lspci output:
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev ff)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)


```Any ideas? 

Thanks! 

--Andrew

---

### Post by angryfirelord on 2010-09-27
bcm43xx is an old driver. You have a choice between STA and b43. STA is the proprietary driver and b43 is the open-source one. The difference is that STA supports more hardware.

First, I would open up Hardware Drivers and see if it detects your card, which will then allow you to install the necessary driver (you need an internet connection to do this).

---

### Post by tacobeans1234 on 2010-09-27
> **angryfirelord said:**
> bcm43xx is an old driver. You have a choice between STA and b43. STA is the proprietary driver and b43 is the open-source one. The difference is that STA supports more hardware.

First, I would open up Hardware Drivers and see if it detects your card, which will then allow you to install the necessary driver (you need an internet connection to do this).

Thanks for the quick response. 
I don't have a connection on this computer, nor can I get one. I'd have to run wire all the way across my apartment building :P

Any alternatives?

---

### Post by bkratz on 2010-09-28
You might want to look at this page

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

especially the section about halfway down labeled

b43/STA - No Internet access

---

### Post by tacobeans1234 on 2010-09-28
> **bkratz said:**
> You might want to look at this page

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

especially the section about halfway down labeled

b43/STA - No Internet access

Can't try it now because I'm at the office, but thanks for the resource! I'll try it as soon as I get home. :D

---

