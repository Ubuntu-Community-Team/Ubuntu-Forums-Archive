---
title: "mythtv mythfrontend recording playback 100% CPU"
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by Nefarous on 2007-01-25
I have a Edgy mythtv .20 backend/frontend setup on my server using a pvr-250 all by following the ubuntu wiki guide, basically default settings all the way around, and I'm using the openbox window manager instead of gnome/kde/xfce.  Everything appears to work fine, but I'm getting an insane CPU load when I'm playing back a recording.

Watching TV and playing back recordings looks just fine, it's not choppy at all.  Running top on the box shows that the CPU is 100% pegged by mythfrontend and Xorg.

I wanted to blame my video card, so I installed mplayer and played the recordings manually and the CPU barely flinched ... 20% or so.

Now I'm perplexed, not sure where to start debugging this.  Is there an easy way to run the mythtv internal player outside of the frontend wrapper?  Watching live TV has similar results.

My setup is using a Athlon XP mobile 2600+, Abit NF7-S v2.0, 512MB of RAM, a really old diamond stealth 3D video card (thought that would be the problem) using the s3virge Xorg driver.  I'm running it at 640x480 on the monitor.

I even tried a ton of scaling options in mplayer, none of them really affected the CPU - except -vo gl - since that would cause me to run software GL speeds - but that was quite choppy - again the mythfrontend playback looks fine - I'm just trying to get the CPU usage down - I've got other things to run on this box.

If mplayer would have pegged the CPU then I'd know where to start (video card) - but without knowing the internals of how mythfrontend is trying to do the playback - I'm not sure - any links or suggestions would be great!

Thanks in advance.

---

### Post by bnuytten on 2008-06-22
Same issue on an Athlon Dual Core 4600+. One core is going to 100%. Running top indeed shows mythfrontend taking up all resources (of that core). Using mythtv-frontend version 0.21.0+fixes16838-0ubuntu3.1.

Before upgrading to Gutsy, it worked like a charm on Feisty. The hardware hasn't changed, ATI driver and hardware acceleration are working...

---

### Post by bnuytten on 2008-06-22
Things that did not work for me:
- booted kernel with "noapic" option set: not much of a difference
- installed xgl: video output totally garbled

Solution (that worked for me):
- install the latest Catalyst drivers (8.6) in stead of the default Ubuntu one's
Not working:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7412 Release

Working:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7659 Release

Video playback is good, mythfrontend taking approx. 30% cpu. 
Still one, rather amusing, issue. I have a dual screen setup. When I play a recording in mythfrontend, it is being displayed twice... one the first screen. One image is stacked on top of the other, so both are stretched. But I guess this has to do with me having a dual screen setup...

---

