---
title: "[SOLVED] Rhythmbox Decodebin Error"
date: 2008-10-08
forum: Multimedia Software
---

### Post by scott_g on 2008-10-08
Hi,

I recently had some troubles with my computer (long story; turns out I had some bad RAM), and ended up re-installed Ubuntu.  However, after the re-install (keeping my old home-partition with all its settings), I can't play music with Rhythmbox.  When I try to import music, it gives the following error:

```

file:///####/####/###.mp3 | Failed to create decodebin element; check your installation.

```

Has anyone seen this before or know what would cause it?  I believe I have the correct plug-ins installed.

Thanks in advance,
Scott

---

### Post by minky311 on 2008-10-08
Do you have this package installed **gstreamer0.10-plugins-base**?
If not install it and see if that solves it.

---

### Post by scott_g on 2008-10-08
Yep;  I have the following gstreamer packages installed:

```

gstreamer0.10-alsa
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-mpegdemux
gstreamer0.10-mpegmux
gstreamer0.10-gnomevfs
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-pulseaudio
gstreamer0.10-tools
gstreamer0.10-x
gstreamer-tools

```

Any other ideas?

Scott

---

### Post by minky311 on 2008-10-08
Have you tried reinstalling rhythmbox?

---

### Post by scott_g on 2008-10-09
Yep; did a complete re-install with no luck.  Same error showed up in totem when I was trying to play a video, but I fixed it by switching Totem's backend to xine.

Any other ideas?

Thanks,
Scott

---

### Post by xc3RnbFO8P on 2008-10-09
Could be a bug:
[https://bugs.launchpad.net/ubuntu/+source/soundconverter/+bug/154617]("https://bugs.launchpad.net/ubuntu/+source/soundconverter/+bug/154617")
Try to reinstall
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps

---

### Post by scott_g on 2008-10-09
That did the trick; re-installing those two fixed the problem.  Thank you very much for your help; this has saved me a lot of time.

Thanks again,
Scott

---

