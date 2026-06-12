---
title: "Backend cant connect to mysql?"
date: 2009-06-19
forum: Mythbuntu
---

### Post by hansoffate on 2009-06-19
When I launch mythfrontend, it loads to a database configuration page.  I have checked my backendlog and it looks like my backend cant connect to mysql. 

I've manually tried logged in with the provided username and password and was able to query the mythconverg database.  I'm pretty sure it should be able to make the connection.  I have double checked to make sure both mysqld and mythtv-backend were restarted.  

Any ideas what would be causing this issue?
Thanks,
-Hans


[mysql settings]
```

[client]
port            = 3669
socket          = /var/run/mysqld/mysqld.sock

[mysqld]

user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3669
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
skip-external-locking
bind-address            = 192.168.1.109

```

[backend log]
```

2009-06-19 11:32:14.544 Using runtime prefix = /usr
2009-06-19 11:32:14.548 Empty LocalHostName.
2009-06-19 11:32:14.548 Using localhost value of grunt
2009-06-19 11:32:14.561 Testing network connectivity to 192.168.1.109
2009-06-19 11:32:14.613 New DB connection, total: 1
2009-06-19 11:32:24.816 Unable to connect to database!
2009-06-19 11:32:24.817 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'hansoffate'@'grunt.local' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-06-19 11:32:24.877 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
................................................................................
2009-06-19 11:32:27.259 UPnPautoconf() - No UPnP backends found
2009-06-19 11:32:27.260 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [192.168.1.109]  
[console is not interactive, using default '192.168.1.109']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [3669]  
[console is not interactive, using default '3669']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [hansoffate]  
[console is not interactive, using default 'hansoffate']
Database password: [opennow]  
[console is not interactive, using default 'opennow']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2009-06-19 11:32:27.454 Writing settings file /home/mythtv/.mythtv/mysql.txt
2009-06-19 11:32:27.463 Closing DB connection named 'DBManager0'

```

---

### Post by hansoffate on 2009-06-29
Bump
Anyone?

---

### Post by joho500 on 2009-06-30
Hi Hans,

I read a post only minutes ago that describes the same problem. Perhaps the solution on [[COLOR="Red"]this page[/COLOR]]("http://www.bramkortleven.be/?p=131") helps?

Cheers,
Joost

---

### Post by purdue512 on 2009-06-30
Same problem. Easy, straight-up 8.10 install. Cannot connect to backend. Why is this part of the MySQL permission problem so sticky? There are posts on this all over the place. Why is this so hard?

---

### Post by hansoffate on 2009-07-06
Thanks for the replies.  My issue was with my mysql bind-address.  I changed it to localhost and it fixed my issue.

-Hans

---

