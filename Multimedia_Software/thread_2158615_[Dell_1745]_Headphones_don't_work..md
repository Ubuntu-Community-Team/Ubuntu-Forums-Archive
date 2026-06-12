---
title: "[Dell 1745] Headphones don't work."
date: 2013-06-29
forum: Multimedia Software
---

### Post by 0no on 2013-06-29
Hello. I'm using Ubuntu 13.04 and my headphones jack doesn't work. After pluging headphones speaker turns off (is muted), but there is no sound in my headphones!
alsabase file:
[INDENT]options snd-hda-intel model=targa-dig
[/INDENT]
[COLOR=#333333]Screens from menu Sound i Alsamixer after pluging headphones.
[/COLOR][http://img805.imageshack.us/img805/8469/dpy.png](http://img805.imageshack.us/img805/8469/dpy.png) (it's in polish)
[http://img14.imageshack.us/img14/7020/tyb.png](http://img14.imageshack.us/img14/7020/tyb.png)

---

### Post by Yellow Pasque on 2013-06-30
Instead of "targa-dig", try "dell-m6": [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1088950/](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1088950/)

---

### Post by 0no on 2013-07-04
Nevermind, everything works perfect now. Thanks.

---

