---
title: "mythtv remote frontend problems"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by voam on 2007-07-13
I am trying to get a new frontend on my laptop to connect to a working frontend/backend combo. I already have one working remote frontend in my desktop machine so I know it is not a matter of binding the backend ip to its actual ip address instead of the loopback address. 

It seems as though the frontend insists on looking at the local mysql server ( which there is none running) instead of trying to look at the host in mysql.txt. Another thing is that everytime I run mythfrontend it forgets the settings for the backend host but always switches back to localhost.

My ~/.mythtv/mysql.txt file has the correct username/password and ip address. 

One interesting note: when I installed the frontend, I followed the instructions for frontend only, instead of choosing the frontend on the existing desktop. So now when the computer automatically logs in it connects to the remote frontend and works properly. But when I log in as myself and start the front end manually, it cannot connect and I get the following errors. 
```

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-07-13 23:04:55.642 Using runtime prefix = /usr
2007-07-13 23:04:55.677 Gnome-Screensaver support enabled
2007-07-13 23:04:55.677 DPMS is active.
2007-07-13 23:04:55.716 New DB connection, total: 1
2007-07-13 23:04:55.719 Unable to connect to database!
2007-07-13 23:04:55.719 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-07-13 23:04:55.774 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-07-13 23:04:55.826 Unable to connect to database!
2007-07-13 23:04:55.826 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-07-13 23:04:55.878 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-07-13 23:04:55.929 Database not open while trying to load setting: GuiVidModeResolution
2007-07-13 23:04:55.930 Unable to connect to database!
2007-07-13 23:04:55.930 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
```

Any ideas?

---

### Post by voam on 2007-07-14
Well it turns out there was a copy of mysql.txt file in my home directory that the frontend insisted on using. It wasn't in ~/.mythtv/mysql.txt but right at ~/mysql.txt. In that file was specified localhost. I had also put some other text in that file for my own purposes thinking that file would not be used. Once I renamed that file it started using the file in the mythtv hidden directory and all is well. :)

---

