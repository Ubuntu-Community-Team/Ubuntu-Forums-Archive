---
title: "HD video playback issues"
date: 2010-10-17
forum: Multimedia Software
---

### Post by joeyjoejo on 2010-10-17
Hi all,

When I play large HD videos in mplayer, the video and sound frequently get out of sync, and the video plays a little strangely (occasionally speeding up and occasionally slowing down). 

I think it's because mplayer is only running on a single core. As I've got a quad-core processor, it seems inefficient. I've seen that there is theoretically a way to get mplayer to work with multicore setups, but it requires compiling with different options. That'd take me a little while to work through. 

Ideally there would be a pre-compiled version in the software centre, or a player which has support built in (again, ideally in the software centre). Is there such a thing available?

thanks,
-Joe

---

### Post by bluekarasu on 2010-10-18
I have a Celeron mono core @ 2Ghz, and I can play 1080p h264 video without problem.
The magic? GPU decoding with vdpau. (you need a nvidia card, a cheap one is fine, I have a 8500GT)

Just set the VDPAU as output for video and enjoy.

GPU decoding must be usable with intel and AMD card too, but I'm not sure how to get it work.

---

### Post by atca on 2012-04-22
[A guide for HD with acceleration under Nvidia with Ubuntu 11.10 any help?]("http://confoundedtech.blogspot.co.uk/2011/12/ubuntu-playing-1080i-hd-content-with.html")

---

### Post by SeijiSensei on 2012-04-22
> **joeyjoejo said:**
> I've seen that there is theoretically a way to get mplayer to work with multicore setups, but it requires compiling with different options.

This is a pretty old thread, so it might be closed.  The answer to this question is to include "threads=N" to the lavdopts option list in mplayer.  If you use "threads=0" mplayer will use as many threads as it finds cores.

---

