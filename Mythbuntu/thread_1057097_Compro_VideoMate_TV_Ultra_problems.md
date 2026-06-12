---
title: "Compro VideoMate TV Ultra problems"
date: 2009-02-01
forum: Mythbuntu
---

### Post by adambomb42x on 2009-02-01
Please forgive my linux noobness. I'm running Mythbuntu 8.10 with a Compro VideoMate TV Ultra and am unable to get the video capture working properly. What linux thinks is the s-video input is really the coax and in MythTV the TV video is scrambled (see attachment). I was testing with TVtime and I get a picture on that but on s-video while the only cable that is plugged in is the coax.

Please help. I'm trying to get this working before the Superbowl tonight, because my mother is in Faith Hill's backup choir and would like to record the event.

---

### Post by adambomb42x on 2009-02-01
I just reinstalled Mythbuntu and was able to scan cable channels, but now I just get a black screen when trying to watch TV.
Here is what was in the logs.
```
==> /var/log/mythtv/mtd.log <==
mtd started at Sun Feb 1 16:15:20 2009
mtd is running on a host called mythbox
16:15:20: Waiting for connections/jobs
16:15:20: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2009-02-01 16:55:09.332 NVR(/dev/video0) Error: Resetting and re-queueing
2009-02-01 16:55:10.316 NVR(/dev/video0) Error: DQBUF ioctl failed.
			eno: Input/output error (5)
```

---

### Post by adambomb42x on 2009-02-01
After running the updates I found that I can no longer scan the channels.

Edit: It's back to the s-video is really the coax after updating.

---

### Post by adambomb42x on 2009-02-02
Bump

---

### Post by adambomb42x on 2009-02-03
bump

---

