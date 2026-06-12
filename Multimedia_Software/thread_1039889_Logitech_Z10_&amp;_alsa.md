---
title: "Logitech Z10 &amp; alsa?"
date: 2009-01-15
forum: Multimedia Software
---

### Post by imaca on 2009-01-15
Hi,
trying to get Logitech Z10 speakers going (under 8.10)- display and volume control work but sound only works under oss. Have read some posts about running under alsa eg: [http://ubuntuforums.org/showthread.php?t=822895](http://ubuntuforums.org/showthread.php?t=822895) but did not work for me.
Settings that don't work:
sound playback : logitech Z10 (alsa)

sound capture : alsa

mixer: logitech z10

Is this the correct settings?
error is:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

---

