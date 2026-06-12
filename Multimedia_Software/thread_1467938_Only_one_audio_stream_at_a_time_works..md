---
title: "Only one audio stream at a time works."
date: 2010-05-01
forum: Multimedia Software
---

### Post by Dennis Beekman on 2010-05-01
I have installed 10.04 and it works fine... except for the audio... i have 2 problems

1. My volume control doesn't actually low or raise the volume eventhough the slider moves...
Only when the slider goes below 20% does it actually lower the volume... between 20% and 100% there is no diffirence.

2. If i start one application playing audio... rhytmbox or totem vor example... and then start another application the audio playback will fail until i restart the application that was playing it.
  Wow will not play sound at all from wine...

Update 1: 
Installing alsa-oss didn't help... but i'll keep working on it.

Update 2:
I solved it :-) ...
I installed all of the following and the problem was solved

```

sudo apt-get install linux-backports-modules-alsa-lucid-generic linux-backports-modules-alsa-lucid-preempt alsa-base alsa-oss alsa-source alsa-utils alsa-tools alsa-firmware alsa-firmware-loaders

```

If anyone else has this problem and this solution solves it then please post it here :-)

---

### Post by Dennis Beekman on 2010-05-02
Bump.... solved :-)

Seems to be a common issue... sticky maybe ? or perhaps make it part of the troubleshooting guide ?

---

