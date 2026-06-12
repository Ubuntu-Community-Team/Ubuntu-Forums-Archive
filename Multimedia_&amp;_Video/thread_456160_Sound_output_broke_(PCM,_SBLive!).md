---
title: "Sound output broke (PCM, SBLive!)"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by glaze on 2007-05-27
I have a weird problem. I watched a DVD using MPlayer. MPlayer crashed at the end of the movie and after that I can't get sound in any application. I use digital PCM signal and an external amplifier. I booted my computer and it didn't help. I compiled a new kernel and that didn't help. Mixer settings are ok, sound card is ok and amplifier is ok. I tested with Kubuntu Live CD and sound works in it, but not in my main installation. The weird part is that AC3 audio works fine, but nothing else works.

---

### Post by Pragmatist on 2007-05-27
Have you tried a "complete" uninstall of Mplayer using Synaptic?

---

### Post by glaze on 2007-05-27
The problem is in every application that plays something, so i think that ALSA broke. I purged and reinstalled it to no avail. MPlayer wasn't from repository, i compiled it myself. I just reinstalled the whole OS and now everything works fine.

---

