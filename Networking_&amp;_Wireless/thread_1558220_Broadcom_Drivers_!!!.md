---
title: "Broadcom Drivers !!!"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by dogeatery on 2010-08-21
I've been putting off a distro upgrade on my HP Mini for over a year now because of the Broadcom drivers being necessary on every new version I want to try out.  But now I really want to run the LTS.  My problem is as follows:

The HP Mini has no wired network port.  So when I go to activate the Broadcom drivers, they try to download but -- duh! -- there is no internet connection.  This is true even on netbook-specific distros like Easy Peasy and UNR.  After having this problem with several different distros, I decided to download the wireless driver as a separate package and save it to a USB stick.  Now I'm trying out a live CD of Peppermint but when I go to install the drivers from the downloaded .deb package, the wireless still didn't work.  I went into the hardware drivers box and noticed there are both a free Broadcom and a proprietary Broadcom driver listed, but when I click activate, it tries to download from the non-existent internet connection.

Am I doing something wrong?  Is there a chance I installed the wrong driver?  Am I supposed to use something else to activate the driver once it's installed?

---

### Post by TossTheTV on 2011-04-10
delete this, posted in appropriate sticky..

---

### Post by Megaptera on 2011-04-10
Have you tried this? Don't forget to re-boot afterwards. Even though it says Maverick I've used it in several versions.

[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

---

### Post by TossTheTV on 2011-04-10
> **Megaptera said:**
> Have you tried this? Don't forget to re-boot afterwards. Even though it says Maverick I've used it in several versions.

[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

yes but that only supports 4311,4312,4321.. my HP Mini 210 for example has the Broadcom 4315. I posted what worked for me in the sticky:
[http://ubuntuforums.org/showthread.php?t=1604868&page=15](http://ubuntuforums.org/showthread.php?t=1604868&page=15)

There is another sticky for if ndiswrapper has problems doing everything automatically :D

---

### Post by bkratz on 2011-04-10
> **TossTheTV said:**
> yes but that only supports 4311,4312,4321.. my HP Mini 210 for example has the Broadcom 4315. I posted what worked for me in the sticky:
[http://ubuntuforums.org/showthread.php?t=1604868&page=15](http://ubuntuforums.org/showthread.php?t=1604868&page=15)

There is another sticky for if ndiswrapper has problems doing everything automatically :D

Glad you got it working, but in the other thread you linked to you state that the 4315 is not supported by STA.

You also linked to 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Where the read me file says (in part)
BRCM                 PCI	PCI
4312 2.4 Ghz	    0x14e4	0x4315 

So you see that  14e4:4315 is in the supported list, it is just another type of 4312.

---

