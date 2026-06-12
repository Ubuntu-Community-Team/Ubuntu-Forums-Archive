---
title: "Stereo sound to be Stereo, not upmixed 5.1"
date: 2009-06-22
forum: Multimedia Software
---

### Post by mattsimis on 2009-06-22
With Ubuntu 9.04, ATI SB HD audio (ALC888 afaik, Abit F-I90 mobo onboard), 5.1 analog cable connections, no pulseaudio (just Alsa) all stereo sound is being upmixed to 5.1 automatically. This makes watching TV Shows and (Stereo encoded) Movies extremely annoying as voices and effects come out of rear speakers (which the viewer is inherently closer to). It also means you dont really even have true stereo as both channels are outputted to the Center channel too.

From looking this up, it appears previous versions (or other sound drivers) correctly outputed stereo as stereo and 5.1 over 5.1 speakers yet people wanted it the other way. I hope changes werent made to pander to people who wanted their speakers to just "do something", however illogical. Stereo should be left and right front, 5.1 should be all speakers. Under Windows there are clever algorithms to pull certain effects and sounds out of a stereo stream on put them in "surround" channels, but they would never put voice or simply "everything" in the rears, a terrible idea if you care about the content at all.

Ive tried many .asoundrc (ttable, slave channels, route duplication etc) settings, they seemingly do nothing. Currently my only "fix" is to mute the Rear and center channels when playing stereo then unmute them if I play AC3 encoded files. Quite tedious, but does show 5.1 is working correctly in the true sense. Is there a more elegant method of doing this? My test aps are Totem and Boxee.

---

