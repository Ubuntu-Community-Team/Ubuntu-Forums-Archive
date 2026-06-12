---
title: "Myth TV installation:  trouble"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by tinker123 on 2007-01-07
Hi.

I am running Ubuntu 6.10.   I have a 3 year old HaugePauge TV card hooked up to a VCR.   I would like to install mythtv so that I can watch and save the output from the vhs tapes, ultimately transferring that output to dvd.

I chose the installation directions for a "mythv frontend desktop" after reading some descriptions over what kind of directions to use
[https://help.ubuntu.com/community/MythTV_Edgy_Frontend_Desktop#head-154439c14a0a18f02b827553323611ff983d721a](https://help.ubuntu.com/community/MythTV_Edgy_Frontend_Desktop#head-154439c14a0a18f02b827553323611ff983d721a)

I have to admit, I am a bit confused over the server vs frontend distinctions.

Anyway, I ignored the steps for installing Ubuntu ( I already have it installed and have no problem with my clock not being 100% accurage or not having an ssh server ).

I went ahead and used synaptic to install mythtv.

I typed "mythfrontend" in a terminal and got a bunch of error messages ( below ) that pretty much amounted to mythtv not being able to conncet to a mysql database.

Where do I go from here?

Thanks in advance for any info

Steve
=========================================
2007-01-07 14:52:20.935 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-01-07 14:52:20.986 Database not open while trying to load setting: GuiHeight
2007-01-07 14:52:20.996 Unable to connect to database!
2007-01-07 14:52:20.996 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-01-07 14:52:21.050 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-01-07 14:52:21.102 Database not open while trying to load setting: MenuTheme
2007-01-07 14:52:21.103 Unable to connect to database!
2007-01-07 14:52:21.103 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

### Post by dpsleep on 2007-01-07
ok, that tutorial is telling you how to install a frontend to connect to a backend on another computer. what im guessing you want it both the back and front end on your single computer. to do that go here [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)

thats the one i used and it works great.

also, if all you want to do is take a connection from your vcr to you comp to record, there are allot easyer ways to do it....
[http://www.linuxtv.org/v4lwiki/index.php/TV_Recording](http://www.linuxtv.org/v4lwiki/index.php/TV_Recording)

i would try to get that working instead

---

### Post by tinker123 on 2007-01-07
Thanks a ton, I will look into it.    Your pointer will also help future people searching the forum, thanks

---

### Post by tinker123 on 2007-01-07
_______

---

### Post by 454redhawk on 2007-01-07
This is the one you need.

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)

---

### Post by tinker123 on 2007-01-08
-----

---

### Post by arnieboy on 2007-01-08
you are getting the above error because mysql server is not running. To make it run, do the following from terminal:
```
mysql_install_db
```

---

