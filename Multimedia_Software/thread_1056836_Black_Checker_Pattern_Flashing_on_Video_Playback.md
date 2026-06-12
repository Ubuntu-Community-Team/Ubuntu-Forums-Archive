---
title: "Black Checker Pattern Flashing on Video Playback"
date: 2009-02-01
forum: Multimedia Software
---

### Post by NimbleRabit on 2009-02-01
Whenever I try to play videos in any of my players (Mplayer, VLC, Totem) I get this black flash throughout playback.  It isn't completely black but a checkerboard type pattern, and it happens relatively often (once every 15 seconds or so, and sometimes quicker).

I'm using Ubuntu 1.10 Intrepid, an NVidia 9600, and the driver version is: NVRM version: NVIDIA UNIX x86_64 Kernel Module  177.82

Any help is appreciated, thanks.

---

### Post by Ollboll on 2009-02-02
I have the exact same problem, except that there is a longer delay in between the flashes, most times around 10-15 minutes but is fairly random. I get the same problem in all the listed programs.

Also Ubuntu Intrepd 8.10 64-bit, 8800GTS 512, Nvidia driver version 177.82.

---

### Post by Rogue Jedi X on 2009-02-04
I'm having the same problem. Players tried are mplayer and Dragon Player. The flicker is constant, twice every second or so.

System is Kubuntu 8.10 64-bit, nVidia 9500 GT, driver 177.82

EDIT: Fixed it! I removed and reinstalled the 177 driver. Hope it works for you, too.

---

### Post by shear on 2009-03-12
Hi everyone.

I'm having the same problem. Running 8.10 x86_64, with a GeForce 9500 GS.

Tried reinstalling nvidia-glx-177, did not work.

The issue only occurs when the video is played back non-fullscreen. Under fullscreen it goes away.

Also, the problem seems to be related to Compiz. When I switch back to Metacity, the problem appears to go away.

EDIT 1: 9500, not 8500.
EDIT 2: Add compiz stuff.

---

