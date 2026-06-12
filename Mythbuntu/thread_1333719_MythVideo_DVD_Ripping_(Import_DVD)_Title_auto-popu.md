---
title: "MythVideo DVD Ripping (Import DVD) Title auto-populate"
date: 2009-11-21
forum: Mythbuntu
---

### Post by pcooley on 2009-11-21
I've recently upgraded to Mythbuntu 9.10.  I recall (maybe incorrectly) that with Mythbuntu 9.04 when the RIP/Transcode menu was displayed it had autofetched the Title of the DVD.

Any advice on how to regain this functionality?

Paul

---

### Post by kratz13 on 2009-11-21
I'm new to this, but is am also wondering about this. When looking at the desktop after exiting the frontend, I can see the title of the CD... Example Hot_Fuzz, but when trying to rip, it shows Unknown.

Chris

---

### Post by dewmanstl on 2009-12-28
I am having the same issue. Any takers??

---

### Post by dannysauer on 2010-01-10
I recall being annoyed at this change (I think it broke in either Intrepid or Jaunty) as well, but I'm not sure what causes it. :)  I just hooked a keyboard up. :/

---

### Post by jquintana on 2010-01-13
So there is no fix for this?

---

### Post by myth1914 on 2010-01-19
I noticed this as well, and after hours of searching, I resorted to importing with other software.

Another potential related issue, when ripping a DVD (legally of coarse) with the "unknown" title as anything other than iso, transcode hangs.  Is anyone else experiencing this?

---

### Post by dannysauer on 2010-01-20
Yes - I've been unable to rip anything for months.  I even have several DVDs (that I own) which I've first run though DVDFab on Windows to remove the CSS stuff, and myth's even unable to rip and transcode those.  Sometimes it will rip the whole DVD, but hang up about halfway through (when it's done with the DVD and before starting to transcode).

---

### Post by dannysauer on 2010-01-20
As it turns out, transcode is working.  I fire up top via an ssh session, and trascode is taking up all the CPU.  After a while, it looke like it failed - but actually, the transcode process has created the .avi I expected.  The progress bar just doesn't update.  Coincidentally, I don't seem to be getting a log file created.  The user running the process has permission to write to the /var/log/mythtv directory as well as the temporary location, but there is no "mtd.log" anywhere on the system.

---

