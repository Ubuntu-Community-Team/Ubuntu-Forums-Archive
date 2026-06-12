---
title: "ReplayGain &amp; Amarok"
date: 2012-07-12
forum: Multimedia Software
---

### Post by CatKiller on 2012-07-12
All my audio files have ReplayGain tags and Amarok supports ReplayGain tags, so all should be peachy.

Unfortunately, Amarok (or potentially Phonon-GStreamer's implementation) is pretty rubbish.

What is supposed to happen is that an audio player reads the tags, applies the required amount of gain to the amplifier stage and then plays the stream - exactly as if you had a list of your preferred volumes for each of your favourite songs written down and twiddled the volume knob before you pressed play. Obviously you'd have to be pretty OCD to actually do that, but that's what computers (and, specifically, ReplayGain tags) are for.

What actually happens is that you get around a second of stupidly-loud-victim-of-the-Loudness-Wars audio before the volume plunges abruptly to where it should be. Exactly like a crappy RMS compressor that doesn't do anything until it's filled its buffer enough to calculate an RMS value (which is the behaviour of most compressors under Linux despite it sounding terrible and being unnecessary) or, to put it a different way, like the appalling Automatic Volume Control system from the early 90s.

Is there anything that can be done (different backend, scripts, or whatever), or are there any pointers to which subsystem is actually responsible for this distinctly sub-optimal behaviour for a bug report?

---

### Post by CatKiller on 2012-07-13
Bump.

---

