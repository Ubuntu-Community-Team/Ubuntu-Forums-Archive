---
title: "Confused about esd/dmix"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by joeljkp on 2007-05-14
I'm confused about the status of software mixing in Ubuntu.

It appears that Ubuntu is an all-ALSA system, using OSS emulation for the old apps. It also appears that dmix is enabled by default (after moving /usr/bin/esd to /tmp, I can still play multiple sounds at once using my integrated sound card).

So I'm wondering: why is ESD enabled by default in GNOME? And why are system sounds disabled if you disable ESD?

Since it appears that the two are redundant, am I right to think that I can disable ESD completely with no ill effects?

---

### Post by jonny_noog on 2008-02-02
> **joeljkp said:**
> 
So I'm wondering: why is ESD enabled by default in GNOME? And why are system sounds disabled if you disable ESD?


I have been wondering exactly the same thing. :confused:

See here for some info that helped me to allow ESD to be enabled but still let ALSA also use the sound card directly:

[http://forum.soft32.com/linux2/Gnome-ESD-sound-events-ALSA-working-ftopict57897.html](http://forum.soft32.com/linux2/Gnome-ESD-sound-events-ALSA-working-ftopict57897.html)

---

