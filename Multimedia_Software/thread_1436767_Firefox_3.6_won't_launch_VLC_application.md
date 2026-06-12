---
title: "Firefox 3.6 won't launch VLC application"
date: 2010-03-23
forum: Multimedia Software
---

### Post by clubsoda on 2010-03-23
Firefox 3.6 wants complete control of my multimedia experience. :razz:
For example, an ASX stream gets played in the browser window, with unwanted zoom-to-fit and no sound. Let's launch VLC in its own window instead.

Tried:-
In Edit->Preferences->Applications, set everything to "Always ask". [Ignored]
Set "Microsoft ASX playlist" to use /usr/bin/vlc. [Ignored]
In Synaptic, make sure package mozilla-plugin-vlc is not installed. [Check]

But still no standalone VLC.

---

### Post by clubsoda on 2010-03-23
Hmmm, partial resolution by removing package **totem-mozilla**.

---

