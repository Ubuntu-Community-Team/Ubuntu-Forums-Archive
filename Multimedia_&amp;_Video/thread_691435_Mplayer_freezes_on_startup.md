---
title: "Mplayer freezes on startup"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by zhark1 on 2008-02-08
Hello,

been using mplayer to display hd content to my tv without problems for a long time now. Today suddenly mplayer freezes for about 10 seconds on startup before starting playback. I've rebooted, tried both mplayer 1.0rc1 and rc2 without it getting any better. There is nothing in the console hinting of any problems, and it also doesn't use much cpu while freezing. 

The last lines output before freezing is this:
```
...
Matroska file format detected.
VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled

```

Had some problems around the time it happened with alsa, but sound seems fine now.

---

### Post by zhark1 on 2008-02-14
EDIT: Problem fixed by itself, still don't know what caused it, but after running mplayer from command line and pressing ctrl+c when it freezes, it was fixed. I also commented the "cache" parameter in my config file, uncommented it afterwards without the problem reappearing.

---

