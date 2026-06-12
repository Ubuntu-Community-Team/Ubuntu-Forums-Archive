---
title: "What happened to MIDI fix in Automatix?"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by EReckase on 2006-06-05
I recently ran Automatix to set up my new installation of Dapper, and I noticed that the Timidity ALSA Sequencer install that was performed for my Breezy installation was not available from the menu.  I've been searching up and down for the manual process that Automatix used to set up Timidity as the MIDI sequencer, but I can't find anything other that the UNinstall process.  Would someone mind telling me what exact steps Automatix went through to set up MIDI playback?

---

### Post by cogadh on 2006-06-06
There might be a good reason for its removal:
[http://www.ubuntuforums.org/showthread.php?t=190288](http://www.ubuntuforums.org/showthread.php?t=190288)

If you want to try manually installing, look at /usr/share/auitomatix/breezy/autoscript_breezy
About a quarter of the way down is the midi fix steps.

---

