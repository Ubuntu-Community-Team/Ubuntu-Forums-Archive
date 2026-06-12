---
title: "Sound from Intel 82801DB-ICH4 Not Working"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by jmull86 on 2007-08-26
I recently installed ubuntu 7.04.  Everything works fine except for the sound.  I went through the Comprehensive Sound guide, checked 'alsamixer' to confirm nothing was muted or that the external amplifier was active.  I also noticed at the end of the gide it suggested adding ```
 "options snd-intel8x0 ac97_quirk=3"
``` to the end of /etc/modprobe.d/alsa-base for anything using the intel8x0 module.  Any other ideas what the problem might be?

---

