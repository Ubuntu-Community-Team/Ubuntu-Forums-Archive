---
title: "720p lags on laptop (Dell E1505/ATI X1400)"
date: 2008-06-12
forum: Multimedia Software
---

### Post by executive on 2008-06-12
720p video image quality looks okay for the most part (but not as good as ffdshow/MPC in XP), but the video would lag every 10 seconds or so. Sound keeps playing but video would freeze and start back on its own. 

I'm using VLC, and mplayer with same result. Very annoying, can someone please help! thanks in advance.

---

### Post by shirilover on 2008-06-13
Try using the following switches for MPlayer:
-lavdopts fast:skiploopfilter=all

---

### Post by executive on 2008-06-14
just realized the lagging problem occurs with ALL video format (not just 720p) in full screen. in window mode (@100%) the video plays fine. But once in full screen, it becomes pixelated and very laggy. it almost feels like there's no hardware acceleration..

---

