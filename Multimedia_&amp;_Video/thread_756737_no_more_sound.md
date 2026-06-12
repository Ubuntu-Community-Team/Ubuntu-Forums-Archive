---
title: "no more sound"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by charlo_be on 2008-04-16
A few days ago I installed the package ubuntustudio-audio and I just lost all my sound. No more start-up sounds, but when I test it under System > Preferences > Sound I get the beep-tone.

Vlc gives sound after manually changing the alsa-settings, switching the soundcard from "hw:2,0" to ""NVidia Nforece etc.". However, restarting vlc will put "hw:2,0" back in there.

Anybody else got something similar, or knows a solution?

thx in advance

---

### Post by charlo_be on 2008-04-17
Seriously, nobody's got a clue?

---

### Post by xc3RnbFO8P on 2008-04-17
Try:
> sudo apt-get install linux-backports-modules-generic

---

### Post by charlo_be on 2008-04-18
I tried that, but it didn't solve anything. Still same situation as before.

---

