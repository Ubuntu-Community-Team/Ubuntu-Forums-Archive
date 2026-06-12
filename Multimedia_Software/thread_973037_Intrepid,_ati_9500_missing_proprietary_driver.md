---
title: "Intrepid, ati 9500 missing proprietary driver"
date: 2008-11-06
forum: Multimedia Software
---

### Post by Noiano on 2008-11-06
Hello everybody,
I recently updated to intrepid and I noticed a weird thing: the restricted driver manager doesn't find any driver for my ati 9500. With ubuntu 8.04 I had the proprietary diver installed and working and now it has gone.

Does anybody have the same problem?:confused:

---

### Post by Yellow Pasque on 2008-11-06
Do you have the fglrx-modaliases package installed? If not, the Ubuntu Intrepid proprietary driver manager (jockey) won't know of fglrx's existence.

If you can't get that to work, follow this:
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22)

---

### Post by Noiano on 2008-11-06
> **Temüjin said:**
> Do you have the fglrx-modaliases package installed? If not, the Ubuntu Intrepid proprietary driver manager (jockey) won't know of fglrx's existence.

If you can't get that to work, follow this:
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22)

That package was installed and also linux-restricted-modules-generic & restricted-manager were installed. I followed the ubuntu way as described on cchtml but I got something like "EE no devices found".

I also tried envyng but I got the same error. I cannot understand what goes wrong: seems like my video card is not supported any more :confused: ?

I attached some log.

Thanks

PS: aticonfig causes segfault :(

---

### Post by frekja on 2008-11-06
I've got an ATI Mobility Radeon 9700 and I also can't get proprietary drivers to work following an upgrade from 8.04 (via restricted drivers or EnvyNG). I've done a bit of googling, and I think the most recent ATI driver broke support for R300 or lower cards - so ubuntu defaulted to "Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL" for me. Seems slower than fglrx, especially with flash.

Does anyone know more about this?

Incidentally, I tried to install an ATI driver using EnvyNG and ended up screwing everything up - so I'd avoid this unless you really know what you're doing.

Edit: I found a possible explanation: [http://ubuntuforums.org/showpost.php?p=6115262&postcount=9]("http://ubuntuforums.org/showpost.php?p=6115262&postcount=9")

Edit2: More info: [http://ingomar.wesp.name/journal/intrepid-fglrx-works-with-xorg-7-4]("http://ingomar.wesp.name/journal/intrepid-fglrx-works-with-xorg-7-4")

---

### Post by Yellow Pasque on 2008-11-06
The official Launchpad bug for this issue (the Ubuntu devs have marked it "Highly Important" and submitted a ticket to ATI/AMD): [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408)

---

### Post by Entity` on 2009-02-08
I have had a similar problem last night when I installed the driver, no matter what I do, I cannot for the life of me, get the driver to recognize my card and work properly.  I'm in my other OS now so my log is not available.

---

