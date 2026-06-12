---
title: "[SOLVED] Cannot connect to backend"
date: 2007-11-13
forum: Mythbuntu
---

### Post by Zero7 on 2007-11-13
I started a new thread for my problem [http://ubuntuforums.org/showthread.php?t=602781&page=3](http://ubuntuforums.org/showthread.php?t=602781&page=3). Hope it is OK to start a new thread, since the OP's problem seems to be resolved, but not mine.

I upgraded from Feisty Fwan to Gutsy Gibbon and I had problem with MythTV after that. Problem is same as [http://ubuntuforums.org/showthread.php?t=602781&page=3](http://ubuntuforums.org/showthread.php?t=602781&page=3) thread.  I got fed up and reinstalled Gutsy Gibbon  afresh with root (/) partition reformatted. 

First I installed mySql-server using Synaptic program manger. Then I installed mythTV using [https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop) instructions and everything went well except setting up mythTV backend and frontend. MythTV control Center is installed correctly.
When I try to Launch MythTV Setup, I get the error saying that unable to connect to mythbackend and  check if the IP is configured correctly.  Appreciate any help I can get. Please provide me with clear instructions as I am not good at deciphering software instructions! 

```
Mythtv.log
2007-11-11 08:54:23.869 Using runtime prefix = /usr
QSettings::sync: filename is null/empty
2007-11-11 08:54:23.970 New DB connection, total: 1
2007-11-11 08:54:23.981 Unable to connect to database!
2007-11-11 08:54:24.014 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-11 08:54:24.137 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-11 08:54:24.231 Failed to init MythContext, exiting.
2007-11-11 10:47:48.417 Using runtime prefix = /usr
QSettings::sync: filename is null/empty
2007-11-11 10:47:48.436 New DB connection, total: 1
2007-11-11 10:47:48.441 Unable to connect to database!
2007-11-11 10:47:48.441 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-11 10:47:48.493 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-11 10:47:48.544 Failed to init MythContext, exiting.
2007-11-11 10:48:43.584 Using runtime prefix = /usr
QSettings::sync: filename is null/empty
2007-11-11 10:48:43.597 New DB connection, total: 1
2007-11-11 10:48:43.601 Unable to connect to database!
2007-11-11 10:48:43.602 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-11 10:48:43.654 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-11 10:48:43.704 Failed to init MythContext, exiting.
```

```

home@home-htpc:~$ tail /etc/mythtv/mysql.txt
DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=htpc

```

I was able to login to mysql and here is the output

```
mysql -u root mysql -p
Enter password: 
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 155
Server version: 5.0.45-Debian_1ubuntu3-log Debian etch distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| mysql              | 
| mythconverg        | 
+--------------------+
3 rows in set (0.00 sec)

select Host,User from user;
+-----------+------------------+
| Host      | User             |
+-----------+------------------+
| %         | mythtv           | 
| 127.0.0.1 | root             | 
| home-htpc | root             | 
| localhost | debian-sys-maint | 
| localhost | mythtv           | 
| localhost | root             | 
+-----------+------------------+
6 rows in set (0.00 sec)



status
--------------
mysql  Ver 14.12 Distrib 5.0.45, for pc-linux-gnu (i486) using readline 5.2

Connection id:          156
Current database:       mysql
Current user:           root@localhost
SSL:                    Not in use
Current pager:          stdout
Using outfile:          ''
Using delimiter:        ;
Server version:         5.0.45-Debian_1ubuntu3-log Debian etch distribution
Protocol version:       10
Connection:             Localhost via UNIX socket
Server characterset:    latin1
Db     characterset:    latin1
Client characterset:    latin1
Conn.  characterset:    latin1
UNIX socket:            /var/run/mysqld/mysqld.sock
Uptime:                 28 min 36 sec

Threads: 1  Questions: 565  Slow queries: 0  Opens: 169  Flush tables: 1  Open tables: 17  Queries per second avg: 0.329



use mysql
Database changed


grant all on mythconverg.* to 'mythtv'@'%' identified by 'htpc';

```

Still I am getting the same error as before and not getting beyond this point. Appreciate your help. TIA :)

---

### Post by OffAxis on 2007-11-13
you logged on to the server with your 'root' account...
can you log on with your 'mythtv' account using your password of 'htpc'?
```
mysql -u mythtv -p
```

---

### Post by uopjohnson on 2007-11-13
It looks like the only problem you have is that your mysql password in mythtv is wrong.  You should do the following:
remove any user specific mysql password files so you can use the system one.
```
rm ~/.mythtv/mysql.txt
```
then change your mysql password for the mythtv user to match the one in your config file /etc/mythtv/mysql.txt
```

mysql -u root -p
Enter Password:
mysql> SET PASSWORD FOR 'mythtv' = PASSWORD('htpc')

```
Where htps is what you posted before as the output of tail /etc/mythtv/mysql.txt

Then run mythtv-setup from the control center.

---

### Post by Zero7 on 2007-11-13
Thanks a lot for quick replies. I am at work and will post the result in the eve. (after 7 PM PST)

---

### Post by superm1 on 2007-11-13
The most important thing here: you install mysql-server first.  This means you *probably* set a root password for mysql.

If you did, then you need to 

```
sudo dpkg-reconfigure mythtv-database
```

And enter that information.

After that

```
sudo dpkg-reconfigure mythtv-common
```

---

### Post by Zero7 on 2007-11-13
> **uopjohnson said:**
> It looks like the only problem you have is that your mysql password in mythtv is wrong.  You should do the following:
remove any user specific mysql password files so you can use the system one.
```
rm ~/.mythtv/mysql.txt
```
then change your mysql password for the mythtv user to match the one in your config file /etc/mythtv/mysql.txt
```

mysql -u root -p
Enter Password:
mysql> SET PASSWORD FOR 'mythtv' = PASSWORD('htpc')

```
Where htps is what you posted before as the output of tail /etc/mythtv/mysql.txt

Then run mythtv-setup from the control center.

I did a quick check during lunch and rm ~/.mythtv/mysql.txt came out with error file not found.

SET PASSWORD FOR 'mythtv' = htpc did not give any error/worked. 

When I try to set up mythtv from Mythbuntu Control Center, it was showing the same error as before.

---

### Post by uopjohnson on 2007-11-13
> **superm1 said:**
> 
```
sudo dpkg-reconfigure mythtv-database
```
And enter that information.
After that
```
sudo dpkg-reconfigure mythtv-common
```
 I knew there had to be an easy way to do that.  
Zero7, do this as it will work far faster than trying to track down all the variables that might affect the mythtv->mysql communication. The root password is whatever you have been entering for your password when you type
```
mysql -u root -p
Enter Password:
```

---

### Post by Zero7 on 2007-11-13
> **superm1 said:**
> The most important thing here: you install mysql-server first.  This means you *probably* set a root password for mysql.

If you did, then you need to 

```
sudo dpkg-reconfigure mythtv-database
```

And enter that information.

After that

```
sudo dpkg-reconfigure mythtv-common
```
This did the trick :)

Thanks a lot uopjohnson, suprem1 and offaxis for all the help.

---

