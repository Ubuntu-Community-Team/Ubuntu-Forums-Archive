---
title: "proposed mythtv updates break"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by feld on 2007-02-24
I found that updates to mythtv in the proposed repo add a new user mythtv@localhost in the mysql database and totally destroy permissions for that user, along with killing its password somehow.

anyone else get this?

---

### Post by jaymode on 2007-02-24
I have also found this anyone know how to fix it?

---

### Post by superm1 on 2007-02-24
Guys what was your old version before the proposed update? Were you using the dapper 0.18, or an external repo for it?

---

### Post by jaymode on 2007-02-24
I was using Edgy. My version was from the official repos 0.20 i believe.

---

### Post by superm1 on 2007-02-24
I'll do some more experiments in some dapper and edgy VMs the next few days.  I had previously done one experiment with these patches no trouble coming from dapper to edgy.

---

### Post by jaymode on 2007-02-25
Well it is giving a QSQLDatabase error for me. Its a lot of stuff like this repeated over and over again:
```
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-02-25 11:49:10.224 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-02-25 11:49:10.281 Unable to connect to database!
2007-02-25 11:49:10.281 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.6' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-02-25 11:49:10.336 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-02-25 11:49:10.392 Database not open while trying to load setting: Language

```

This is very frustrating. I have tried to go back to the old Mythtv from the repos and still have this problem.

---

### Post by kerinin on 2007-02-26
I just experienced this same problem.  the update installed mythtv-common and uninstalled mythtv-frontend and mythtv-backend.  when i try to reinstall them i get this:

```
The following packages have unmet dependencies:
  mythtv: Depends: mythtv-frontend (= 0.20-0.2ubuntu2.1~proposed1) but it is not going to be installed
          Depends: mythtv-backend (= 0.20-0.2ubuntu2.1~proposed1) but it is not going to be installed
E: Broken packages

```

This seems like a packaging problem - does anyone know how to fix this?  I just mythtv a lot...

---

### Post by jaymode on 2007-02-26
Well I just went ahead and decided to compile mythtv myself and it works. I also redid the database from scratch, so this might not be the best option.

Btw, I used the code from the 0.20-fixes branch and it seems to be working very well.

---

### Post by superm1 on 2007-02-26
I just installed a fresh edgy VM and updated it to all the current updates.  I then enabled the proposed repository and had no troubles with the update.

You must have changed your mysql password since mythtv installation or something to that nature.

---

### Post by kerinin on 2007-02-26
I think the problem is only in the 64-bit repos

---

### Post by jaymode on 2007-02-27
I think it may have to do with having changed the database permissions and I had not changed the password. I had my permissions set all computers on my local network could connect to the backend. However, before I removed it, I also tried setting the IP of the server to 'localhost' instead of the IP, but that still did not work correctly.

---

