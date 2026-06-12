---
title: "alsamixer (Invalid Argument) + no mic without model=generic"
date: 2012-04-02
forum: Multimedia Software
---

### Post by deltaluca on 2012-04-02
Trying to get my microphone working on my desktop.

Setting snd-hda-intel model=generic lets the microphone work, but it also seems to set my audio to mono from stereo.

Trying to run alsamixer and see if there's something in there I can set which is not exposed through Gnome sound menu gives me an error:

"cannot load mixer controls: Invalid argument"

I've also tried looking for more model names to try out, but there doesn't seem to 'be' any listed at all for my device which is listed by: 'cat /proc/asound/card0/codec* | grep Codec' as: Realtex ALC887

Results of alsa-info.sh: [http://www.alsa-project.org/db/?f=f9c6e03837dc431981eeb1fde0ae93fcd3fa1f8f](http://www.alsa-project.org/db/?f=f9c6e03837dc431981eeb1fde0ae93fcd3fa1f8f)

---

### Post by deltaluca on 2012-04-03
*bump* anyone?

---

