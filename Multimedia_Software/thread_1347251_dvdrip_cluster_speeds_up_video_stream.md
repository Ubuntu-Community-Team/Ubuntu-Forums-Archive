---
title: "dvd::rip cluster speeds up video stream"
date: 2009-12-06
forum: Multimedia Software
---

### Post by KiLaHuRtZ on 2009-12-06
So when I encode a video normally, everything is fine.  When I do it in cluster mode the resulting video stream has been sped up.  At first I thought this was an a/v sync issue, but then I realized my overall playback was shortened.  The audio is fine (normal timestamp), the video moves to fast (faster timestamp than it should be).  I figured this is a transcode issue since in cluster mode, it encodes the audio and video independently.  Just wanted to know if anyone else has had this happen and if so how to correct it.

---

### Post by paulisdead on 2009-12-06
Wow, I had that problem years ago when I used to run gentoo, and they've still not fixed it.  It's because  you can't turn on the "Use PSU Core" option in cluster mode.
[http://www.exit1.org/dvdrip/doc/concepts.cipp#concept_psu_core](http://www.exit1.org/dvdrip/doc/concepts.cipp#concept_psu_core)
[quote=DVD::RIP]5.11 PSU core
	[ Content ] [ Top ]

The PSU core is a transcode mode, which applies a special handling for movies consisting of several PSU's. PSU stands for Program Stream Unit, and is a DVD internal concept of dividing the video stream into independent parts.

With NTSC sources (and also some PAL movies) these PSU's may cause serious A/V synchronization issues, which the PSU core mode tries to solve (for NTSC movies dvd::rip switches PSU core by default on). This works for most movies. If you can't get proper A/V sync with your movie (even with PSU core enabled), please contact the transcode developers and provide sample material.

dvd::rip enables the PSU core by default for NTSC titles, which have more than one PSU. You can't use the cluster mode or fast frame range transcoding with it. [/quote]
So that's always made the cluster mode kind of useless to me, since it never syncs up correctly.  If you must use the cluster, maybe you could adjust the frames per second with avidemux or something.  I swear that must have been like 4-5 years ago I messed with this, can't believe they still haven't fixed it.

---

### Post by KiLaHuRtZ on 2009-12-06
Thanks, I have seen that before.  I guess my next question is; is it possible to cluster encode a title with only one PSU?  As it stands, I can do a 1.5 hour video in 3-3.5 hours on one machine or, with the CPU time I have available, 30 minutes across my cluster.

---

