---
title: "Dell XPS L702X with two external displays - pointer trail"
date: 2013-12-26
forum: Multimedia Software
---

### Post by hasan247 on 2013-12-26
Hi there,

I've recently installed Ubuntu 13.10 on my Dell XPS 17 L702X laptop.

The relevant specs are as follows:

17.3in HD (1600X900) LED TrueLife Display (So not the 3d screen)
NVIDIA GT555M Mobile Graphics
Intel HD3000 Mobile Graphics (I think)
NVIDIA Optimus technology

I have two displays plugged into the laptop - one via the hdmi port which I believe connects directly to the NVIDIA chip, and one to the Mini Display Port which I believe connects to the Intel chip.

On my vanilla Ubuntu install, I am pleased to see that I can use all three of my screens out of the box, however there are a few problems.

First of all the fan is constantly screaming in Ubuntu and the machine feels far too slow. I think this may be because all of the fancy UI effects are being processed by the Intel chip instead of the NVIDIA chip.

On the screen connected to the HDMI port, there is horrific lag which leads to a pointer trail and makes typing in terminal very frustrating as the last letter you've typed takes forever to show up often meaning you type it twice.

What I would like is to be able to run all 3 of my screens without any lag and have all of the effects run through the NVIDIA chip so that the laptop doesn't get so hot.

I would appreciate and suggestions/solutions and also some indication of what to do if the solution prevents me from logging on.

Thanks

---

### Post by oldfred on 2013-12-26
Other posts blame nVidia for running hot.

 Updates to nVidia Prime with 14.04 (only)
[http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI)
Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

---

