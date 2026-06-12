---
title: "Control centre backup settings / schedule."
date: 2014-02-25
forum: Mythbuntu
---

### Post by roburk on 2014-02-25
Hi
 
I have been using the mythbuntu control center to back up my mythtv, but I have just realised that the database has not been backed up for some reason. Looking at the backup files I can see that the “mythconverg-<date>.sql” script is of zero bytes.
I have since manually backed up(!)
 
Anyway, this all lead me to try and see why this is happening, but I can’t find anything on where mythbuntu CC stores any of its settings or its schedule.

Does anyone know? I have looked in the database and can’t find anything in there. The crontab is empty for this host so it does not appear to be in there either, I’m stumped!

If I can't sort out why it is not working for me then I'll switch to a far more manual method and use the local cron, but first I will want to cancel the existing, non-working backup schedule. How would I do this?

Many thanks

Rob

---

