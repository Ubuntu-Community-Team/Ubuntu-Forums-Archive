---
title: "Canon Digital IXUS 901S image uploading"
date: 2009-01-10
forum: Multimedia Software
---

### Post by arohanui on 2009-01-10
I was given a Canon IXUS 901S digital camera for Christmas, and now I'm trying to upload the images from it onto my Ubuntu system.  Gtkam doesn't seem to offer the IXUS as an option under Camera>Add Camera.

Any idea how I can get my images uploaded?  Sorry, I've very little undstanding of photo file formats and applications.

(Is this the correct forum for this?)

---

### Post by arohanui on 2009-01-11
bump

---

### Post by lesliek on 2009-01-11
If you have little understanding, I have even less!

However, when I connect my camera (already turned on) to my computer via USB, I get invited to upload photos via the F-Spot Photo Manager. I'm sure it was installed by default.

Have you by chance tried to use it instead of Gtkam? Maybe it'd work.

Edit: Sorry. I should've added that my camera is NOT the same as yours, but that's no reason not to try.

---

### Post by arohanui on 2009-01-12
Thanks so much, that was a really good idea.

Unfortunately, I get the following errors:
```
Unable to mount Canon, Inc. Canon Digital Camera
Error initializing camera: -53: Could not claim the USB device

Unable to mount Linux 2.6.22-14-generic ehci_hcd EHCI Host Controller
Error initializing camera: -53: Could not claim the USB device
```

Anyone know what this means?

---

### Post by arohanui on 2009-01-12
It's possible that the following (from /var/log/syslog) is related:
```
Jan 13 06:19:55 Athena kernel: [ 2321.210661] Inbound IN=eth0 OUT= MAC=00:26:54:0d:e7:85:00:90:1a:a0:03:df:08:00 SRC=208.80.152.2 DST=121.73.18.143 LEN=1500 TOS=0x00 PREC=0x00 TTL=50 ID=20264 DF PROTO=TCP SPT=80 DPT=61871 WINDOW=15 RES=0x00 ACK URGP=0 
```

---

### Post by arohanui on 2009-01-15
I've been able to get it to work under Windoze (thankfully) simply by plugging it in and turning it on, but would very much like to be able to upload them directly to Ubuntu.

---

### Post by joshzam on 2009-01-25
Sorry I can't help with mounting your camera, but have you tried a card reader? Ubuntu mounts my Canon no problem, but I still prefer to stick the memory card into a card reader and transfer the files that way. I find it to be faster.

---

