---
title: "Atomatic record with mythtv"
date: 2014-07-16
forum: Mythbuntu
---

### Post by charlie23 on 2014-07-16
Hello!
I'm trying to record a channel with mythtv during 24hs every day.
Also, I want to record in parts of 30 minutes.
Exists some scripts o commands to program this tasks with the linux console?

---

### Post by aelfric55 on 2014-07-17
If you want to do this by scripts from the console, then Mythtv is probably much more than you need. Any number of small Linux viewer applications can tune a card and record from the console. kaffeine, VLC, mplayer, xine, Linux-DVB-apps, etc. A mostly complete list of such apps may be found at [http://linuxtv.org/wiki/index.php/TV_Related_Software](http://linuxtv.org/wiki/index.php/TV_Related_Software)

From Mythtv itself, I suppose you could set a recording rule from Schedule Recordings --> Manual Schedule for each half-hour segment and set the rules to record daily. One possible glitch may be that the Manual Schedule menu (at least in my installation of 0.27) seems to lack a reference both for "0" o'clock and for "24" o'clock, so setting up a manually-scheduled recording to start between midnight and 1 AM is a bit of a puzzle.

---

