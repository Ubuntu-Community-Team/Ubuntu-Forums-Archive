---
title: "QSqlQuery::exec: empty query and syntax errors"
date: 2008-05-04
forum: Mythbuntu
---

### Post by GordonEndersby on 2008-05-04
Hi guys,

My backend crashed today.
It was picked up by monit and restarted.
This is the mythbackend.log from around that time.
As you can see there are a lot of mysql errors.
"QSqlQuery::exec: empty query" is repeated over hundreds of lines of the log. Then it goes into the syntax errors again repeated over hundreds of lines.
I was out at the time and the box was just sitting there.
No recording scheduled and no other jobs scheduled.
Does anybody know what this is?

2008-05-04 13:00:02.692 adding: mythtv as a client (events: 0)
2008-05-04 13:01:12.733 Reschedule requested for id -1.
2008-05-04 13:01:13.574 Scheduled 77 items in 0.8 = 0.04 match + 0.79 place
QSqlQuery::exec: empty query
QSqlQuery::exec: empty query.....

<< Hundreds of lines the same>>

....QSqlQuery::exec: empty query
QSqlQuery::exec: empty query
QSqlQuery::exec: empty query
QSqlQuery::exec: empty query
222yyyy-22MM-22dd 22hh:22mm:22ss.22zzz DB Error (GetOverlappingPrograms 1):
Query was:
SELECT title,          subtitle,      description,        category,       catego
ry_type,        starttime,      endtime,        subtitletypes+0,audioprop+0,   videoprop+0,        seriesid,       programid,        partnumber,     parttotal,        syndicatedepisodenumber,        airdate,        originalairdate,        previouslyshown FROM program WHERE chanid   = :CHANID AND       manualid = 0       AND       ( ( starttime >= :STIME1 AND starttime <  :ETIME1 ) OR         ( endtime   >  :STIME2 AND endtime   <= :ETIME2 ) )
Driver error was [2/1064]:
QMYSQL3: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':CHANID AND       manualid = 0       AND       ( ( starttime >= :STIME1 AND star' at line 1

<< Hundreds of lines the same till the backend crashes and is restarted by monit.
No other instances for the rest of the day.

Thanks

Gordon

---

### Post by superm1 on 2008-05-04
> **GordonEndersby said:**
> Hi guys,

My backend crashed today.
It was picked up by monit and restarted.
This is the mythbackend.log from around that time.
As you can see there are a lot of mysql errors.
"QSqlQuery::exec: empty query" is repeated over hundreds of lines of the log. Then it goes into the syntax errors again repeated over hundreds of lines.
I was out at the time and the box was just sitting there.
No recording scheduled and no other jobs scheduled.
Does anybody know what this is?

2008-05-04 13:00:02.692 adding: mythtv as a client (events: 0)
2008-05-04 13:01:12.733 Reschedule requested for id -1.
2008-05-04 13:01:13.574 Scheduled 77 items in 0.8 = 0.04 match + 0.79 place
QSqlQuery::exec: empty query
QSqlQuery::exec: empty query.....

<< Hundreds of lines the same>>

....QSqlQuery::exec: empty query
QSqlQuery::exec: empty query
QSqlQuery::exec: empty query
QSqlQuery::exec: empty query
222yyyy-22MM-22dd 22hh:22mm:22ss.22zzz DB Error (GetOverlappingPrograms 1):
Query was:
SELECT title,          subtitle,      description,        category,       catego
ry_type,        starttime,      endtime,        subtitletypes+0,audioprop+0,   videoprop+0,        seriesid,       programid,        partnumber,     parttotal,        syndicatedepisodenumber,        airdate,        originalairdate,        previouslyshown FROM program WHERE chanid   = :CHANID AND       manualid = 0       AND       ( ( starttime >= :STIME1 AND starttime <  :ETIME1 ) OR         ( endtime   >  :STIME2 AND endtime   <= :ETIME2 ) )
Driver error was [2/1064]:
QMYSQL3: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':CHANID AND       manualid = 0       AND       ( ( starttime >= :STIME1 AND star' at line 1

<< Hundreds of lines the same till the backend crashes and is restarted by monit.
No other instances for the rest of the day.

Thanks

Gordon
Sounds like a corrupted SQL table possibly.  Check for consistency in mythweb or phpmyadmin

---

### Post by GordonEndersby on 2008-05-05
All the checkboxes in the database section of mythweb say ok.

Im wondering what would have caused it rather than just fixing the database aferwards. I havnt seen anything like this before.

Does anyone recognise from the queries what process may have been running at the time?

Thanks

Gordon

---

### Post by sjwk on 2008-07-14
Hi Gordon,
Just wondered if you (or anyone else) had come up with a solution to this?  My Mythbuntu box is doing exactly the same thing.  After the backend has been running for a bit, it stops talking to the database until I restart the backend.  It doesn't crash, the frontend doesn't think the backend has gone away - but I can't see any recorded programs in the list or edit any schedules.

The database itself is fine - looking at the output in the logs for the failed queries, it looks as though the backend has stopped expanding macros and passing the macro text to mysql, which unsurprisingly can't parse the query.

For instance, one failure in the logs is for:
```
SELECT DISTINCT chainid FROM tvchain WHERE endtime > :FOURHOURSAGO ;
```
..which fails because mysql hasn't the faintest idea what ':FOURHOURSAGO' is, but knows that it certainly can't be used as a comparison with a date.  I'm assuming that should be expanded into an expression before being sent to mysql?

If it was a database/mysql issue, I wouldn't expect restarting the backend to solve it, but it does - for another day or two.

Anyone got any hints as to where to look?  The machine is all up to date, and the problem is getting a bit irritating.  I've been bouncing back and forth between Myth and Windows Media Center for the past few years and this is the first time that a myth-based solution has had reliability problems that make it as trust-worthy as Media Center... :)

Steve.

---

### Post by kelvinelk on 2009-03-26
I dont believe this is a mysql issue. It is just complaining when it is given duff information. The "FOURHOURSAGO" should be converted in to something that mysql can action i.e. an actual time. This indicates that the problem should lie within the mythtv code.

---

### Post by bewsher on 2009-09-04
Hi All.
 
This error seems to be the same as the on discussed here:
 
[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/330272](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/330272)
 
At the time of posting this, they have not found a solution yet. But it seems to be related to EIT in 0.21 (they think it's fixed in 0.22, but noone knows what is actually causing it, and it's not, as yet, been tested.)
 
Which is a pain as I'm having the same problems. A google search for:
 
```
222yyyy-22MM-22dd 22hh:22mm:22ss.22zzz
```
 
Is how I got to both that page and this one. 
 
If I find anything more out, I'll let you know.
 
Adam

---

