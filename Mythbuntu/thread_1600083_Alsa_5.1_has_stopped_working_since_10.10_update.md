---
title: "Alsa 5.1 has stopped working since 10.10 update"
date: 2010-10-18
forum: Mythbuntu
---

### Post by bruk on 2010-10-18
I only noticed the 5.1 had disappeared when I played a dvd and couldn't hear any voices.

My setup is an Asus M2N M/B, with an AD1988 chip onboard.

I have the appropriate "options snd-hda-intel model=3stack" in my alsabase.conf file, which worked previously, and the alsamixer even reports 6ch as a mode, with all of the correct volume controls.

If I try speaker-test, all but the front left/right channels are silent. Bizarrely though, the upsampling to 5.1 in myth does work, with audio coming out of all of the speakers.

I've seen no similar posts regarding this kind of issue with 10.10, so I'm either having a unique problem, or the problem just hasn't been cropping up yet with 10.10 being so new.

Anybody have a clue as to why I appear to have 6ch 5.1 enabled, but it won't actually playback properly?

---

