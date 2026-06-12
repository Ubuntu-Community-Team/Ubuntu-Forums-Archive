---
title: "KPhone no sound"
date: 2010-01-24
forum: Multimedia Software
---

### Post by klinzter on 2010-01-24
hi all,

i dont have output (no sound) from kphone, but i see the plugin kphone in the sound preferences.

and i saw this erros in the syslog

Jan 24 22:06:43 lap pulseaudio[2000]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Jan 24 22:06:43 lap pulseaudio[2000]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Jan 24 22:06:43 lap pulseaudio[2000]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.


best regards

---

