---
title: "Sound Broken"
date: 2008-11-01
forum: Multimedia Software
---

### Post by lucasl on 2008-11-01
Hi,
I did a routine update of packages today, with everything as normal.
However, on reboot, my sound didn't work. all my devices still show up through aplay -l and alsamixer is all turned up.
I tried previous kernels, which didn't work. I then tried using onboard audio. The little drum to show the login is ready worked, but then the long startup drums only came from my subwoofer quietly. Now I get nothing from the sound card and a high pitched buzzing from the onboard when I play sound.
Any ideas? The sound card uses a CMedia CM8738 and the onboard is HDA Intel.

---

### Post by lucasl on 2008-11-01
Muted some things in alsamixer and the buzzing went away.
Also, piping /dev/urandom to /dev/dsp makes loud static.

---

