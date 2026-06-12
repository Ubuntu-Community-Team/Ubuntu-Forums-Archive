---
title: "Video playback not smooth: Chromium, MPV, anything"
date: 2019-08-05
forum: Multimedia Software
---

### Post by interschollasticwhittle on 2019-08-05
Hi everyone,

I'm having a problem with playing back videos. It doesn't seem to matter if it's in Chrome or MPV. It freezes for about half a second about once every twenty or thirty seconds. It doesn't seem to matter if the video is h264, mp4 or whatever. I've checked ```
glxinfo | grep "direct rendering"
``` and it returns, ```
direct rendering: Yes
```. Chromium reports it is using MojoDecoder and MPV ```
hwdec: vaapi
```. Top also reports that MPV is using about 10% processor when playing, I'm using Intel Integrated graphics on X11.

Any help would be much appreciated.

System:
Surface Book with Performance Base i7
RAM 8GB
Ubuntu 19.04

---

### Post by wildmanne39 on 2019-08-05
*Thread moved to **Multimedia Software a more appropriate sub-forum**.*

---

### Post by SeijiSensei on 2019-08-05
Is the file on the local machine or being played over the network?

If it's on the network, are you connecting using NFS (preferred) or CIFS/Windows networking?  If you are using a network, copy the file to your local machine and play it from there.  Any better?

---

### Post by interschollasticwhittle on 2019-08-05
Thanks very much for the advice. The files are playing from the local ssd. It does look like they're playing over a network, though.

---

### Post by SeijiSensei on 2019-08-07
I don't really understand that.  If they're on the local drive, they're not going over a network.

You're basically using something like
```
mpv /path/to/my/file.mkv
```

right? I've never had glitches doing that.

You could try installing smplayer as a front-end to mpv.  In Options > Preferences > Video you can choose among the various video drivers available. Even with just the xv driver, I had no problem playing a 1080p video with Hi-10 encoding and AC3 audio.

This is on a fairly old HP laptop with generic Intel hardware.

---

