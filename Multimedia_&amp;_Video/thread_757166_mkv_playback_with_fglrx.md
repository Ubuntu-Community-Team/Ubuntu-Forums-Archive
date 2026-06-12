---
title: "mkv playback with fglrx"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by SuperAndy on 2008-04-16
I have been doing some experimentation, and it seems that on my graphics card - an ati X800, using fglrx drivers, mkv playback is pretty much impossible, at least if you want to have a smooth video. it will render one frame every 2 or 3 seconds.

I have found a lot of threads complaining, and I have tried to do a lot of googling about the cause. Just to clarify, this is the fglrx drivers both with and without a compositing window manager. Whatever I use, i get jerky or no video playback, on all output modules in mplayer, vlc, totem-gstreamer and totem-xine. In mplayer the video plays at a strange aspect ratio, and will not extend to full screen. In the others, the video plays very slowly, or not at all.

If i change xorg to load the radeon driver, and reboot, I can load mkv's in mplayer without a problem, even 720p ones. Therefore, this must be an issue with the binary fglrx driver. Is it something i am mising in xorg.conf, or is it just a fundamental limitation with fglrx?

I have had top running while attempting to play mkvs in fglrx, and neither the CPU or RAM is max-ing out.

---

