---
title: "How do I change ALSA driver?"
date: 2006-03-13
forum: Multimedia &amp; Video
---

### Post by Torrance on 2006-03-13
ALSA has incorrectly loaded up a driver for my soundcard, and now anything that tries to play sound brings my system to a halt. How do I change the soundcard settings? **I want the system to ignore the soundcard, so how do I configure ALSA so that it loads up NO soundcard driver, and NEVER attempts to play sound??**

---

### Post by mlind on 2006-03-13
alsa modules are loaded by */etc/modprobe.d/alsa-base*. I guess you can disable
alsa modules by commenting contents of this file. Insert # at the beginning of each
non-empty line.

executing command: *gstreamer-properties* from terminal, you can change
which audio driver your system uses.

---

