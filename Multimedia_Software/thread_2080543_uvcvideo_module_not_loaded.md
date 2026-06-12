---
title: "uvcvideo module not loaded"
date: 2012-11-04
forum: Multimedia Software
---

### Post by Sisophon2001 on 2012-11-04
Hi,

When I start lubuntu my webcam will not work in cheese or skype. To fix the problem I need to load the uvcvideo module like this:

```
sudo modprobe uvcvideo
```

Now everything works perfectly.

Where can I add uvcvideo to the list of modules that should load on start-up, and why is it not loaded automaticly? I think a USB device should be automaticly detected. I want it to work for all users.

This is my webcam

```
lsusb
Buss 001 Device 003: ID 0ac8:c33f Z-Star Microelectronics Corp. Webcam
```

Garvan

---

### Post by Sisophon2001 on 2012-11-06
BUMP

Also I found out that the driver is first loaded then unloaded. I am using the Samsung mini computer in my signature below.


> garvan@garvan-N148P:~$ dmesg | grep uvcvideo
[   15.902089] uvcvideo: Found UVC 1.00 device WebCam SCB-0340N (0ac8:c33f)
[   16.037516] usbcore: registered new interface driver uvcvideo
[   22.352162] usbcore: deregistering interface driver uvcvideo
garvan@garvan-N148P:~$ 

---

### Post by Sisophon2001 on 2012-11-26
Is there anyplace elce you would recomend that I could look for help on this issue?

---

### Post by Sisophon2001 on 2013-01-01
The problem was solved using "samsung-tools" to turn on the webcam.

---

