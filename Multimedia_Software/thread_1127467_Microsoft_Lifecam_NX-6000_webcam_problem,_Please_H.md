---
title: "Microsoft Lifecam NX-6000 webcam problem, Please Help!"
date: 2009-04-16
forum: Multimedia Software
---

### Post by ycason on 2009-04-16
I have been trying to find a webcam that will just work with Ubuntu.  It has been a frustrating experience.  I bought the NX-6000 webcam on the suggestion of [http://linux-uvc.berlios.de/]("http://linux-uvc.berlios.de/").

I can't get this webcam to even display a picture.  It is showing up on the list of webcams in cheese, but when I select it I only get a white box.  Please Help!

---

### Post by ycason on 2009-04-16
I've been searching a long time and trying various methods to make this thing work.  I updated to Jaunty hoping that the new version of Ubuntu would have an updated UVC driver, but that did nothing.  Here's some relevant output from lsusb and dmesg.

```
$ lsusb
Bus 001 Device 009: ID 045e:00f8 Microsoft Corp. LifeCam NX-6000.
```

```
$ dmesg | grep uvc
uvcvideo: Found UVC 1.00 device Microsoft&#65533; LifeCam NX-6000 (045e:00f8)
uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
```

---

### Post by tamasrepus on 2009-04-20
I hate to ask, but does the camera work on Windows?

The device itself maybe defective/DOA.

---

### Post by PtPub on 2009-11-01
I dont know if this thread is still live but I get the same results with lsusb, and gmesg and my camera DOES work in windows.
It is NOT DOA

Anyone found a way to make it work>>??

---

### Post by Alex_W on 2009-11-08
Just wanted to share: on my HP dv4200, NX-6000 works with Skype (both video AND mic) on Jaunty + 2.6.31.5 kernel parctically out of the box. To make the internal mic work, you would need to go System --> Preferences --> Sound and choose the webcam in the Audioconferencing section (and do same in Skype settings, of course). Sound didn't work on 2.6.30 series (video did). 2.6.28 series -- didn't even test 'cuz this laptop has integrated Intel 915 video which requires tweaking.

Good Luck!

---

