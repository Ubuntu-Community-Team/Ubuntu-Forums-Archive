---
title: "System|Preferences|Sound|Devices| ... Test -- No sound?"
date: 2008-11-25
forum: Multimedia Software
---

### Post by Ubuntist on 2008-11-25
Sound playback works on my Intrepid system except that there are no system sounds.

Under System|Preferences|Sound|Devices, I have set the playback options to autodetect. The funny thing is that when I click any of the test buttons, I hear nothing.  If I change the playback option from autodetect to an ALSA setting, I *do *hear a tone, but with ALSA settings I get no sound from web pages.

Is this behavior a clue as to why I have no system sounds?  Is there something else I can learn from it?

By the way, what should happen when I click the test button associated with sound capture?  Regardless of setting, I hear nothing.

---

### Post by Milligram on 2008-12-07
Hi,

Open a terminal and enter:

gnome-volume-control

Check that "PCM" is not muted, this has been the case for me a couple of times...

/Andreas

---

### Post by Ubuntist on 2008-12-08
Thanks for the suggestion, Milligram.  I've checked, and I find that no PCM settings (PCM, PCM center, etc.) are muted and they're all set to maximum.

---

