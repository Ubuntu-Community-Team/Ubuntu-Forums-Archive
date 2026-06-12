---
title: "Spdif PCM failure after AC3 usage"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by Spacejack on 2007-10-18
Others have posted this problem before, but no one seems to have posted a real solution to the problem, so here it is again.

Running Gutsy on an ASUS motherboard with onboard sound (SIS SI7012).  AC-3 audio was not passing through correctly when enabled in Totem and VLC; it would switch back and forth continuously between AC-3 passthrough and analog output, producing a mess.

MPlayer was able to pass through the AC-3 audio without trouble, and continues to do so.  HOWEVER, all PCM output from the SPDIF output is either not coming, or is muted.  There is a signal being produced, which is detected by the receiver/amp, but no sound.  Volume controls are normal.  Mplayer cannot play PCM through the output nor can VLC, Totem, or XMMS.  Analog output works fine.  MPlayer crashes sometimes when loading a file during playback of another file, particularly if the first file was AC-3.  Uninstalling/reinstalling Mplayer and ALSA did not help and the problem persists even after hard reboot.  This suggests that some switch or other isn't getting thrown properly, but what is it?

---

### Post by korcsi on 2007-10-30
In package "alsa-utils" is "iecset".

For me "iecset audio on" can help.

Sorry for my english.

---

### Post by Spacejack on 2007-10-30
This worked!  Thank you very much!

---

