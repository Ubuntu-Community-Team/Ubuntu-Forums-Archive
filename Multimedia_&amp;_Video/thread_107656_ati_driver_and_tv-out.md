---
title: "ati driver and tv-out"
date: 2005-12-23
forum: Multimedia &amp; Video
---

### Post by splater on 2005-12-23
Hi everybody,

I convert myself to Ubuntu !!!! The instalation was without any trouble as the instalation of the last ati driver.

The only thing is that I can't get video working on the tv-out .... I can see my desktop  on my laptop and on my TV but when I launch a video, it only appears on my laptop.

Config:
ATI mobility 9700
1280x800
VLC player

Anyone has an idea ?

thx

---

### Post by buellman on 2005-12-23
Hi!

Put
```
Option          "OverlayOnCRTC2"
```
in the Section "Device" of your xorg.conf.

Greets. Buellman

---

### Post by splater on 2005-12-23
Thank you for your answer.

with this option I have only video on tv now ... Do you know if it's normal and or if there is a way to have video on both ?

thx

---

### Post by buellman on 2005-12-23
Hmmm...  I have the same problem :-/

Greets. Buellman

---

