---
title: "Pandora Radio"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by shendric on 2007-12-21
Anybody able to play Pandora Radio on Gutsy? I was able to finally get the flash plugin to work (although the sound is delayed a bit, which is annoying) using PulseAudio, but Pandora just crashes Firefox.

---

### Post by yabbies on 2007-12-21
pandora works fine for me

---

### Post by shendric on 2007-12-21
Apparently, the problem is something about my PulseAudio server no longer working.  I'm not sure why.

---

### Post by shendric on 2007-12-21
Strangely enough, I removed my asound.conf, so that PulseAudio won't work, and now Pandora works just fine.

Very strange, because I had added PulseAudio, so that my flash player would use sound, because it wouldn't before.  Now, it only works without PulseAudio.

(*shrug*)

---

### Post by atomkarinca on 2007-12-21
PulseAudio is known to be buggy with flash. If you don't experience important differences between w/ and w/o PulseAudio, then I think you should go with plain ALSA.

Here's the quote from Ubuntu Wiki:

> Be Default, libflashplugin (Flash 9 support in Firefox) doesn't work properly with PulseAudio.

Go to [WWW] [http://pulseaudio.vdbonline.net/libflashsupport/](http://pulseaudio.vdbonline.net/libflashsupport/) and download the deb package (as of this posting) libflashsupport_1.0~2219-1_i386.deb (9kb) and install it.

Restart Firefox to enable audio output from flash. 

---

### Post by shendric on 2007-12-21
Yeah, I don't know where I read that PulseAudio would be useful for Flash.  I'm happy without it right now, so I'll just stick with ALSA.

---

