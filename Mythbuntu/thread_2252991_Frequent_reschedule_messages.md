---
title: "Frequent reschedule messages"
date: 2014-11-16
forum: Mythbuntu
---

### Post by Adam_Jacobs on 2014-11-16
I've noticed recently that my mythbackend log is getting very frequent messages about rescheduling. Here is a typical extract:

```
Nov 16 09:15:52 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 1 0 2014-11-16T11:25:00Z EITScanner
Nov 16 09:15:53 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 196 items in 0.8 = 0.44 match + 0.00 check + 0.35 place
Nov 16 09:17:54 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 1 0 2014-11-16T13:00:00Z EITScanner
Nov 16 09:17:55 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 196 items in 0.8 = 0.45 match + 0.01 check + 0.35 place
Nov 16 09:18:37 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 1 0 2014-11-16T09:45:00Z EITScanner
Nov 16 09:18:38 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 196 items in 0.8 = 0.45 match + 0.00 check + 0.36 place
Nov 16 09:20:13 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 1 0 2014-11-16T09:45:00Z EITScanner
Nov 16 09:20:14 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 196 items in 0.8 = 0.45 match + 0.00 check + 0.35 place
Nov 16 09:23:17 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 1 0 2014-11-16T10:00:00Z EITScanner
Nov 16 09:23:18 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 196 items in 0.8 = 0.45 match + 0.00 check + 0.35 place
Nov 16 09:23:32 htpc mythbackend: mythbackend[2291]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 60.0 GB w/freq: 15 min
Nov 16 09:24:03 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 1 0 2014-11-16T09:35:00Z EITScanner
Nov 16 09:24:04 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 196 items in 0.8 = 0.45 match + 0.00 check + 0.35 place
Nov 16 09:26:13 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 1 0 2014-11-16T11:50:00Z EITScanner
Nov 16 09:26:14 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 196 items in 0.8 = 0.44 match + 0.00 check + 0.35 place
Nov 16 09:28:41 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 1 0 2014-11-16T11:25:00Z EITScanner
Nov 16 09:28:41 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 196 items in 0.8 = 0.45 match + 0.00 check + 0.36 place
Nov 16 09:29:30 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 1 0 2014-11-16T12:30:00Z EITScanner
Nov 16 09:29:31 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 196 items in 0.8 = 0.44 match + 0.01 check + 0.36 place
Nov 16 09:31:06 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 1 0 2014-11-16T10:15:00Z EITScanner
Nov 16 09:31:07 htpc mythbackend: mythbackend[2291]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 196 items in 0.8 = 0.46 match + 0.00 check + 0.35 place
```

I'm sure it never used to do that, or at least not do it anything like as frequently.

Is this normal behaviour, or does it point to some sort of a problem? Using MythTV 0.27 on Ubuntu 14.04.

Many thanks

Adam

---

### Post by khPWXxF on 2014-11-16
Mine is similar - a pair of reschedules every two or three minutes. 
```
grep 'Reschedule' mythbackend.log | wc -l
```
reports 3901 reschedules since 2nd November.
That database is busy!

Phil

---

### Post by Adam_Jacobs on 2014-11-22
Hm. So either it's normal behaviour or we both have a problem. Anyone know which?

---

### Post by Lester_Burnham on 2014-11-22
Hi,

I have seeing similar things, plus database errors with EIT in Australia only on the channel 7 multiplex.

```
grep 'Reschedule' mythbackend.log | wc -l
```
2863 since November 13

Now the database errors
```
grep 'DB Error' mythbackend.log | wc -l
```
9418 since November 13
> Nov 23 09:05:45 server152 mythbackend: mythbackend[7506]: E EIT mythdb.cpp:183 (DBError) DB Error (programrating insert):#012Query was:#012INSERT INTO programrating        ( chanid, starttime, system, rating) VALUES (?, ?,    ?,  ?)#012Bindings were:#012:CHANID=1073, :RATING="PG", :START=2014-11-22T22:30:40Z, :SYS=""#012Driver error was [2/1062]:#012QMYSQL3: Unable to execute statement#012Database error was:#012Duplicate entry '1073-2014-11-22 22:30:40--PG' for key 'chanid'
Nov 23 09:05:46 server152 mythbackend: mythbackend[7506]: E EIT mythdb.cpp:183 (DBError) DB Error (programrating insert):#012Query was:#012INSERT INTO programrating        ( chanid, starttime, system, rating) VALUES (?, ?,    ?,  ?)#012Bindings were:#012:CHANID=1073, :RATING="PG", :START=2014-11-22T21:58:10Z, :SYS=""#012Driver error was [2/1062]:#012QMYSQL3: Unable to execute statement#012Database error was:#012Duplicate entry '1073-2014-11-22 21:58:10--PG' for key 'chanid'
Nov 23 09:08:33 server152 mythbackend: mythbackend[7506]: E EIT mythdb.cpp:183 (DBError) DB Error (programrating insert):#012Query was:#012INSERT INTO programrating        ( chanid, starttime, system, rating) VALUES (?, ?,    ?,  ?)#012Bindings were:#012:CHANID=1072, :RATING="PG", :START=2014-11-22T22:08:30Z, :SYS=""#012Driver error was [2/1062]:#012QMYSQL3: Unable to execute statement#012Database error was:#012Duplicate entry '1072-2014-11-22 22:08:30--PG' for key 'chanid'
Nov 23 09:08:34 server152 mythbackend: mythbackend[7506]: E EIT mythdb.cpp:183 (DBError) DB Error (programrating insert):#012Query was:#012INSERT INTO programrating        ( chanid, starttime, system, rating) VALUES (?, ?,    ?,  ?)#012Bindings were:#012:CHANID=1072, :RATING="PG (A)", :START=2014-11-22T22:41:00Z, :SYS=""#012Driver error was [2/1062]:#012QMYSQL3: Unable to execute statement#012Database error was:#012Duplicate entry '1072-2014-11-22 22:41:00--PG (A)' for key 'chanid'


When I get a chance, I might delete all channel 7 multiplex's and re-scan. But I did see a few old bug with reports with similar errors.
Anyone else seeing these errors?
It looks like channel 7 are using place holders until they have the correct data.
( chanid, starttime, system, rating) VALUES (?, ?,    ?,  ?)

mythbackend --version
Please attach all output as a file in bug reports.
MythTV Version : v0.27.4-19-g65d92fd
MythTV Branch : fixes/0.27
Network Protocol : 77
Library API : 0.27.20141016-1
QT Version : 4.8.6

Lester

---

