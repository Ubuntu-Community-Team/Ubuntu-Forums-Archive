---
title: "MythTV Cant connect to database"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by R0B071CxN1NJ4 on 2007-08-16
I installed MythTV Backend and MythTV Frontend and configured it and when i tried to run it it gave me the message "Cannot connect to master backend server" so i ran this

```
~# mythbackend
```and this is what i got:

```
2007-08-16 16:43:40.998 Using runtime prefix = /usr
2007-08-16 16:43:41.023 New DB connection, total: 1
2007-08-16 16:43:41.043 Unable to connect to database!
2007-08-16 16:43:41.043 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '***.***.***.***' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-08-16 16:43:41.097 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-08-16 16:43:41.154 Failed to init MythContext, exiting.
```

i have no idea what to do next.

note: the i replaced the ip address with asteriks thats not the way i entered it into the program

---

### Post by tgm4883 on 2007-08-16
Did you follow any guide?

If you set everything to 127.0.0.1, then it shouldn't be trying to connect to a mysql database on anything other than 127.0.0.1

---

### Post by R0B071CxN1NJ4 on 2007-08-16
thats what i set it too because i was thinking the same thing. and i followed the ubuntu guide but it didnt touch very much so i followed the on screen instructions in mythtv

---

### Post by tgm4883 on 2007-08-16
> **R0B071CxN1NJ4 said:**
> thats what i set it too because i was thinking the same thing. and i followed the ubuntu guide but it didnt touch very much so i followed the on screen instructions in mythtv

You followed this guide?
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

Cause that one works great.  And just to be clear, the ip address that you replaced with *** wasn't 127.0.0.1 right?

---

### Post by R0B071CxN1NJ4 on 2007-08-16
yes that is the guide i followed and that is correct

---

