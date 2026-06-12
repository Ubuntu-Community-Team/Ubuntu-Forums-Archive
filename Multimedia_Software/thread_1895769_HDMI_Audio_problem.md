---
title: "HDMI Audio problem"
date: 2011-12-15
forum: Multimedia Software
---

### Post by osheari1 on 2011-12-15
Hi guys, im new to ubuntu (11.10)
Im having a problem getting the sound to go through HDMI to my surround sound stereo system. It worked on my windows so i know its not a hardware problem.
I have an HDMI cable routed from my stereo to my GTX 560Ti graphics card hdmi port.
Ive tried a bunch of trouble shooting for it and cant seem to get it to work.

if you have any idea how to get it to work I would appreciate the help

---

### Post by wolfen69 on 2011-12-15
I'm going to ask an obvious question here. Have you gone into the sounds settings to make sure HDMI audio is selected?

---

### Post by BicyclerBoy on 2011-12-16
You have to be using the nVidia proprietary driver for HDMI audio.

I believe the GTX560 needs a (relatively) recent driver >= 275, nVidia recommends 290.

Once you have that post:
aplay -l
dmesg | grep HDMI

---

