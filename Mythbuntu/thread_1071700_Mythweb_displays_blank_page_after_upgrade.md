---
title: "Mythweb displays blank page after upgrade"
date: 2009-02-16
forum: Mythbuntu
---

### Post by lingenfr on 2009-02-16
Ok, I did two things today. I installed the unstripped ffmpeg libraries and I did the today's upgrade (firefox, etc.). When that was complete, mythtv is working, but mythweb only displays blank pages. Apache is giving me the 'It Works!' page, but nothing comes up with mythweb. No error, just a blank page. As part of installed the unstripped ffmpeg, it removed and reinstalled mytharchive. Any ideas? Thanks.

Update: Looks like it is a bug in php5 [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053)

I followed the work around and got it going again.

---

### Post by lofgren on 2009-02-18
Nice one - thanks :)

---

### Post by CarloMagno on 2009-03-30
Thanks for the info, I didn't know where to look for the solution.
For me the solution posted in
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053/comments/14](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/329053/comments/14)
worked like a charm.
Could be a security risk if there is no other access control?

---

### Post by klc5555 on 2009-03-30
Thanks! I noticed Mythweb in 7.10 suddenly stopped working but I had no clue as to where to track it down.

I wonder if Canonical will push a patch or a backlevel downstream before 7.10's End of Service on April 12th, or just leave it broken.

In the meantime, I guess I'll see whether I can implement the workaround.

Cheers! :)

---

### Post by lingenfr on 2009-03-31
I think that before applying a workaround to a workaround, I would think about a reinstall.

---

