---
title: "MythTV and PVR150's"
date: 2012-02-16
forum: Mythbuntu
---

### Post by jlp_engineer on 2012-02-16
I have been using Mythbuntu for several years now.  I have two P4 systems with 875 based boards, with 2 Gig of memory.  One processor is 3.4Ghz, and the other is 3.2GHz.  One system has three (3) PVR150's and the other contains 2 ATi HDTV Wonder cards, and one PC HDTV 5500 card.  The analog cards are in a slave backend, and the digital cards are in the master.  The digital cards work well with Mythbuntu 11.04.  Loading 11.10 results in a hung system at boot.  The PVR-150's in the first system is what I am having trouble with. When I load 11.04 and configure the three PVR-150's, the resulting analog stations that are tuned, about 80% of the time, result in video that is distorted, jumping, and with freezing and stuttering.  Once the distortion starts, about 25% of the time, I get either the error "Error opening jump program file" or "Video frame buffering failed too many times".  

I have tried tuning a digital station first (on the master), as suggested by one of the MythTV bug tracking reports.  Maybe this will not work for me, as the digital cards are in a separate system.

I have tried disabling HyperThreading on my P4 - no change.

I have tried running the backend booted to a text only mode - no change.

I have tried updates in the 0.24.1 fixes branch, up until 3 or 4 weeks ago - no change.

I have tried loading Mythdora 12.23 (MythTV version 0.23) and it resulted in a 100% working system with perfect video, but when I applied updates, and updated MythTV to 0.24, attempting to tune ANY analog station resulted in a hung frontend.  Sooooooooooooooo, close.

On a whim, I tried loading Ubuntu 11.04, and then used Synaptic to load the MythTV modules, and it resulted in a working system, with perfect video on all of my PVR-150's.  I could change channels over a dozen times before I ran into any kind of trouble.  But I got absolutely no distorted video.  Instead, about every dozen or so channel changes, I get a long pause on the frontend, and then I see the main menu with the error message "Video frame buffering failed too many times.".  And that is fairly consistent - the engineer in me likes consistency.  I have not applied updates or loaded the fixes branch yet - should I?  I would like to isolate the problem first, but the only tools I have is a persistent attitude and my hardware engineering background. 

I would prefer to stick with Ubuntu, as it is what I know.  Does anyone have any suggestions, what to try next?  

One last note, is that Mythbuntu 8.10 works perfectly on my analog tuners, but I cannnot use version 8.10 any more, as I cannot update it, and I need to run later versions of MythTV for the VDPAU support on my remote front ends.

Thanks to all for any help.

---

### Post by nickrout on 2012-02-16
It is very hard to know whether this is a driver problem or mythtv problem. When you upgraded myth from .23 to .24 did the kernel get updated too?

On a "broken" system does mplayer /dev/video0 work?

---

### Post by jlp_engineer on 2012-02-17
> **nickrout said:**
> It is very hard to know whether this is a driver problem or mythtv problem. When you upgraded myth from .23 to .24 did the kernel get updated too?

On a "broken" system does mplayer /dev/video0 work?

Well, I can only assume that the kernel was updated as well.  Ubuntu 11.04 is loaded on it now, but I could re-load the image I made of Mythdora 12.23 before the update, and then check the kernel version before and after.

On a broken system (running Mythbuntu 11.04), I have tried cat /dev/video0 > video.mpg, and the distortion is still there.  

Thanks.

---

### Post by jlp_engineer on 2012-02-22
> **nickrout said:**
> It is very hard to know whether this is a driver problem or mythtv problem. When you upgraded myth from .23 to .24 did the kernel get updated too?

Nick,

