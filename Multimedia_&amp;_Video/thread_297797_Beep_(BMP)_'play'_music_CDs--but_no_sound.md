---
title: "Beep (BMP) 'play' music CDs--but no sound"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by wilberfan on 2006-11-11
My Beep Media Player (BMP) plays all my music files--except if they're on a music CD.

I got it to recognize the cd-player, it will load the files (even looks up the titles, etc.), and the counters even start--but there is no audio.

I've tried each of the three output choices (eSound, OSS, and ALSA) but none produce any sound.

Any ideas?

---

### Post by Ed.Corcoran on 2006-11-21
Under Preferences -> Plugis choose CD Audio Plugin and click Preferences.

Under the Device tab, change Play Mode from Analog to Digital Audio Extraction. 

Analog uses less CPU cycles, I think, but only works if you have an audio cable running from your CD-ROM drive to your sound card.

---

### Post by wilberfan on 2006-11-22
> **Ed.Corcoran said:**
> Under Preferences -> Plugis choose CD Audio Plugin and click Preferences.

Under the Device tab, change Play Mode from Analog to Digital Audio Extraction. 

Dude.  Awesome!   I worked, first-try!  8)

---

