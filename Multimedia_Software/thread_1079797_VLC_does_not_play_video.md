---
title: "VLC does not play video"
date: 2009-02-24
forum: Multimedia Software
---

### Post by SuperSonic4 on 2009-02-24
I am using VLC 0.94 from the repository but it won't play video files, it will play audio (such as audio cd or mp3) but it will not play video files, including audio embedded into the video. I have tried with flv, avi and mpeg files and none work.

I am using Kubuntu 8.10 64 bit with KDE 4.2 and Qt 4.4.3


Running vlc in a terminal with gives

```
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::setClipRegion: Painter not active
QPainter::setClipping: Painter not active, state will be reset by begin
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 128.31 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  128 (GLX)
  Minor opcode of failed request:  31 (X_GLXCreateWindow)
  Serial number of failed request:  53
  Current serial number in output stream:  54
Segmentation fault

```

I know it is not the file because SMPlayer works without a problem


**note my solution was to change the default video output to default from openGL**

---

### Post by tombom62 on 2009-02-24
try this:
[http://ubuntuforums.org/showthread.php?t=1057114](http://ubuntuforums.org/showthread.php?t=1057114)

---

### Post by binbash on 2009-02-25
change the video output at vlc preferences

---

### Post by nelskurian on 2009-02-25
Try the other players like mplayer,etc.

---

### Post by SuperSonic4 on 2009-02-25
> **tombom62 said:**
> try this:
[http://ubuntuforums.org/showthread.php?t=1057114](http://ubuntuforums.org/showthread.php?t=1057114)

I tried that but it was already installed

> **binbash said:**
> change the video output at vlc preferences

This seems to have worked, I'll try it on some different files, not to mention it doesn't flicker with desktop effects on unlike smplayer. Cheers :D

> **nelskurian said:**
> Try the other players like mplayer,etc.

I tried smplayer, mplayer, dragonplayer and kmplayer and all worked.

---

