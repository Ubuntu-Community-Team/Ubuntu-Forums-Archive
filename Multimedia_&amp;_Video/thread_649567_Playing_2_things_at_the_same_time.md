---
title: "Playing 2 things at the same time?"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by RudolfMDLT on 2007-12-25
Hi there,

I used to be able to do this in Kubuntu - I'm running Ubuntu 7.10 now. I think it has something to do with Xine but I haven't been able to fix it: How do I setup my sound so that I can play multiple audio tracks at the same time? that is, have something streaming in FireFox and an mp3 playing in Exile?

Thanks for any help!

Rudolf

---

### Post by Frants on 2007-12-25
I've been tired of not being able to play something in VLC and XMMS at the same time. Found the setting in XMMS to use the libALSA instead of libOSS. This did the trick.

Perhaps you can change the output in Exaile to ALSA and see if it makes any difference? Right now I can play streaming flash or wmv in Firefox together with XMMS (and I suppose with other media players aswell).

---

### Post by weblordpepe on 2007-12-25
From what I've found, OSS is old and ALSA is new.

Alsa lets more than one app use the sound device at a time, while OSS doesnt. (I may be wrong, but thats how it seems).
I think you can get fake OSS --> ALSA wrapper drivers or something but I don't know anything about it.
I would like to know more too. Hopefully somone in the know will reply.

---

### Post by RudolfMDLT on 2007-12-26
ALSO VS OSS! Thats what I had forgotten! :) Thanks! the packadges are "alsa-base" and "alsa-oss". I'll see how well it works through this week.

---

