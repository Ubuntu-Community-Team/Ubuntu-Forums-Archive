---
title: "Forcing it to record"
date: 2008-12-17
forum: Mythbuntu
---

### Post by pt123 on 2008-12-17
is there any way of getting mythtv to just record even if somehow the epg or the signal is indicating a different program.

I choose a show to record from the epg. But when the time arrives to record the show Mythtv doesn't record it. I am assuming the show starts late or the epg is altered and it doesn't record. This is so bloody annoying. 

Is there a special hidden feature that can be triggered so mythtv doesn't try to be "smart" and record the program based on the times initially set.

---

### Post by uMuppet on 2008-12-17
You can do a time based record in Manual Schedule.

Goto
Manage Recordings -> Schedule Recordings -> Manual Schedule

Then it'll be kinda like an old school VCR

---

### Post by pt123 on 2008-12-17
> **uMuppet said:**
> You can do a time based record in Manual Schedule.

Goto
Manage Recordings -> Schedule Recordings -> Manual Schedule

Then it'll be kinda like an old school VCR

That is irritating, having to input the times. The point of the EPG is to save you work by giving you the times. 

Does everywhere in the world follow their EPG strictly, or just backwaters like where I like (Australia) have trouble sticking 100% to the EPG.

I really don't see why there is a big fuss if the show starts 1 minute late.

There is plenty of disk space, and no conflicting recording, why can't it just bloody record than causing heart ache.

---

### Post by SiHa on 2008-12-17
...thing is, in my experience Myth doesn't try to be smart. In fact I've found it to be a bit dumb in certain situations- I set a recording to 'record in this timeslot every week' but if the start time changes by 5 mins it won't record. Very annoying on BBC1 on a Saturday night! 
In other words, if you schedule a recording for 10:55 (say) and it shows up in the upcoming recordings list. Then it should record regardless of whether the program starts late, or even if it isn't shown at all.
If it's not recording then that suggests a problem, rather than Myth being to clever for it's own good.

Might be worth a look at the backend log around the time the recording is scheduled to see what it's doing.

---

