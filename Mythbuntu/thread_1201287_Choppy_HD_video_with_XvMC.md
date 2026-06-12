---
title: "Choppy HD video with XvMC"
date: 2009-06-30
forum: Mythbuntu
---

### Post by thegooch49 on 2009-06-30
Hi, I'm using dual Xeon 3.0GHz procs, and GF6800 with XvMC. I'm having choppy playback in HD. Audio and video seem a bit off. When I start the frontend with verbose, I have lines and lines of:

NVP: Video is 3.2002 frames behind audio (too slow), skipping A/V wait.

Any idea what this could be? Any tweaks that anyone could think of? I looked at some diffn't playback profiles. I tried CPU+ and CPU-- and they both do the same thing unfortunately. 

Thanks for any help or suggestions.

---

### Post by ian dobson on 2009-07-01
Hi,

Maybe try the "slim" playback profile. I found that worked best for me before I went over to the VDPAU backports.

Regards
Ian Dobson

---

### Post by thegooch49 on 2009-07-01
> **ian dobson said:**
> Hi,

Maybe try the "slim" playback profile. I found that worked best for me before I went over to the VDPAU backports.


Wow, that did the trick! Slim is the key. Much smoother playback, things are looking good now. Thanks for the tip Ian.

---

