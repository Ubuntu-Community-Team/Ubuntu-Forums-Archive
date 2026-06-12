---
title: "LMMS 0.4.13 &quot;Regression&quot;"
date: 2012-02-12
forum: Multimedia Software
---

### Post by Joseph Schwenker on 2012-02-12
I've been experiencing a problem after updating from LMMS 0.4.12 to 0.4.13. Apparently, there was a regression in 0.4.12 that caused the "Slow Morph Choir" sound from the ZynAddSubFX plugin to cutoff an echo at the end of notes.

Unfortunately, I built a rather lengthy song on top of the buggy plugin, and I'm now finding that I am unable to re-export the song because of the resulting echos and the clashing chords they form.

Is there a way I can downgrade to LMMS 0.4.12 or disable the echo in some way?
I'm on Ubuntu 11.04 32-bit.

---

### Post by Joseph Schwenker on 2012-02-13
bump

---

### Post by neu2buntu on 2012-02-14
i would try going to zynaddsubfx(lmms gui), edit instrument, SUBsynth> edit, amplitude> amplitude envelope and lower the R.dt ( release time ) whilst in play mode in your song, this will reduce the echo effect. *note this Slow Morph Choir does not have any effects applied*

---

### Post by Joseph Schwenker on 2012-02-14
> **neu2buntu said:**
> i would try going to zynaddsubfx(lmms gui), edit instrument, SUBsynth> edit, amplitude> amplitude envelope and lower the R.dt ( release time ) whilst in play mode in your song, this will reduce the echo effect. *note this Slow Morph Choir does not have any effects applied*

You, sir, are a genius. And an epic one, at that. You have completely solved my problem.

Kudos, internets, and cookies to you.

---

