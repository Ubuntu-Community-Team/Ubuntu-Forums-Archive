---
title: "ffmpeg encoding mpegts"
date: 2011-11-08
forum: Multimedia Software
---

### Post by adismsc on 2011-11-08
Hi,
is there anybody who can help me with video encoding? I want to encode video to MPEG-TS with null packet (PID 0x1fff). Anybody know how to do this? Is it possible?

My current command:

ffmpeg -i audio.mp2 -i video.mpg -s 720x576 -minrate 3200k -maxrate 3200k -bufsize 3200k -vcodec libx264 -vpre libx264-iptv -acodec copy -r 25 -f mpegts out.mpg

---

