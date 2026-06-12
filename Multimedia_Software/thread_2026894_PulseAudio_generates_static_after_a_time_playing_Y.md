---
title: "PulseAudio generates static after a time playing YouTube vids"
date: 2012-07-15
forum: Multimedia Software
---

### Post by Nutria on 2012-07-15
Happened in 10.10 Maverick with older versions of FF and Flash and also now in 12.04 (skipped 11.04 and 11.10) with the current Flash.

Web browser is FF, if that matters.

**Sometimes** it's after only a couple of minutes, **sometimes** it doesn't happen at all, and **sometimes** it's halfway through a long video.  **Sometimes** reducing the video quality helps.  There's no pattern that I've been able to discern.

It also happens when playing videos at nola.com but none that I can remember from espn.com.

This never happens when playing local videos using mplayer and vlc or music via aqualung.

Doing "killall pulseaudio" and waiting a minute eliminates the static at that moment, but there's no guarantee that it won't appear again in a little while.

**Importantly**, this never happens on my wife's computer, which runs 10.10.

Google has been no use.

Thanks for any tips.

---

### Post by qzjul on 2013-06-23
I've also been experiencing this, in 12.04; Browser Chrome; I can't seem to find anybody other than this so far who's had this problem.  I just do service pulseaudio restart and close/reopen the tab and it goes away.  But I'd reallly prefer to not have to do that 2-3 times per day while working :(

---

