---
title: "fglrx freezing during video"
date: 2010-01-05
forum: Multimedia Software
---

### Post by osarusan on 2010-01-05
I'm running 9.10 x64 version on an Athlon II x4 with 4 gigs of ram and an ATI Radeon HD 4770 card, using the fglrx driver. I'm also using Compiz.

However, I'm having a pretty major problem with video playback. Some time after starting playback, the entire system appears to freeze up. At least the video does, anyway. The audio continues to play, but the mouse is locked in place and the video frame doesn't move. I tried alt-prscr-k, but couldn't kill X. I tried ctrl-alt-f1 and f2 but again, no change. Ctrl-alt-delete had no response either. In the end, I've been having to use alt-prscr-REISUB to restart the machine.

This problem happens at unpredictable times. The other night, I watched about 1 and a half hours of DVD before it happened, and then after restarting I couldn't watch 10 seconds before freezing again. Just now, again, I started watching a video file, and the system locks up a few seconds in to the video, every time (and a different place every time).

I tried both the ati and radeonhd drivers as well, but I couldn't get the results I wanted with my 2-monitor display. I've only been able to get my monitors the way I want them using fglrx. But without being able to watch video, it's pointless anyway.

I'm lost for what to do... I've spend the last 24 hours installing and uninstalling and reinstalling the different ATI drivers over and over, only to come back to this problem. Is there something I'm missing completely?

---

### Post by csaratchand on 2010-01-05
1. To begin with, try turning off all desktop effects (Compiz). This should free up resources for rendering of video by the GPU.
2. How did you install fglrx? Did you have a look at: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) , especially the section on *Install the fglrx Driver from ATI Catalyst 9.12 For Ubuntu 9.10 Karmic*?

---

### Post by osarusan on 2010-01-05
I disabled Compiz and am currently watching video... it *seems* stable, but then again, yesterday I was watching for over an hour before it locked up. I'll definitely post again if it freezes up again.

I installed fglrx using jockey, I believe? I used the Hardware Drivers menu from System>Administration. However, I while I was trying the open source drivers, at one point I did follow those instructions to install Catalyst 9.12... However I couldn't boot into anything but a black screen. I'll try it again in a bit and see if it works now that Compiz is disabled.

(Is there no way for Compiz to work with fglrx? I thought I read somewhere that it does work...)

---

### Post by osarusan on 2010-01-05
Well, I tried the new driver... it installed fine, but again it just boots into a black screen. I can see the white Ubuntu loading logo, then both my monitors report no signal. If I hit ctrl-alt-f1, the signal comes back and I can use the virtual console.

I'm in safe graphics mode now, trying to figure out what to do to make get this driver to work, but I'm at a total loss. Any ideas?

---

### Post by osarusan on 2010-01-05
Ahhhhhhhh okay.

I thought I had disabled compiz, but apparently not. I removed it completely and it finally booted up.

I'm getting a lot of graphical anomalies and fragmenting... I'll see if I can fix them with Catalyst.

---

### Post by csaratchand on 2010-01-05
1. I think the GPU (ATI 4770 in your case) can't **simultaneously** do both the tasks of sustaining compiz desktop effects and rendering video. This may be partly on account of software and hardware limitations. Since you have two monitors this problem of overworking the GPU seems to be exacerbated. If your problem is primarily on account of software limitations (at present) then you may expect performance improvements over time as fresh drivers are released. 
2. The best way to install fglrx from ATI Catalyst 9.12 is to create the deb files as described in [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI). Then install the deb files. Do follow the instructions. It should work, especially since your GPU is supported by ATI Catalyst 9.12. If there is a problem then do report back.

---

### Post by osarusan on 2010-01-05
Thanks for your help. Building the debs as written worked out -- I just had to completely uninstall compiz first. I can live without compiz as long as everything else works.

---

