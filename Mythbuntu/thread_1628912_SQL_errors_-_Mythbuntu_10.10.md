---
title: "SQL errors - Mythbuntu 10.10"
date: 2010-11-23
forum: Mythbuntu
---

### Post by lsheaves on 2010-11-23
Hi All,

Frontend errors... I am seeing the following adnausium in the frontend log..

2010-11-23 22:22:54.861 DB Error (MarkAsInUse -- select):
Query was:
SELECT count(*) FROM inuseprograms WHERE chanid   = :CHANID   AND starttime = :STARTTIME AND       hostname = :HOST                                                         NAME AND recusage  = :RECUSAGE
Bindings were:
:CHANID=1024, :HOSTNAME=backend, :RECUSAGE=player,
:STARTTIME=2010-11-23T22:22:00
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right                                                          syntax to use near ':CHANID   AND starttime = :STARTTIME AND       hostname = :HOSTNAME AND recusage' at line 1

2010-11-23 22:22:54.895 Error preparing query: SELECT count(*) FROM inuseprograms WHERE chanid   = :CHANID   AND st                                                         arttime = :STARTTIME AND       hostname = :HOSTNAME AND recusage  = :RECUSAGE
2010-11-23 22:22:54.896 Driver error was [2/144]:
QMYSQL3: Unable to prepare statement
Database error was:
Table './mythconverg/inuseprograms' is marked as crashed and last (automatic?) repair failed

Does anyone have any suggestions on repair?

Thanks

---

### Post by geoffp on 2012-03-04
I just started seeing this, and am baffled as well. I've repaired all my tables as best I know how with mysqlrepair.

When that didn't work, I dropped the inuseprograms table and re-created it, but the mythfrontend log still claims that the table is marked as crashed, and that the last repair failed, which can't be right, so I give up.

---

### Post by nickrout on 2012-03-04
Restore your database from the last good backup. The backup and restore functions are well documented in the wiki.

---

