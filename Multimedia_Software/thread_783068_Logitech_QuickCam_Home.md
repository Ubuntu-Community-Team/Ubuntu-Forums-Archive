---
title: "Logitech QuickCam Home"
date: 2008-05-05
forum: Multimedia Software
---

### Post by MemoryDump on 2008-05-05
Hi all,

I'm trying to setup my Webcam and haven't had much luck so far.

Has anybody had success in configuring this type of camera?

Bus 005 Device 005: ID 046d:0801 Logitech, Inc. QuickCam Home

If so what were the steps you took? I tried using it with amsn and cheese and it says no webcam found.

thanks
-MD

---

### Post by linuxwizard on 2008-05-05
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. ( Video Plugin if it shows V4L change to V4L2 or if it shows V4L2 change to V4L.)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by kah00na on 2008-05-07
That Ekiga did not pick up the Logitech webcam.  I have the same one and just tried this and it did not work.  here's my output from lsusb:

```
darkestrella:~$ lsusb | grep Logi
Bus 001 Device 003: ID 046d:0801 Logitech, Inc. QuickCam Home
darkestrella:~$ 
```

---

### Post by linuxwizard on 2008-05-07
Thinking more about this webcam if I remember right I tried helping someone else with this same cam and it is not supported in Linux. I am still doing some searching on this. Alot of Logitech webcams will just work.

Your cam is not listed > Bus 001 Device 003: ID 046d:0801 Logitech, Inc. QuickCam Home

[http://www.quickcamteam.net/hcl/linux/logitech-webcams](http://www.quickcamteam.net/hcl/linux/logitech-webcams)
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

### Post by linuxwizard on 2008-05-07
Can't find anything on that webcam working.
 
Unsupported
Logitech QuickCam Home is currently not known to work. > [http://qce-ga.sourceforge.net/#supported](http://qce-ga.sourceforge.net/#supported)

---

