---
title: "No Sound After Install"
date: 2008-07-24
forum: Multimedia Software
---

### Post by ToshiBoy on 2008-07-24
This has me stumped: I tried the Live CD on my new laptop (Asus F3Sg), and everything, including the sound, worked perfectly well. Then I installed the whole system, and now there is no sound, but also no error message as far as I can see. It's almost as if the sound is muted, but I checked and it's set to 100%. I guess, since it works from the LiveCD the soundcard is working and there must be a way to configure it. How do I go about finding out what the Live CD does in terms of sound, and what the installation does differently?

---

### Post by ToshiBoy on 2008-07-24
All fixed. Found an answer in [_another threat that was posted here_]("http://ubuntuforums.org/showthread.php?t=753679").

It's a different model but the advice worked. Scroll down towards the bottom of the threat. Add the following two lines

```
options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel
```

to 

/etc/modprobe.d/alsa-base

then reboot or restart alsa...

done.

---

