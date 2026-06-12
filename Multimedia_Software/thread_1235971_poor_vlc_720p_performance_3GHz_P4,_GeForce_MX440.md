---
title: "poor vlc 720p performance: 3GHz P4, GeForce MX440"
date: 2009-08-09
forum: Multimedia Software
---

### Post by neurophyre on 2009-08-09
When trying to play back some 720p MKV files, vlc 1.0.1 drops frames.  The problem gets much worse whenever there are subtitles on the screen, or when there's a menu overlaid (for example, by right-clicking or moving the mouse).

System is running Ubuntu 9.04 on a 3GHz P4 w/512KB L2, 1GB RAM, on a GeForce MX440 with the nVidia X server installed.  Native output resolution is 1360x768 to a flat panel TV.

Is there any way I can boost performance in general, and remedy the massive frame drop problem when menus or subtitles are displayed?  The problem seems to be worse on files with a higher bitrate.  Is all the decoding taking place on the host CPU, or is there a way to do some of it on the video card -- I'm guessing not with H.264, but perhaps I'm wrong?

---

### Post by neurophyre on 2009-08-15
I'm at a loss here, been googling for some time and can't even find out for sure if this hardware is somehow inadequate to play 720p x.264.  It's a 3GHz P4, 512KB L2, 533 FSB, with a GeForce MX440 video card.  I've installed VLC 1.x.

---

### Post by neurophyre on 2009-08-24
This problem is mostly solved, though VLC still performs notably worse on this machine than on a similar machine running Windows.

1) In appearance preferences, turn visual effects to None
2) Use Movie Player instead of VLC

Also, switched from wireless to ethernet, which improved playback in very high bitrate x.264 files.

---

