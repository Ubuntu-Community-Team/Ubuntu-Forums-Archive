---
title: "Mythtv: No scheduled recordings"
date: 2013-04-05
forum: Mythbuntu
---

### Post by itlarson on 2013-04-05
I have stored recordings, recording rules,  a schedule, and space in home and root.  But  mythtv shows no upcoming recordings-  and any new recordings I make don't show up.  What's going on?

I have run out of root space recently,  but I freed up more with "sudo apt-get clean"

---

### Post by itlarson on 2013-04-06
I did some more digging this morning and managed to find a solution.  looking in /var/log/mythtv/mythbackend.log I found:

Apr  6 10:16:15 itlmyth mythbackend[4211]: E Scheduler mythdbcon.cpp:825 (prepare) Driver error was [2/144]:#012QMYSQL3: Unable to prepare statement#012Database error was:#012Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed
Apr  6 10:16:15 itlmyth mythbackend[4211]: E Scheduler mythdb.cpp:192 (DBError) DB Error (AddNotListed):#012Query was:#012SELECT record.title,       record.subtitle,           record.description, record.season,              record.episode,     record.category,           record.chanid,      channel.channum,             record.station,     channel.name,                record.recgroup,    record.playgroup,          record.seriesid,    record.programid,          record.inetref,     record.recpriority,        record.startdate,   record.starttime,          record.enddate,     record.endtime,            record.recordid,    record.type,               record.dupin,       record.dupmethod,          record.findid,                                   record.startoffset, record.endoffset,          channel.commmethod                          FROM record INNER JOIN channel ON (channel.chanid = record.chanid) LEFT JOIN recordmatch on record.recordid = recordmatch.recordid WHERE (type = 1 OR type = 2 OR type = 5 OR type = 7) AND       recordmatch.chanid IS NULL#012Driver error was [2/144]:#012QMYSQL: Unable to execute query#012Database error was:#012Table './mythconverg/recordmatch' is marked as crashed and last (automatic?) repair failed

This seemed to indicate a corupted database, which I had once a couple of years ago.  That time it caused the frontend to freeze when starting playback, or skiping ahead.  Fortunatly I keep a text file of notes about mythtv.  I found the solution there:

sudo  mysqlcheck -u mythtv -pXXXXX  --repair mythconverg

Substitute the password from mythfrontend->setup->general->screen 1 for the X's, with no space after the "-p".

Then all I had to do is restart the backend:

 sudo  stop mythtv-backend
 sudo  start mythtv-backend

---

