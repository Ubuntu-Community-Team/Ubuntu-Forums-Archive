---
title: "How to make ATI  Radeon better."
date: 2011-05-10
forum: Multimedia Software
---

### Post by Duncan Williams on 2011-05-10
I am using proprietory ati drivers for my hd3650 graphics card.
It is amazing in windows but in ubuntu unity it is noticeably not as good (specially with videos).
Is there other tools or settings I can use to increase the performance.
Also windows catalyst control centre has overclocking and allows my 24" monitor at 1920by1080 to run at 75mhz.
The ubuntu catalyst control centre doesn't have these options, is there a way to access these settings.

I tried looking at aticonfig and got lost.

Any help/comments appreciated.

---

### Post by handy on 2011-05-10
If you are not playing games that are intensely 3D, & you are not using a notebook where fan speed & power management is critical, then you will very likely get better 2D performance;- movies & such with the Gallium open-source drivers.

If you want the cutting edge kernel/driver stack, then use the how-to in "Ubuntu Stuff:" found in the first post of this thread:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by demilord on 2011-05-10
The open source drivers of ati has been so much increased.. its almost outperforming the closed source drivers... and the open source are so much more stable then the closed source...
Here you can see the performance chart of the drivers.. and other benchmarks

[http://www.phoronix.com/scan.php?page=home](http://www.phoronix.com/scan.php?page=home)

---

### Post by Duncan Williams on 2011-05-11
The AMD Catalyst™ 11.5 Proprietary Linux x86 Display Driver was released a few days back. I am installing that and sticking with it for now at least.
Thanks for the links phoronix is very interesting for me.

I re-accessed my situation.

I have my new (for me) ati rd3650 / 512mb graphics card installed.

I have a dual boot grub.
* windows XP with ati catalyst set to optimum everything, also over-clocked and at 75mhz (can only get 60mhz in ubuntu).
1920 by 1080 resolution - 32 bit colour.
 
* ubuntu unity with ati catalyst set to optimum everything
1920 by 1080 resolution.

My mp3 and mp4 collection (50gig) is stored on my windows partition. I can access the files easy but performance of videos is degraded if not copied to ubuntu partition.

Windows is setup with no frills but full updated drivers and support for all peripherals.

So if I want to watch a HD movie or play a 3d game I just reboot into windows.
I use ubuntu unity for everything else and the graphics are clear and crisp at full resolution.

After reading material related to this issue over the last few days. I now realise that the drivers and the kernel are constantly being updated.
Thanks for your help and info.

---

### Post by handy on 2011-05-11
My wife watches videos (well over 1TB of them available) over our 10/100 Mbit LAN, on her machine with absolutely no problems what so ever. She's using a version of OS X.

I can do more than the same thing that she is doing (simultaneously I might add):= Watch a video, whilst encoding another video via HandBrakeCLI, & be downloading multiple torrents & have a LOT of Firefox tabs open at the same time.

I use the open-source AMD/ATi Gallium driver stack. I watch movies in a variety of formats (predominantly .mp4) on 1920 x 1200 res'.

The aforementioned driver stack isn't as good as Catalyst for 3D games, but apart from that, the open-source driver stack from my experience is superior to Catalyst in every other way.

One of the wonderful things about the open-source stack, is that it is SO easy to upgrade. & I know what I'm talking about as I use Arch with its rolling release (daily in my case) upgrade system, & I also have been using the AMD/ATi associated GIT packages & kernel & I have had roughly 3 problems over the last 18 months. :D

---

### Post by Duncan Williams on 2011-05-12
ok, i'll give the gallium drivers a go and se what happens, I am a bit wary though, coz if I upset anything and go back to failsafe graphics mode, wud be sad, so pondering.

---

### Post by lonfucius on 2011-05-12
> **Duncan Williams said:**
> 
* windows XP with ati catalyst set to optimum everything, also over-clocked and at 75mhz (can only get 60mhz in ubuntu).
1920 by 1080 resolution - 32 bit colour.


what do you mean by "75mhz, 60mhz"? are you talking about Pixel Clock Bandwidth? Or it's typo for 75hz, 60hz refresh rate?

If you want to get 75mhz pixel clock, or 75hz refresh rate with Catalyst driver, use "xrandr --newmode <custom modeline>" to get it.

And to enable the UVD function to watch H264 & VC1 videos, you need mplayer-vaapi

and for overclocking gpu settings, you may check the last few paragraph of "aticonfig --help"

I'm using fglrx driver from the repo, and have encountered similar problem to yours, and it was solved. hope these infomation helps!

---

### Post by Duncan Williams on 2011-05-13
yes meant 75 hz.
as in refresh rate.

Could you go through what you said in more detail for me, a beginner. please?
I want to set my refresh rate to 75hz.
I want to slightly overclock my gpu.
I want to use all aspects of gpu and videoram.

thanking you.

---

### Post by Duncan Williams on 2011-05-13
*If you want to get 75mhz pixel clock, or 75hz refresh rate with Catalyst driver, use "xrandr --newmode <custom modeline>" to get it.*
tried this command in terminal - no result.

*and for overclocking gpu settings, you may check the last few paragraph of "aticonfig --help*"
had a play around in aticonfig to wary to change settings in there.

*And to enable the UVD function to watch H264 & VC1 videos, you need mplayer-vaapi*
looked at mplayer-vaapi - Don't know if I have other files that it needs, don't know if I should install all mplayer things in synaptic. Don't know if its totem or other one.

so, I'll just leave it all as it is in case I mess something up.
Thats why I like the windows `ati control centre' just switch things on and off.

It's all running fine accept videos sometimes jerky and few other minor issues.

---

