---
title: "How do I remove the last x seconds from a video with mencoder?"
date: 2009-05-21
forum: Multimedia Software
---

### Post by Rytron on 2009-05-21
Hi.
How do I remove the last x seconds from a video with mencoder? For example I'd like to remove the last 10 seconds from video.avi.

I do know that this line cuts away the first five seconds of a video:
```
mencoder -o credit1.avi -ss 00:00:05 -ovc copy -oac pcm -af volume=10 video.avi
```

Anyone know?

---

### Post by andrew.46 on 2009-05-21
Hi Rytron,

You could use the '-endpos' option:

> 
-endpos <[[hh:]mm:]ss[.ms]|size[b|kb|mb]> (also see -ss and -sb)

Stop at given time or byte position.
NOTE: Byte position is enabled only for MEncoder and will not be
accurate, as it can only stop at a frame boundary.  When used in
conjunction with -ss option, -endpos time will shift forward  by
seconds specified with -ss.

    EXAMPLE:
      -endpos 56
         Stop at 56 seconds.
      -endpos 01:10:00
         Stop at 1 hour 10 minutes.
      -ss 10 -endpos 56
         Stop at 1 minute 6 seconds.
      -endpos 100mb
         Encode only 100 MB.


All the best,

Andrew

---

### Post by Rytron on 2009-05-22
> **andrew.46 said:**
> Hi Rytron,

You could use the '-endpos' option:



All the best,

Andrew

Thank you andrew.46 AKA Andrew.
):P

---

