---
title: "Can't Upgrade Database"
date: 2009-10-26
forum: Mythbuntu
---

### Post by uncle hammy on 2009-10-26
I have successfully managed to upgrade to 0.22 using the mythbuntu-repos.  However, after I am done, I go to mythtv-setup and I am greeted with a "MythTV wants to upgrade your database schema from 1214 to 1244...." message.  I select upgrade, then upgrade again for the backup message. It works for about 5 seconds, and closes...that's it, that's all.

So I run mythtv-setup again and this time I am greeted with "MythTV wants to upgrade your database schema from 1230 to 1244...." message.  SO it would appear that the db upgrade PARTIALLY finished (which is confirmed by looking at the tables, I have all the "old" tables now).   So, I do the upgrade, upgrade thing again, only this time it doesn't go any further.  No matter what, I am stuck on 1230.

Here's the backend logs
```

2009-10-26 19:29:41.745 Upgrading.
2009-10-26 19:29:41.746 Newest MythTV Schema Version : 1244
2009-10-26 19:29:41.750 Upgrading to MythTV schema version 1231
2009-10-26 19:29:42.366 DB Error (Performing database upgrade): 
Query was: ALTER TABLE dtv_multiplex ADD COLUMN    default_authority varchar(32) CHARACTER SET utf8 NOT NULL default ''; 
Error was: Driver error was [2/1060]:
QMYSQL3: Unable to execute statement
Database error was:
Duplicate column name 'default_authority'
 
new version: 1231
2009-10-26 19:29:42.397 Database Schema upgrade FAILED, unlocking.
2009-10-26 19:29:42.398 Couldn't upgrade database to new schema

```

Seeing that, I tried to remove the default_authority column from the dtv_multiplex table and run the upgrade again....no luck, stuck there.

I now have approximately 500 backups of my database, but I have yet to actually have an upgraded db.

If I drop the mythconverg altogether, and reinstall mythtv-database so I have a blank db, then everything works fine.  Obviously, this is a tad less than satisfactory.

Anyone have any suggestions?  This is getting quite frustrating.

---

### Post by uncle hammy on 2009-10-27
OK, I figured this out.  When I tried to do my upgrade on the preivous night, the db was actually upgraded.  When I restored my db back to 0.21 because of the crashes, any tables that were new from the upgrade left behind.  Therefore I had the "already exists" issues.

I ran Toad's Compare feature, found the extra tables and deleted them and the db upgrade went through fine.

---

### Post by acodring on 2009-10-29
I said yes to a bunch of upgrades with Avenard's testing repo configured to get an nvidia upgrade without noticing that a bunch of myth .22 upgrades were also selected.

I really didn't plan on going to .22 anytime soon, but now that I'm there it may be easier to fix the database problem than to go back to .21.

**Can you elaborate a little on who this Toad character is, and where he keeps his compare feature? ** Much as you described above, I'm stuck at DB 1231.

Thanks!

---

