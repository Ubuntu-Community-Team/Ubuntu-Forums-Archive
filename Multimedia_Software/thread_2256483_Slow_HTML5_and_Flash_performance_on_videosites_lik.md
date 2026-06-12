---
title: "Slow HTML5 and Flash performance on videosites like Youtube on Chromium or Chrome"
date: 2014-12-12
forum: Multimedia Software
---

### Post by username9 on 2014-12-12
Good evening.

So recently I installed Ubuntu 14.04 on a Laptop and everything is fine (at least after dealing with the numerous initial problems with drivers and so on), except for the fact that the performance of HTML5 and Flash on Chromium and Chrome are absolutely horrid.

For example, if I watch a 720p or even a 1080p video on the Laptop in Firefox using Flash, the CPU usage is at 30-60% at most. With HTML5 (or flash) even at 720p, the CPU will go up until 100% and the frame-rate will begin to suffer.

Is this an HTML5 limitation or can this be fixed? 

Best regards.

---

### Post by tgalati4 on 2014-12-12
Welcome to the forums.

What is your graphics card?

Open a terminal and post:

```
lspci | grep VGA
```

and

```
grep WW /var/log/Xorg.0.log
```

---

