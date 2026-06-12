---
title: "vlc playback on xvideo making video freeze every few seconds"
date: 2008-11-06
forum: Multimedia Software
---

### Post by lashi on 2008-11-06
G'day. 

So, after upgrading to 8.10, I noticed that video was behaving extremely badly under VLC. I was just watching DX50 coded videos, that worked perfectly fine under 8.04.

I mucked around for a while, and made some headway to solving the problem from switching the VLC output to OpenGL, rather than XVideo (which I think is default). This was still not the best option, but it was much better than the video freezing every few seconds.

I tried many other things, for instance, increasing the cache from 300ms to 5000ms. I was initially playing the video off a DVD - so I decided to copy it to the disk and try. The problem still persisted. This told me that it wasn't a seek issue with my DVD, and it was something more fundamental.

I also noticed a CPU load burst at every position when the video froze. I was inclined to think that this was either an XOrg issue, or a kernel issue. I highly doubted the latter, but it was easier to test that than muck around with XOrg internals. So, I booted 2.6.24-21-generic. To my surprise, I was able to watch videos flawlessly using the XVideo extension as output.

Can other people also verify this for me?

---

### Post by willywortel on 2008-11-13
Please tell me how to do that... I am going insane with this problem. I thought it was the lack of video memory (256mb) But then again the graphic card can  tap into my ram (3gig) if it wants to. And with Hardy it was perfect.

---

### Post by JesterDev on 2008-11-13
Confirmed. I had the same issue in the last days that 8.10 was in beta. Didn't matter what Codec, nor did it matter if it was on DVD. I had major issues. After bootng 2.6.24-21-generic the problem has gone away. 

Often the audio would continue playing, but video would freeze. I also had issues with out of sync audio on videos that played fine before. 

Issue seems to be resolved now.

---

### Post by Maconvert on 2008-11-25
What exactly did you do to fix this problem?
I have it with the latest VLC media player and Ubuntu 8.10 and it's driving me nuts.

---

### Post by bluegene on 2008-12-14
i had the same issue with vlc freezing after a couple minutes of playback. I am using Ubuntu 8.10 with proprietary ATI drivers and compiz enabled. Later, I decided to use SMPlayer and had no problems with it so far even with compiz fusion enabled. You might give it a try though. :)

```
$ sudo apt-get install smplayer
```

---

### Post by Colt45 on 2008-12-18
New Ubuntu convert, I did a fresh install of 8.10 several weeks back and have been experiencing this problem.  Signed up to the forums to reply and bump thread in the hope that someone more knowledgeable has the ability to track down the cause of this bug and fix it for intrepid.

Another thread discussing issue on VideoLAN forum.

[http://forum.videolan.org/viewtopic.php?f=13&t=53415](http://forum.videolan.org/viewtopic.php?f=13&t=53415)


I haven't reverted to an older hardy kernel yet, so I'm not sure if that fixes this issue.

Has anyone considered this may be related to similar problems being reported with Xorg High CPU usage in Ubuntu 8.10?  Every time I observed video freezing Xorg would jump about 10% in CPU usage.

Maybe this is related to this bug..

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972)

---

### Post by Colt45 on 2008-12-19
I find it hard to believe that more people are not experiencing this problem.

Skipping/Freezing observed with fresh install of Ubuntu 8.10.  Happens when booting under kernel 2.6.27-7 and 2.6.27-9. I've tried nvidia drivers 177.80 and 177.82.

The Skipping/Freezing isn't observable directly after a fresh boot of the OS.
It only seems to show up a few hours after the OS has been running. 

[FONT="Courier New"]
OS.........................: Ubuntu 8.10
Kernel.....................: 2.6.27-9-generic (x86_64)
...........................: 2.6.27-7-generic (x86_64)
X.Org Server...............: 1.5.2
OpenGL.....................: 2.1.2
NVIDIA ....................: 177.80
...........................: 177.82
File-System................: ext3[/FONT]

---

### Post by rocker9455 on 2008-12-20
I got a very similar problem as well, i can open up an avi file and then watch it for a few seconds then its will blackout and sound continue then when i open to full screen it flickers the video but then when in full screen doesnt :/

---

### Post by Colt45 on 2008-12-20
> **rocker9455 said:**
> I got a very similar problem as well, i can open up an avi file and then watch it for a few seconds then its will blackout and sound continue then when i open to full screen it flickers the video but then when in full screen doesnt :/

I haven't experienced any blackout issues, only random skipping/freezing that always corresponds with around a 10% CPU spike in Xorg.

