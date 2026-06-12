---
title: "Movie Player louder than Audacious"
date: 2008-08-20
forum: Multimedia Software
---

### Post by habicht on 2008-08-20
Why is the sound in Movie Player louder than in Audacious?

I turned all settings to max volume:
- in both applications
- in Gnome's Volume Control
- in the console Alsa Mixer

In Audacious I've tried the Alsa Output Plugin as well as the PulseAudio Output Plugin. Doesn't change anything.

---

### Post by caiooiac on 2009-08-18
I know it past almost a year, but as I haven't found any other mention of this, and have just discovered the problem, I'm posting!

In audacious, under Preferences --> Replay Gain, there's a Preamp and a Default Gain option. The default gain is -9,00 dB. Just put 0dB and it will be as loud as any other application.

That's it

---

