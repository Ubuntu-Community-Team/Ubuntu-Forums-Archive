---
title: "Sound issues."
date: 2009-04-28
forum: Multimedia Software
---

### Post by And1945 on 2009-04-28
Hi,

I have an HP DV5 Pavilion laptop, which runs Ubuntu 9.04. The sound works from the speakers, but that was until I added a line in my alsa-base file. Back then my sound worked from the headphones. This is the contents of:

/etc/modprobe.d/alsa-base

> # Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5


Looking in the rearview mirror, I'd rather have sound from my headphones. But ultimately, it should switch back and forth, right?

Is there a way to get sound from the speakers, and then when you plug in headphones, the speakers shut off.
Or would it be easier some other way, to just get proper sound from the headphones?

Remember, headphones is priority.

---

### Post by And1945 on 2009-04-28
Nevermind. Found the answer here: [http://ubuntuforums.org/showthread.php?p=7167170&posted=1#post7167170](http://ubuntuforums.org/showthread.php?p=7167170&posted=1#post7167170)

---

