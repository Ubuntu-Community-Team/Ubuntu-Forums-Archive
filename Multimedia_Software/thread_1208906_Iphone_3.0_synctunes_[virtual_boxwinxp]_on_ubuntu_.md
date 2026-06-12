---
title: "Iphone 3.0 sync/tunes [virtual box/winxp] on ubuntu workaround!"
date: 2009-07-09
forum: Multimedia Software
---

### Post by teh'p3nsi0n3r on 2009-07-09
Ok, I have found a solution for those who use Ubuntu and have an iPhone and the 3.0 firmware.

first off ubuntu 9.04 recognises my iphone but only as a camera and mounts it, i can get my images off of it using fspot/browing the mounted device.

For this work around to work, you will need to do the following:
-------

download virtualbox (not the ose version as it does not support usb) you can get a .deb off of the virtualbox site, you'll need to setup windows xp inside a vb with full sound etc and **folder sharing**. (people having problems with sync'n iphones inside vB the solution is on the VB forum, i did a little hunting, its simple, keep your xp resolution at 800x600 (don't ask, it just works).

then make sure you setup guest editions installed inside of virtualbox/windows xp (for usb support).
i had my iphone connected to ubuntu during this whole process btw.

shutdown your virtual xp.

you will need to enable usb support in VB, right click your virtual xp (do not launch) > settings > usb > tick enable usb controller & enable usb 2.0 (EHCI) controller. and select the iphone device, this should show up.

inside your vb, download and install copy trans manager:
[http://www.copytrans.net/copytransmanager.php](http://www.copytrans.net/copytransmanager.php)

(For this tutorial, i am using copytrans manager as its my choice for syncing and copying tunes to my iphone.)** (do not run it, as it requires itunes to be installed.)** 

next you will need to install itunes+quicktime installer (which is what i did as copytrans seems to require some itunes components.) you can get the latest version which supports the 3.0 firmware off the apple site.

This should be it!, once booting up your VB, windows xp should reconise your iphone as a new device, install/setup the device itself, and will reconise it and sync it (you will get a new pop up bubble saying new hardware is ready to use).

Open Copy trans manager (free) (this is what i am using to copy tunes to my iphone, it is light weight and free. i personally dont like itunes.) and you'll see it will reconise the songs on your iphone.)

If you've setup folder sharing in VB you should be able to browse your tunes in xp in explorer through VB and drag and drop them into copytrans manager, and it will work away and copy the tunes to the iphone. :)

so far i've managed to copy accross individual tracks and albums (purchased btw!).

happy sync'n. :guitar:

---

### Post by ron5678 on 2009-07-11
CopyTrans Manager via Virtual Box Windows XP guest with iTunes already installed worked well for me.  Faster and more stable than iTunes was here.

Thanks teh'p3nsi0n3r for the info here

---

### Post by teh'p3nsi0n3r on 2009-07-14
Hey ron5678, glad my work around worked out for you. Yea I agree, I find iTunes sluggish to use, copy trans manger was alot faster, especially when all i want to do is copy some tunes to my iPhone. I hope others cam benefit from this too. :)

---

### Post by Ranko95 on 2009-07-22
thanks! I like to use a tinyxp too. Although i would like to use something in ubuntu. i really do hate windows, but i cant run everything in ubuntu. Is there a way to use banshee or amarok? i know there is a way to do it with an ipod touch 1g. im pretyy good with all the jailbreak stuff. I have jailbroken and edited my DBversion but it still wont work. any sugguestions?

---

### Post by teh'p3nsi0n3r on 2009-07-22
> **Ranko95 said:**
> thanks! I like to use a tinyxp too. Although i would like to use something in ubuntu. i really do hate windows, but i cant run everything in ubuntu. Is there a way to use banshee or amarok? i know there is a way to do it with an ipod touch 1g. im pretyy good with all the jailbreak stuff. I have jailbroken and edited my DBversion but it still wont work. any sugguestions?

all i know is that 3.0 firmware still is not compatible with Ubuntu yet as apple made changes to the firmware. This is so far the only solution i could think of and works pretty well cosidering. It should hopefully only be a matter of time till someone thinks of a work around so we can sync directly into ubuntu, I hope that day comes soon. :)

---

