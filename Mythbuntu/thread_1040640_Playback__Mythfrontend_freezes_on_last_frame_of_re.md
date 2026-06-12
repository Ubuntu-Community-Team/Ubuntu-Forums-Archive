---
title: "Playback / Mythfrontend freezes on last frame of recordings."
date: 2009-01-15
forum: Mythbuntu
---

### Post by mtgregor on 2009-01-15
I've been experiencing an issue with Playback / Mythfrontend freezing on the last frame of a recording. Not sure if this is coincidental to my recent upgrade to 8.10 or not. I've briefly looked through the logs but haven't noticed anything yet.

Has anyone else experienced this issue before?

---

### Post by egandy on 2009-01-16
I have the same problem on 8.04.  It is usually happens when I am watching a show that is also being com. flagged at the same time.  Shows that I record on channels with weak signal also act up.  Letting the show finish playing to the end with out fast forwarding the last minute eliminates most of the freezing for me.  My problems are worse when I have it set to com flag more than 1 show at a time or if I set the job cpu setting higher than low.

---

### Post by mtgregor on 2009-01-18
Update: Once the system freezes, I notice in the System Monitor that the mythfrontend process is waiting for "hrtimer_nanosleep". Not sure if that piece of information is of any use for anyone that could help me?



My mythfrontend.log has the following entries that I believe align with the time the system was frozen before I ended the mythfrontend process.

```
2009-01-18 18:47:50.393 Video sync method can't support double framerate (refresh rate too low for bob deint)
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 1280 x 720
2009-01-18 18:47:50.395 Video timing method: USleep with busy wait
2009-01-18 18:47:52.116 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:47:53.066 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:47:54.826 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:47:58.146 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:00.257 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:01.071 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:01.902 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:02.772 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:03.642 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:06.310 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:10.701 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:12.288 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:13.768 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:14.795 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:16.473 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:18.899 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:19.732 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:21.185 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:22.179 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:23.621 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:24.396 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:30.406 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:31.379 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:32.350 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:35.124 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:37.459 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:38.689 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:40.328 NVP: Prebuffer wait timed out 10 times.
2009-01-18 18:48:41.126 couldn't find base dialog
2009-01-18 18:48:41.215 DPMS Reactivated.
```

---

