---
title: "Sony Net-Sharing cam not recognized in webcam mode."
date: 2010-08-13
forum: Multimedia Software
---

### Post by xBiocorex on 2010-08-13
Hallo there Ubunters, just a quick question. I have a Sony GC1 Net-Sharing Camera, and it has the ability to be a webcam when connected to the computer. Back on XP, this was picked up instantly, but Ubuntu doesn't seem to recognize it, and I've been to the webcam help topic on the Ubuntu website and it gets me nowhere.

---

### Post by xBiocorex on 2010-08-16
Okay, I've tried a few things, and I noticed that a lot of people say to edit the gstreamer-properties. I found something interesting, when using v4l2 it says "cannot identify device /dev/video0" Would this mean that it knows my webcam exists? Although, it says the same withing with the camera unplugged...

---

### Post by no2498 on 2010-08-17
in a terminal cam plugged in type, lsusb
unplugged same thing
post it here

---

### Post by xBiocorex on 2010-08-19
Unplugged...

```
 Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 005 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
```

and plugged in...

```
 Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 005 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 054c:032d Sony Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
```

I see it, that Sony Corp... so it knows it's there at least.

---

### Post by xBiocorex on 2010-08-26
Bump~

---

