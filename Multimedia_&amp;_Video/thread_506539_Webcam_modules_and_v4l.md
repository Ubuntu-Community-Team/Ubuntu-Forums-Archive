---
title: "Webcam modules and v4l?"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by leo1981 on 2007-07-21
Hi,
most webcams don't have support on linux, mine has too much.
I have a Trust 120 Spacecam.
There are 2 modules: gspca and sn9c102.

About gspca: Sonix sn9c10x + Pas106 
It is v4l compliant
It works with: Camorama, xawtv, Kopete
It doesn't work with Ekiga.

About sn9c102: SN9C1xx PC Camera
It is v4l2 compliant
It works with: Ekiga
It doesn't work with: Camorama, xawtv, Kopete

By default, the system (Ubuntu feisty) loads both of them, but only sn9c102 uses the device.
I'd like to use one single module for all.
Right now I have to use insmod/rmmod to switch between v4l and v4l2.
Is there any other solution?

I tried to upload all modules and software, but with no results.
gspca v1.00.18
sn9c102 v1.48
ekiga v2.0.9

Can I load the device in /dev/video0 and /dev/video1 in the same time, with different modules?

Do you have any suggestion?

---

### Post by YannickDefais on 2007-07-23
Hi,

You should go with V4L2 only. Video 4 Linux 2 (V4L2) is an improvement over Video 4 Linux(V4L).

Regards,
Yannick

---

