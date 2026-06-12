---
title: "sound broken after pulseaudio upgrade"
date: 2008-11-22
forum: Multimedia Software
---

### Post by Bulletbeast on 2008-11-22
After last night's automatic pulseaudio update (0.9.13-1ubuntu3~ppa1), sound has stopped working for me. At boot, the jingle was turned into a second of noise, and in xmms2 using alsa output songs are accelerated to the point of becoming noise, too. Curiously, starting Rhythmbox seems to fix that, however, closing it makes it happen again. Help!

---

### Post by psyke83 on 2008-11-22
That's not an official update for PulseAudio. If you look at the version string you'll see this package is from somebody's PPA. 

Check your /etc/apt/sources.list to determine where the update originated from, disable the repository, and downgrade the PulseAudio packages.

---

### Post by Bulletbeast on 2008-11-22
It was ppa.launchpad.net... I can't even trust that, it seems.

---

