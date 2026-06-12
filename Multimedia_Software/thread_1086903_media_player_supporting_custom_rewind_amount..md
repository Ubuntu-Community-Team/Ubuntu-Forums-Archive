---
title: "media player supporting custom rewind amount."
date: 2009-03-04
forum: Multimedia Software
---

### Post by qns8dn3 on 2009-03-04
Most media players support skipping forward and rewinding back with Left key and Right key as shortcuts. Is there a media player supporting setting customized skip amount and rewind amount of time?

smplayer and mplayer has Left key to rewind 10 seconds and Up key to rewind one minute but I don't know if it's possible to set it to rewind 5 seconds and 30 seconds.

---

### Post by rvm4000 on 2009-03-04
smplayer allows to customize the seeking times (Preferences -> Interface -> Seeking).

Anyway, setting a value of less than 10 seconds probably won't work correctly with most videos, as mplayer always seeks to a key frame, and usually there's one every 10 seconds... It may work though with mpeg files.

---

### Post by andrew.46 on 2009-03-04
Hi qns8dn3,

MPlayer can be customised in this manner. All the details can be seen here:

[http://www.mplayerhq.hu/DOCS/HTML/en/control.html](http://www.mplayerhq.hu/DOCS/HTML/en/control.html)

complete with a sample input control file.

All the best,

Andrew

---

