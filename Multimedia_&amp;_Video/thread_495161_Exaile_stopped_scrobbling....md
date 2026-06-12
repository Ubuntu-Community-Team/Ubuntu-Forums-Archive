---
title: "Exaile stopped scrobbling..."
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by ScreamingNoises on 2007-07-07
Hey, i've installed Exaile a few days go, and it was working very well... but yesterday it stopped Scrobbling. I have no idea why, i've tried to update to a new version, and even make a clean install, but it is still not scrobbling. The error log is this one:
```
[13:25:57] Attempting to submit track 05. Friend Of A Friend from In Your Honor: Two by Foo Fighters to last.fm
[13:25:57] -----------------------
[13:25:57]  submit_to_scrobbler ( /usr/share/exaile/xl/audioscrobbler.py @ 7):
[13:25:57] -----------------------
[13:25:57] Traceback (most recent call last):
[13:25:57]   File "/usr/share/exaile/xl/audioscrobbler.py", line 25, in submit_to_scrobbler
[13:25:57]     album=tr.album)
[13:25:57]   File "/usr/share/exaile/xl/audioscrobbler.py", line 762, in posttrack
[13:25:57]     self.post()
[13:25:57]   File "/usr/share/exaile/xl/audioscrobbler.py", line 821, in post
[13:25:57]     self.auth()
[13:25:57]   File "/usr/share/exaile/xl/audioscrobbler.py", line 669, in auth
[13:25:57]     raise AudioScrobblerHandshakeError(msg)
[13:25:57] AudioScrobblerHandshakeError: AudioScrobblerHandshakeError: Tried to reauthenticate too soon after last try (last try at 2007-07-07 12:19:11)

```

Any help or suggestion is welcome...
Thanks...

---

### Post by ScreamingNoises on 2007-07-10
Problem kind of solved:p
I think that the problem is this:
I've extracted some cd's with soundjuicer, and the tags of the music from  this cd were "music bleh.mp3" for example (I didn't had yet noticed the .mp3 termination), and when audioscrobbler from exaile tried to send the information regarding this music the last.fm rejected it... 
But what was bothering me was that i couldn't submit some musics that once had been submited...
My guess is that when Exaile tried to submit several incorrect musics, last.fm canceled my rights of scrobbling for awhile...
This is my theory ;)

Anyway, just deleted the termination and now it's scrobbling smoothly.
Great program BTW:D

---

