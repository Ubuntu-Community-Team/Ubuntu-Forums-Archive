---
title: "problems configuring mythbackend"
date: 2007-11-15
forum: Mythbuntu
---

### Post by netlord on 2007-11-15
hi

i installed mythbuntu on an htpc. when i try to configure the backend i get this error message:
>      sudo mythbackend
    [sudo] password for netlord:
    2007-11-15 21:04:26.135 Using runtime prefix = /usr
    2007-11-15 21:04:26.149 New DB connection, total: 1
    2007-11-15 21:04:26.150 Unable to connect to database!
    2007-11-15 21:04:26.150 Driver error was [1/2003]:
    QMYSQL3: Unable to connect
    Database error was:
    Can't connect to MySQL server on 'mediacenter' (111)

    QSqlQuery::exec: database not open
    QSqlQuery::exec: database not open
    2007-11-15 21:04:26.200 DB Error (KickDatabase):
    Query was:
    SELECT NULL;
    No error type from QSqlError? Strange...
    2007-11-15 21:04:26.251 Failed to init MythContext, exiting.



as i had seen on another thread i tried to access the mysql database. this works whitout a problem.
i can connect to the mythconverg database and i can see the 75 tables.

what else its going wrong?

---

### Post by kevinatkins on 2007-11-15
Hi,

I'm assuming the database server is on the same machine as the backend.

You probably need to do a 'sudo dpkg-reconfigure mythtv-common' and answer the questions. If my assumption above is correct, you can use 'localhost' as the name / IP of the machine running MySQL, accept the rest as defaults. You'll need to supply the password which was randomly generated when MythTV was installed.. If you don't have it, you might need to change the MySQL password for the MythTV user...

---

### Post by netlord on 2007-11-15
hi

your assumption is right. the back- and the frontend are on the same machine

i tried your tip, using the password from /etc/mythtv/mysql.txt, and i got no error message.
but when i try to start the mythtvbackend i get the same error message as before.

what else can i do?

cu
netlord

---

### Post by kevinatkins on 2007-11-15
Hmm, strange.. 

How are you trying to start the backend configuration?

---

### Post by OffAxis on 2007-11-15
have you tried **127.0.0.1** as the backend IP or just l**ocalhost**?

---

### Post by superm1 on 2007-11-15
[SIZE=6]**don't**[/SIZE] start the backend that way.

```
sudo /etc/init.d/mythtv-backend restart
```

---

### Post by netlord on 2007-11-16
> **kevinatkins said:**
> Hmm, strange.. 

How are you trying to start the backend configuration?

via *sudo mythbackend*

> **OffAxis said:**
> have you tried **127.0.0.1** as the backend IP or just l**ocalhost**?

i tried both. none worked...


> **superm1 said:**
> [SIZE=6]**don't**[/SIZE] start the backend that way.

```
sudo /etc/init.d/mythtv-backend restart
```

i´ll try this.

and the i´ll report

---

