---
title: "Sound card problem"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by calcite on 2006-08-15
I have a very weird problem, my soundcard is picked up by lspci

calcite@calcite-Dev:/$ lspci | grep audio
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 11)
calcite@calcite-Dev:/$

But when I boot up I get a kernel message say "Codec ready: Codec not ready"
the funny thing is I've tried other distros that I have used in the pass and the sound work and now on that very same version it doesn't,
my /proc/asound/cards contains to soundcard.... does anyone know whats up with this ?

---

