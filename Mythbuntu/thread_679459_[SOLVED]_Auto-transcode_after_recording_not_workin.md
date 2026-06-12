---
title: "[SOLVED] Auto-transcode after recording not working"
date: 2008-01-27
forum: Mythbuntu
---

### Post by ubnewbie2 on 2008-01-27
I am trying to get my recordings to transcode automatically after recording.  The commercial flagging job is running automatically, but not the transcode job. It doesn't even appear on the job queue.

I know mythtranscode works, because I can schedule the job manually on one of my already recorded programs.  It appears on the job queue and runs properly.

When I schedule a recording in mythweb, the auto-flag and auto-transcode boxes are both ticked, and the medium quality  transcoder is selected.


So, what can I check or do to try and get mythtranscode running automatically?

---

### Post by a_posse_ad_esse on 2008-01-27
Is the option "allow auto transcode jobs" set?  Sometimes things get overlooked or deselected by accident.

---

### Post by ubnewbie2 on 2008-01-27
> **a_posse_ad_esse said:**
> Is the option "allow auto transcode jobs" set?  Sometimes things get overlooked or deselected by accident.

Sometimes mythtv buries settings in strange places.  I found the settings for the default transcode, and to make the auto-transcode setting default to "on", and logically, you'd think that would be enough.

But no, there's another setting, squirreled away in the recording profile, which I think is the one you are referring to.  I found it by googling around earlier tonight, and only just proved it now works.

So thanks, you have confirmed it for me, and I'll mark the thread as solved.

---