I re-loaded Mythdora 12.23, but when I tried to update just the kernel or MythTV, a secondary screen popped up saying that it needed to load all these other updates (that I didn't select) as well.  Loading Fedora with MythTV seems like a good troubleshooting step, but I would rather load Ubuntu, as it is what I am familiar with.

While I have Mythdora loaded, do you know if there is a way to update just the kernel or just MythTV without having to load all the rest of that other garbage with it?  The update manager doesn't seem to allow it, although everything has check marks next to it, that you can "un-check".  Not very useful if you have to load all the updates anyway :-(

---

### Post by nickrout on 2012-02-22
> **jlp_engineer said:**
> Nick,

I re-loaded Mythdora 12.23, but when I tried to update just the kernel or MythTV, a secondary screen popped up saying that it needed to load all these other updates (that I didn't select) as well.  Loading Fedora with MythTV seems like a good troubleshooting step, but I would rather load Ubuntu, as it is what I am familiar with.

While I have Mythdora loaded, do you know if there is a way to update just the kernel or just MythTV without having to load all the rest of that other garbage with it?  The update manager doesn't seem to allow it, although everything has check marks next to it, that you can "un-check".  Not very useful if you have to load all the updates anyway :-(

I have never run fedora, although I used redhat way back when ...

so the answer is that i do not know.

Do be aware though that the mythdora project is effectively dead. [http://mythdora.com/?q=node/5808](http://mythdora.com/?q=node/5808)

---

### Post by wirepuller134 on 2012-02-22
I don't think I would count Mythdora out yet.  Ryan is still working on taking it in a different direction.  
As far as updating Mythdora, there are step by step instruction for it on the forum.

---

### Post by jlp_engineer on 2012-02-24
> **nickrout said:**
> I have never run fedora, although I used redhat way back when ...

so the answer is that i do not know.

Do be aware though that the mythdora project is effectively dead. [http://mythdora.com/?q=node/5808](http://mythdora.com/?q=node/5808)

Dead or not, I have to go with what works...

I finally figured out, by playing around with "YUM", how to upgrade just MythTV without updating anything else like the kernel or other packages.  

```


su root
yum upgrade mythtv

```

It then upgraded MythTV and all related programs.  The kernel is still the older version.  So what was the result?  Yum upgraded Mythbackend to 0.24-2 fixes branch (from 0.23), and well, my PVR150's are still working. The ONLY change is that I have noticed some delays in getting video about 10% of the time, with a small amount of video artifacts on those few channel changes.  The majority of the time I still get perfect video on any of my PVR150's, which is fine by me. 8-) 

I am not a programmer - this I have said many times, but I have done some assembler and a little C programming many years ago.  With what I have done and experienced so far in all the iterations I have tried, I can't help but put out a theory, in the hopes that it will reach someone with the necessary skills to either confirm (and perhaps fix) or deny my hypothesis. So here goes... [-o<

I would say that the bugs being tracked on the MythTV site, particularly (click on the number to see bug) [9177]("http://code.mythtv.org/trac/ticket/9177"), [9201]("http://code.mythtv.org/trac/ticket/9201"), [9769]("http://code.mythtv.org/trac/ticket/9769"), [9830]("http://code.mythtv.org/trac/ticket/9830"), [9846]("http://code.mythtv.org/trac/ticket/9846"), [10206]("http://code.mythtv.org/trac/ticket/10206"), and [10244]("http://code.mythtv.org/trac/ticket/10244"), are all due to a bug in the kernel, and that MythTV is showing different manifestations of the bug, depending on what tweaks to the MythTV code are done to squash this bug.  :idea:  My best guess is that it is in the IVTV driver or a related library, and has been there for years, and rears its head under the right conditions.  The last statement is just based on the fact that I had a working system under Mythbuntu 8.10, and as soon as I loaded Mythbuntu 9.10 (and all after it) video from my PVR150's stopped working.  Various things were done in MythTV to fix it, but nothing worked 100%. :confused:

However, as I said before, I haven't given up on Ubuntu or Mythbuntu, I will still be using Mythbuntu 11.04 for my other backend, and all my frontends.  This will at least get me by until this is figured out by someone smarter than me.  I am also hoping that the hang I get trying to boot my servers (P4 875 based boards) on 11.10 is also fixed - maybe Mythbuntu 12 will be worth the wait. ;-)

Any and all comments welcome.

---

### Post by nickrout on 2012-02-24
One of the difficulties with *buntu is that the kernel version is closely tied to the release version.

You'd be freer to choose which kernel you are on with something like Arch or gentoo.

Also if you want to try another custom built myth LinHES is good (based on Arch).

---

