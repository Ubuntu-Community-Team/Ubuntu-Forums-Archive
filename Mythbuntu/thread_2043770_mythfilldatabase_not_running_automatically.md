---
title: "mythfilldatabase not running automatically"
date: 2012-08-17
forum: Mythbuntu
---

### Post by alldunn on 2012-08-17
Hi guys.  I am in need of a little help again.  Mythfilldatabase is not running all of a sudden automatically.  I can run it manually without any issues.  I don't see anything in the mythfilldatabase log at all.  I recently had a problem with my network card where it completely died.  During that time my date/time wasn't able to update and for some reason set itself way ahead (almost a month).  I mention this because the latest entry in the log file is Aug, 31.  I don't know if this has anything to do with mythfill not running or what.  I have looked through the mythbackend log, but don't see anything about mythfill unless I missing something.  I am hoping someone can help point me in the right direction.  I am running Mythbuntu 12.04 and MythTV .25 BTW.
Thanks for any help!

---

### Post by azmyth on 2012-08-20
I ran into the same problem years ago. Not sure if it's the same issue. The problem I had is mythfdb would hang and the process would still be running so myth wouldn't start another process thus in 14 days my guide data would be blank. I can't remember if I could start a manual mfdb process. What I ended up doing was adding cron job to kill mfdb 2 hours past the last hour set for mfdb to run. I figure if it hasn't completed by then it has hung. I'm not sure if it was bug or what but I haven't looked into it since my workaround works. You can just do a 

ps -A | grep mythfilldatabase

to see if it still running.

---

### Post by alldunn on 2012-08-20
It doesn't appear to be running at all.  I just checked the running processes and didn't see it running.  What kicks mythfilldatabase off?  I'm assuming mythbackend, but don't see anything in the backend log regarding mythfill.  If I could see a log of where this process is attempting to run, I could probably troubleshoot it a little easier.

---

### Post by azmyth on 2012-08-23
You set it to kick off in the BE but I can't remember where. You could always trying running a cron job at a certain time for running mythfdb.

---

