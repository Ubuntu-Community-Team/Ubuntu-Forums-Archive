---
title: "Poor Video Performance on Performance Machine"
date: 2011-01-14
forum: Multimedia Software
---

### Post by AzSoftwareDeveloper on 2011-01-14
So I have been searching for quite some time to see if I could answer this question. I am no stranger to coding, or configuring Linux dists,  but I haven't spent much time, if any, working on video. 

I have no idea what to call it, if it's referred to as frame dropping, or what. But it seems like there is a problem with only part of the screen refreshing, leaving a disparity between the frames directly above, and directly below a horizontal line.

In Windows there doesn't seem to be this problem, the refresh rate is high enough to the point where video playback is very smooth, and there is no frame dropping (again, not sure if I'm referring to this correctly).

Here are the specs to the machine

MSI 790FX-GD70
AMD Phenom II x6 1090T - Stock Clock
8gb of ddr3 (1600mhz)
2x ATI Radeon HD5750's (1GB of DDR5 on each)
Antec 1000W PSU
100GB OCZ SSD - (For Operating Systems)
3x 1TB Samsung Spin Point HDD's

As you can see, there is not a problem with low end hardware performance, and I am running the AM64 Ubuntu 10.10. 

I can't seem to get great video quality with Ubuntu, which saddens me. I've tried logical settings on most video players. Technically I can't get SMPlayer to work at all, but maybe that's just me.

---

### Post by cchhrriiss121212 on 2011-01-14
Try disabling compiz.

---

### Post by AzSoftwareDeveloper on 2011-01-14
> **cchhrriiss121212 said:**
> Try disabling compiz.


Never enabled it, that I know of. Is there additional work to do that other than just selecting "none" under "visual effects" under appearance?

---

### Post by cchhrriiss121212 on 2011-01-14
No, that means compiz is disabled. 
What driver are you using? Have you installed va-api?
Have you tried X11 video output in VLC? This also might help: go to /  Tools / Preferences / Input & Codecs / Codecs ... and set "Skip  H.264 in-loop deblocking filter" to "All

---

### Post by AzSoftwareDeveloper on 2011-01-14
> **cchhrriiss121212 said:**
> No, that means compiz is disabled. 
What driver are you using? Have you installed va-api?
Have you tried X11 video output in VLC? This also might help: go to /  Tools / Preferences / Input & Codecs / Codecs ... and set "Skip  H.264 in-loop deblocking filter" to "All


That actually helped a lot. I'm using the regular ATI drivers though. It seemed to also help to set deinterlacing to "on" and mode to "discard".

---

### Post by AzSoftwareDeveloper on 2011-01-26
I'm starting to think that the AMD drivers for their Radeon series in anything other than windows suck a lot.

For a while, I had it working, but then I plugged in my 2nd monitor into the 2nd video card, and disabled CrosfireX. After that, the only way I could have a working Ubuntu install was to have two seperate Xscreens, but I didn't like that. Everytime I enabled "Xinerama", the ATI driver would crash the Xserver.


I went to the closest working situation I had, with both monitors connected to the first video card, and enabled crossfireX, and kept "Xinerama" off, but was still able to keep one desktop (as I had wanted).

Now videos are running fine, and I can use both monitors well, which I like, but I'm still getting horrible video performance.

IDK if I'm gonna have to just suck it up and not care about it, and watch my HQ videos in Windows, or if theres a solution

---

### Post by cchhrriiss121212 on 2011-01-27
>  			 		   		 		 		I'm starting to think that the AMD drivers for their Radeon series in anything other than windows suck a lot.

That is pretty much accurate, but they are always improving and I think a new version of Catalyst has just been released. I think it depends on how much time you want to spend on this issue, look into va-api if you haven't already or even multi-threaded mplayer.

---

