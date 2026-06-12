---
title: "[SOLVED] No guide data in mythweb"
date: 2008-07-17
forum: Mythbuntu
---

### Post by Levander on 2008-07-17
Am I the only one who can view guide data fine in mythfrontend, but nothing shows up in mythweb?  

The last date was July 9 (about) that I could view guide data for in mythweb.  July 10 (about) guide data just never showed up in mythweb.  

I am running Gutsy and have dist-upgraded to 0.21 (still in Gutsy).  This problem started before I dist-upgraded.

---

### Post by Levander on 2008-07-18
I finally found out what my problem is by finding this very old post:

[http://www.mail-archive.com/mythtv-users@mythtv.org/msg23934.html](http://www.mail-archive.com/mythtv-users@mythtv.org/msg23934.html)

Funny that 3 years later, that bug is still in mythweb.

I was getting my listings for free using zap2xml.  When I finally decided screw it, I just fork over the $20, I added Schedules Direct without removing my zap2xml video source or the zap2xml channels.  Going back and deleting the zap2xml video source and channels using mythtv-setup, the mythweb program guide now works.

If I weren't lazy, I'd figure out how to report this as a bug for mythweb.  Maybe I'll do that in the next couple of days?

---

