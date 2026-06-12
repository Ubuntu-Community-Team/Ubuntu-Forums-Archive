---
title: "[SOLVED] Sound distortion in 8.10"
date: 2008-11-19
forum: Multimedia Software
---

### Post by andreselsuave on 2008-11-19
Hi there, 
I'm desperately trying to fix the distorsion on my sound in ubuntu 8.10, and I have given up :P 
I've read a lot of posts, I've tried to install pulseaudio, I've tried to reinstall alsa... nothing works.... I get distorted audio no matter what I try. Any help please?
If you need extra information ask for it and tell me how I get it (for example lspci or sth like that).
BTW: I had no problem at all with 8.04

---

### Post by andreselsuave on 2008-11-19
Solved it :P 
So stupid solution that im embarrased hehe ... ^_^

```
alsamixer -Dhw
```

I had too high the PCM volume...

---

