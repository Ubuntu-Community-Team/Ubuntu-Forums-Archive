---
title: "unity uses cpu to draw?"
date: 2014-04-22
forum: Multimedia Software
---

### Post by kurja on 2014-04-22
Hiall,

I have a decent gpu (nvidia gtx 560 ti) but I notice that moving and/or resizing windows on 14.04 64b isn't smooth and stresses the cpu (Q6600), all four cores go up to 1/3 load according to system monitor just wiggling around one window on the desktop. That's not supposed to happen, is it?!? I have the 331 driver in use. Perhaps related, html5 youtube videos play very poorly, as if there was no hardware acceleration at all, flash is noticeably better as long as I don't try 720p or higher in full screen.

Any ideas??

---

### Post by jbaerboc on 2014-04-22
I'd recommend installing "Unity Tweak Tool" i think it was called and check your settings in there. If memory serves there is a section devoted to shiny things unity does that you can disable or change settings on. I personally have all the pretty settings down as low as they go and have no issues with CPU load. I have a Nvidia 9600GT video card if that helps at all.

There's also a Compiz Settings Tool i think it's called that lets you further tweak your graphical settings for unity. Use that one with caution though as you can bonker Unity with it.

---

### Post by jbaerboc on 2014-04-22
Oh also did you upgrade or do a fresh install? Is 14.04 using a different graphics card driver than you had before? Could be it went back to the default neuvou [or whatever its called ] non-proprietary driver on you so it's not using your video card to its potential.

---

### Post by kurja on 2014-04-23
I did a clean install, and I definitely do have the 331 driver in use, and ```
/usr/lib/nux/unity_support_test -p
``` returns all green.

I don't mind tuning down on the eye candy (I usually do anyway) it's just that putting such high load on the cpu from just resizing or moving a window, well that just doesn't seem right.

---

### Post by jbaerboc on 2014-04-23
> **kurja said:**
> I did a clean install, and I definitely do have the 331 driver in use, and ```
/usr/lib/nux/unity_support_test -p
``` returns all green.

I don't mind tuning down on the eye candy (I usually do anyway) it's just that putting such high load on the cpu from just resizing or moving a window, well that just doesn't seem right.


Completely agree, not sure why that's happening. I can say I don't have the kind of a problem though. Sounds like it's something specific to the setup or install running on your machine.

---

### Post by kurja on 2014-04-24
so if you open system monitor to see cpu loads, and wave it around the cpu trends stay at the bottom?

---

### Post by kurja on 2014-04-24
I also notice in Nvidia Settings monitor page that GPU load stays at zero or one % while the cpu load goes up to 33% upon moving a window on the desktop.

---

### Post by jbaerboc on 2014-04-24
Hmm I guess it does impact it slightly. One of my cores bounces up to 22% utilization for a second but the other stays down at regular levels. That seems to be the only impact of having sys monitor open and moving it around.

---

