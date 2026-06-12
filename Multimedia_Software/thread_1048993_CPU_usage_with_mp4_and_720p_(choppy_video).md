---
title: "CPU usage with mp4 and 720p (choppy video)"
date: 2009-01-24
forum: Multimedia Software
---

### Post by patsissons on 2009-01-24
I have been having some issues lately with high def mp4 containers on my system.  here are the pertinent stats:

intrepid, amd opeteron 170 (dual core 2GHz), 2GB ddr400, nvidia GeForce 8600, nvidia driver 180.17, 2.6.27-9-generic, x64, kubuntu-desktop

I think that is all that is important, but if there is anything else it's easy for me to find out.

So the problem is that when i try to play any sort of HD content (1080p or 720p) that is in an mp4 container my system nearly dies, and as a result the video often stutters and becomes choppy (or sometimes just goes into slow motion, depends on the player).  This is the case for all video players that i have tried (kaffeine, mplayer, vlc).  I am using the Xvideo driver (-vo xv in mplayer, similar in kaffeine and vlc).  At first I thought that it was a hardware problem, but I recently tested out a mov container and an mkv container.  These two containers play fine, by which i mean there is moderate CPU usage, but nothing like 100% usage that i get with mp4 containers.

I am curious if anyone has experienced these kind of issues.  They are rather annoying and I want more than anything else to get to the bottom of it.  I will likely test out these mp4 files under windows in a few days to see if it is the kernel itself.  When playing the mp4 files I notice that the CPU is spending an abnormally large amount of time in the kernel, especially as compared to mkv and mov.  I really don't know why mp4 files warrant such kernel use, but i would be enlightened to know why.

---

### Post by jfluet on 2010-06-05
I get the same thing but .mkv and .mp4 are choppy and slow motion a bit. my cpu is an old office computer so its slow 40gb hard drive 256X2 of ram pentium 4, and I have no idea what else is in there.
if any one has a free computer tower, I'm poor and would much appreciate it.

---

### Post by xzero1 on 2010-06-05
Try mplayer with the -nosound option. I've had a lot of playback issues related to sound. If that works try the oss audio driver.

---

### Post by xzero1 on 2010-06-06
> **xzero1 said:**
> Try mplayer with the -nosound option. I've had a lot of playback issues related to sound. If that works try the oss audio driver.

:confused:Correction:
oss?? I meant to say sdl
For mplayer use: mplayer -ao sdl ...

In any case I have had better luck with sdl than alsa on some files.

---

