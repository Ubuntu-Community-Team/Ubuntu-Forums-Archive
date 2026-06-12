---
title: "help troubleshooting"
date: 2011-05-16
forum: Mythbuntu
---

### Post by itlarson on 2011-05-16
Could anyone help me in figuring out what is wrong with my mythbox?  When I try to play recordings, the front-end sometimes freezes on the first frame.  Other times it will play, but freeze when I try to skip forward or back in the recording.  Occasionally the recording plays normally, but this is the exception.  These are recordings made over a wide period of time, some of which I know played normally in the past. They are spread between two hard-drives, so drive failure can't be the cause. To make things even stranger, I see similar results when I play the recordings directly in VLC. No changes had been made to this machine previous to this happening, and no updates had been installed recently.  Here are a few log excerpts:  

```

2011-05-16 00:55:05.410 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-05-16 00:55:05.421 NVP(0): prebuffering pause
2011-05-16 00:55:06.164 NVP(0): Prebuffer wait timed out 10 times.
2011-05-16 00:55:06.999 NVP(0): Prebuffer wait timed out 20 times.
2011-05-16 00:55:07.833 NVP(0): Prebuffer wait timed out 30 times.
2011-05-16 00:55:08.667 NVP(0): Prebuffer wait timed out 40 times.
2011-05-16 00:55:09.501 NVP(0): Prebuffer wait timed out 50 times.
2011-05-16 00:55:10.335 NVP(0): Prebuffer wait timed out 60 times.
2011-05-16 00:55:11.170 NVP(0): Prebuffer wait timed out 70 times.
2011-05-16 00:55:12.004 NVP(0): Prebuffer wait timed out 80 times.
2011-05-16 00:55:12.175 TV: Attempting to change from WatchingPreRecorded to None
2011-05-16 00:55:12.180 TV: Changing from WatchingPreRecorded to None
2011-05-16 00:55:12.838 NVP(0): Prebuffer wait timed out 90 times.
2011-05-16 00:55:13.672 NVP(0): Prebuffer wait timed out 100 times.
2011-05-16 00:55:13.673 NVP(0), Error: Timed out waiting for prebuffering too long. Exiting..
2011-05-16 00:55:14.507 NVP(0): Prebuffer wait timed out 110 times.
2011-05-16 00:55:14.507 NVP(0), Error: Timed out waiting for prebuffering too long. Exiting..
2011-05-16 00:55:14.507 NVP(0), Error: Video frame buffering failed too many times.
2011-05-16 00:55:15.341 NVP(0): Prebuffer wait timed out 120 times.
2011-05-16 00:55:15.341 NVP(0), Error: Timed out waiting for prebuffering too long. Exiting..
```

Am I wrong to suspect hardware issues?  I think I'll boot a live CD tonight, and see if I can play recordings from there.

---

### Post by itlarson on 2011-05-16
This seems to have fixed itself- mostly, for now at least.  I've got a feeling it will be back, though.  As of a few minutes ago all but two of my recordings are playing normally.  The two that don't play were made right about the time this issue started.  Here's what I got from troubleshooting:

-It's not the drives, because it affects both of them.  
-It's not the OS, because I had the same problem running off a live CD.
-It's not Mythtv because VLC had similar problems.
-It's not the video card, because I network mounted my mythbox's file-system to another computer, and couldn't play many of the recordings from there either.
-It's not the sata cables, because I replaced them with new locking cables.  Also there being two drives should have eliminated this possibility.  I replaced them anyway, since I had the cables.

What this leaves (that I can think of):
-The sata controller on the motherboard could be going bad.  
-Bad RAM, possibly?
-Unspecified generalised weirdness.

So, if this doesn't immediately re-occur as soon I sit down in front of the TV with my supper, (which is how it originally happened), I will do the following tests:
-RAM
-Smartctl long test
-xfs_check (my drives use xfs, which can get cranky sometimes).

PLEASE! if anyone can see anything I missed, or has any input at all, your input is greatly appreciated.

---

### Post by tgm4883 on 2011-05-16
You may want to review this page

[http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause](http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause)

---

