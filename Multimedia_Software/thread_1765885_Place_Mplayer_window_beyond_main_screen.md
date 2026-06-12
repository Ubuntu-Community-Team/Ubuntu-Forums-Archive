---
title: "Place Mplayer window beyond main screen"
date: 2011-05-23
forum: Multimedia Software
---

### Post by GeoMX on 2011-05-23
I have a dual monitor setup, both have 1280x720 resolution, and I would like to make Mplayer play videos directly on the second monitor, so I'm trying this:

> mplayer -geometry 1280x720+1280+0 video.mp4

But it's not working, as soon as it detects the video would be placed beyond first screen, Mplayer starts on this first screen at 0,0.

However, if I try using:

> mplayer -geometry 1280:0 video.mp4

It works! Unfortunately, I also want to resize the video so that it fits in the second screen.

Does anybody know if it's possible to tell Mplayer to resize the video and also place its window beyond the first screen?

Thanks in advance for your help.

---

