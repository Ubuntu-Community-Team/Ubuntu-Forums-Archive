---
title: "Sound occasionally cuts out"
date: 2009-12-04
forum: Multimedia Software
---

### Post by Chunz0r on 2009-12-04
Hi - running Ubuntu 9.10, occasionally my sound will just cut out; I have to mute/unmute it for it to work again. Where should I start debugging this? Nothing relevant is appearing in /var/log/syslog.

This only seems to happen when I do something - nothing in particular, might be opening a new firefox window or nautilus, or clicking on an arbitrary menu. I get a small click/hiss through my speakers, and after that no sound.

EDIT: I've been logging pulseaudio's output -- this is what I get [I believe] when the sound cuts out [attached]. Anyone see the problem?

---

### Post by Chunz0r on 2009-12-04
An even more specific time-frame log [attached]

---

### Post by Chunz0r on 2009-12-12
Nobody got any ideas?

---

### Post by RedSingularity on 2009-12-12
Did you try reinstalling pulseaudio all together?

---

### Post by Chunz0r on 2009-12-13
Yep, also tried reformatting/installing karmic multiple times, but no result.

---

### Post by RedSingularity on 2009-12-13
If you have reinstalled the system multiple times with no success.......it may just be that your sound card is not supported by ALSA.

---

