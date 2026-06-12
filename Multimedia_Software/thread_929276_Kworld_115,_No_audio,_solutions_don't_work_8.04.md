---
title: "Kworld 115, No audio, solutions don't work 8.04"
date: 2008-09-24
forum: Multimedia Software
---

### Post by Cogman on 2008-09-24
So I am trying to get the analog channels to pipe audio to my motherboard sound. Well, I have two problems.

1. My motherboards line-in doesn't work (Asus P5Q-E)
2. apparently my tuner doesn't have an alsa mixer.

I've tried all the different installation tutorials that I could find, but none seam to work. What is weird is that I can record sound but can't listen to it from my motherboard (So mencoder pointed to /dev/dsp1 will record sound, but mplayer pointed to /dev/dsp1 won't play any sound)

Sound does come out of the card itself, but its a pain to have to switch where my speakers are plugged into ever time I want to watch tv.

I deduce that there is no mixer from this message given by wine.

"fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer"

any help would be appreciated.

---

