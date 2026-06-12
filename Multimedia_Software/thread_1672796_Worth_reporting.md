---
title: "Worth reporting?"
date: 2011-01-21
forum: Multimedia Software
---

### Post by msknight on 2011-01-21
Not sure if this is worth reporting. Found the following in my syslog.

Jan 21 16:10:44 michelle pulseaudio[18125]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Jan 21 16:10:44 michelle pulseaudio[18125]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Jan 21 16:10:44 michelle pulseaudio[18125]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Jan 21 16:11:27 michelle pulseaudio[18125]: ratelimit.c: 1 events suppressed

Ubuntu 10.10, 64 bit, fully patched to this moment.

Not sure how to file a bug, or what other information would be needed.

---

