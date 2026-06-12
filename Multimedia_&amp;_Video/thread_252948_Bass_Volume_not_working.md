---
title: "Bass Volume not working"
date: 2006-09-07
forum: Multimedia &amp; Video
---

### Post by XenoPhex on 2006-09-07
I'm running the latest version of Ubuntu (Dampper) on a Dell Inspiron 600m (1.5Ghz Pentium Centrino) and I also have a Creative Audigy 2 ZS Notebook PCMCIA sound card. Right now I have a 5.1 hooked up to the thing but for some reason the Bass Volume bar doesn't effect the sound of the Bass. I've tested this on a few songs and it seems that the Bass Volume doesn't work at all. Does anyone know of anything I could do to control sound better? (I currently play songs on the .5 Beta of Listen Music Player).

---

### Post by detectiveinspekta on 2006-09-07
Try unmuting tone
use
```

alsamixer

```
go to tone then press m to unmute if it already isn't.

Not always works

---

### Post by XenoPhex on 2006-09-08
I tried that but it seems to have the same effect as the usual volume control. Also when I turn tone on, my sound becomes all spaztastic and staticy

---

### Post by baronbliss4 on 2007-03-22
ok i got mine to work using Alsamixer. i turned the master volume all the way up. Checked the box for tone. It messed up my sound so finally, i adjusted the pcm level. all the sound came out clear, i adjusted the bass level, then turned the pcm up until it was as loud as possible without distorting. (note: i don't know if it matters, but the only boxes checked are tone and external amplifier. when the sound went insanely distorted at first, i started clicking every checkbox to make it stop.....)

---

