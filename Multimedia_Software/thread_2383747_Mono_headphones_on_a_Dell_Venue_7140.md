---
title: "Mono headphones on a Dell Venue 7140"
date: 2018-01-29
forum: Multimedia Software
---

### Post by slatye on 2018-01-29
Hello everyone,

I'm struggling to get sound working properly on a Dell Venue 11 7140 with Lubuntu 17.10 (also tried Ubuntu MATE 17.10 with no luck). Works fine over the speakers, works fine through headphones under Windows 8.1, but headphones under Linux seems to result in a mono output (eg. the various binaural videos on YouTube give no spatial separation, whereas they did under Windows). For audio where there's a background sound that would play through both sides and a foreground side that would only play through one (eg. almost any movie) the background sound is much louder than the foreground one (presumably because it's adding the channels together), rendering foreground speech largely unintelligible.

ALSA info: [http://www.alsa-project.org/db/?f=bdd1c4a959b38d2aa733ecb7ebd1f0b74a923243](http://www.alsa-project.org/db/?f=bdd1c4a959b38d2aa733ecb7ebd1f0b74a923243)

I've been trying a bunch of suggestions from forum threads and so far the only thing I've managed to do is kill the sound completely (by adding "options snd-hda-intel model=dell-headset-multi power_save=0 index=1,0" to /usr/share/alsa/alsa.conf). Removing index=1,0 at least lets the sound work again. Most of the suggestions seem to be for very old Ubuntu versions; I've applied what I could but haven't yet had any success. Using the alsa force-reload option tends to just lock-up the system completely (to the extent that a power-cycle is required to recover) - so I've just been restarting after each change.

In alsamixer, if I mute either HPO R or HPO L then it at least stops adding the channels together - but I still get sound from both sides of the headphones. If I mute both then I get no sound, as expected. 

Is there anything I can do to trace were the problem might be?

Thanks,
slatye

---

