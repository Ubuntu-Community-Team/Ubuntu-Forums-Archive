---
title: "frontend freezes"
date: 2011-07-18
forum: Mythbuntu
---

### Post by itlarson on 2011-07-18
My frontend has started freezing, either when the recording starts, or when I try to skip ahead.  I think this snippet from the frontend log may be the crux of it:

Table './mythconverg/recordedseek' is marked as crashed and last (automatic?) repair failed

Is there a safe way to fix this, or should I restore the most recent database backup from before the problem started?  Recordings play perfectly in smplayer using vdpau.

---

### Post by itlarson on 2011-07-18
Nevermind- in my "notes" file I found the following:

mysqlcheck -u mythtv -p<password> --repair mythconverg

I haven't needed to do that since .21, and had forgotten about it.  If anyone else has the same problem-  substitute your database password for <password>.  You can find it in the frontend settings.  You don't need to be root.

---

