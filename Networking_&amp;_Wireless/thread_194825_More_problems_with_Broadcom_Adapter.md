---
title: "More problems with Broadcom Adapter"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by IronStomach on 2006-06-12
Hi, everyone-

I just installed Ubuntu 6.06 for the first time on my Acer Aspire 3003 a few days ago, and I must say, I'm very pleased with it... except for the wireless card. I've gone through the various different tutorials on how to get Broadcom wireless cards working, and everything seems to be configured properly (ndiswrapper reports that the drivers and hardware are present), but there's one thing that may be messing things up. In the Networking menu (System > Administration > Networking) the wireless card is listed as eth1 instead of wlan0. Maybe my computer thinks that the wireless card is... wired, or something. Any ideas?

(Note: Using latest versions of the bcmwl5.inf and .sys files from the Acer support page)

---

### Post by maddbaron on 2006-06-12
i had same issue check the newbie board there are solutions for u. i have an aspire 3000 and i did everything and finally got it to work. u can go into my posts its like 2 or 3 days old i got my wireless working friday.

---

### Post by djgrandmarquis on 2006-06-24
Does your Aspire 3003 have a Broadcom BCM4318 like mine does? This post worked incredibly well:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by tangela on 2006-06-24
I did this and it worked fine for me Broadcom 843 (Air Force One model). Somebody says that Ubuntu identifies well the device, but has not the firmware, so can't use right:

sudo apt.get install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
 
You can find more information [http://www.ubuntuforums.org/showthread.php?t=185174]("http://www.ubuntuforums.org/showthread.php?t=185174")

;)

---

