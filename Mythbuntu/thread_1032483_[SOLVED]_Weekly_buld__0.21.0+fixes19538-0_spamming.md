---
title: "[SOLVED] Weekly buld  0.21.0+fixes19538-0 spamming the log file"
date: 2009-01-06
forum: Mythbuntu
---

### Post by ian dobson on 2009-01-06
Hi,

I've just upgraded to  0.21.0+fixes19538-0ubuntu0+mythbuntu2 on my 64bit backend and am now seeing alot of messages about mythcommflag in the log file:-

```

2009-01-06 18:59:43.539 EITHelper: Added 1 events
^H^H^H^H^H^H^H^H^H^H^H  7%/ 88fps^H^H^H^H^H^H^H^H^H^H^H  7%/ 88fps^H^H^H^H^H^H^H^H^H^H^H  7%/ 88fps^H^H^H^H^H^H^H^H^H^H^H  7%/ 87fps^H^H^$
2009-01-06 19:00:08.755 EITHelper: Added 1 events
^H^H^H^H^H^H^H^H^H^H^H  8%/ 86fps2009-01-06 19:00:10.152 EITCache: Wrote 16 modified entries of 244 for channel 32437 to database.
2009-01-06 19:00:10.162 EITCache: Wrote 1 modified entries of 206 for channel 32438 to database.
2009-01-06 19:00:10.181 EITCache: Wrote 27 modified entries of 312 for channel 32439 to database.
2009-01-06 19:00:10.187 EITCache: Wrote 4 modified entries of 192 for channel 32440 to database.
2009-01-06 19:00:10.200 EITCache: Wrote 22 modified entries of 421 for channel 32441 to database.
^H^H^H^H^H^H^H^H^H^H^H  8%/ 85fps2009-01-06 19:00:10.738 EITScanner (5): Now looking for EIT data on multiplex of channel 43001
2009-01-06 19:00:10.741 EITCache: Pruning all entries that ended before UTC 2009-01-05T19:04:33
2009-01-06 19:00:10.748 EITCache: Deleting old cache entries from the database
2009-01-06 19:00:11.560 EITScanner (5): Started passive scan.
2009-01-06 19:00:11.960 EITHelper: Added 1 events
^H^H^H^H^H^H^H^H^H^H^H  8%/ 85fps^H^H^H^H^H^H^H^H^H^H^H  8%/ 86fps2009-01-06 19:00:12.766 EITHelper: Added 1 events
^H^H^H^H^H^H^H^H^H^H^H  8%/ 86fps2009-01-06 19:00:13.570 EITHelper: Added 1 events

```

Looks as if mythcomflag is trying to write to the log file rather than loosing the status information to /dev/null.

Regards
Ian Dobson

---

### Post by ian dobson on 2009-01-07
Hi,

OK found the problem, the setting for mythcommflag command in the settings tables was abit screwed up.

Regards
Ian Dobson

---

