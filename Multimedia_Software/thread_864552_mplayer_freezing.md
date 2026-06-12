---
title: "mplayer freezing"
date: 2008-07-19
forum: Multimedia Software
---

### Post by jgallen23 on 2008-07-19
I'm having issues when using mplayer via cli on hardy.  When I execute mplayer blah.mp3, the player freezes, but when I execute mplayer -ao alsa blah.mp3 it runs fine.  Does anybody know why this is happens?  Is there anyway to make it so I don't have to type -ao alsa all the time?

---

### Post by shirilover on 2008-07-19
Sure, just add the following to ~/.mplayer/config. Create this file if it doesn't already exist.

ao=alsa

---

### Post by dannyboy79 on 2009-06-17
> **shirilover said:**
> Sure, just add the following to ~/.mplayer/config. Create this file if it doesn't already exist.

ao=alsa

i am so glad for google. i was pretty upset when a fresh Hardy install trying to watch movies (mpg or avi) would crash mplayer. when I did the above all is well now.

---

