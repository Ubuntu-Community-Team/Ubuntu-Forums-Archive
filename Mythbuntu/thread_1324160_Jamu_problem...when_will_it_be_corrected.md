---
title: "Jamu problem...when will it be corrected?"
date: 2009-11-12
forum: Mythbuntu
---

### Post by williammanda on 2009-11-12
I ran into a problem where the videos would not play after they had metadata after a day or so. I found out that there was an issue with jamu that was causing this. I had to remove the cron files so that jamu would not run again  and reset the metadata for the videos. See this post for more details:

[http://ubuntuforums.org/showthread.php?t=1318635]("http://ubuntuforums.org/showthread.php?t=1318635")

Since I removed the cron files will this effect the recordings as well? Is there a fix in the works?
Thanks

---

### Post by ian dobson on 2009-11-12
Hi

As you've disabled the cron scripts that call jamu, jamu shouldn't run and so you shouldn't have any problems.

As the problem is known I'd imagine that someone is working on it and there will be a solution sometime. I've not looked at the problem but I imagine the problem is a changed database structure/colums in the metadata table.

Regards
Ian Dobson

---

