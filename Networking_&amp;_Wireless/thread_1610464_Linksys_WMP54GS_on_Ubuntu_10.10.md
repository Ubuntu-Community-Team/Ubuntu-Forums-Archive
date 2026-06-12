---
title: "Linksys WMP54GS on Ubuntu 10.10"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by helephant on 2010-10-31
I have an IBM System x3200 and I'm trying to install drivers for a Linksys WMP54GS Broadcom BCM4318 AirForce One 54g 802.11g 14e4:4318. The kernel is 2.6.35. I finally successfully installed Ndiswrapper. I have tried several different drivers already. The computer sees it but it's not detected by ifconfig or iwconfig. This is my first experience with Ubuntu (already regretting it) and if you can dumb down your explanation as much as possible, that would be great. Just to let you know, I followed these instructions ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) and I've gotten nowhere.

Also, when I run 'modprobe ndiswrapper' I get a 'WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.' I get the same thing again beneath it but 'ndiswrapper' instead of 'blacklist.' When I blacklisted 'bcm43xx,' 'b43,' 'ssb,' and 'b43legacy,' I first didn't use the '.conf' file but I did after that. I would take them out of the original blacklist file (without the .conf) but I'm not sure how to.

---

### Post by OneUniqueGeek on 2010-11-28
I am a total newbie to Ubuntu as well, and I can't seem to get my WMP54GS to work. :/ Any help would be appreciated! :D

---

