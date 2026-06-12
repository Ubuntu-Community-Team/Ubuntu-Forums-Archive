---
title: "Livestation stops other application's audio"
date: 2009-02-22
forum: Multimedia Software
---

### Post by broecher on 2009-02-22
Hello,

I have Hardy with Gnome. I installed Livestation and it works well enough, but even after closing it, no other applications can play audio until i restart my desktop.
It seems that audio problems are common with this app, but not my exact problem...

Thanks in advance!

---

### Post by mocha on 2009-02-23
> **broecher said:**
> Hello,

I have Hardy with Gnome. I installed Livestation and it works well enough, but even after closing it, no other applications can play audio until i restart my desktop.
It seems that audio problems are common with this app, but not my exact problem...

Thanks in advance!

Sounds like it's seg faulting pulseaudio.  Try running "pulseaudio -D" to see if that gets your sound back.  In the future you can run Livestation as "padsp livestation" or "pasuspender livestation".

---

### Post by Axel Larator on 2009-05-26
**padsp livestation** works up to jaunty

plain and simple - good job - thx

---

### Post by lklk on 2009-11-16
"padsp livestation" works in 9.10-64
but "pasuspender livestation" works better.

---

### Post by lklk on 2010-05-19
neither seems to work with 10.04-64

---

