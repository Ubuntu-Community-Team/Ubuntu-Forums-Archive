---
title: "Flash not smooth in Ubuntu 10.04 64"
date: 2010-06-16
forum: Multimedia Software
---

### Post by Fred Jones on 2010-06-16
ubuntu 10.04 64bit
Firefox 3.6.3
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.3) Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3
Flash Player version 10,1,53,64

I have a dual boot configuration with Windows 7 and Ubuntu 10.04 64. While flash videos are watchable, they are not nearly as smooth in Ubuntu 10.04 64 as in Windows 7 especially when I switch to fullscreen. I use firefox as my default browser in both operating systems. Actually, I have tried the newest versions of Google Chrome, SeaMonkey, Opera and others yet the problem still remains. I have tried disabling Compiz as well. Nothing seems to help except switching to Windows 7 to watch fullscreen flash videos. While this works, it is not the solution that I would prefer. Anyone know any way to make flash videos in firefox or any other browser in linux play as well as they do in Windows?

---

### Post by lovinglinux on 2010-06-16
See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by dascheer on 2010-06-22
> **lovinglinux said:**
> See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

I'm having the same problem, and when I followed the link and read the HOWto, nothing improved.  Running dual-boot windows 7 and ubuntu 10.04 64-bit.  Tried chrome and firefox workarounds, but nothing seems to work.  Added the "OverrideGPUValidation = 1" to /etc/adobe/mms.cfg, which didnt help, either.

---

### Post by cbrunhaver on 2010-06-22
This is just the state of flash in linux.  Until this 10.1 release cycle, it was just as bad under OSX, with frame dropped on the highest spec dual xeon nahalem core desktops (see anandtech article).

I have a reasonably modern computer (3.1 gHz AMD Athlon 64 X2 6000+ and an nVidia 9600GT).  

We need GPU acceleration, as what is found on the other platforms in 10.1 but Adobe punted on the issue.  Here is a post by the adobe linux team:

[http://blogs.adobe.com/penguin.swf/2010/01/welcome_to_the_thicket.html](http://blogs.adobe.com/penguin.swf/2010/01/welcome_to_the_thicket.html)

Now is the time to get them to implement VA-API support (with VDPAU / XvBA back ends).

---

### Post by desnaike on 2010-06-22
Hey guys/gals I hope this helps but I always for years now after installing all my plugins and codecs and as root copy and paste the files from usr/mozilla folder into all my browsers plugin folder directly avoiding the symlinks and I have perfect playback worth a try.

---

### Post by xzero1 on 2010-06-23
It seems for 64 bit, flash 10.1 was a downgrade. What I find helps a little is to turn off "enable hardware acceleration" which is enabled by default.

---

### Post by WinterRain on 2010-06-23
I'm still using the native 64bit flash 10.0.45.2 and it runs smooth as silk.

---

### Post by eisenwyrm on 2010-06-24
> **WinterRain said:**
> I'm still using the native 64bit flash  10.0.45.2 and it runs smooth as silk.

From recent readings 10.0.45.2 and earlier versions have a "critical"  security advisory. [Read here.]("http://www.adobe.com/support/security/advisories/apsa10-01.html") So many may want to avoid that route. :!:

My problem, might be same issue, is Flash lagging, creating graphical anomalies (video smearing when scrolling same page) or just crashing Firefox/OS.

Strange thing is I have two *Identical *HP/Compaq EVO D510's. Both same hardware, same Ubuntu version (10.04), both have OS updates installed. "Identical"

The Only difference is one has an nVidia video card, the other OEM chipset. The one running the "on-board" video is the one having problems. **Both ran Flash fine using the _on-board video_ under Windows XP**, so the hardware shouldn't be the problem.

I am new to the Lynux world via Ubuntu (just less than a week) but my experience in the nightmare of Windows :evil: tells me this has just got to be a chipset compatibility plug-in issue. 

Two days now I have been searching for an answer but I keep getting threads such as these. So it is time I stop and pull over and ask for directions...

So question is:
Is this a Flash vs OS issue?
or
Is this a Chipset vs OS issue?
or
Maybe something else...
:confused:

Please point the way! :-D

---

