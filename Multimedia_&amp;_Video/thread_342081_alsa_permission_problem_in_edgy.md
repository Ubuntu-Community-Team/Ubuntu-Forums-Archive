---
title: "alsa permission problem in edgy"
date: 2007-01-19
forum: Multimedia &amp; Video
---

### Post by paca on 2007-01-19
Alsa only works for root
for example:
```
aplay tada.wav
```
works perfect for root but not for other users...

users get this error msg:
aplay: main:547: audio open error: Permission denied

i'v added the user to the audio and root grp but same problem

help !

---

### Post by paca on 2007-01-19
works... just had to log out/in in X

---

