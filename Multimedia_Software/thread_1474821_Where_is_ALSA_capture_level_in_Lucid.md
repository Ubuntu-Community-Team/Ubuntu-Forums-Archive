---
title: "Where is ALSA capture level in Lucid?"
date: 2010-05-06
forum: Multimedia Software
---

### Post by bobince on 2010-05-06
The ability to set the ALSA volume level for audio capture seems to be gone. In Karmic and previously this was possible through gnome-volume-control.

Now in Lucid there's a fader for the 'Input' tab, but it seems only to be a software (PulseAudio?) fader applied on top of the hardware level, with a very limited range.

My (Thomann SC450USB) microphone's volume defaulted extremely quiet, so it was impossible to boost the volume to anywhere near usable levels from this fader. There also seems to be nothing in pavucontrol. I was able to fix it by resorting to alsamixer from the console (then pressing F6, F4), but surely normal users can't be expected to do that, can they?

Have I missed something?

---

