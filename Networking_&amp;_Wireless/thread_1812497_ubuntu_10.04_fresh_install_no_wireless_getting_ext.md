---
title: "ubuntu 10.04 fresh install no wireless getting extremely frustrated"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by octopiocyopi on 2011-07-26
I've had so  many issues with 11.04 Natty that could not be solved so I just fresh  installed Ubuntu 10.04 from a USB as my netbook does not have a CD  drive. Well, after installing and restarting I have no wireless. I ran  iwconfig and I got pan0      no wireless extensions. How do I fix this?

lspci says

ken@ken-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
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
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

---

### Post by mikewhatever on 2011-07-26
Looks like your only option is compiling from source:
[http://ubuntuforums.org/showthread.php?t=1721229](http://ubuntuforums.org/showthread.php?t=1721229)

---

### Post by octopiocyopi on 2011-07-26
> **mikewhatever said:**
> Looks like your only option is compiling from source:
[http://ubuntuforums.org/showthread.php?t=1721229](http://ubuntuforums.org/showthread.php?t=1721229)

Compiling from the source did not work :/

---

### Post by mikewhatever on 2011-07-26
Too bad, and I can't possibly offer anything but commiseration, unless you'll be willing to provide details.

---

### Post by wildmanne39 on 2011-07-26
Hi, run these commands in a terminal please
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

