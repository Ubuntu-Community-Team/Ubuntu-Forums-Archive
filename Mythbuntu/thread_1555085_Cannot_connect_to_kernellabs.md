---
title: "Cannot connect to kernellabs"
date: 2010-08-17
forum: Mythbuntu
---

### Post by mw3845 on 2010-08-17
I'm trying to set up my HVR-2250 and need to connect to kernellabs.com. Every time I try to connect, it just times out. Is there an alternative available or am I the only one experiencing this?


Thanks in advance,
mw

---

### Post by LowSky on 2010-08-17
looks like kernel labs is having issues again... what verison of Ubuntu are you using... if its 10.04 you may not need to use kernel labs

---

### Post by bbc581 on 2010-08-17
I am having difficulty connecting to kernellabs.com as well.

The developer, Steven Toth has recently announced analog support for the HVR-2250 chipset (see Google cache of the below link)

SAA7164 Analog support complete?
[www.kernellabs.com/blog/?p=1443]("http://ubuntuforums.org/www.kernellabs.com/blog/?p=1443")

First draft is available from [URL="http://kernellabs.com/hg/%7Estoth/saa7164-v4l"]http://kernellabs.com/hg/~stoth/saa7164-v4l
[/URL] Firmware is available from [URL="http://www.steventoth.net/linux/hvr22xx/firmwares/4019072"]http://www.steventoth.net/linux/hvr22xx/firmwares/4019072
[/URL] 
I get the distinct impression that I need to review my use of 
make menuconfig
as I am unable to get the analog support to work correctly.  Luckily, I think I was able to follow the other steps with success.

PM me if you would like to some help on this as it would appear we are possibly working on the same thing...  I downloaded everything back on August 7th, 2010.  I can email you whatever you need.

Although I am using Mandriva, it couldn't hurt to have a hand - that is if you're interested in the analog support?

> **LowSky said:**
> looks like kernel labs is having issues again... what verison of Ubuntu are you using... if its 10.04 you may not need to use kernel labs<br />
<br />

---

