---
title: "Myth has no video in Live TV"
date: 2009-01-02
forum: Mythbuntu
---

### Post by emkamau on 2009-01-02
Help anyone
I've had a working Mythtv setup now for many months. Three days ago I ran out of disk space on the root partition (Myth storage directories have plenty of space). After creating space (moving and renaming myth storage directories and changing same in myth-setup) and rebooting I soon noticed that I now have garbled/scrambled video or just cross hatching in mythtv when I watch Live TV or programs recorded since then. Older recorded programs are fine. Audio is fine as is channel changing and recording, and the logs indicate everything is working well; the video has just disappeared. 

dmesg shows ivtv initialises the PVR150  however in increases its priority from 32 to 64. I've been dealing with this for a couple of days now with no luck.

I'm running 64bit Ubuntu 8.04 with NVIDIA AGP graphics card and a Hauppuage PVR 150 on AMD Athlon 3200+ 2GB RAM, 2.6.24-18-generic kernel, 0.21 mythtv.

Anybody have any pointers as to where I can look or what I can do?

thanks

emk

---

### Post by emkamau on 2009-01-04
Solved!
Oh well there were no responses to this message, but I managed to solve the issue and it was the stupidest thing. I finally after much tribulation swapped out an SVideo cable and that did the trick.

I'm still not sure why a cable would affect LiveTV but not mythvideo and recording. But here is the sequence I went through (see quoted post for background).

After much googling I came across a thread somewhere from 2004 (sorry link lost) that recommended a hardware reset of my Hauppauge pvr150 card. Only way to do this is to power cycle the computer. So I disconnected all cables from the card and shutdown (and disconnected the power cord) the computer for a day. I also shutdown my DirecTV Sat box overnight. Following day, today, I had no video/display on the TV but I had video over xvnc. So I suspected the svideo cable from the graphics card to the TV was at fault I replaced it and voila everything works.

I should add that I had previously, during my tribulations, swapped the graphics card to TV and the Tuner card to Sat box cables to no effect. I can't explain why the cable was the problem. It seems to make no sense to me, since only LiveTV was initially affected.

Anyway its working and I don't have to reinstall/setup mythtv again. Given the choice I would pick a root canal than a mythtv reconfiguration.
Moral of this story, check your cables first!

emk


> **emkamau said:**
> Help anyone
I've had a working Mythtv setup now for many months. Three days ago I ran out of disk space on the root partition (Myth storage directories have plenty of space). After creating space (moving and renaming myth storage directories and changing same in myth-setup) and rebooting I soon noticed that I now have garbled/scrambled video or just cross hatching in mythtv when I watch Live TV or programs recorded since then. Older recorded programs are fine. Audio is fine as is channel changing and recording, and the logs indicate everything is working well; the video has just disappeared. 

dmesg shows ivtv initialises the PVR150  however in increases its priority from 32 to 64. I've been dealing with this for a couple of days now with no luck.

I'm running 64bit Ubuntu 8.04 with NVIDIA AGP graphics card and a Hauppuage PVR 150 on AMD Athlon 3200+ 2GB RAM, 2.6.24-18-generic kernel, 0.21 mythtv.

Anybody have any pointers as to where I can look or what I can do?

thanks

emk

---

