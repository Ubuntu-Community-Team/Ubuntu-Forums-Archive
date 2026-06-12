---
title: "Mythtv: &quot;Couldn't open file abort.dat&quot;"
date: 2010-04-21
forum: Multimedia Software
---

### Post by Kepesk on 2010-04-21
I've had some problems with MythTV recently, and I realized that this was because my hard drive was full.  I traced the problem to my mythbackend.log files, which were several gigabytes in size.  The weird thing is that the log files are filling with this:

```
2010-04-21 07:47:28.661 Failed to decode frame.  Position was: 0
2010-04-21 07:47:28.916 Couldn't open file abort.dat
2010-04-21 07:47:29.170 Failed to decode frame.  Position was: 0
2010-04-21 07:47:29.414 Couldn't open file abort.dat
2010-04-21 07:47:29.593 Failed to decode frame.  Position was: 0
2010-04-21 07:47:29.852 Couldn't open file abort.dat
```

I did some research, and this issue appears to normally be associated with commercial flagging problems.  However, my commercial flagging jobs all appear to be running normally, and the log fills with this junk even when there are no jobs in the queue and mythcommflag isn't running.  To make matters worse, this is difficult to troubleshoot because there is no abort.dat file anywhere on my system.  I can see this possibly being a permissions problem with the directory that abort.dat is supposed to be, but I have no clue where that is.

Has anyone out there experienced this problem, or can anyone at least tell me where abort.dat is normally found?

Thanks!

---

### Post by Kepesk on 2010-05-22
I have new information on this one:

I've discovered that mythtranscode is causing this.  I can fix it by killing all mythtranscode jobs and deleting the affected video file and the outrageously large log files.  However, it just starts happening again after a couple of days.  The recordings it occurs on seem to be random; I can't make heads or tails of it, and I'm tired of losing videos to this bug.

Also, I upgraded MythTV to the latest 0.23 fixes, but this still occurs.

Can anyone at least point me in the right direction?

Thanks!

---

