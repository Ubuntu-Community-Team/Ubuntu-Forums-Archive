---
title: "Change V4L2 to V4L?"
date: 2010-10-06
forum: Multimedia Software
---

### Post by dougydecimate on 2010-10-06
Back when I first initially used Ubuntu my webcam worked flawlessly everywhere. I believe the version was 8.01 or something of the like but at the time I had wireless internet and it was a HUGE hassle so I switched back to windows. Now (10.04) the drivers for webcams seem to have changed from V4L to V4L2 and I had to configure things here and there to make my webcam work and I've got everything working except for userplane chats. I get a REALLY zoomed picture very rather poor quality. I want to get rid of V4L2 and get V4L back. 

I assume this is possible but I haven't the slightest clue on how to make it work.

First off, it says I require a kernel 2.6.x up to 2.6.11 now.. I haven't the slighest clue on how to "make" my own kernel or whatever. If I recall correctly there was a button I could press before, perhaps on boot-up, to change what kernel I could log-on with? Is it the same before? Is the kernel required even listed if so? If not, I have absolutely no close how to "make" my own.

Secondly, I've thoroughly read the install doc that came with the drivers I looked up for my webcam and I don't quite understand this either:

```
Compiling it
============
The driver module can be built without modifying your kernel source tree.

Before trying to compile the driver, ensure that you've configured your
kernel, and updated the dependencies:
'make [config|menuconfig|xconfig]; make dep'.

Make sure, when compiling the driver, you use the same version of compiler as
was used to compile your kernel. Not doing so can create incompatible binaries.

as root
goes to gspcav1 directory and run:
./gspca_build 
```

Can ANYONE help me in anyway whatsoever? Even if it's the slightest amount of information on either of the problems I've listed it would be a great help.

---

### Post by mikewhatever on 2010-10-06
Run **gstreamer-properties** in a Terminal window, in the window that opens click the 'Video' tab, change the 'Default Input'.

---

### Post by dougydecimate on 2010-10-06
> **mikewhatever said:**
> Run **gstreamer-properties** in a Terminal window, in the window that opens click the 'Video' tab, change the 'Default Input'.

I ended up with this.

[IMG]http://i56.tinypic.com/2v9ub5z.png[/IMG]

I'll assume it's because I don't have the driver instead.

---

### Post by mikewhatever on 2010-10-06
Standard usb webcams should mostly just work without you having to install drivers from CDs like in Window. Have you tried it on a clean Lucid installation? Can you post the output of **lsusb** .

---

### Post by no2498 on 2010-10-06
he most likely needs the v4l compat so file

the v4l is part of v4l2 now days

---

### Post by dougydecimate on 2010-10-06
Nevermind. I fixed it.

Had to set the website (userplane.com) to "always allow" on this site. 

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager09.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager09.html)

---

