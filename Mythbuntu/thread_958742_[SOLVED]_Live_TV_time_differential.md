---
title: "[SOLVED] Live TV time differential"
date: 2008-10-25
forum: Mythbuntu
---

### Post by uncle hammy on 2008-10-25
I have something that is occurring on only one of my front ends.  About 3 weeks ago, I noticed that when I start Live TV, info showed a 30 second time differential immediately (i.e. 00:01 of 00:31), rather than the typical 3 second differential.  

Now, it's up to a 50 second differential immediately when starting Live TV (i.e. 00:01 of 00:51).  So, the spread seems o be growing.

Any ideas what might be causing this?  It doesn't seem to effect anything, I'm more curious.

Thanks,
Scott

---

### Post by uncle hammy on 2008-10-25
I found out what was going on.  Apparently when I set up my frontend only machine, NTP was not part of the installation, and the clock was slwoly drifting from my backend server.

ntpdate brought it back into line, and I installed ntp, so hopefully I should be good.

---

