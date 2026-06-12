---
title: "ndiswrapper won't use anything but wlan0"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by ianhogben on 2006-06-03
Hello,

I'm a bit confused here. I have a Broadcom 4303 wireless card, which is working OK on an Ubuntu Dapper Drake install. Had some problems initially because the bcm43xx drivers were conflicting, but that's all sorted now. ;) 

I have entered "alias eth1 ndiswrapper" in /etc/modules.conf but when modprobing ndiswrapper it always comes up as wlan0. Am I doing something wrong?

Also, is it normal for the NetworkManager Applet to not detect a working ndiswrapper card? I am always getting "No network devices have been found". Seems strange to me...

I'd appreciate any help here - and would be over the moon if someone could point me to the ndiswrapper module options doco. :-)

-Ian.

---

