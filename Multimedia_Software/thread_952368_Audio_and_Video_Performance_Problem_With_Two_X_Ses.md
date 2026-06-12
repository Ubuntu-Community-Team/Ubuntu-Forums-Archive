---
title: "Audio and Video Performance Problem With Two X Sessions"
date: 2008-10-19
forum: Multimedia Software
---

### Post by kbranch on 2008-10-19
I'm currently using my secondary PC to watch TV with MythTV and to run a second copy of World of Warcraft, which I control from my primary PC with [Synergy]("http://synergy2.sourceforge.net").  I keep WoW on its own X session so that the key presses always go to where they're supposed to (rather than whatever window currently has focus), even if I'm on the other X session watching TV.  This worked well with Ubuntu 8.04, but the video playback from Myth now stutters for a second, then freezes when I switch to the X session WoW is running on under 8.10.  WoW seems to behave normally when its X session isn't being viewed, but even playing an MP3 with Mplayer will stutter and freeze as soon as I switch out.

Any ideas on how to either fix the freezing problem, or alternatively to make sure the input from Synergy always goes to a specific window so I don't have to run two X sessions in the first place?

---

### Post by kbranch on 2008-10-31
After some trial and error, I discovered that having it use OSS rather than ALSA fixed the problem.  Somehow I doubt 8.10 actually includes OSS, so I'm sure it's just the ALSA emulation, but it does what I need it to.  I'd be interested in a better solution if anybody knows what's actually going on, though.

---

