---
title: "No sound at all..."
date: 2010-02-19
forum: Multimedia Software
---

### Post by aridattebayo on 2010-02-19
I am currently running UNR 9.04 on an Asus EEE PC 900, recently installed it, installed flash and now I have NO SOUND. When my computer boots up I have sound at the login screen and when I log in (I have custom wav files for that) but once I get to my desktop, its gone. No sound playing files in audacity, rhythmbox, no sound when watching youtube videos in Firefox.... we have tried everything, including resetting alsa.

I have NO clue what is wrong.

Thanks in advance, and sorry if this has been posted before.

ETA - problem seems to be solved, I am guessing its something with my startup sounds that kills the sound system, I disabled all of my startup sounds and it returned to normal.... Is there any way I can have custom start up sounds and not have it ruin the sound for other things?

---

### Post by bcschmerker on 2010-02-20
What were/are your settings in GNOME Sound Properties?  GNOME Display Manager Setup?  These will give me clues to the "no sound" issue.  From my own experience, Accessible Login in GDM should **not** be enabled, as GDM will then hog the audio resources.

---

