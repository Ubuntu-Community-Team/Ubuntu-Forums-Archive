---
title: "hear sound see no video in firefox"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by dr.silly on 2007-05-10
I hear the sound but I don't see any video when totem 'plays' any video on web. I reinstalled all codecs etc. still doesn't work

---

### Post by dr.silly on 2007-05-10
now I'm not hearing sound either just a black screen where the video should be playing

---

### Post by dr.silly on 2007-05-10
sometimes I hear sound sometimes not

totem is really messed up

---

### Post by LollYouSuckZor on 2007-05-10
Vid codes?

---

### Post by dr.silly on 2007-05-10
I have them (and reinstalled)

---

### Post by dr.silly on 2007-05-10
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/111605](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/111605) this is exactly my prob except sometimes it plays sound

---

### Post by dholwerda on 2007-05-11
from the terminal or alt+f2 type gstreamer-properties
select the video tab
change default output plugin to X Window System (No xv)

---

### Post by dr.silly on 2007-05-12
that did it! Thank You!

---

