---
title: "Newbie alert - Creating initial user for MythTV"
date: 2010-12-22
forum: Mythbuntu
---

### Post by Skarr11 on 2010-12-22
I've been struggling for a couple of days now with extremely marginal success trying to get a MythTV setup going, and I realized that I may have started off on the wrong foot:

I created a user named "mythtvone" and was setting everything up using that name.  However, as I'm reading through documentation, it appears that the user should be simply "mythtv" because of sql database, file permission, and other issues.  It just seems like MythTV wants to look for the "mythtv" user.

Can anyone confirm this?

---

### Post by Fkewl on 2010-12-23
I created my user under the name "HomeUser" and works fine

But, i did add HomeUser to groups witch gives him access to everything

---

### Post by Skarr11 on 2010-12-23
Thanks for the reply.

I added the user "mythtvone" to the mythtv group.

What's confusing me at the moment is configuring the mysql database.  I changed the owner from mythtv to mythtvone.

When I look at the /etc/mythtv/mysql.txt file, I get this:

```
DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=h98kDwwW
```

I entered the database using

```
sudo mysql -u root -p mysql
```

I poked around a little resulting in this:
```

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| mythconverg        |
+--------------------+
3 rows in set (0.00 sec)

mysql> select Host,User from user;
+-----------+------------------+
| Host      | User             |
+-----------+------------------+
| %         | mythtv           |
| 127.0.0.1 | root             |
| localhost | debian-sys-maint |
| localhost | mythtv           |
| localhost | root             |
| mythtvone | root             |
+-----------+------------------+
6 rows in set (0.00 sec)

mysql> status
--------------
mysql  Ver 14.14 Distrib 5.1.41, for debian-linux-gnu (i486) using readline 6.1

Connection id:        1802
SSL:            Not in use
Current pager:        stdout
Using outfile:        ''
Using delimiter:    ;
Server version:        5.1.41-3ubuntu12.8 (Ubuntu)
Protocol version:    10
Connection:        Localhost via UNIX socket
Client characterset:    latin1
Server characterset:    latin1
UNIX socket:        /var/run/mysqld/mysqld.sock
Uptime:            3 hours 20 min 59 sec

Threads: 1  Questions: 2850  Slow queries: 0  Opens: 774  Flush tables: 1  Open tables: 64  Queries per second avg: 0.236
--------------
```

At this point I'm not sure how to proceed.  Thanks.

---

### Post by Skarr11 on 2010-12-23
Oh, one more thing:  I edited the mysql.txt file and changed the DBUserName and DBPassword entries as shown below:

```
DBHostName=localhost
DBUserName=mythtvone
DBName=mythconverg
DBPassword=mythtvone
```

When I look at the mythbackend.log I get this:

```
................................................................................
2010-12-23 16:10:03.624 UPnPautoconf() - No UPnP backends found
2010-12-23 16:10:03.625 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-12-23 16:10:03.626 Deleting UPnP client...
2010-12-23 16:10:04.234 Failed to init MythContext, exiting.
2010-12-23 16:10:04.299 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-12-23 16:10:04.300 Using runtime prefix = /usr
2010-12-23 16:10:04.300 Using configuration directory = /home/mythtv/.mythtv
2010-12-23 16:10:04.301 Unable to read configuration file mysql.txt
2010-12-23 16:10:04.301 Empty LocalHostName.
2010-12-23 16:10:04.301 Using localhost value of mythtvone
2010-12-23 16:10:04.309 New DB connection, total: 1
2010-12-23 16:10:04.314 Unable to connect to database!
2010-12-23 16:10:04.314 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)
```

Hope this helps.

---