It doesn't matter what codec.  It isn't limited to 0.9.4 either, because i installed 0.8.6h a few hours ago and I'm already seeing the same symptoms.  I've got an AMD X2 4400, and vlc only uses max 50% of one core during 720p playback. The hardware isn't the issue here as playback worked fine under XP.

---

### Post by Colt45 on 2008-12-25
Posted this solution to the forums at 

[http://forum.videolan.org/viewtopic.php?f=13&t=53160&p=177984#p177984](http://forum.videolan.org/viewtopic.php?f=13&t=53160&p=177984#p177984)





Credit goes to shaundennie 
[http://www.nvnews.net/vbulletin/showthread.php?t=106746](http://www.nvnews.net/vbulletin/showthread.php?t=106746)


**UPDATE**: *12/26/08*
The steps in this post fix tearing in XVideo/X11 and improve desktop responsiveness, but they do not fix the skipping issue.



Problems with desktop responsiveness mainly appear to be attributed to Compiz or Ubuntu's autodetection of refresh rate.  Compiz or Ubuntu will round down display refresh from 59.99Hz to 50Hz instead of setting it to 60hz.  This rounding down of 10Hz seems to cause  the slowdown that many people are experiencing with Ubuntu desktop performance.   To overcome this, you need to manually set your display refresh rate to 60Hz in CompizConfig Settings Manager.


**Fore note**:
----------------------------------------------------------------------------------------------------------------------
A few days before executing the steps below, I reverted to Nvidia 173.14.12 and VLC 0.8.6h
It's entirely possible that you may be fine using Nvidia 177.80 or 177.82 with VLC 0.9.4
or later after following the steps below.  I have not tested further. If you encounter success
with newer drivers or newer vlc, please post results.



----------------------------------------------------------------------------------------------------------------------
**STEPS**: *Compiz Configuration*

1. Download CompizConfig Settings Manager from Ubuntu repository.
2. Navigate to.. System --> Prefences --> CompizConfig Settings Manager
3. Navigate to.. General --> General Options
4. Click "General Options" to open window
5. Click "Display Settings" tab
6. Uncheck "Detect Refresh Rate"
7. Move "Refresh Rate" slider to 60, or set 60 in the box
8. Check "Sync to VBlank"
9. Click back button to move back to main CompizConfig window
10. Navigate to.. Utility --> Video Playback
11. Uncheck "Video Playback" then exit the CompizConfig Settings Manager.


**STEPS**: *Nvidia Configuration*

1. Pull up nvidia-settings
.. Navigate to.. Applications --> System Tools --> nvidia-settings
.. or open a terminal, type "nvidia-settings" , press enter
2. Click "X Server XVideo Settings"
3. Check "Sync to VBlank" _IF_ not checked
4. Click "OpenGL Settings"
5. Uncheck "Sync to VBlank" _IF_ checked
6. click quit button
7. click quit button
8. Reopen nvidia-settings to verify that config changes were saved.
.. IF they were saved, you are done with step 8.
.. IF they were not saved, ~/.nvidia-settings-rc in your home directory
.. may be under root permissions. You will need to chown chgrp for the file.
.. Then you will need to start back at Step 1 and repeat all steps.

**IMPORTANT**: Reboot your machine when finished. The driver changes won't function correctly until you reboot

---

### Post by geekgeek on 2008-12-26
Hi all,

I'm having this problem on Ubuntu which I have just installed onto my eeepc 1000.

The funny thing is, I never this problem when I was using the defult Xandros distro to playback AVI files.

Changing to Open GL and applying Colt's Compiz settings seems to have helped somewhat, but video is still freezing up and prone to artifacting, though audio is entirely unaffected.

I wonder if anyone else has a solution? Sorry but it's quite frustrating for a linux newbie :(

---

### Post by Colt45 on 2008-12-26
> **geekgeek said:**
> Hi all,

I'm having this problem on Ubuntu which I have just installed onto my eeepc 1000.

The funny thing is, I never this problem when I was using the defult Xandros distro to playback AVI files.

Changing to Open GL and applying Colt's Compiz settings seems to have helped somewhat, but video is still freezing up and prone to artifacting, though audio is entirely unaffected.

I wonder if anyone else has a solution? Sorry but it's quite frustrating for a linux newbie :(
Yeah, I seem to have spoke too soon..


There still remains some skipping that coincides with Xorg CPU spikes.

---

### Post by Colt45 on 2008-12-26
After frame skipping started to appear again, I went back and started watching top output in terminal. Top refreshes pretty fast; I would switch over from vlc to terminal window quickly to see what happened in top before top would refresh. It seems that while I was focusing on the 10% CPU spike in Xorg, that I overlooked a 5-7% spike by "gnome-screensaver".

How could a random coinciding "gnome-screensaver" spike be related to VLC?  By default VLC has a "Disable screensaver" option enabled.   Probably not the best explanation, so somebody please feel free to correct any mistakes, but VLC sends a signal every so often to ping the screensaver so that it resets the clock and registers constant activity.

I unchecked "Disable screensaver" option, saved preferences, restarted VLC.  Random skipping is gone now, but the screensaver always turns on after the specified time interval.  You can workaround this by disabling the screensaver in Ubuntu.   Unfortunately, If I disable the screensaver in Ubuntu, then the monitor always stays on.  The monitor is set to turn off after 20 minutes of inactivity through separate power management settings, but won't when the screensaver itself is disabled.

Can someone experiencing this problem try to reproduce my results and verify this?  If they are reproducible, then the problem appears to be how VLC's Disable screensaver function interacts with "gnome-screensaver" in Ubuntu.

[img]http://img257.imageshack.us/img257/7551/topoutputwm8.png[/img]

---

### Post by rjmoerland on 2008-12-27
Colt45, I'll try the screensaver setting. I have VLC 0.9.4-1ubuntu3 installed on a fresh install of Xubuntu 8.10, no Compiz, free nVidia drivers, and I also experience video freezes during playback. Usually the only route to recovery is to restart VLC. Totem and (S)Mplayer play fine though.

---

### Post by jimmal on 2008-12-29
same issue for me

---

### Post by rjmoerland on 2009-01-02
> **rjmoerland said:**
> Colt45, I'll try the screensaver setting. I have VLC 0.9.4-1ubuntu3 installed on a fresh install of Xubuntu 8.10, no Compiz, free nVidia drivers, and I also experience video freezes during playback. Usually the only route to recovery is to restart VLC. Totem and (S)Mplayer play fine though.

Well, no change there. VLC's video output still freezes. SMplayer's video sometimes freezes and then catches up again. The only player that's been playing without a glitch is Totem.

---

### Post by Colt45 on 2009-01-03
> **rjmoerland said:**
> Well, no change there. VLC's video output still freezes. SMplayer's video sometimes freezes and then catches up again. The only player that's been playing without a glitch is Totem.

I lack sufficient experience to troubleshoot X.org , but it looks more and more like the cause is directly related to those Xorg cpu spikes.  Are you using ATi or Nvidia? Open source drivers or proprietary binary?

Disabling Compiz never helped me.  The unfortunate thing is that nobody seems interested in tracking down this problem.  I spoke with Jb from the videolan project, and he was disinterested. I tried Xorg devs next and they pointed the finger at Nvidia once I said I had installed Nvidia's binary.  Nvidia never responded to my inquiry.  Everyone seems to be pointing fingers somewhere else and Nvidia won't even respond.

---

### Post by soxs on 2009-01-03
For this only happens if I coppy more than 2 GB of files and watching a video on the same disk. Otherwise I am just fine withvideoplayback (except BluRay extrem fast motion sequenzes, ther I get aswell these hangs.) [Using an ati integreated 300 somwhat chipset and an AMD Pehnom 9500 CPU]

---

### Post by fermulator on 2010-03-07
Same thing happens here.

I have two PCs this happens on:

#1
 * ATI open source drivers
 * Quad Core
 * 4GB RAM
 * ATI Radeon X1950
 * Ubuntu 9.10
 * 1920x1200 (DVI, 1080p output, LG 42" TV)

#2
 * ATI proprietary drivers
 * Quad Core
 * 4GB RAM
 * ATI Radeon HD 4870
 * Ubuntu 9.04
 * 1280x1024 (DVI, LCD monitor)

I tried configuring compiz as suggested (refresh up to 60Hz, vsync, and disabling video playback in compiz), but it has no effect.

The interesting thing is that on PC #1, it happens 100% reproducible on certain frame segments in a certain movie.  If I play the same movie on #2 (the one with the more powerful and latest video card), the problem are less likely to happen, and aren't as reproducible.)

Wondering if this is because the HD 4870 has an x264 decoder, but the X1950 doesn't have a hardware decoder for this? Another factor might be resolution ...

Since VLC is single threaded, certain frames in the movie cause the device to tip over?

---

### Post by fermulator on 2010-03-07
I also just tried: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Didn't help.

Tried in:
 * vlc, smaplayer, mplayer, totem ... all have the same issues.  (vlc is the least issues though)

---

### Post by fermulator on 2010-03-08
Another point (this might warrant a change in thread title) ... it isn't just xVideo playback, it's also x11 playback.  I've tried a few others (openGL, ... etc .. i forget), and the rest are even worse.  xVideo and x11 are the two best in my testing.

---

