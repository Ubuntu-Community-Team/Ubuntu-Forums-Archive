---
title: "Ubuntu 7.04 &amp; MythTV/MySQL error"
date: 2008-04-14
forum: Mythbuntu
---

### Post by bonestx on 2008-04-14
I have an Ubuntu 7.04 install that is also running a MythTV backend/frontend.  It is the master backend for an XBMC MythTV Xbox.  I used the main Ubuntu 7.04 install guide.

My problem:  This box has been working fine for 9+ months and on Sunday it started giving me errors.  I may have upgraded mySQL quite awhile back, but I'm pretty sure I'd rebooted since then.

Here's what I see in /var/log/mythtv/mythbackend.log when I try to start the backend:
[I]2008-04-14 21:43:06.826 Using runtime prefix = /usr
2008-04-14 21:43:06.842 New DB connection, total: 1
2008-04-14 21:43:06.844 Unable to connect to database!
2008-04-14 21:43:06.845 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-04-14 21:43:06.916 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-04-14 21:43:06.986 Failed to init MythContext, exiting.[/I]

Some text from /var/log/debug that might be of interest:
[I]Apr 14 20:35:21 Midleton /etc/init.d/mysql[5921]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Apr 14 20:35:21 Midleton /etc/init.d/mysql[5921]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Apr 14 20:35:21 Midleton /etc/init.d/mysql[5921]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Apr 14 20:35:21 Midleton /etc/init.d/mysql[5921]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists![/I]

What I've tried
[LIST]
[*]bind-address of /etc/mysql/my.cnf is the ip of my backend server
[*]/etc/mythtv/mysql.txt and /usr/share/mythtv/mysql.txt match -- both have localhost for DBHostName
[*]Used the User Admin tool to make sure my login is part of the mysql group
[*]Tried to: "adduser -s /sbin/nologin -m -g mysql mysql" but it didn't like the -m and -g commands
[*]sudo mysqld --skip-grant-tables
080414 21:57:26 [ERROR] Fatal error: Can't change to run as user 'mysql' ;  Please check that the user exists!
080414 21:57:26 [ERROR] Aborting
080414 21:57:26 [Note] mysqld: Shutdown complete
[/LIST]

Dumb things I've done:
[LIST]
[*]Changed the password in /etc/mysql/debian.cnf to the password for mythconverg tables.  There isn't a backup of debian.cnf with the old password anymore.
[/LIST]

There are probably several other things I've already tried, that I'm forgetting right now.  Thanks for your help.

---

### Post by bonestx on 2008-04-16
Ok, I managed to solve it myself!  With a LOT of internet searching...  I'm not guaranteeing that all these commands are exactly right (I had to close some of the windows where I execute them).

Here's what I did:
1.  Created a mysql user and made it part of the mysql group.
2.  The ownership of /var/run/mysqld had been changed to root
chown mysql:mysql /var/run/mysqld -R
3.  After I got this fixed I had some problems running querries against my mythconverg database, so I ran the chown on that too:
chown mysql /var/lib/mysql -R
4.  I reset my debian-sys-maint password by using the following commands:
To startup mysql:
mysql -u root -t mysql -p 
Then:
UPDATE mysql.user SET Password=PASSWORD('newpwd') WHERE User='debian-sys-maint' 

I hope this helps someone else.

---

