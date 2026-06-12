---
title: "PulseAudio - global stereo enhancement / channel delay effect"
date: 2012-01-22
forum: Multimedia Software
---

### Post by Ciosunio on 2012-01-22
Hi,

i was wondering if there's any possibility to apply system-wide effect like channel delay or something like stereo enhancer to work together with global EQ (pulseaudio-equalizer) or some plugin to produce same effect in MPD?

In Windows' foobar2000 was Channel Mixer plugin that allows to set delay to channels. It produces nicer sound to which I got used to...

I don't want to use crap like Clementine, Banshee or other media players because i like simplicity and speed of the Sonata + MPD :D

---

### Post by Ciosunio on 2012-01-23
I've found that there's possibility to load LADSPA plugins to ALSA.

Plugin, I want to load to ALSA:
[COLOR="Red"]/usr/lib/ladspa/lcr_delay_1436.so:
 L/C/R Delay (1436/lcrDelay)[/COLOR]

How to edit ~/.adoundrc to load this plugin?

---

