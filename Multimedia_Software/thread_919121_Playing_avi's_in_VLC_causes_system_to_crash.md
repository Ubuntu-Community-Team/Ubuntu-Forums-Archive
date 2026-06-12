---
title: "Playing avi's in VLC causes system to crash"
date: 2008-09-13
forum: Multimedia Software
---

### Post by udbhav on 2008-09-13
Hi, I've literally been running Ubuntu for 2 days, so forgive me if my questions have some really obvious answers.  I couldn't seem to find a solution that worked on any of the forum posts I read.

I'm currently running Hardy Heron on a Lenovo T400 Laptop.  It has an Intel Graphics Media Accelerator 4500MHD onboard.  Every time I play an avi in VLC, I hear audio for a couple of seconds, and then either the screen freezes or goes black.

So far, I tried enabling the Medibuntu repository and installing all the packages suggested by the [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") on this forum.  I also tried disabling all visual effects.

Research I did about the driver for the video card led me to believe that I should not have to install any drivers, as they should have been included with my distribution of Ubuntu.  Am I wrong about that?

Any help and/or suggestions would be appreciated.  Thanks.

---

### Post by icheyne on 2008-09-13
Have you tried opening the avi file with Totem or (better) SMPlayer?

---

### Post by udbhav on 2008-09-13
I tried it in MPlayer (and SMPlayer is just a front-end right?) with the same results.  The screen froze.

---

### Post by icheyne on 2008-09-13
Sorry, but no idea. I had a look at [http://www.thinkwiki.org](http://www.thinkwiki.org) and could not find anything.

Maybe reinstall the video drivers?

---

### Post by eellenoff on 2008-09-15
I have the same problem

T400
Intel GMA 4500MHD
3GB Ram
Intel P8400
Ubuntu Hardy Heron

---

### Post by udbhav on 2008-09-15
After doing some research it seems that since this a brand new video card, support for the card for Linux is not quite in place.  Should I just keep updating the xserver-xorg-video-intel packages over the next few months in the hope that this issue gets corrected, or is there some better method?

---

### Post by udbhav on 2008-09-15
I uninstalled my video drivers, and re-installed them, as suggested, and avi's play correctly.  Unfortunately, I somehow also managed to turn off the ability to use any desktop effects.  Will look into that next.  Thanks for the help

---

### Post by icheyne on 2008-09-15
This page might help:

[http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=2](http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=2)

> Aside from Fedora and a few other distributions, these new packages won't be  pushed into most distribution package repositories until they are readying a next  major release. For instance, Ubuntu users will need to wait until October with  [Ubuntu  8.10]("http://www.phoronix.com/scan.php?page=search&q=Ubuntu+8.10") "Intrepid Ibex" before the latest Mesa / Intel code appear  and thus "out of the box" support for these Intel IGPs. 

---

### Post by eellenoff on 2008-09-15
udbhav - can you specify what you did to uninstall / reinstall the driver?  I'm new to linux/ubuntu and while I would know how to handle the issue in Windows, I'm not quite sure what to do under linux

---

### Post by udbhav on 2008-09-16
I thought I had resolved the issue, but I haven't.  Turns out the video playing was a fluke.  I'm just getting started myself.  I uninstalled the appropriate package through synaptic and then downloaded the drivers again.  That article posted earlier was actually very helpful in clearing up some of my confusion.  The drivers that come bundled with Hardy do not offer full support for the Intel 4500MHD.

---

### Post by eellenoff on 2008-09-17
using synaptic, I found the drivers, but how do I download the new intel driver that they were talking about? xf86-video-intel 2.4.0 driver.  I searched in synaptic, but only the older version comes up, and all the links I found on the web go to [http://www.phoronix.com/scan.php?page=news_item&px=NjYwOQ](http://www.phoronix.com/scan.php?page=news_item&px=NjYwOQ) but where do I go to actually download the driver package?

---

### Post by udbhav on 2008-09-18
[http://intellinuxgraphics.org/]("http://intellinuxgraphics.org/")

---

### Post by camputer on 2008-09-18
I am having the exact same problem on my Lenovo SL 400! I will definitely watch this thread for a solution, as I have yet to figure it out.

---

### Post by lolostich on 2008-09-18
try this


[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by camputer on 2008-09-20
Any luck on figuring this out?

---

### Post by petyo on 2008-09-23
This helped me:
[http://ubuntuforums.org/showthread.php?t=926860&highlight=t400](http://ubuntuforums.org/showthread.php?t=926860&highlight=t400)

I disabled the Intel card from the BIOS, rebooted, enabled the ATI drivers, rebooted again. Video plays well now. Even with the compiz goodies. 

At first, i tried this fix (first result in google)
[http://interskh.info/2008/09/t400-video-crashes-x-in-ubuntu.html](http://interskh.info/2008/09/t400-video-crashes-x-in-ubuntu.html)

But it did not work. Maybe this + ATI made it. 

After the wireless and the video, my problems are all resolved, and I am one happy T400/Ubuntu user...

Now I should find a way to change the keyboard, since the left side is flexing way too much. Damn.

---

### Post by camputer on 2008-09-25
But thing is, I don't have an ati card. I only have the Intel GMA X4500 graphics card.

---

### Post by alfalekos on 2009-03-16
hi!
I have the same problem. Have you found a solution? 
I have just installed ubuntu 8.04 and formed into ubuntu-studio. 
I am working on a new:

Lenovo Thinkpad SL300
ram: 2GB
Processor: Intel Core 2 Duo, @ 1.80 GHz.
Graphics Media Accelerator (GMA) 4500MHD

I faced the problem with Totem, Kaffeine and VLC. Usually the monitor goes black. Only restart makes it work again. The same happens with totem Firefox plug-in when and videos in Firefox. 

Same problem when trying to open .avi or .mp3 files with one of the Totem, Kaffeine and VLC.   

I tried everything mentioned in the conversation of the thread. Nothing worked.

Any ideas?

Thanks a lot.

---

