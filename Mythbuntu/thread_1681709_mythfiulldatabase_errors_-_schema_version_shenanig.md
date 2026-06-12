---
title: "mythfiulldatabase errors - schema version shenanigans"
date: 2011-02-04
forum: Mythbuntu
---

### Post by fnaah on 2011-02-04
Mythfilldatabase has stopped running on my backend with the following error:

2011-02-05 08:40:34.845 Current MythTV Schema Version (DBSchemaVer): 1264
2011-02-05 08:40:34.845 Not allowed to upgrade the database. Skipping backup.

Error: MythTV database has newer TV schema (1264) than expected (1254).


I'm running an 0.23 backend (because I use XBMC as a frontend), and I'd like to keep it that way until xbmc has support for the 0.24 backend. I had some grief about a month ago when I tried to upgrade the whole backend to 0.24 (which is when I discovered xbmc's lack of compatibility...) but I managed to get everything working again after reinstallling the 0.23 backend and restoring the database from an old backup that happened to be lurking in /var/lib/mythtv/db_backups/.

Unfortunately now though, there are only five days' worth of backups in that folder, and mythfilldatabase had been failing silently for about a week, so I can't restore the db again.

Any clues what's going on here? I can still use XBMC as a front end to view recordings and live tv, so I don't think the database schema has actually changed, but mythfilldatabase won't run and thus I have no guide data.  Grateful for any assistance.

---

### Post by fnaah on 2011-02-08
anyone?

---

### Post by nickrout on 2011-02-08
mythfilldatabase does not backup the database so that is not the cause of backup failures.

what output do you get when you run the script /etc/cron.weekly/mythtv-database.

What do you see if you run mythfilldatabase from the command line?

---

### Post by ian dobson on 2011-02-08
Hi,

Looks as if you did't restore enough from your backup. If nothing else works restore the entire database from the backup or manually edit the database changing the schema version necessary. Manually editing the database is not recommended but that's your last chance.

Regards
Ian Dobson

---

### Post by fnaah on 2011-02-08
Nick, I'll post the results when I get home tonight.

Ian, not sure what else I could have restored - back in December I dumped the database entirely and restored it using the mythconverg_restore.pl script (using instructions from here:[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)). Unfortunately now though the backup is no longer in that folder (and stupidly i didn't copy it somehwere else at the time), so unfortunately I can't do that again (there only seem to be backups from the last five days in there).

I'm not adverse to the idea of manually changing the schema version number, as at this stage I'm looking at a complete rebuild to get my listings data working again. I'm not terribly attached to the recorded programs I have, I'm one of those odd users who mostly uses myth for liveTV, so a complete rebuild wouldn't be that devastating, just time consuming, and very very low in Wife Appreciation Factor (any time that I have spare time to try and fix the issue, she seems to be watching something.)

---

### Post by fnaah on 2011-02-09
No result from that database command at all.

> Last login: Wed Feb  9 18:11:20 2011 from 10.0.0.7
matt@mythfnaah:~$ /etc/cron.weekly/mythtv-database
Could not open required defaults file: /etc/mysql/debian.cnf
Fatal error in defaults handling. Program aborted
/usr/bin/mysqlcheck: Got error: 1045: Access denied for user 'matt'@'localhost'                                (using password: NO) when trying to connect
matt@mythfnaah:~$ sudo /etc/cron.weekly/mythtv-database
[sudo] password for matt:
matt@mythfnaah:~$

(wasn't sure if I needed sudo, so ran it without and then with.)

the output from mythfilldatabase on the command line is the same as my original post.  Here's the full output:

> matt@mythfnaah:~$ mythfilldatabase
2011-02-09 18:40:13.848 Using runtime prefix = /usr
2011-02-09 18:40:13.848 Using configuration directory = /home/matt/.mythtv
2011-02-09 18:40:13.848 Empty LocalHostName.
2011-02-09 18:40:13.848 Using localhost value of mythfnaah
2011-02-09 18:40:13.856 New DB connection, total: 1
2011-02-09 18:40:13.861 Connected to database 'mythconverg' at host: localhost
2011-02-09 18:40:13.861 Closing DB connection named 'DBManager0'
2011-02-09 18:40:13.862 Connected to database 'mythconverg' at host: localhost
2011-02-09 18:40:13.865 Current MythTV Schema Version (DBSchemaVer): 1264
2011-02-09 18:40:13.865 Not allowed to upgrade the database. Skipping backup.

Error: MythTV database has newer TV schema (1264) than expected (1254).

Database Host: localhost
Database Name: mythconverg

2011-02-09 18:40:13.878 Incorrect database schema
2011-02-09 18:40:13.878 DataDirect: Deleting temporary files
matt@mythfnaah:~$

---

### Post by nickrout on 2011-02-09
Never seen that problem before with mythfilldatabase.

Intrigued to know more about what you want 0.23 for - what xbmc functionality are you relying on, there are at least 3 methods to get access to myth from xbmc.

---

### Post by fnaah on 2011-02-09
I'm using XBMC as a remote frontend, accessing myth with the (surprisingly enough) myth:// protocol.

I rarely schedule recordings, and when I do I use mythweb. I mostly use XBMC to watch live TV. (It's a long story - the room where the TV is has extremely poor reception, and I'm renting, so I can't put up an external antenna.)

So are there other methods of watching livetv from a myth backend from an XBMC frontend?

From what I understand, the nice people at XBMC should be integrating 0.24 support into a future version ("real soon now"), however in the meantime live TV stops every half hour because there is no program data available. Also, I have no idea what's on at any time, and the other (i *think* unrelated) issue of XBMC taking upwards of two minutes to change channel (depending on how recently mythtv-backend was restarted) makes channel surfing tedious and frustrating, even with Australia's limited FTA channels.

---

### Post by fnaah on 2011-02-09
Hokay, so i manually changed the DBShemaVer value in mythconverg.  Mythfilldatabase is now running, fingers crossed.

---

### Post by fnaah on 2011-02-09
2011-02-10 02:15:39.887 MythContext: Connecting to backend server: 10.0.0.9:6543 (try 1 of 1)
2011-02-10 02:15:39.888 Using protocol version 56
2011-02-10 02:15:39.949 mythfilldatabase run complete.


Huzzah! Fixed. Thanks for the assistance. :)

---

### Post by rasos on 2011-10-10
I had a similar problem running MythBuntu 10.04 , when suddenly a database schema mismatch appeared. It turned out, that our son's Linux machine with 11.04 seems to have claimed to the MythBuntu server that it is a second backend server. 

None of the methods exporting/importing the database helped. Finally we upgraded the MythBuntu server to 11.04 , now it's offering the 0.24 MythTV version with the new schema to all clients. 

Find a detailled explanation of one of the maintainers [here]("http://www.mythtvtalk.com/error-mythtv-database-has-newet-tv-schemea-1264-than-expected-1254-a-14965/#post57983").

---

### Post by nickrout on 2011-10-10
You do NOT need to update ubuntu versions to change your mythtv version. Use mythbuntu-repos.

---

