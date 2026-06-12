---
title: "Sound - Audio - List of alsa-base options/fixes"
date: 2008-09-20
forum: Multimedia Software
---

### Post by komputes on 2008-09-20
Hi everyone, I was recently searching for a list of alsa fixes. There are many instances where some audio does hardware not work (i.e. microphone, headphone jack, input jack etc.). There are many solutions that instruct to append a line in /etc/modprobe.d/alsa-base such as:

```
options snd-hda-intel model=3stack-dig
```(Reported to fix the Microphone on an eeePC)

OR

```
options snd-hda-intel position_fix=1 model=lenovo
```(Reported to fix internal speakers mute when jack is in headphones input on a Toshiba A200 / A120)

What I was wondering is if there is a central place where I can find a list of all these alsa fixes/options.

:guitar:

---

### Post by Yellow Pasque on 2008-09-20
[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

