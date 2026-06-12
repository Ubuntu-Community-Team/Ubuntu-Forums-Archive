---
title: "Upgrading DB from 1215 to 1244 FAIL"
date: 2009-12-25
forum: Mythbuntu
---

### Post by wheniwork on 2009-12-25
Have problems... The two opstions i'm told to try end in the same results.

Out put when trying to run mythbackend and upgrade db.

```
Shall I upgrade this database? [yes]  yes
2009-12-25 13:59:56.214 Newest MythTV Schema Version : 1244
2009-12-25 13:59:56.218 Upgrading to MythTV schema version 1215
2009-12-25 13:59:56.218 New DB connection, total: 3
2009-12-25 13:59:56.218 Connected to database 'mythconverg' at host: localhost
2009-12-25 13:59:56.803 Database corruption detected. Unable to proceed with database upgrade. (Table: oldprogram, Warnings: 2)
2009-12-25 13:59:56.803 Your database must be fixed before you can upgrade beyond 0.21-fixes. Please see http://www.mythtv.org/wiki/Fixing_Corrupt_Database_Encoding for information on fixing your database.
2009-12-25 13:59:56.803 Database Schema upgrade FAILED, unlocking.
2009-12-25 13:59:56.803 Couldn't upgrade database to new schema

```

Both the fix link in the output and this one:

[http://www.gossamer-threads.com/lists/mythtv/users/406111#406111](http://www.gossamer-threads.com/lists/mythtv/users/406111#406111)

Do not help. Any ideas?

SQL Status:

```
mysql> status;
--------------
mysql  Ver 14.12 Distrib 5.0.67, for debian-linux-gnu (i486) using readline 5.2

Connection id:		1011
Current database:	mythconverg
Current user:		XXXX@localhost
SSL:			Not in use
Current pager:		stdout
Using outfile:		''
Using delimiter:	;
Server version:		5.0.67-0ubuntu6 (Ubuntu)
Protocol version:	10
Connection:		Localhost via UNIX socket
Server characterset:	latin1
Db     characterset:	utf8
Client characterset:	latin1
Conn.  characterset:	latin1
UNIX socket:		/var/run/mysqld/mysqld.sock
Uptime:			9 hours 9 min 21 sec

Threads: 3  Questions: 39295  Slow queries: 0  Opens: 15168  Flush tables: 1  Open tables: 64  Queries per second avg: 1.192
--------------

```

The ```
Db     characterset:	utf8
``` is correct according to the fix located: 
[http://www.mythtv.org/wiki/Fixing_Corrupt_Database_Encoding#Recognizing_the_difference](http://www.mythtv.org/wiki/Fixing_Corrupt_Database_Encoding#Recognizing_the_difference)
Note the part that says: > Note that once upgraded to post-r16789 SVN trunk (or 0.22 or above), the output of the status command will differ--namely, the Db characterset will be utf8 in a properly-configured system. The value of the others is not important on post-r16789 SVN trunk/0.22+ versions of MythTV. 

Even after I get my DB freshly backed up with all latin1 sets, myth changes the Db Characterset to utf8, apparently becuase it is supposed to.

Any help would be great. Thanks.

---

### Post by ian dobson on 2009-12-26
Hi,

Maybe you have database corruption rather than just incorrect encoding. Maybe try repairing the database:-
[http://www.databasejournal.com/features/mysql/article.php/10897_3300511_2/Repairing-Database-Corruption-in-MySQL.htm](http://www.databasejournal.com/features/mysql/article.php/10897_3300511_2/Repairing-Database-Corruption-in-MySQL.htm)

Regards and good luck
Ian Dobson

---

