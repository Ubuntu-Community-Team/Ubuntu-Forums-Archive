---
title: "Video Stuttering all of a sudden"
date: 2010-06-18
forum: Multimedia Software
---

### Post by hansoffate on 2010-06-18
All of a sudden, my HTPC started stuttering from one day working fine to the next skipping about 5 times a minute.  I haven't installed any new programs or services, let alone update my system.  

Here is some pertinent info.  Let me know if you need to know anything else.
Linux grunt 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686

  System load: 2.25                Memory usage: 51%   Processes:       200
  Usage of /:  93.0% of 681.77GB   Swap usage:   0%    Users logged in: 1

cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
stepping        : 13
cpu MHz         : 2200.000
cache size      : 2048 KB


Free -mt while playing video
hansoffate@grunt:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:          2012       1962         50          0         17       1366
-/+ buffers/cache:        577       1435
Swap:         5895         33       5862
Total:        7908       1995       5913

This system was working fine playing HD content, but now it can barely play SD content. I tried restarting my system and my media server, but there seems to be no change in playback. I also tried disabling some unnecessary services, but I'm not exactly sure which one are superfluous.  

Any ideas on how to resolve this issue?

Thanks,
-Hans

---

### Post by hansoffate on 2010-06-21
After troubleshooting around with this more, I noticed that it only stutters for HD content playback.  It stutters during MKV on the computer HD or from the network and occasionally for MythTV HD recordings.

I'm starting to think this may be a RAM issue.

Any Suggestions?
-Hans

::RESOLVED::  I installed XFCE and started using it instead of GNOME.  Now everything seems to be playing fine.

---

