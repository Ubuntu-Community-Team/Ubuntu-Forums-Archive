---
title: "Logitech QuickCam Communicate STX"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by jstad on 2006-12-22
I just bought a Logitech QuickCam Communicate STX and am having problems getting it to work under ubuntu 6.10. I followed the suggestions in a thread dated almost a year ago but to no avail. Anyone know how to get the webcam recognized? I tried easycam2 but when runnning the application, it says it does not see any webcam connected to my PC. Also the spca5xxx driver site says my cam is supported but I dont know how to get it loaded (modprobe spca5xxx didn't work). Absolutely ANY help is appreciated.


Also is it possible to get webcam support when running AIM through wine? (curious)

---

### Post by budgie9 on 2006-12-22
Try loading the driver using Easycam2, which you can download in the download manger.
I don't know if this will help but perhaps worth a try.

---

### Post by jstad on 2006-12-22
Um as i said in the original post. I tried easycam2 and it didnt work...... :-\

---

### Post by budgie9 on 2006-12-22
You can't blame me for trying either. Sorry I missed that.
I can't help otherwise, but my Logitech Messenger works fine, and that was the way I got it to work, when nothing else would have it work.
Why not try unloading the files and trying again, it may just work.

---

### Post by den benne on 2006-12-26
did you try this howto [http://ubuntuforums.org/showthread.php?t=303330&highlight=QuickCam](http://ubuntuforums.org/showthread.php?t=303330&highlight=QuickCam)

---

### Post by jstad on 2006-12-26
I did the howto and when I finish loading the plugin and stuff all I get in my dmesg is:

[17199212.076000] Linux video capture interface: v1.00
[17199212.080000] usbcore: registered new driver spca5xx
[17199212.080000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered

My camera is connected and still nothing seems to detect it. It is not listed under /dev/video or /dev/video0 either.

---

### Post by handband2 on 2007-01-11
> **jstad said:**
> I did the howto and when I finish loading the plugin and stuff all I get in my dmesg is:

[17199212.076000] Linux video capture interface: v1.00
[17199212.080000] usbcore: registered new driver spca5xx
[17199212.080000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered

My camera is connected and still nothing seems to detect it. It is not listed under /dev/video or /dev/video0 either.

jstad,

I'm having the same problem as you.  Also, when I run 
```
lsmod | grep v4l
```
I get
```
v4l2_common            17280  2 tuner,bttv
```

v4l detects my tuner card but not my Quickcam STX

Does anyone have any ideas how to get v4l to detect my Quickcam?

Edit:  I got it working going here [http://www.ubuntuforums.org/showpost.php?p=1909921&postcount=1]("http://www.ubuntuforums.org/showpost.php?p=1909921&postcount=1")

---

### Post by hencke on 2007-01-12
Hi!

I have a Logitech QuickCam Communicate STX Plus for Skype and it seemed to be detected by just plugging it in the USB socket. In both Ubuntu 6.10 and 6.06 Ekiga recognized it when I selected V4L in the "Video devices" tab in preferences. At least in Dapper I also had WengoPhone recognize it.

The problem was(/is) the output from the camera: poor quality and zoomed in compared to Win. Seemed like I had only a 320x240 part of the hole 640x480 picture, luckily from the middle of the picture. =)

My lsusb output is:

Bus 001 Device 002: ID 046d:08ad Logitech, Inc.

(note that there are at least 2 different possible IDs for QC Communicate STX)

I haven't tried the latest drivers from [http://mxhaard.free.fr/](http://mxhaard.free.fr/)
Has anyone else experienced this kind of problem? Did a driver update solve it? Or was there some other solution? What was your lsusb output?

Well, I hope the driver will be updated and the problem solved in Feisty Fawn (and also hope that Skype for linux will have web cam support by then)!

By the way "lsmod | grep v4l" doesn't give me anything. Does this mean the driver isn't actually loaded, and even if it's updated in Feisty, I'll still have to compile it? To be honest, just know I'm not sure whether to ask "Why is my camera working (partially)?" or "Why isn't my camera working fully?" =)

Thanks,

HK

---

### Post by Ningbojoe on 2007-05-20
Try this, it had my Logitech Communicate installed in 30 seconds.;)

[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

---

### Post by dawna_2001 on 2007-11-05
How do i get the appripriate driver??????  I have ubunto 7.04 they are only tar not deb????

---

### Post by hencke on 2007-11-06
> **dawna_2001 said:**
> How do i get the appripriate driver??????  I have ubunto 7.04 they are only tar not deb????

Which camera do you have? To find out the exact model, you can open a terminal and type
```
lsusb
```
while your camera is plugged in. I have a "Bus 001 Device 002: ID 046d:08ad Logitech, Inc." and as indicated at [HTML]http://mxhaard.free.fr/spca5xx.html[/HTML] it is supported by the spca5xx kernel driver, which ships with the ubuntu kernel to my knowledge. If I recollect, my camera just works by plugging it in. You can see if it is working by opening Ekiga and telling it to display video. You might have to toggle in between using the V4L1 or V4L2 module (in Ekiga). Good luck!

---

### Post by dawna_2001 on 2007-11-07
Bus 002 Device 003: ID 046d:08d7 Logitech, Inc.  that is the exact model and it is supported and I have the driver loaded and it shows, but it still says no camera detected in ekiga it shows /dev/video0 and when i test it says no device found????????????????????????

---

### Post by Ituxlinux on 2007-11-07
I did have the same problem in my laptop (7.04), and it solved when I use a different usb port, the one in the backside.  No idea why, but now it works ok from that port.

---

### Post by hencke on 2007-11-08
> **dawna_2001 said:**
> Bus 002 Device 003: ID 046d:08d7 Logitech, Inc.  that is the exact model and it is supported and I have the driver loaded and it shows, but it still says no camera detected in ekiga it shows /dev/video0 and when i test it says no device found????????????????????????

I had ubuntu 7.04 installed a while ago, but my webcam (and sound and ...) doesn't work now (I upgraded to ubuntu 7.10). I remember having to have to play around with the ekiga settings to get it to work the first time, but this probably isn't your case. Is this what happens when you plug the webcam in:
lsusb shows the device, but the led on the camera doesn't blink?

That is what happens in my ubuntu 7.10 (upgraded) installation, but in kubuntu 7.10 (fresh install) the webcam blinks during startup and again more when I open kopete settings, where I can see that the camera works (so it's not a usb-port issue in my case).

In ubuntu 7.10 (upgraded) I have v4l module in ```
/etc/X11/xorg.conf
``` so it should work, but in kubuntu 7.10 (fresh install) I don't have v4l (or v4l2), so it shouldn't work (but it does)? I guess I can't help you too much, but I will post if I happen to find a solution.

(By the way, we have the same webcam name, but you probably have a newer one as it is 08d7 opposed to my 08ad. I think this is completely irrelevant as your camera should also be supported.)

---

### Post by dawna_2001 on 2007-11-10
k my webcam works on a different machine with ubuntu 7.10 newly installed.  I upgraded from 7.04.  The camera stll doesn't work.  I have used Easycam2 and with/without the spca driver.  This is starting to get real frustrating.  Can someone please help me????????

---

