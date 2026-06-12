---
title: "Myth scheduler - not too smart sometimes"
date: 2008-06-11
forum: Mythbuntu
---

### Post by ubnewbie2 on 2008-06-11
I have a show (Show A), which is set to start recording 5 minutes early because the station commonly is a bit ahead of schedule late at night, and I kept missing the first few minutes.

So now, I want to record a show (show B), which is immediately before show A on the same channel, however, mythtv refuses to schedule it, saying another show with higher priority is already scheduled.  The actual problem is the 5 minute early start on show A, Removing the 5 minute early start, let's both shows record normally.

Myth's scheduler has all the info it needs to realise that it can record show B, either leaving off the last 5 minutes, which will end up in the show A recording, or it might forgo the 5 minute 'start early' for show A, and record all of show B.

I might add that ALL my shows default to 25 minute optional overrun, because you never know when a station might be running overtime.  This mechanism, mostly, works, and so I think an optional 'start early' would work too.  I am running mythbuntu 7.10 btw.

---

### Post by danbodoh on 2008-06-11
Yea, I found this same problem with old mythtv (0.20).  I ended up forcing show B to start late using the scheduling params.  So I'd watch the beginning of show B at the end of show A, and then continue onto the show B recording.

It seems that it would be an easy fix to the scheduler - if there's only one tuner, just switch from A -> B sometime between the beginning of B and the end of A.

Dan Bodoh

---

### Post by ebike on 2008-06-11
Yes, the scheduler is dumb, I have two tuners setup and multirecord=2 and do you think I can get two frontends to watch channels on different multiplexes at the same time... nope, the scheduler only wants to use the two virtual tuners that are tuned into the current multiplex, which means I can't watch two multiplexes on separate backends .... crazy:confused:

The only way I can watch two multiplexes together is to set multirecord=1 but then I can only do two things at once. Surely with two tuners and multirecord turned on, I should be able to watch any channel on both multiplexes at any time, in fact, if there are ten channels on each and I set multirecord=10, I should be able to stream 20 streams, either watching or recording ...... or so you would think.](*,)

---

