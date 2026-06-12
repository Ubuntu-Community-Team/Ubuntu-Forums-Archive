---
title: "Sound disappears 3 minutes into recording"
date: 2008-08-05
forum: Mythbuntu
---

### Post by agent5150 on 2008-08-05
Hi,

My mythbuntu 8.04 was working flawlessly until all of a sudden I have this mysterious sound issue. 

Live TV: 
sounds works right after the system is booted.  I can switch channels and sound works fine.

Recording playback:
Sound only works about for 3 minutes then there is no audio at all for the remaining part of the recorded show.

All recordings following the 1st recording (since last boot) have no audio.

Live TV after watching a recorded show with no sound:
no audio at all.  Now the only way I get audio back is to reboot the system.  Live TV will have audio until another recording kicks off and sound is gone.

my device in General setup is set to /dev/dsp

I don't see any errors in backend logs or even in frontend.

I am using PVR 350 to capture and Nvidia FX5200 AGP to output to TV.  Could this be a PVR 350 failing or getting too hot while recording??  

All other audio works fine (DVD, CD, MP3 Music files, AVI/MP4 movies via Xine) even when no audio in live tv and recordings.

Desperate for a solution !!!

---

### Post by agent5150 on 2008-08-07
Adding more info on this issue.
I have tried all of the following Live TV decoding methods:
Standard (ffmpeg)
XvMC generic
XvMC Nvidia
above with/without opengl sync
with/without extra and aggressive audio buffering set to yes.

Problem still exist.
Any Takers !!!

---

