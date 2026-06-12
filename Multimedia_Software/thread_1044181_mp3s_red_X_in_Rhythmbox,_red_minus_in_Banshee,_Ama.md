---
title: "mp3s: red X in Rhythmbox, red minus in Banshee, Amarok ok"
date: 2009-01-19
forum: Multimedia Software
---

### Post by zim2dive on 2009-01-19
Was trying to get Rhythmbox to see a DAAP share (running Firefly server on another machine)... RB would start to connect then segfault tho.  So I went to file a Bugzilla and it asked for a stack-trace... directing me to install rhythmbox-dbg .. ok sure, no biggee, I did that

sudo apt-get install rhythmbox-dbg

At this point I don't see anything to indicate a change (should I?), I still only see Rhythmbox in the menu.. (incidentally, Rhythmbox only seems to launch every OTHER time I select it from the menu.. I see the round ball come up for 2-3 seconds then nothing.. I launch it again and it works.. this has been since day 1)....

Ok, so I think I have rb-dbg installed now, I guess, and when I launch RB, I can now connect to my DAAP server... excellent I think... except when I go to play a shared song, I get a red X next to the song, then the next, and the next, then a few more, then it locks up and I have to force quit... sigh.

So I copied a song locally (no DAAP share).. and I can't even play that (again a red X).  

I tried Banshee... similar result there (a red minus).

Amarok is playing them find (but Amarok doesn't retrieve playlists from the DAAP server, and the others do), so Amarok is not a long-term solution for me.

Any ideas?

I have uninstalled and reinstalled the restricted codecs.. also per other debug hints I saw, I nuked my rhythmbox libraries in .gnome and .gconf... to no avail.

thanks,
Mike

---

### Post by mc4man on 2009-01-19
Read here
/usr/share/doc/rhythmbox-dbg/readme
and
[https://wiki.ubuntu.com/DebuggingProcedures](https://wiki.ubuntu.com/DebuggingProcedures)

[https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace)

---

### Post by zim2dive on 2009-01-19
> **mc4man said:**
> Read here
/usr/share/doc/rhythmbox-dbg/readme
and
[https://wiki.ubuntu.com/DebuggingProcedures](https://wiki.ubuntu.com/DebuggingProcedures)

[https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace)

Do those have any info about how I can get mp3's playing again (that is a gating issue) ?

ie. I can't really do any debug/backtrace until I can get the mp3's playing...

I'm trying to understand what the red X/- are trying to tell me.  At 1st I thought it meant "missing file", but when it can't even play a locally stored file, then I think it must be something else..

---

