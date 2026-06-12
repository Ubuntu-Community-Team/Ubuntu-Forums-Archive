---
title: "What blows the recording schedule"
date: 2009-11-09
forum: Mythbuntu
---

### Post by MonsterMaxx on 2009-11-09
Myth has been working fine.  A week or so I upgraded to 9.10, all seemed to work fine.

Tonight I sat down to watch House and nothing was recorded.  The whole upcoming recording schedule is gone - blank.

All the listing information looks normal, as does Recording Schedules  (Manual, Custom), but the upcoming is blank.

Seems like this happened a few years ago too and I fixed it somehow, but I forge how.

????

---

### Post by nickrout on 2009-11-09
> **MonsterMaxx said:**
> Myth has been working fine.  A week or so I upgraded to 9.10, all seemed to work fine.

Tonight I sat down to watch House and nothing was recorded.  The whole upcoming recording schedule is gone - blank.

All the listing information looks normal, as does Recording Schedules  (Manual, Custom), but the upcoming is blank.

Seems like this happened a few years ago too and I fixed it somehow, but I forge how.

????

probably a corrupt database. try ```
optimize_mythdb.pl
``` 

[http://www.mythtv.org/wiki/Optimize_mythdb.pl](http://www.mythtv.org/wiki/Optimize_mythdb.pl)

Its probably not installed as an executable by default, it'll be here:

```
/usr/share/doc/mythtv-backend/contrib/maintenance/optimize_mythdb.pl
```

---

### Post by MonsterMaxx on 2009-11-09
no joy

---

### Post by nickrout on 2009-11-09
> **MonsterMaxx said:**
> no joy

what sort of messages did you get when you ran that command?

---

### Post by MonsterMaxx on 2009-11-09
no errors, just analyzed then repaired/optimized for each table

running a mythfilldatabase now

---

### Post by alexyz on 2009-11-10
> **MonsterMaxx said:**
> The whole upcoming recording schedule is gone - blank.

Actually you're tuner isn't working, probably just need to reboot.

explained here: [http://ubuntuforums.org/showpost.php?p=8276735&postcount=2](http://ubuntuforums.org/showpost.php?p=8276735&postcount=2)

I had the same idea at first - must be a database problem.  Thankfully I got lucky and saw the above before spending too much time on it.  This strikes me as incredibly brain dead.  Yes, the tuner is gone.  Yes, the recordings will not be done.  But the recording RULEs still exist!  The sensible thing would be for recordings to be in some state like "scheduled but will not record because your tuner is hosed."  Maybe that's difficult to do for some reason.

---

### Post by MonsterMaxx on 2009-11-10
I did a reboot, tuner is fine.

What fixed it was a mythfilldatabase (maybe the combo with an optimize.)  I tried to post that last night but the forum was unresponsive.

Thanks for the assistance.

---

### Post by gwagchunks on 2009-11-10
I have the same problem. At first I thought it was due to using bios wakeup but notice it does it all the time now (expect for restart from the shutdown menu). I found this link after I found my backend log was showing: MySQL server has gone away

[http://www.gossamer-threads.com/lists/mythtv/users/376325](http://www.gossamer-threads.com/lists/mythtv/users/376325)

which then has a link to:

[https://lists.ubuntu.com/archives/ubuntu-server-bugs/2009-February/009799.html](https://lists.ubuntu.com/archives/ubuntu-server-bugs/2009-February/009799.html)

also I found:

[https://bugs.launchpad.net/mythbuntu/+bug/356789](https://bugs.launchpad.net/mythbuntu/+bug/356789)

I'm not sure how to change the mysqld_safe. Need to investigate further.

---

### Post by alexyz on 2009-11-11
gwagchunks:  that problem is with mysql 5.0 and probably fixed in 5.1 (ubuntu 9.10) - so I think a different issue from the OP.

---

