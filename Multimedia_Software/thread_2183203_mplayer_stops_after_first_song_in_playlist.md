---
title: "mplayer stops after first song in playlist"
date: 2013-10-24
forum: Multimedia Software
---

### Post by uh-huh on 2013-10-24
At the cli I enter ```
$mplayer -shuffle -playlist My_Playlist.m3u
```. 

When mplayer reaches the last second of the first song it just quits. No error message. It doesn't crash. I can skip to the next song by hitting enter, but the same thing happens: mplayer stops what it's doing at the last second, then nothing.

BTW have just upgraded from 12.04 to 12.10, then immediately to 13.04. Shortly before this I purged mplayer and upgraded to mplayer2. I note the .mplayer/config file is empty. Is there an option I should add to it to stop this behaviour?

---

### Post by andrew.46 on 2013-10-24
Can you give the commandline and full output just to be sure? Add a -v in there for extra info... BTW moving to MPlayer2 is not necessarily an *upgrade* :)

---

### Post by uh-huh on 2013-10-24
Weird. Added the -v and it worked! Took away the -v and it still works.

---

### Post by tgalati4 on 2013-10-24
Can someone list the primary differences (or annoyances) between mplayer and mplayer2?

Incidently, you can run *mplayer -v -v -v* for even more diagnostics.

---

### Post by andrew.46 on 2013-10-24
> **tgalati4 said:**
> Can someone list the primary differences (or annoyances) between mplayer and mplayer2?

The view from one side is here:

[http://www.mplayer2.org/differences/](http://www.mplayer2.org/differences/)

Bear in mind that like most forks there was a little ill feeling involved...

---

### Post by monkeybrain20122 on 2013-10-25
There is a new fork for mplayer2 [https://github.com/mpv-player/mpv/blob/master/DOCS/man/en/changes.rst](https://github.com/mpv-player/mpv/blob/master/DOCS/man/en/changes.rst)
I haven't seen any new commit or update in mplayer2 for 6-8 months, some suggest on the arch forum that it may be dead.

---

