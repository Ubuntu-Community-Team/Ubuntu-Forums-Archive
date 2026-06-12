---
title: "libmp3lame is installed, but kdenlive can't encode mp3"
date: 2013-06-29
forum: Multimedia Software
---

### Post by UsernameNumber on 2013-06-29
I am running kdenlive 0.8.2.1 on Precise, and when I try to render a video as mpeg4, it says "unsupported audio codec: libmp3lame". I found another thread on this forum that recommended installing lame and re-running the kdenlive configuration wizard, but it turns out I already have it installed. 

```
$ sudo apt-get install -y lame libmp3lame0 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lame is already the newest version.
libmp3lame0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 320 not upgraded

```

I've tried re-running the wizard anyway but it's made no difference. Any other ideas? I have the same problem with the xvid and h264 codecs. :(

---

### Post by Yellow Pasque on 2013-06-29
You need the "-extra" libav packages: Installing libavcodec-extra-53 should take care of it IIRC.

---

### Post by Untold on 2013-09-17
I went into home/.kde/share/config and opened kdenliverc in text editor.  I searched for the lame code libmp3lame and put a 0 after it to make it libmp3lame0.  Saved and restarted my kdenlive and it works perfect.

---

