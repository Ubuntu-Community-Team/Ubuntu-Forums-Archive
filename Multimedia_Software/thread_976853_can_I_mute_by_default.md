---
title: "can I mute by default?"
date: 2008-11-09
forum: Multimedia Software
---

### Post by garytr23 on 2008-11-09
Anyone know a quick way to have sound muted by default on startup?  I'm a student... and sometimes I forget to mute it after my previous session.. so I bring up my laptop during class (usually late) along with embarassing noises :-).

I have a shiny new lenovo SL300 running 8.10. I'm pretty familiar with pulseaudio and alsa configuration, just wondering if there's an official, clean, 'ubuntu preferred' way of doing it that won't cause more problems later. 

Also, I've been an ubuntu user since 6.06... I haven't posted much tho.

---

### Post by lovinglinux on 2008-11-09
Add the following command to System >>> Preferences >>> Session:

```
amixer -q set "Master" 0% mute
```

---

