---
title: "Deleting tuners"
date: 2009-12-14
forum: Mythbuntu
---

### Post by badger_fruit on 2009-12-14
Hi
I have a bit of a strange one I wonder if someone can help me at all ...

9.04 Mythbuntu with Myth 0.22

Had a freecom USB card but got very poor picture through it so removed it from the system (unplugged it and rebooted) and then went into the myth-tv backend to remove it from the configuration. I discovered you can't just delete a single capture card; you can either:-

1. Delete all capture cards
2. Delete all capture cards from THESERVER

So I chose option 1 (as I only have the one backend) and re-created the two remaining capture cards.  I then loaded up the backend and did a MythfillDB as normal.

When I went into the web-gui I noticed I somehow had not two as expected, but FOUR encoders listed!!!

My question therefore is **HOW DO I ACTUALLY REMOVE ALL ENCODERS AND TUNERS FROM THE SYSTEM?! **(so I can start afresh without loosing my recordings etc)

Thank you for reading and any ideas or suggestions you may have!
Regards

---

### Post by NightStorm on 2009-12-14
It is no better in 9.10.  I had 4 tuners, deleted 1 and added it again and now I have 5.

---

### Post by badger_fruit on 2009-12-14
how odd ... also, very frustrating - i use mythtv on ubuntu (well, mythbuntu) for the backend but on my front-ends, I always am now getting the message that "not all channels are available on certain tuners" - doesn't say which though!!

Fortunately, the recording side seems to be working ok, only assigning upcoming recordings to valid tuners.

Perhaps I might have a poke around in the DB and see if I can manually hack them out ....
* note to self to perform a DB backup first!! *

---

### Post by NightStorm on 2009-12-14
I'd be curious if you can get the myth backup and restore script to work.  This weekend I tried.  The backup worked fine, but the restore would not.  I followed the directions and dropped the mythconverg database then used the mc.sql script to recreate it.  That script does not make any tables.  The restore script would abort complaining that there were already tables in the mythconverg database.

Now before doing all of this I made sure that both the front and backends were not running.  I then tried doing a "drop database mythconverg" followed by a "create database mythconverg".  There should be no tables, right?  Wrong: all of the tables were there.  So I then started doing a "drop table ..." one by one and occassionally double checking with a "show tables".  The tables would disappear and then after some time period would re-appear.  Most frustrating.

There must have been some background process running that I did not notice which was replacing the tables.  Still .. I can't help but wonder if this is somehow related to the tuner issue.  It is as though something is adding back the deleted entries.

     - Bruce

---

### Post by nickrout on 2009-12-14
> **NightStorm said:**
> I'd be curious if you can get the myth backup and restore script to work.  This weekend I tried.  The backup worked fine, but the restore would not.  I followed the directions and dropped the mythconverg database then used the mc.sql script to recreate it.  That script does not make any tables.  The restore script would abort complaining that there were already tables in the mythconverg database.

Now before doing all of this I made sure that both the front and backends were not running.  I then tried doing a "drop database mythconverg" followed by a "create database mythconverg".  There should be no tables, right?  Wrong: all of the tables were there.  So I then started doing a "drop table ..." one by one and occassionally double checking with a "show tables".  The tables would disappear and then after some time period would re-appear.  Most frustrating.

There must have been some background process running that I did not notice which was replacing the tables.  Still .. I can't help but wonder if this is somehow related to the tuner issue.  It is as though something is adding back the deleted entries.

     - Bruce

Check that there are no remote frontends doing anything, or stray ones on the backend. ps ax|grep myth is a good start to looking. You want to make sure mythtv-setup hasn't run and isn't running since dropping the db.

---

