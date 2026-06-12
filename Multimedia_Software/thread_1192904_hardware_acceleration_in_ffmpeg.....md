---
title: "hardware acceleration in ffmpeg...."
date: 2009-06-20
forum: Multimedia Software
---

### Post by mc4man on 2009-06-20
... any advantage?

I noticed while reviewing my building of ffmpeg as a debian package set (/user, shared. unstripped, w/ matching -dev's) that by installing libav-29 and it's -dev that some form of hardware accel is enabled in ffmpeg.

i'm thinking this may be useful for vlc, but wonder does it offer any use in ffmpeg itself and what the state of hwaccel is in ffmpeg atm.

(noting that I don't have the hardware to test atm., though maybe on
 laptop, will have to check
From ffmpeg configure in build log
```
Enabled hwaccels:
h263_vaapi		mpeg4_vaapi		wmv3_vaapi
mpeg2_vaapi		vc1_vaapi

```

source/info for libav
[http://www.splitted-desktop.com/~gbeauchesne/libva/](http://www.splitted-desktop.com/~gbeauchesne/libva/)


[http://freedesktop.org/wiki/Software/vaapi](http://freedesktop.org/wiki/Software/vaapi)

---

