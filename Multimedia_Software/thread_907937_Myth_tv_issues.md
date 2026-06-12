---
title: "Myth tv issues"
date: 2008-09-02
forum: Multimedia Software
---

### Post by chris1112 on 2008-09-02
I have just installed mythtv on the latest ubuntu version and for some reason I can not get the backend to start. This is what I am getting from the logs. I found this log with this command  /var/log/mythtv/mythbackend.log. Any Ideas?


[I][I]2008-09-01 16:35:54.162 Using runtime prefix = /usr, libdir = /usr/lib
2008-09-01 16:35:54.277 Empty LocalHostName.
2008-09-01 16:35:54.414 Using localhost value of MythBox
2008-09-01 16:35:55.765 New DB connection, total: 1
2008-09-01 16:35:55.952 Unable to connect to database!
2008-09-01 16:35:56.079 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'
 (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-09-01 16:35:56.480 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
................................................................................
2008-09-01 16:35:58.991 UPnPautoconf() - No UPnP backends found
2008-09-01 16:35:59.113 No UPnP backends found

No UPnP backends found
[/I][/I]

---

### Post by wolfen69 on 2008-09-02
try running ```
mythfilldatabase
```

---

### Post by chris1112 on 2008-09-02
wolfen69 this is what I got. I think, it wants me to run setup but that is what I'm trying to do?

chris@MythBox:~$ mythfilldatabase
2008-09-01 22:05:37.088 Using runtime prefix = /usr, libdir = /usr/lib
2008-09-01 22:05:37.092 Empty LocalHostName.
2008-09-01 22:05:37.092 Using localhost value of MythBox
2008-09-01 22:05:37.139 New DB connection, total: 1
2008-09-01 22:05:37.160 Connected to database 'mythconverg' at host: localhost
2008-09-01 22:05:37.165 Closing DB connection named 'DBManager0'
2008-09-01 22:05:37.168 Connected to database 'mythconverg' at host: localhost
2008-09-01 22:05:37.190 There are no channel sources defined, did you run the setup program?
2008-09-01 22:05:37.190 DataDirect: Deleting temporary files
chris@MythBox:~$

---

### Post by chris1112 on 2008-09-02
I should also add, I get this when trying to set up the backend.

chris@MythBox:~$ /usr/bin/mythtv-setup
 * Stopping MythTV server: mythbackend                                   [ OK ] 
 * Restarting MythTV server: mythbackend                                        No /usr/bin/mythbackend found running; none killed.
                                                                         [ OK ]
chris@MythBox:~$

---

### Post by sofasurfer on 2008-09-02
I have the same problem. I run "system>administration>mythtv backend setup". I am then given the option to close mythbackend.I click "ok" and then I get a terminal window flashing messages and then the mythtv screen comes up and I chose "english" and the a screen says "no upnp backends found". I can continue but I really can't acomplish anything. I think I need a backend even though I clicked on mythtv backend in my system menu.
When I cancel the program I am asked if I want to run mythfilldatabase. So I click "ok" and I get the terminal windows and I don't know what to do with it.

Can anyone get me started?

---

### Post by chris1112 on 2008-09-02
This is what I&#8217;m getting when I try to reinstall the backend

E: mythtv-backend: subprocess post-installation script killed by signal (Interrupt)
E: mythtv-backend-master: dependency problems - leaving unconfigured

Sofasurfer how long have you been fighting with this issue. I have about two days, with two reinstalls of ubuntu

---

### Post by sofasurfer on 2008-09-02
About the same with me. I installed a tv tuner card and want to use mythtv with it but for such a popular package it sure isn't easy to figure out.

---

### Post by chris1112 on 2008-09-02
Anybody have any ideas or can point me in the right direction.

Thanks Chris

---

