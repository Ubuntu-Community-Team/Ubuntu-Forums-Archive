---
title: "Amarok 2.1 blocks sound in flash"
date: 2009-06-08
forum: Multimedia Software
---

### Post by Revelation60 on 2009-06-08
Hi,

When Amarok 2.1 is running, other applications like flash haven't got sound anymore :( Has anyone got a clue what might cause that? With older version you could have music blended from multiple sources.

---

### Post by KimAndersen84 on 2009-11-25
Hi...

I would suggest that you run in either Konsole or Terminal: **sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*** (kdesu perhaps). I am not an expert. However, it will show you which program uses the sound system. To be able to play sound from more than one program you need a soundserver. Hence install PulseAudio. Run sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq* again. PulseAudio should be the first in the list. If not, kill the programs before PulseAudio and restart them afterwarts.

Kim

---

### Post by Zorael on 2009-11-27
You don't need a sound server to play from several sources at once. You need a sound mixer, which is included in ALSA. Still, applications can hog exclusive access and cause stuff like this. (To an extent, PulseAudio works by trying to put itself inbetween apps and ALSA, offering its own API where supported and emulating ALSA's where not.)

Do you have the **phonon-backend-xine** package installed?

---

