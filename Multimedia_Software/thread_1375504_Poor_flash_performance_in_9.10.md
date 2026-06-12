---
title: "Poor flash performance in 9.10"
date: 2010-01-08
forum: Multimedia Software
---

### Post by helix on 2010-01-08
Ubuntu 9.10, slow in Firefox as well but I use Chrome as my main browser. Its a ATI radeon x850xt and I'm using the "extra" visual effects setting but it does this when i try either of the other options even "none".

Other video runs fine, .avi, .ogm, .mkv.... its not a video performance issue just a flash performance issue.

---

### Post by wojox on 2010-01-08
32 or 64 bit?

---

### Post by helix on 2010-01-08
32bit. Video only as well I might add. The audio is fine.

---

### Post by wojox on 2010-01-08
Try this [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by helix on 2010-01-08
> **wojox said:**
> Try this [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

no dice :(

---

### Post by Torchmann on 2010-01-08
> **wojox said:**
> Try this [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

I have found that for my system installing flash does not break firefox it breaks gnome.
whatever it is in the binaries that adobe flash unstalls on the drive related to the system lag is prevalent through subsequent OS system installs and will not go away until performing a drive wipe and NOT installing flash again.
I've tried flash10 with gnome, kde, ubuntu feisty, karmic, kubuntu, ubuntu studio, debian lenney, and ultimate edition. in every case flash 10 lags not just firefox...it lags the entire system. You will notice increased cpu and memory usage and increased latent network traffic with your browser off.
The latent increases will be persistent with network connected apps disabled and through new installs. wiping the drive removes the  problem which is hidden from synaptic. installing flash 10 reinstates the problem. something in flash is acting like a rootkit or a trojan regardless the source of the system lag.
Firefox is probably not the problem.
I have a multi boot system. flash 10 works perfectly with windows explorer and flash under windows xp but exhibit the same flash10 issues under wine that persist under linux.
So i"m presuming there is no incompatibility with flash and my bios or system hardware.
Again...It's like when you browse to an attack site and a Windows oriented trojan or rootkit is in memory and trying to run on a linux system. whatever it is persists on the drive through reinstalls

---

### Post by Project PWNED on 2010-01-08
> **wojox said:**
> Try this [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

**Ubuntu 9.10, slow in Firefox as well but I use Chrome as my main browser.**

---

### Post by helix on 2010-01-09
This is still an issue, any other ideas?

---

### Post by helix on 2010-01-11
bump?

---

### Post by helix on 2010-01-12
I reinstalled all the flash related stuff and things like youtube seem to be working for the most part but only certain websites have laggy video now. The audio is still unaffected.

---

### Post by TBABill on 2010-01-12
Although the flash updates have improved, the Adobe website states that there remains NO hardware acceleration for Flash in Linux distros...so your CPU works that much harder dealing with software acceleration.
 
I do have a feeling the Gnome based distros are worse. I run Flash on OpenSUSE 11.2 and Mandriva 2010, both with pretty good results (and both KDE). Just a thought...my Ubuntu 64 is much slower than either of the others with Flash. In fact it's smooth on SUSE and Mandriva but I just don't like KDE much so I stick with Ubuntu for now (keep coming back).

---

### Post by helix on 2010-01-12
Is there a third party flash driver that has hardware acceleration? This is very troubling something like this can happen. Flash is one of the most popular internet tools ever.

---

### Post by TBABill on 2010-01-13
They will have it released sometime for Linux with hardware acceleration, but right now they have only gotten Mac and Windows completed. I can't recall whether version 10 will eventually have it or if it's a later release. 
 
I tried to play a few flash games on Ubuntu but they were slow and glitchy. I switched over to Mandriva (dual boot) and they play fine. It looks like it's not a kernel issue in how they deal with flash, but maybe the graphical interface? (KDE vs Gnome) OpenSUSE and Mandriva both work pretty well with it considering the issue, but Ubuntu, Mint and MEPIS seem to struggle more.

---

### Post by no2498 on 2010-01-14
? any of you set the gstreamer-properties to no xv
look in cheese

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

### Post by master620 on 2010-01-15
> **no2498 said:**
> ? any of you set the gstreamer-properties to no xv
look in cheese

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

i'm hoping this works.. my problem isn't exactly video lag or anything, its more like i click on something in the flash games/videos, and nothing happens... i have to click it over 2 million times (almost literally) just to get something to happen...

---

### Post by helix on 2010-01-17
> **no2498 said:**
> ? any of you set the gstreamer-properties to no xv
look in cheese

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

Hey thanks for the reply, mine was set correctly and I'm still experiencing poor performance.

---

### Post by helix on 2010-01-18
Anything else to try??

---

### Post by MagicDragon on 2010-03-30
I have similar performance with gnome.
I installed KDE and that fixed all the performance issues with flash.

---

### Post by shikhar_sharma on 2010-03-30
Hi there,
i would recommend you to contact adobe because if they find that this is a bug you would be notified soon enough.But the thing is you cant call adobe tech support because this is a free product.you would have to write a mail to mail to them.You can create a free adobe account and then create a tech support case.Send that case to them.You would be notified in 1 2 days.although they say that you would be notified in 2 3 hrs.I know this because i worked in adobe tech support for an year.This seems to be a bug.You can try searching the knowledgebase of adobe.Many relevant articles are out there.Also this is a problem specific to one machine.have you tried running a clean install of ubuntu and then installiing a flash player.because i use ubuntu and have never faced an issue with flash player.

---

