---
title: "no grabber=run xmltv configure???"
date: 2010-01-28
forum: Mythbuntu
---

### Post by linuxhippy on 2010-01-28
I'm trying to set up mythbuntu 9.10 with an external DVD player on an S-video cable in video source setup (backend).  I choose "no grabber" as the listing grabber "default" as the channel frequency table and then cannot save these entries but am met with:

Run xmltv configure command

I try doing sudo xmltv configure and am told command not found.  What is this?

---

### Post by SiHa on 2010-01-29
Sounds like it might be [[COLOR="Blue"]_this_[/COLOR]](https://bugs.launchpad.net/mythbuntu/+bug/452468) bug.

Do you get the "run xmltv configure" when you are trying to move the selector down to the bottom - Back/Next/Finish?
If so, keep trying and it will eventually move!

---

### Post by linuxhippy on 2010-01-29
that's exactly what happens...it just doesn't do that when you specify Schedules Direct.  My free trial ends with them today too-I hope I can watch TV tomorrow without accessing their database.

---

### Post by linuxhippy on 2010-01-29
That worked...I just hit TAB many times till it let me finish.  Thanks!

---

### Post by SiHa on 2010-01-29
Glad it's sorted!
> **linuxhippy said:**
> I hope I can watch TV tomorrow without accessing their database.

Should be able to for as long as you have data in your EPG, you just won't get anything new. Even then though, you should still be able to watch TV, but the EPG will show 'Unknown' for everything, and you won't be able to schedule recordings except manually.

---

### Post by linuxhippy on 2010-01-29
actually I cannot find any shows but a few on Schedules Direct.  I record everything manually.  If the service could find shows for me like 24 and Lost I would gladly subscribe to it.  Can you find shows on Schedules Direct?

---