### Post by acodring on 2009-10-29
OK, I found your Toad friend [http://www.quest.com/toad-for-mysql/](http://www.quest.com/toad-for-mysql/)
And a Windows VM to run it in.

Which of the Compare tools did you use?

[LIST]
[*]Schema Compare
[*]Data Compare
[*]Text Diff Viewer
[/LIST]

I can connect to my live database and I have gunzipped *.sql database backups of the 1214 and 1230 versions of the db to work with.

I tried Schema Compare but wasn't sure where to get the schema. 
I tried Data Compare but it wanted to compare two live databases. 
I tried Text Diff Viewer against the two backup files but it blew up with out of memory errors.

Should I keep trying to figure out the Text Diff Viewer?

Any pointers gratefully accepted!

Cheers,
Andrew

---

### Post by uncle hammy on 2009-10-29
I used the schema compare, however you may have an issue.  I restored an old backup as a new database (I called it Mythtv_2).  I did this only to compare the table structures of the old db to my current version of the db to see what had got left behind when I restored without dropping first.

I then used Toad's schema compare tool to compare the restored db to the current db, and Toad showed y the 4 tables that existed in the current version to the old version, and I dropped them.  Once I figured out the differences, and cleanup my current db, I dropped the Mythtv_2 Db I had created.

Where you may have an issue is having an old backup to compare with...

FWIW, the tables that were left behind when I restored my old db without dropping were....

channelscan_dtv_multiplex (the one probably causing you to be stuck at 2130)
netflix
tvosdmenu
websites

As always, I would highly recommend you make a backup of your current db before do anything at all.

Good Luck!

---

### Post by acodring on 2009-10-29
OK! Thanks for the tips. 

I've tried to write down a bunch of what I did in case it helps another poor googler who lands here in future. I'm not an expert, this isn't the 'right way' to do anything. It's just the way I flailed through and it moved me ahead to the next step/problem.


On mythbox:

me@mythbackend:/media/mythstorage/dbbackups$ mysqldump -u mythtv -p mythconverg >manualbck20091029.sql
Enter password: 

On windows vm:

- Start Toad
- Connect to database mythconverg as user mythtv with password
- Click on "Explore database objects"
- Set Autocommit to off
- Search for and right click "Drop Table" for 4 tables you listed above. (I didn't have a 'websites' table)
- Commit changes
- Cross fingers

On mythbox:

- Start mythbackend from a console, and watch the FAIL

Shall I upgrade this database? [yes]  
2009-10-29 20:40:31.937 Newest MythTV Schema Version : 1244
2009-10-29 20:40:31.961 Upgrading to MythTV schema version 1231
2009-10-29 20:40:50.875 DB Error (Performing database upgrade): 
Query was: ALTER TABLE dtv_multiplex ADD COLUMN    default_authority varchar(32) CHARACTER SET utf8 NOT NULL default ''; 
Error was: Driver error was [2/1060]:
QMYSQL3: Unable to execute statement
Database error was:
Duplicate column name 'default_authority'
 
new version: 1231
2009-10-29 20:40:50.875 Database Schema upgrade FAILED, unlocking.
2009-10-29 20:40:50.876 Couldn't upgrade database to new schema
ICE default IO error handler doing an exit(), pid = 15897, errno = 32


On Windows VM:

- Navigate to 'dtv_multiplex' table, 'default_authority' column
- Delete 'default_authority' column, with prejudice
- Commit changes
- Close Toad

On mythbox

- Cross fingers
- Start mythbackend
- Upgrade fails again, one of the tables I dropped earlier is missing

Shall I upgrade this database? [yes]  
2009-10-29 20:47:00.378 Newest MythTV Schema Version : 1244
2009-10-29 20:47:00.384 Upgrading to MythTV schema version 1231
2009-10-29 20:47:19.170 DB Error (Performing database upgrade): 
Query was: ALTER TABLE channelscan_dtv_multiplex ADD COLUMN    default_authority varchar(32) CHARACTER SET utf8 NOT NULL default ''; 
Error was: Driver error was [2/1146]:
QMYSQL3: Unable to execute statement
Database error was:
Table 'mythconverg.channelscan_dtv_multiplex' doesn't exist
 
new version: 1231
2009-10-29 20:47:19.170 Database Schema upgrade FAILED, unlocking.
2009-10-29 20:47:19.170 Couldn't upgrade database to new schema

- curse
- log into mysql
- drop database mythconverg
- create database mythconverg
- mysql -u mythtv -ppassword mythconverg < manualbck20091029.sql

On Windows VM

- Open Toad again
- Don't bother dropping other tables
- Navigate to 'dtv_multiplex' table, 'default_authority' column
- Delete 'default_authority' column, with prejudice
- Commit changes
- Close Toad

On mythbox

- Cross fingers
- Start mythbackend
- Database upgrades complete ok
- mythbackend complains about something and quits but that's probably another thread so I'll stop running on here...

2009-10-29 21:05:34.972 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
ICE default IO error handler doing an exit(), pid = 16910, errno = 32

---

### Post by stdPikachu on 2009-11-02
Ran into this problem myself when upgrading, when the identity of Toad was still unknown :D

Similar problem here, only complicated by the fact that my database is aeons old - I'm still using the same DB I was when I first installed Myth on Gentoo in 2004. As per usual, Myth's funky UTF8/latin1 charset handling came to bite me in the **** - posting this for anyone else who might run into the "corrupt database encodings" problem as semi-coherently described [here](http://wiki.mythtv.org/wiki/Fixing_Corrupt_Database_Encoding). Procedure that worked for me was as follows (just make sure you know what you're doing first!):

Create database;
[INDENT]mysql > create database mythconverg;
ALTER DATABASE mythconverg DEFAULT CHARACTER SET latin1;
[/INDENT]
Take my 0.21 dump from just before the upgrade
Change the in-DB flag from utf8 to latin1
[INDENT]cat mythconverg20091028.sql | sed 's/SET NAMES utf8/SET NAMES latin1/' >  mythconverg20091028import.sql[/INDENT]
Now I ran into a dunch of troubles restoring the DB from this converted file - the munged unicode/latin stuff in some of the tables created some bogus duplicate entries that MySQL refused to import. Luckily for me I was able to just drop the whole table since it wasn't important;
[INDENT]grep -v "INSERT INTO \`people\` " mythconverg20091028import.sql > mythconverg20091028import_nopeople.sql[/INDENT]
Now if it'd been a more important table I may well have been up effluent creek sans paddle, but I'm sure it would have been reasonably easy to delete just the dupe entries with some judicious sed usage.


After that the DB a) imported cleanly and b) upgraded cleanly. I originally wasted an hour attempting to upgrade the schema manually, but got stuck into an infinite loop of creating/deleting column entries that the mythsetup program would later choke on.

Don't have any other MySQL DB's on this box at present (Postgres FTW, as they say) but if anyone knows what my server/DB status *should* look like I'd be very much obliged.
```
std@prospero:~$ mysql -u root -p mythconverg -e 'status;'
Enter password:
--------------
mysql  Ver 14.14 Distrib 5.1.37, for debian-linux-gnu (x86_64) using  EditLine wrapper

Connection id:          3151
SSL:                    Not in use
Current pager:          stdout
Using outfile:          ''
Using delimiter:        ;
Server version:         5.1.37-1ubuntu5 (Ubuntu)
Protocol version:       10
Connection:             Localhost via UNIX socket
Client characterset:    latin1
Server characterset:    latin1
UNIX socket:            /var/run/mysqld/mysqld.sock
Uptime:                 5 days 7 hours 6 min 22 sec

Threads: 8  Questions: 5266540  Slow queries: 0  Opens: 1276  Flush tables: 1  Open tables: 64  Queries per second avg: 11.509
--------------
```

---

### Post by nerver on 2009-11-04
Hey,

In case anyone else comes across this thread and is looking for a quick and easy fix, I was able to resolve this issue using the following steps:

*please note, you need to have a good database backup in order to use this method*

```
mysql -u mythtv -pyourpassword
```

mysql> ```
drop database mythconverg;
```
mysql> ```
exit
```

```
sudo /etc/init.d/mysql restart
```

```
mysql -u mythtv -pyourpassword
```

mysql> ```
create database mythconverg;
```
mysql> ```
exit
```

download the mythconverg_restore.pl script found here: 
[http://svn.mythtv.org/trac/browser/trunk/mythtv/programs/scripts/database/mythconverg_restore.pl?format=txt](http://svn.mythtv.org/trac/browser/trunk/mythtv/programs/scripts/database/mythconverg_restore.pl?format=txt)

```
chmod +x mythconverg_restore.pl
```

```
mythconverg_restore.pl --verbose --directory /path/to/backup/directory --filename mythtv_backup.sql
```

run mythtv-setup and upgrade database

then start up mythfrontend and it will ask you to upgrade a few of the database sections

afterwards you should have your old .21 database working nicely with mythtv .22

Cheers,
-Sean

---

### Post by stafio on 2009-11-08
I ran into the same issue and the fix posted by nerver worked perfectly for me. Thanks!

---

### Post by frugal on 2009-11-09
nerver's post totally saved me too! Still have to test further but looks promising, thanks a ton!

One minor point, it looks like for me the copy of mythconverg_restore.pl that was under /usr/share/mythtv for Mythbuntu 9.10 worked fine.

I only mention that because it seems like all of the mythtv.org sites are unreachable for me at the moment so thought people might be interested in knowing that the local copy appears to work.

---

### Post by nerver on 2009-11-09
Glad I could help guys :)

Thanks for the tip frugal, I didn't realize that script was already available in Mythbuntu 9.10. 

Cheers,
-Sean

---

