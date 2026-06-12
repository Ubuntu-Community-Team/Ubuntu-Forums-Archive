---
title: "B&amp;W Windows and IO Wait"
date: 2008-08-13
forum: Multimedia Software
---

### Post by bilijoe on 2008-08-13
Recently (and only since I upgraded to 8.04.1) I have been experiencing more and more situations where one or more windows fade to Black and White, and my processor runs up to between 50% and 100% (usually around 85%-90%), with the system monitor showing all the time being in the IO Wait state (occasionally, a spike of System activity occurs). 

I have several folders containing a lot of images (I collect Hubble photos--BIG hi res files, photos, fantasy art, and celebrity pix), and this condition often occurs when I close an image--the window containing the folder I opened the image from will go B&W, sometimes for several minutes (I've had it last for almost 5 minutes).

I also get this condition when viewing video clips--the length of the clip doesn't seem to affect the likelihood of the problem occurring, it can happen after a 15 second clip, or a 1 hour "movie".  Again, it is when closing the video player (I use both Totem and VLC--I find that VLC isn't always the "go-to" video player it seemed to be under 7.10, sometimes Totem works better), and it's the window containing the folder from which the video was launched that goes B&W.

Today. I had it happen when trying too watch a DVD.  When the system would go to load up and start the DVD, the player window (I tried both Totem and VLC--both acted exactly the same(?)) went B&W and the system monitor showed the processor goint to 100% in IO Wait.  I have a Dell Inspiron system, with a 2.8GHz Pentium IV Hyperthreading processor, running in hyperthreading mode.  When I open the System Monitor Page, it shows 2 processors, and when I'm in this IO Wait mode, both processor graphs show up close to 100% (though this page does not show the processors' state, the System Monitor display in the upper screen panel shows the IO Wait state, but shows only one graph for the processor).

In addition to the processors' odd behavior, I have 4Gb of ram installed (Sys Mon front page shows only 3.5Gb-?-), and when this fade to B&W behavior is occurring, the Sys Mon often shows 100% of the memory being used, usually 50% user, 50% cache.  The Swap space NEVER gets used however.

I am using the video adaptor on the main board--there is no other video/graphics card installed.  I cannot tell from the documentation supplied by DELL, but the video may be 128MB DDR2 NVIDIA Quadro FX 500 (I am looking for a good diagnostic/hardware ID utility that will run under Linux, but haven't found one yet, otherwise I'd have more info).

I hope somebody can help me figure out what's going on here, as it is getting real annoying.  I first blamed it on FireFox3, and downgraded to v2.  The problem seemed to go away.  Mozilla must consider v3 to be post-Beta now, as when I visited their site recently, it upgraded me to v3 (without asking), and made no mention of Beta status.  I was going to downgrade again, until I realized that the B&W problem happens when FierFox isn't even running.

I just ran a test where I tried to play a DVD, and got the following:

SysMon in panel:
CPU @ 77%, approx 1/3 User, 2/3 System (oddly, no IO Wait this time)
Memory: 66%in use by programs, 33% cache

SysMon Window:
CPU1: 96%
CPU2: 97%
Memory 64% in use
Processes: CPU usage
     --totem: 38%
     --gdm: 25%
     --gnome-system-monitor: 15%
     --Xorg:10%
System Load: between 2% and 3%

Output from 'top':
CPU(s): 37% User, 45% System, 16% id, all others 0%
Mem:   3627600k total,  3513120k used,   114480k free,    30980k buffers
Processes: CPU usage
     --totem: 75%
     --gdm: 52%
     --gnome-system-monitor: 17%
     --Xorg: 17%
System Load: between 2.15% and 2.65%

I can't think of any more information that might be useful.  I hope one of you Ubuntu-Linux Gurus out there can shed some light on what's happening here.  Any feedback or suggestions will be greatly appreciated.
EDIT: 8/17:  Really?  None of you Ubuntu-Linux Wizards out there can give me any idea what might be going on?  Do I have this in the wrong forum?

---

### Post by bilijoe on 2008-08-18
Hmmm, I guess an edit doesn't get you a bump.  Anyway, did I put this in the wrong forum?  Or is this just too difficult a question for you Gurus out there?  Any help?  At all? Pleeze!

---

