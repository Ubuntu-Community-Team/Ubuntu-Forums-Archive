---
title: "Logitech Webcam Not Working; gstreamer-properties freezes"
date: 2009-04-25
forum: Multimedia Software
---

### Post by plinydogg on 2009-04-25
Hi folks,

I've got an ASUS laptop with a built-in Logitech webcam that I'm having trouble getting to work. When I run Cheese the webcam light comes on but the program never really initializes. Taking a picture produces the shutter sound, but that's it. No picture is displayed or saved. Similarly, with luvcview, there's just a black screen and that's it.

Here's my lsusb:

```
Bus 002 Device 003: ID 174f:8a34 Syntek 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Also, when I run gstreamer-properties, select the "video" tab and attempt to test the "default input" the program hangs.

Any help would be much appreciated. 

Thanks!

---

### Post by plinydogg on 2009-04-27
<bump>

---

### Post by plinydogg on 2009-04-30
<bump> + 1

---

### Post by plinydogg on 2009-05-03
<bump> + 2 (the penultimate bump)

---

### Post by xc3RnbFO8P on 2009-05-03
Are you still using Gusty, maybe its time to install Jaunty?

---

### Post by plinydogg on 2009-05-06
Ringi: Thanks for the response. Actually, I need to update that...I'm using Jaunty.

---

