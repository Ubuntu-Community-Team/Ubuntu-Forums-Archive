---
title: "Media Player Crash"
date: 2009-05-12
forum: Multimedia Software
---

### Post by VodkaMartini on 2009-05-12
After I upgraded to 9.04, Mplayer asked for GStreamer plugin when it has finished installing I restarted my pc and then tried to play an avi video and mp4 video. If I don't see the Mplayer window (Mplayer window is behind firefox window, game, or whatever window is it) It plays normally, but If I focus on Mplayer window, It loads and then closes as it loads the video.

How could I fix that?

---

### Post by VodkaMartini on 2009-05-28
bump*

any help? because I can't watch any movies

---

### Post by xzero1 on 2009-05-28
Something you could try: Run gstreamer-properties in a terminal. Click video, and under "default output" select another output driver instead of autodetect.

---

