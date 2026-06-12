---
title: "Workaround for audio problems in Wine / World of Warcraft, etc under 8.04"
date: 2008-06-03
forum: Multimedia Software
---

### Post by unixg33k on 2008-06-03
I don't know if anyone else has been having this problem, but after some research I've found that a lot of people are having a problem with PulseAudio and Wine, Skype, Flash, etc.  I noticed that my sound quality in World of Warcraft went way down when i upgraded to Hardy, and also noticed that I could not have sound in Warcraft and have an MP3 playing in the background at the same time (multiple sound inputs from multiple apps).

If anyone else is having this problem - here's a workaround until they get Pulse working properly:

Go to System> Preferences> Sound.  Select "ALSA - Advanced Linux Sound Architecture" as the default option for each of the categories on the Devices tab.  Then, run winecfg and hit the Audio tab.  Check "ALSA" as the sound device, and uncheck "OSS".

This fixed the problem for me.  Hope it helps others.

---

