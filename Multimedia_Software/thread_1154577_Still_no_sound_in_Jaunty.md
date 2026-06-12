---
title: "Still no sound in Jaunty"
date: 2009-05-09
forum: Multimedia Software
---

### Post by Yuxuan on 2009-05-09
[Ubuntu detects the sound cards and everything]("http://xs538.xs.to/xs538/09176/screenshot725.png"), but the problem is that I don't hear any sound at all(from the speakers). I tried unmuting every channel in every device in the volume control, but still no luck.

Windows can play the audio without error, though, and when I was using Ubuntu 8.10, nothing was wrong, either.

I followed the sticky, but, still no sound.

---

### Post by psyke83 on 2009-05-09
Check the "hidden" controls in the volume control applet. You can find them by clicking on the "Preferences" button, and then enabling checkmarks for each mixer entry you wish to display.

Ensure you un-hide the "External Amplifier" mixer, and try toggling it on/off. Check *all* possible mixers besides this one, though - every sound card is different.

---

### Post by Yuxuan on 2009-05-09
I unhid all controls, but I couldn't find the "External Amplifier" mixer.

Edit: I also unmuted all of the tracks, but still nothing.

---

### Post by psyke83 on 2009-05-09
If you have multiple sound cards, PulseAudio may have chosen the wrong card. If that's the case, refer to my guide (especially Part A, Step 5).

---

