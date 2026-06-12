---
title: "Vlc glitching with 64bit 10.10"
date: 2010-11-06
forum: Multimedia Software
---

### Post by kesman on 2010-11-06
Hey!

How would I go finding out what causes glitching in .avi -videos in VLC player?
This started happening after changing from 32bit 9.04 to 64bit 10.10 :F

---

### Post by Enigmapond on 2010-11-06
You're probably going to have to be a bit more specific and explain what exactly is happening rather than.. "glitching" which doesn't really say much...:)

---

### Post by kesman on 2010-11-06
Well, every 10 seconds or so the video freezes for ~0,1 seconds, glitches so to say.

---

### Post by efflandt on 2010-11-06
What video card/chip do you have and are you using default or proprietary drivers (driver version?)?

---

### Post by kesman on 2010-11-06
It's an Acer Aspire 5020 laptop with ATI Radeon x700. I'm using the default driver that's installed through repositories. I have proposed and unsupported updates checked.
I'll check the driver version in a minute, it's on another pc that is in use currently.

---

### Post by kesman on 2010-11-06
```
[    21.786] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    21.786] (II) Module ati: vendor="X.Org Foundation"
[    21.786]    compiled for 1.9.0, module version = 6.13.1
[    21.786]    Module class: X.Org Video Driver
[    21.786]    ABI class: X.Org Video Driver, version 8.0
[    21.786] (II) LoadModule: "radeon"
[    21.787] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    21.787] (II) Module radeon: vendor="X.Org Foundation"
[    21.787]    compiled for 1.9.0, module version = 6.13.1
[    21.787]    Module class: X.Org Video Driver
[    21.787]    ABI class: X.Org Video Driver, version 8.0
[    21.787] (II) LoadModule: "vesa"

```
this is from /var/log/Xorg.0.log, looks like driver version 1.9.0 to me. FGLRX doesn't support old hardware, so don't suggest to try it. Here is the complete log: [http://www.pastebin.fi/?NDc1Yj](http://www.pastebin.fi/?NDc1Yj)

---

