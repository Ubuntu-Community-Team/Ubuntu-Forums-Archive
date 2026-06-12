---
title: "Encrypted DVD won't play?"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by Saubazi on 2006-11-06
I am a bit mystified - I put a dvd in and totem or whatever that is says something about maybe missing libdvdcss.
"The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

Mplayer equally says something about missing "libdvdread: Encrypted DVD support unavailable."

installed xine and I get:

This is xine (X11 gui) - a free video player v0.99.4.
(c) 2000-2004 The xine Team.
libdvdread: Encrypted DVD support unavailable.
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdread: Encrypted DVD support unavailable.
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).

So what gives?

---

### Post by mazirian on 2006-11-06
Perhaps you are "trying to play an encrypted DVD without libdvdcss"?

There are codecs that are necessary to decrypt the dvd for playback.  Those codecs are illegal in certain countries, including the US because they violate the DMCA.  The codecs are nonetheless available in third party ubuntu repositories.

---

### Post by Saubazi on 2006-11-06
Never mind I solved it thx for pointing the direction...

---

