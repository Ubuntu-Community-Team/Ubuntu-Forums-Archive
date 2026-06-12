---
title: "Hardy has weird video colors"
date: 2008-04-26
forum: Multimedia Software
---

### Post by haletd on 2008-04-26
I just upgraded both of my computers to hardy.  One of my systems has weird colors now with video playback, this happens regardless of the program I am using.  I am running hardy 64bit, asus p5w motherboard, 8600gt, intel quad 6600.  I thought it was a codec issue but I dont think this is the problem.

---

### Post by cojoco on 2008-04-26
Don't have anything offer except confirmation: I also have weird colours, I think the Red and Blue channels are always flipped upon video playback.

I have downloaded the NVidia drivers from Gnome desktop to get special effects, and am running an 8500 video card on an AMD system, 32-bit Hardy.

---

### Post by shad0w_walker on 2008-04-26
Have you tried disabling desktop effects? It may be a weird bug with video playback going through compiz.

---

### Post by mc4man on 2008-04-26
If it's totem,
[http://ubuntuforums.org/showthread.php?t=769209](http://ubuntuforums.org/showthread.php?t=769209)

---

### Post by cojoco on 2008-04-26
mc4man's fix seems to work for Movie Player and Totem, but not Kaffeine.

To summarize:

- Bug appears to be in NVidia proprietary drivers, which get enabled when you enable desktop effects

- To fix from Totem, 

Edit -> Preferences -> Display

Adjust Hue slider to maximum or minimum.

I'm using KDE, but I assume that the the Gnome initialization causes the problem.

---

### Post by haletd on 2008-04-27
Well, after some searching i found a fix:

launch gstreamer-properties from terminal
change the video output plugin to custom
change the video output pipeline to:

ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink

Bug in the proprietary drivers that swaps the U and V planes.
The IY12 and I420 formats are identical except that the U and V planes are swapped, so we swap the swap 


worked for me!

---

