---
title: "Aspect ratio problem"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by imrazor on 2006-06-26
I'm having a weird problem with several media players. With any 4:3 resolution, kaffeine and gxine play back video at a 1:1 aspect ratio. This means that all video played has a stretched out look to it and has black borders at the left and right edges when played full screen. VLC plays video back normally, but I like Kaffeine's interface and would prefer to use it instead. Does anyone know how xine detects the aspect ratio, and how to tinker with it?

---

### Post by MetalMusicAddict on 2006-06-26
Try playing with the decoder or driver it uses. vx I think is one. Sorry Ive been using Totem lately. I think theres also aspect settings.

---

### Post by imrazor on 2006-06-30
I found the source of the problem, though it puzzles me. The problem appears to be the proprietary Nvidia driver/module. When I remove "nvidia" from xorg.conf and replace it with "nv" all my aspect ratio problems magically vanish. What's interesting about this is that I had a similar problem with the proprietary ATI drivers on my old laptop.

The problem with this solution is that I lose 3d/OpenGL. I'm getting used to VLC, though I'd prefer kaffeine. Has anyone else seen this problem with the proprietary video drivers, or better yet, found a solution to this problem?

Totem also exhibits this problem, and the only media players I've found that don't are VLC and KMplayer. KMplayer's playlist management is a joke, so that leaves VLC, which is tolerable.

---

### Post by shakespeare on 2006-07-08
The same problem occurs with ATI drivers for Radeon etc. Even though the mpeg header explicitly says 4:3 aspect (checked with dvdpatcher), mplayer and xine use the aspect ratio of the display, which is 16:9 in my case (1920x1200). Only vlc plays mpeg files properly.

This causes all sorts of grief when trying to author a video dvd from dv files, as the usual tools (qdvdauthor, kmediafactory, dvdstyler) all seem to rely on mplayer's mencoder, which uses the *wrong* aspect ratio.

---

