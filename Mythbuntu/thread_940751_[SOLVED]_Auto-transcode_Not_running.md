---
title: "[SOLVED] Auto-transcode Not running"
date: 2008-10-07
forum: Mythbuntu
---

### Post by Eric Boring on 2008-10-07
My friends,

I have searched the forums, but not found any magic incantations to help solve this problem. I have set the backend to allow auto-transcoding, set up transcoding profiles, and set my recording schedules to auto-transcode. I know that transcoding works because I have scheduled transcoding jobs manually through mythweb and the run.

But my new recordings refuse to put the transcoding job into the job queue.

There are a few threads about this, reminding to check settings in the backend (General Settings) and on the Front End (Recording Profiles). I've done both, but still no luck.

Any suggestions?

Thanks,

-Josh

---

### Post by Eric Boring on 2008-10-08
I think this may be one of the great mysteries of the myth, but I thought I'd bump it once or twice just in case....

Edit: I guess this is a bug. [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/238052](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/238052)
Bummer.

---

### Post by Ronno6 on 2008-10-08
I sympathize with your plight..........I have the same situation with my Audio Buffer Overflow and playback speed problem (I think they're related.)I get no suggestions there,either. 

I've set up auto commercial flagging and transcoding as per normal methods and they run normally. 

Your jobs do not even show in the queue? If they show but do not run, that's one problem. If they don't even make into the queue, that's gotta be something deeper.

---

### Post by Eric Boring on 2008-10-13
What's that emoticon for banging your head against the wall? I need that one! 

I stumbled across another checkbox for enabling auto-transcode jobs:

from the frontent:

Utilities/Setup > Setup > TV Settings > Recording Profiles > MPEG 2 Encoders.

I think the last option will depend on your capture card. What threw me off was that I always went to the second option on the last page (Transcoders), since I wanted to transcode.

At any rate, for anyone else struggling with this, I think there are three places you need to enable automatic transcoding:

[LIST]
[*]mythtv-setup (in the backend settings)
[*]mythfrontend > Setup > Setup> TV Settings > Recording Profiles > MPEG2 Encoders
[*]when you schedule the recording itself. 
[/LIST]

Hope that helps someone. 

-Josh

---

