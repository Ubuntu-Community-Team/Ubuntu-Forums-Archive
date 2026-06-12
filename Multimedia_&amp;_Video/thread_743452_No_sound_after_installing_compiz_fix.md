---
title: "No sound after installing compiz fix"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by go_lanche on 2008-04-02
I had a problem that I managed to figure out myself that I thought might come up for others. I recently installed compiz and got it all working properly but my sound went away after the install. I went crazy trying to get into ALSA and follow the excellent instructions found at [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449"). Nothing I was doing seemed to work so I went back into System --> Preferences -- > Sound and fixed the entire problem by selecting the actual soundcard's mixer (in my case nvidia). Somehow the compiz installation had reset it to an ALSA that wasn't working. This reminded me that its always a good idea to make that there's gas in the tank before you take your engine apart.

---

