---
title: "64bit Microdia/Sonix Webcam Driver"
date: 2009-04-17
forum: Multimedia Software
---

### Post by afrodeity on 2009-04-17
I have been trying to solve this problem. A cheap Chinese iSonix/Microdia Webcam which is unsupported in Hardy.


After following directions given [here]("http://www.64bitjungle.com/ubuntu/amiga-emulation-with-e-uae-on-ubuntu-32-and-64-bit") /

I determined it was a Microdia 0c45:613b

I opened it and found this:

CNLTF
LT - 168G
085CMTB02 (The B could be an 8)

After googling CNLTF and LT - 168 I found [this site]("http://members.driverguide.com/driver/detail.php?driverid=622034"): 

and this information.

SONIX 0×0c45 0×607c

Pseudo Chip ID

——– ————

MC311P CNLTF LT-168

The above would seem to suggest what my box says, which is the cam is distributed via Sonix and is an iSonic IS-WOO1

Can’t seem to find my bridge or sensor. Please help.

I then found this:

[http://www.linux-projects.org/modules/mydownloads/]("http://www.linux-projects.org/modules/mydownloads/")

It appears the driver is available for Fiesty.

I then downloaded source for it, but of course, it won't compile on 64bit, or will it?

If I try to make, all I get is "warning: initialization from incompatible pointer type"

---

### Post by afrodeity on 2009-04-23
5 days and no response? Anyone with a solution?

---

### Post by afrodeity on 2009-05-28
This is now fixed. See here
[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs]("http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs")

---

### Post by afrodeity on 2009-06-01
Now if only somebody would package this and make it part of Ubuntu Easycam, life would be so much easier [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

---

### Post by afrodeity on 2009-06-01
I would like to use Cheese with my Microcodia Webcam. Cheese uses the gstreamer framework. When I test gstreamer, a "multimedia systems selector" applet pops up, but quits if I test video.


 ```
gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not negotiate format [gstbasesrc.c(2387): gst_base_src_start (): /pipeline0/v4l2src0:
Check your filtered caps, if any]
Segmentation fault

```


Camorama on the other hand just fails miserably with 

```
 Could not connect to vide device (dev/video0). Please check connection
```

---

