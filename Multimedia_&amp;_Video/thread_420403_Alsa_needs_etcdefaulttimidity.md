---
title: "Alsa needs /etc/default/timidity"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by DavidS on 2007-04-23
I upgraded from Edgy to Feisty yesterday.

I have sound, but every time I boot I am told that Alsa can't be started, because timidity is not configured, and I need to edit /etc/default/timidity.  I've had a look at this file, but I have no idea what I am supposed to put in it.  The current version of the file only has one active line, which (with the preceding comment) is:

# Setting overrides (of /etc/timidity.conf) for the ALSA sequencer daemon
TIM_ALSASEQPARAMS="-B2,8 -Os"

Any help would be much appreciated.

---

### Post by ubromtoo on 2007-05-28
Bump

---

