---
title: "OpenGL Issues with ATI X1250"
date: 2012-09-12
forum: Multimedia Software
---

### Post by friskyg on 2012-09-12
I'm fairly new to lubuntu although I did do quite a lot OpenGL programming on Unix platforms many years ago.   
 
I'm trying to configure lubuntu 12.04 on a HP T5730 (thin client PC) with an onboard ATI X1250 graphics chip to run XBMC as a media center.  I installed lubuntu with the latest open source radeon drivers - but when I installed and ran XBMC the screen is missing triangles and flickers randomly.   Knowing that XBMC is OpenGL based I then checked glxgears and it is suffering the same problem (missing triangles).
 
I have spent the last 2 days searching the web (and these forums) to find a solution to this.   I really want to avoid installing ubuntu 8.0 just to be able to use the legacy proprietary ATI drivers. I have tried:
[LIST]
[*]Installing and using the latest xorg-edgers drivers (no difference)
[*]Installing the software only gl driver (libgl1-mesa-swx11).  This fixes glxgears, however then xbmc wouldn't run.   I eventually got xbmc to run with the software driver by setting the env variable *export MESA_GLX_FORCE_ALPHA=1*.  However performance was abysmmal.
[*]Setting vblank_mode=1 or 0 (no difference)
[/LIST]Eventually I stumbled across something which does fix the issue - although it is very odd.   If I play an mp4 video using mplayer before running glxgears or xbmc (with the standard libgl1-mesa-glx drivers) then suddenly both work properly - and the xmbc performance is actually pretty good considering my hardware.
 
Obviously mplayer is resetting the OpenGL/xserver state in some way - even though I'm using mplayer with the xv output driver (ie mplayer -vo xv myvideo.mp4).  Does anyone have any idea why this behaviour and is there a better fix then me playing a video using mplayer each time I log in?

---

### Post by newhans on 2012-12-10
Hi there,

i'm also owner of a HP T5730 and failed to get XBMC  running on it. I try it with XBMC Live, XBMCbuntu, standard Ubuntu and  some other Distros, but always having problems with Radeon X1250... The  next step will be an installation of Ubuntu 8.04 with the old AMD  drivers. Is there someone that made already experiences with it, or  generaly have success with any other MediCenter software for this  machine??

---

### Post by stigweed on 2013-01-06
> **friskyg said:**
> Eventually I stumbled across something which does fix the issue - although it is very odd.   If I play an mp4 video using mplayer before running glxgears or xbmc (with the standard libgl1-mesa-glx drivers) then suddenly both work properly - and the xmbc performance is actually pretty good considering my hardware.
 
Obviously mplayer is resetting the OpenGL/xserver state in some way - even though I'm using mplayer with the xv output driver (ie mplayer -vo xv myvideo.mp4).  Does anyone have any idea why this behaviour and is there a better fix then me playing a video using mplayer each time I log in?

I'm having exactly the same problem. Did you work out what mplayer does to fix it? Thanks for sorting that much

Also on an Ati Readon X1250 graphics card on an LG E300 laptop.

---

### Post by rrich1974 on 2013-01-07
i have a an ati x1270. there is not supported anymore by ati. the only chance is the radeon driver. 
for me, it runs quite well, the performance is almost the same as proprietary driver in windows 7. 
i use vlc, mplayer (from console) or XBMC for 1080p hd movies. i must admit that xbmc is the best media player.

you can use mplayer with a certain output by adding a line in the home-.mplayer conf. 
i dont know exactly the line, it goes something like "mplayer -vo xv"

---

### Post by stigweed on 2013-01-14
Hi all, 
Unfortunately I'm not getting anywhere with this...
First run: ```
xinit xbmc
```
and I get xbmc with a flickering screen divided up into triangles.

However, if first I run
```
startx
mplayer x.mp4
```
then killall Xorg and run xinit xbmc then xbmc will load up and look fine as above. But this seems to work with many apps (quicksynergy, firefox) but not for example xcalc. I'm guessing some library that these 'higher level' apps load (but xcalc doesn't) is doing something that fixes the screen flicker before xbmc.

As a seriously ugly work around, I'm running this script to start xbmc (by first starting a firefox x session, killing it then starting a new one for xbmc:

```
xinit firefox &
sleep 8
killall Xorg
sleep 5
xinit xbmc &

```

Anyone have any idea why this should be happening or how I can avoid this trouble?

---

