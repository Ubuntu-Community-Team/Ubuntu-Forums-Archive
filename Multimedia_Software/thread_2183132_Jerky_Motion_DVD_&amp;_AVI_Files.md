---
title: "Jerky Motion DVD &amp; AVI Files"
date: 2013-10-23
forum: Multimedia Software
---

### Post by chideock on 2013-10-23
Having loaded and got working libdvdcss I now see on Totem Movie Player for both DVDs and AVI files from the harddisk jerky, stop & go playback. System is Ubuntu 12.04 brand new clean install a couple of days ago.

How to fix this?
Thanks

---

### Post by ajgreeny on 2013-10-23
I doubt this is related to your libdvdcss2 situation but more to your graphic card driver or similar.  I'm not even sure that libdvdcss2 is needed for .avi playback; surely it is solely for encrypted commercial DVDs.

What hardware are you running and has this problem just happened after a period when everything was OK?

---

### Post by chideock on 2013-10-23
This is a clean install, first time working on this old desktop, i386, vga output. The vid card is an ati card, i'll have to confirm that tomorrow. Read a help file about DMA for the hardrive and dvd rom, so, wondering if that may be the issue. I loaded XBMC and had the same problem as Totem.

Will check the system tomorrow.

---

### Post by ajgreeny on 2013-10-24
What is an "old desktop" in hardware detail please?  It may simply be that the machine is too low in spec for good video playback.

---

### Post by chideock on 2013-10-24
I checked my system and DMA is enabled for both the dvd-rom and harddrive. Not sure where to go from here to solve this jerky motion.

---

### Post by mc4man on 2013-10-24
Maybe try vlc though the results could be the same

log out & log into a unity-2d session, see if it's any better

try a lighter version of ubuntu like xbuntu or lubuntu

get better hardware

---

### Post by chideock on 2013-10-24
I'll try VLC but I'm with you probably the same
Don't know how to do the Unity 2d session; I'll look that up
Hardware, good idea, I have a win xp portable that I'm thinking of loading Ubuntu on and before I did that I want to understand how to get these utilities runningand the computer I' using has no OS except Ubuntu. It is a 2gig memory, Intel Pentium 4CPU 3.2GHz x2,graphics Gallium 0.4 on AMD RV620, 32bit machine, with a 200gb HD

---

### Post by qyot27 on 2013-10-24
Processor-wise (and memory-wise), that's *more* than powerful enough to play back DVD-spec MPEG-2 and standard definition MPEG-4 ASP* (which is what I'm assuming those .avi files are).  I'd look at the graphics card, and at the desktop environment - Unity may be too much of a strain on the graphics card to permit output to screen correctly at the same time.  The graphics card seems like it'd be new enough to be fine here, but if the AMD drivers are bad or something else went south then I guess it's plausible.

*aka Xvid

It may be the compositor; if you go into xfce or LXDE and make sure anything like Compiz or compton is turned off, it may play back fine.

---

### Post by chideock on 2013-10-26
I logged into unity2d. The dvd and avi files run smooth at twice or more the speed than normal. Same for totem mplayer and XBMC. As a note youtube vids run very fast as well. I have yet to figure out about compiz or compton.
Thanks for the help everyone.

Compositor was off in xfce4. DVD & avi files run smooth but at high speed in Totem mplayer and xbmc under xfce.

---

### Post by chideock on 2013-10-26
I decided to start from scratch. Did a clean reinstall of ubuntu 12.04 after reseating my vid and sound cards. Everything works fine after doing all the software install to get libdvdcss working.

Thank you everyone for the help

---

