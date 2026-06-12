---
title: "White noise using external microphone"
date: 2011-02-17
forum: Multimedia Software
---

### Post by agestrada on 2011-02-17
My microphone **was working properly** until four days ago. I'm not sure if this appeared after a system update,  I'm using LL 10.04. This is my onboard HDA Intel chip,from 'lspci':

00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)

I can record sounds  from the microphone, but  white noise is accompanied. The weird  thing is that when I unplug the microphone, I can still hear the white noise. I've tried modifying the settings in  **gnome-volume-control** and in **alsamixer** without luck. The white noise is persistent.  I've read this can be related to **pulse audio** but no one seems to know how to **reset** it to its default configuration. 

Thanks,

---

### Post by marin123 on 2011-02-17
if you think its because of pulseaudio, you can restart it.
```
pulseaudio -k
pulseaudio -D
```

but i had problems with 10.04 and sound and i had to to alsa upgrade everytime i got new kernel. now i'm using 10.10 and sound works excellent :)

---

### Post by agestrada on 2011-02-17
[FONT=monospace]Killing pulseaudio didn't solve the problem, and -D options gives:

[/FONT]```
~$ pulseaudio -D
E: main.c: Daemon startup failed.
```[FONT=monospace]

I was thinking on some way to reset it to its defaults settings but couldn't find anything similar.

Thanks,
[/FONT]

---

### Post by marin123 on 2011-02-17
i think daemon startup is failed because it has already autostarted.

---

### Post by agestrada on 2011-02-18
It seems that I found a solution. Just forget about Pulse and set Alsa as the default input/output plugin using


```
gstreamer-properties
```I'm not completely sure that's what fixed the problem but it's the last thing I tried before solving this annoying issue.

edit: I was wrong, the problem is still there.

---

