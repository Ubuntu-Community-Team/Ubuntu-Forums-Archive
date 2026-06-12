---
title: "[SOLVED] Update to Intrepid. Mythtv record scheduling problem"
date: 2008-11-08
forum: Mythbuntu
---

### Post by Kheops_74 on 2008-11-08
Since i update to Intrepid 8.10, i didn't see the tv show that i scheduled. I check in mySql (table :record) and they are there. 

If i add new program to the schedule, they appear in the table (mySql) but not in the schedule menu of the frontend.

Any idea?

K

---

### Post by newlinux on 2008-11-08
Are your tuners available? Check you tuner status and backend logs. Can you watch livetv?

---

### Post by Kheops_74 on 2008-11-09
The tuner work. I can watch TV. If i go in the "schedule recordings"-"Upcoming recordings" menu, there is no tv show. Before the update to intrepid, my show was there. If connect directly to mySql in the table record, i see my tv show. 

    It look like the backend don't see the scheduled recordings anymore.

K

---

### Post by newlinux on 2008-11-09
The record table actually doesn't completely determine what gets recorded. It holds information for the recording rules. The schedule determines what is going to get recorded based on the rules, and it determines recordings dynamically (so for instance, if one tuner goes down or something it can dynamically reschedule the show to another tuner).It might help if you looked through your logs in general to see if there is a problem. 

You might also try repairing your database tables.

---

### Post by Kheops_74 on 2008-11-09
I don't see problem in the log. What do you mean when you say "try repairing your database tables"? Do you use a tool to do this? 

I found a perl script (CheckMythDB.pl) and the only problem that it found is "157 channel entries do not have a valid dtv_multiplex" I try to find what dtv_multiplex means.

K

---

### Post by Kheops_74 on 2008-11-09
OK it works. I have to put 127.0.0.1 in local backend AND master backend. I see my recording schedules and it records. 

I'm not sure if it's the right solution since. I still have a problem to connect from an other box (frontend), but it works if the frontend and the backend are on the same box.

K

---

