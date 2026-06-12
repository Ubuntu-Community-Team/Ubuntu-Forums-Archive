---
title: "sound works at console, not in X"
date: 2009-11-04
forum: Multimedia Software
---

### Post by ynnhoj on 2009-11-04
so, i'm trying to get a fairly lightweight setup on my netbook. i installed with mini.iso, and have been installing applications as necessary. i've installed alsa, and use alsamixer to adjust levels and cmus to play music. i can play my ogg files just fine using cmus from the console, but after i start X my sound ceases to work. once i start X if i try to run **alsamixer** in xterm, i get:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```
and if i try to play a song in **cmus**, i get this error:
```
Error: opening audio device: No such file or directory
```
why would it work fine and then not work once i start X, i wonder..? i'm sure i've just missed some little config along the way, but i can't figure out what :o

---

