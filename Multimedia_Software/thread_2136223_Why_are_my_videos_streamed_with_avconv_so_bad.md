---
title: "Why are my videos streamed with avconv so bad?"
date: 2013-04-16
forum: Multimedia Software
---

### Post by daloonik on 2013-04-16
I'm using avconv to stream videos with an rtsp link. But the videos that I save are so bad, they're unwatchable! The video is distorted; it cuts out, as well as the audio. Whole seconds are missing. I'd like to know if any other people have better luck saving these files. Here's the command that I am using: <code>avconv -fflags discardcorrupt -i "rtsp://medias-rtsp.tou.tv/vodtoutv/_definst_/mp4:005/mp4/d/2013-04-08_20_00_00_dragon_0009_800.mp4" -c:v copy -c:a copy dragon_s2e1.mp4 </code>. Also, I get the occassional "non-existing SPS 1 referenced in buffering period" error. Is this a network issue? Are there more flags that I can add to avconv to save a better video?
Thanks!

---

