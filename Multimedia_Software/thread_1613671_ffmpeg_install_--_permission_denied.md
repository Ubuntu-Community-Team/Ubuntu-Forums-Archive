---
title: "ffmpeg install -- permission denied"
date: 2010-11-04
forum: Multimedia Software
---

### Post by Axcelon on 2010-11-04
I am trying to install ffmpeg codecs on a machine that does not have an internet connection.

I have compiled everything, but when I run:

make install

as the install file indicates I get the following response:

INSTALL libavdevice/libavdevice.a
install: cannot create regular file `/usr/local/lib/libavdevice.a': Permission denied
make: *** [install-libavdevice-static] Error 1

What do I need to do to install the codecs so I can use the Movie Player to watch various mpeg, avi, and other files?

---

### Post by andrew.46 on 2010-11-04
Hi Axcelon,

You will need to use:

```
*sudo* make install
```

Or better still use checkinstall, but I am not so sure that installing FFmpeg to your system will help with media playback.

Andrew

---

### Post by Axcelon on 2010-11-05
Okay, so how do I install Apple Lossless and mpeg, avi, DivX, etc drivers on a computer without an internet connection.

I can download whatever I need to with another computer.

---

### Post by andrew.46 on 2010-11-06
Hi Axcelon,

No Internet connection makes things more than a little difficult, particularly under Ubuntu where the dependency scheme is always needing to download more packages. So I am not sure how to advise you on this one...

Apologies,

Andrew

---

