---
title: "Poor video quality compared to Windows."
date: 2012-11-15
forum: Multimedia Software
---

### Post by BertN45 on 2012-11-15
I use the webcam for talking to family in Europe using Skype. Sometimes ago I bought a cheap webcam based on CIF Single Chip, knowing that the expected video quality would be relatively poor. It is not very good using my laptop with windows Vista, see picture webcam2. The resolution can be 640x480.

I have made the same picture under the same light condition with Ubuntu 13.04 and 12.04 with the same very bad result see webcam1. The resolution is stuck on 320x240.

I am willing to buy a more expensive webcam, but if I look at the difference in quality I doubt whether I should spend money on it.
I also have the idea that the whole video processing is shaky, since I experienced a number of complete system crashes in both 12.04 and 13.04, where the dumps were written directly to my screen. 
What is your advice, should I spent any money on a better webcam or wait till Microsoft improves the video processing for Skype?
They turn out new official releases of Skype relatively fast, first 4.0 and today 4.1.

Note 1 that I left the light in the picture to prove that the webcam is working in Ubuntu.
Note 2 I tried gstreamer-settings without getting any better result.

---

### Post by mocha on 2012-11-18
Maybe it's an old camera?  Then you have to install the V4L1 library.  Install the package libv4l-0, then load the library before running your program

```
$ LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

---

### Post by BicyclerBoy on 2012-11-18
You can run
gstreamer-properties
& try testing the webcam with v4l2 or v4l1..

Could install/run
guvcview
- the best webcam s/w IMO..
- this prgm allows you to adjust all possible settings, hopefully the settings will stick.. 

(I would remove/uninstall "cheese" at the same time)

It is possible that "skype" uses webcam settings that editable by gconf-editor.

---

