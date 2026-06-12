---
title: "VDPAU performance issues on SMplayer &amp; Compiz"
date: 2011-04-29
forum: Multimedia Software
---

### Post by Eromatic on 2011-04-29
Using either MPlayer or mplayer2 under the video player SMplayer, when clicking on any drop-down menus, the video will freeze and then skip. Once the drop-down menu animation has completed, the video playback will play normally. This happens when using VDPAU to play back H.264 MKV files. Audio playback of the video is never interrupted. 

Any ideas as to why VDPAU will not play nice with SMplayer & Compiz?



System Info:

AMD BE-2400
1GB System Memory
Natty Narwhal 11.04 
Ubuntu Classic with Effects
Nvidia 9500GT
Video Driver 270.41.06-0ubuntu1

---

### Post by Eromatic on 2011-05-03
I found a bug report on Launchpad that appears to be related to the issue that I am seeing.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/761402](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/761402)

---

