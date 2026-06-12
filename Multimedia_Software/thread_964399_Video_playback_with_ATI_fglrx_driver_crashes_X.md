---
title: "Video playback with ATI fglrx driver crashes X"
date: 2008-10-30
forum: Multimedia Software
---

### Post by betamike on 2008-10-30
I installed the proprietary ATI drivers on 8.10.  Compiz was working fine, and nothing seemed wonky.

I went to try to play an avi with Totem, and X crashed.  I restarted and tried again, with the same effect.  I also tried a different video file just in case, but X still crashed.

I have a Mobility Radeon X700

Anyone experiencing a similar problem, or know how to fix?

(I was using the open source drivers prior to this, but they periodically froze the entire system while playing videos)

---

### Post by dave_abrahams on 2009-01-07
Whenever I am running compiz with fglrx, it isn't instantaneous, but if I watch enough video, X itself will crash.  I have to ssh into the machine or ctrl-alt-delete to get control back.

---

### Post by kdreimiller on 2009-02-12
i updated to 9.1 a week ago and its mostly good, except that i do get the occassional system crash when i try to watch a video.  i have no idea why.  i can reboot completely to get my system back up.  im clueless

---

### Post by zuzoa on 2009-07-21
I also use the proprietary "fglrx" driver and whenever I try to play video in Xine, mplayer, etc, X crashes. I have been switching to the open-source "ati" driver beforehand when playing video, but it has become quite a nuisance.

I think ATI is the party at fault here.

---

### Post by zetanuxi on 2009-07-21
I have a similar problem.
I run an ATI x1600 Pro and neither the restricted or the fglrx drivers worked. the video failed so catastrophically that i had to reinstall Ubuntu. I couldn't edit any of my settings in recovery mode either. 

Also, for some reason, the drivers from the ATI site will not run Jaunty. I get an error saying that the drivers are not appropriate for my distrobution. Anyone else have this issue? I really need to have this resolved as that the computer with this issue is my media center. I'm currently having to run the release candidate for Windows 7 and I really don't want to.

---

### Post by ssri on 2009-07-21
> **zetanuxi said:**
> Also, for some reason, the drivers from the ATI site will not run Jaunty. I get an error saying that the drivers are not appropriate for my distrobution. Anyone else have this issue?

ATI, in their infinite wisdom, moved all cards below 2400HD to legacy status, meaning Catalyst 9.3 is the end of the line for your x1600 when it comes to proprietary drivers for them.  Jaunty only supports Catalyst 9.4 and up due to the version of xserver used (1.6.x).  Any attempts at installing Catalyst 9.3 or 9.4 and above in Jaunty for your card will only result in fail.  Your best bet is to use the default opensource radeon driver that comes with Jaunty (or the newest rewrites in git) and descend into xorg.conf hell in order to setup everything correctly.  However, there will be regressions with 3D acceleration and, in my case, stability with the radeon drivers (reported X lockups with enabled desktop effects).  As such, I reverted back to Intrepid and Catalyst 9.3 and have been happy with the stability ever since.  Also, I'm happy with the ease I can see up my S-Video out with ATI's config tool (be sure to disable xrandr).

---

