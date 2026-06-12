---
title: "Problems with External Webcam"
date: 2010-01-10
forum: Multimedia Software
---

### Post by _rex on 2010-01-10
So my Microsoft Lifecam NX-3000 used to work with 9.04, but I can't seem to get anything from it now (Xubuntu 9.10). It still shows up fine when i enter lsusb, but it won't show up as a video device anywhere else. I have faith that this bug is a simple fix for someone who knows what they're doing, but unfortunately I don't. If it's relevant this is on my aging Toshiba Satellite.

---

### Post by gradinaruvasile on 2010-01-10
Open a terminal and type:

xawtv

What happens?

---

### Post by _rex on 2010-01-11
Xawtv wasn't installed, so I installed it in the spirit of inquiry, entered the command and got:

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.31-17-generic)
xinerama 0: 1280x800+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

---

### Post by _rex on 2010-01-14
Just hoping for some support... I know it's M$ so i may be up a certain creek without a paddle, but I'd rather not buy a new one. I tried using gspca... but I have been unable to compile the thing (tried patches, all the fixes I could find online). Am I out $30 for a Logitech camera?

---

### Post by lorsen on 2010-01-14
Did you have a look at this page: [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

