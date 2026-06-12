---
title: "Remote quit working on PVR-150 w/IR port after updates"
date: 2007-12-17
forum: Mythbuntu
---

### Post by michalikt on 2007-12-17
I let my system (gutsy) update last week and now regret it.  I have a PVR-150 with the IR receiver port and my remote no longer works.  Hopefully, they will fix it in the next batch of updates and I'll get a functional remote again.

If anyone could point me to a fix in the meantime, I'd really appreciate it.

From advice in another thread I've tried the following:

> > **axelsvag said:**
> Look in this [HTML][http://ubuntuforums.org/showthread.php?t=590909&highlight=lirc1/HTML]

In that thread, it said:

[QUOTE]I edited the line
DEVICE=""
to
DEVICE="/dev/lirc1"
saved
and restarted lirc.


I tried that but it did not help.  The only lirc item in /dev is lircd.
[/QUOTE]

> > **uopjohnson said:**
> I would start a new thread with this.  You should also update your lirc button mapping by checking the box for that in mcc.

Updating the mapping in MCC did not help.

Ted

---

