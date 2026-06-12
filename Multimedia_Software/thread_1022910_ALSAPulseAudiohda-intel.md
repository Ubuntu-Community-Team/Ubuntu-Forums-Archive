---
title: "ALSA/PulseAudio/hda-intel"
date: 2008-12-27
forum: Multimedia Software
---

### Post by atngplusultra on 2008-12-27
I've posted about this before.

I've got a Toshiba A135-S4677 and I'm running 8.10

All the sound works alright, **except** for the fact that my headphones will neither mute the audio nor play audio at all.
The "FRONT" option from my volume control window is not present, as it has been in the past.
I tried adding sound option lines to alsa-base, and that, if I remember correctly, killed sound altogether. Thankfully, a "killall pulseaudio" solved it.

Anyway, something isn't right, but I've gone through every comprehensive how-to, and from a fresh install no less.

---

