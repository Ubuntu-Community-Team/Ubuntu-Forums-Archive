---
title: "video playback beyond 2048 pixels"
date: 2010-04-26
forum: Multimedia Software
---

### Post by spotspot on 2010-04-26
I have a 30" LCD with 2560x1600 pixel resolution.  I would like to make and play videos at this resolution, but software decode is too slow, and the GPU accelerated decode (VDPAU) maxes out at 2048 pixels.  It might be possible to decode 2Kx2K and cut-and-paste and reorganize the rectangles to fill 2560x1600.  But someday I plan on getting a 4K screen (4096x2160 pixels) and I would like to support that too.  For that it seems two video streams decoded by two GPUs and exactly synchronized would work.  Does anyone know how to play back videos for devices like these?  Is anyone working on it?  Who can I talk to?  Thanks, -Spot

---

### Post by spotspot on 2010-04-29
bump?

---

