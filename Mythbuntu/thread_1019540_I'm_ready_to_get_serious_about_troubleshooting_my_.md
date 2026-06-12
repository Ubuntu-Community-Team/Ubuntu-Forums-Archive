---
title: "I'm ready to get serious about troubleshooting my playback issues."
date: 2008-12-23
forum: Mythbuntu
---

### Post by whosmatt on 2008-12-23
I'm honing in on the right settings for smooth and relatively synchronized HD tv playback, but one thing still causes me trouble, and I have a perfect example of it.  Last night, while watching *Charlie and the Chocolate Factory* on ABC, my video just "froze" and I had to exit (esc) to the menu.

Here is the frontend log at that exact moment:

```

2008-12-22 22:16:36.392 RingBuf(/var/lib/livetv/1111_20081222220747.mpg): Waited 8.0 seconds for data to become available...
2008-12-22 22:16:37.684 Checking to see if there's a new livetv program to switch to..
2008-12-22 22:16:37.686 WriteAudio: buffer underrun
2008-12-22 22:16:38.357 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:44.436 RingBuf(/var/lib/livetv/1111_20081222220747.mpg) Error: Waited 16 seconds for data, aborting.
2008-12-22 22:16:48.602 [mpeg2video @ 0x7f175b14be90]Warning MVs not available
2008-12-22 22:16:48.697 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:49.381 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:50.048 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:50.715 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:51.382 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:52.066 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:52.766 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:53.433 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:54.100 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:54.767 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:55.451 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:56.118 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:56.785 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:57.453 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:58.120 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:58.787 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:16:59.454 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:00.121 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:00.788 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:01.455 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:02.122 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:02.789 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:03.457 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:04.124 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:04.791 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:05.458 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:06.125 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:06.809 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:07.509 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:08.176 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:08.843 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:09.511 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:10.178 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:10.845 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:11.512 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:12.179 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:12.846 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:13.513 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:14.180 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:14.847 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:15.515 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:16.182 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:16.865 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:17.533 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:18.200 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:18.867 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:19.534 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:20.201 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:20.858 TV: Attempting to change from WatchingLiveTV to None
2008-12-22 22:17:20.881 NVP: Prebuffer wait timed out 10 times.
2008-12-22 22:17:20.986 ~OpenGLVideoSync() -- begin
2008-12-22 22:17:20.986 ~OpenGLVideoSync() -- middle
2008-12-22 22:17:20.986 ~OpenGLVideoSync() -- end
2008-12-22 22:17:21.251 TV: Changing from WatchingLiveTV to None
2008-12-22 22:17:21.308 DPMS Reactivated.
2008-12-23 03:43:16.708 Received a remote 'Clear Cache' request

```

Mythbuntu 8.10 x64
Hardware specs:

Dell Dimension 8400
P4 3.0 GHz, HT enabled
1.25 GB RAM
80GB SATA drive formatted ext3 mounted as / (also contains swap)
500GB SATA drive formatted ext3 mounted as /var/lib/mythtv
pcHDTV 5500
Hauppauge PVR-150
PCIe Nvidia 7300LE
Using on-board audio.

I also should mention that /var/lib/livetv (which, as you may have guessed is where i keep my live tv recordings) is on the 80GB drive.

I'm guessing by looking at the log file that it might be a drive issue, but specifically what?  Other times when this happens I do nothing and playback resumes shortly.  It doesn't happen all the time, and often it doesn't happen at all.

---

### Post by 4dognight on 2008-12-23
in a terminal, try running vmstat 2, and look to see if your CPU is maxing out. You can also look to see if the IOwait is giving you problems. If your myth box is also a Backend. it could be some of the other processes running periodocally bumping your disk IO or CPU up.

---

### Post by whosmatt on 2008-12-23
> **4dognight said:**
> in a terminal, try running vmstat 2, and look to see if your CPU is maxing out. You can also look to see if the IOwait is giving you problems. If your myth box is also a Backend. it could be some of the other processes running periodocally bumping your disk IO or CPU up.

Def not CPU; I had a look via htop while it was happening.  Didn't look at disk i/o though.  Will do next time it happens.

---

### Post by newlinux on 2008-12-23
does it only happen with livetv? Does it only happen with HD or SD playback?

---

### Post by whosmatt on 2008-12-24
> **newlinux said:**
> does it only happen with livetv? Does it only happen with HD or SD playback?

It only happens on live tv, and I have only noticed it on hd content, but I almost never watch anything but Hd sports live, so that may not help much.

---

### Post by newlinux on 2008-12-24
If it only happens with livetv, I'd definitely look into disk issues next time it happens... Since you are using ext3 I would turn on the "delete files slowly" option in the backend, and maybe consider using a faster filesystem like xfs.

---

### Post by jaakan on 2008-12-25
Sounds like the I/O across the Motherboard might be the issue, since LiveTV buffers to the Harddrive and plays back what is currently being buffered with a delay.

---

### Post by whosmatt on 2008-12-25
> **newlinux said:**
> If it only happens with livetv, I'd definitely look into disk issues next time it happens... Since you are using ext3 I would turn on the "delete files slowly" option in the backend, and maybe consider using a faster filesystem like xfs.

Yeah; I assume that each session of live tv corresponds to an mpg file and that deleting happens as needed while watching tv.  In that case (assuming that I don't want to change anything else about my system) would the "delete files slowly" option help?  I don't remember right now if I have that set or not, and I'm not at home to troubleshoot.

Alternately, I suppose I could back up and restore my secondary drive as xfs and have live tv record to that drive instead; i have it going to my / drive now just to make better use of that extra ~60GB.  I also have a ton of space on my freenas server but so far just using that for static video and audio content.

-M

---

