---
title: "HDE (SiGma Micro) 1c4f:3002 - Video not transfering"
date: 2010-12-28
forum: Multimedia Software
---

### Post by krzysz00 on 2010-12-28
I am attampting to get an HDE Webcam to work with Ubuntu 10.10. Ths lsusb entry is:
```
Bus 002 Device 002: ID 1c4f:3002 SiGma Micro 
```
The webcam is detected as /dev/ideo0, but when I attempt to use it, I get the following message in dmesg and a black screen instead of video.
```
[ 3124.878851] uvcvideo: Failed to query (135) UVC control 11 (unit 2) : -32 (exp. 1).
```

Any help?

---

### Post by krzysz00 on 2010-12-28
Is this the wrong forum? If it is, could the thread please be moved?

---

### Post by krzysz00 on 2011-01-02
bump bump.

(If I should be asking the uvc developers, please speak up)

---

### Post by vlad1977 on 2011-01-04
Hey, I got the same camera for video-gmailing and went straight ahead to look for solution.
Turns out that it works fine with skype and gmail videochat.
And it's not working with video recording software like cheese.
Cheese's manual suggests using 'gstreamer-properties' to diagnose operability.
I am thinking now, can that be a non-UVC camera?

---

### Post by krzysz00 on 2011-01-05
Yeah, its working now, strange.

---

