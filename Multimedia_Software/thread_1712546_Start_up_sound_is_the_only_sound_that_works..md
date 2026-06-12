---
title: "Start up sound is the only sound that works."
date: 2011-03-22
forum: Multimedia Software
---

### Post by t0rment2004 on 2011-03-22
Literally. Just the login and startup noises. Nothing else.

I assume my sound card isn't the issue because it plays the noises.

Lenovo r61i

---

### Post by lidex on 2011-03-22
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by t0rment2004 on 2011-03-22
[http://www.alsa-project.org/db/?f=8af91d970a3f387c9c4a0afd2140dc5d8ceac3a3](http://www.alsa-project.org/db/?f=8af91d970a3f387c9c4a0afd2140dc5d8ceac3a3)

---

### Post by Yellow Pasque on 2011-03-23
It's likely a pulseaudio issue if you can play login/logout sounds (they use ALSA directly).
Try purging pulse configuration and restarting pulse:
```
cd ~
rm -rf .pulse*
pulseaudio --kill
```

---

### Post by lidex on 2011-03-23
> **Temüjin said:**
> It's likely a pulseaudio issue if you can play login/logout sounds (they use ALSA directly).
Try purging pulse configuration and restarting pulse:
```
cd ~
rm -rf .pulse*
pulseaudio --kill
```
A good point and one I didn't think of.
@t0rment2004
Did that work for you? A couple of commands to see what pulse is doing:

```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

