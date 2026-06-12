---
title: "No sound on iPhone after converting flv to mp4 with ffmpeg"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by HilliBilly on 2008-04-01
hi,

i have a strange problem. after converting a youtube video (.flv) to mp4 i can see (and listen!) this video in totem movie player (with sound!) but copying this video with gtkpod to an iphone i loose the sound. other video files on the iphone (from other sources but also copied with gtkpod) have sound.

this is how i converted the video:

$ ffmpeg -i waiting_on_the_world_to_change.flv -acodec copy -vcodec mpeg4 waiting_on_the_world_to_change.mp4

what am i doing wrong?

---

