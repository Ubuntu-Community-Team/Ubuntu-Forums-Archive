---
title: "Myth-Frontend doing it's own thing"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by SarahKH on 2007-02-16
Installed the MythTV frontend packages in 6.10, installation goes well and Synaptics says it's all good. 

Application > Video > mythfrontend and after a few seconds up pops the configuration screens. I configure the frontend properly, feeding it the correct username / password and IP address for the backend machine AND make sure it's using a unique ID for the frontend (I'm working on multi-front end system). 

I get this:

Database error was:
Access denied for user 'root'@'192.168.0.116' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-02-16 16:19:45.220 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-02-16 16:19:45.300 Unable to connect to database!
2007-02-16 16:19:45.300 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'root'@'192.168.0.116' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-02-16 16:19:45.368 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-02-16 16:19:45.420 Database not open while tryin

Page upon page, upon page of this cruft. 

Now, haha! You'd be thinking "Sarah, you're not running MySQL and you haven't done the first stage setup of giving root a password.  And you'd be partially right... I haven't on this machine (192.168.0.116) because it's a Frontend only install and shouldn't need it.  I have, however got Mythbackend and MySQL quietly trundling away on 192.168.0.1 

So. Why, despite Frontend being told several times to connect to 192.168.0.1 (or darkstar) is it insisting on looking locally for the sodding backend / database?  
I've turned on the complete gamut of logging on the Backend and it's not even attempting to connect to the DB and write it's settings. 

Ideas please?

---

### Post by SarahKH on 2007-02-16
Sorry. I'm a moron. 

Fault not the myth package... it's all the frontends.

Idiotic MySQL has decided it doesn't like remote access any more, yay!

Serves me right for getting to focused on the problem and not the cause.

---

### Post by Erlander on 2007-02-17
I'd look at the mysql.txt in the hidden folder .mythtv off your user folder.

It includes the current password.  I'd then use that password in my frontends.

Rob

---

### Post by FryerFox on 2007-04-30
Also, see this post:

[http://ubuntuforums.org/showthread.php?p=2322564#post2322564](http://ubuntuforums.org/showthread.php?p=2322564#post2322564)

It seems that the new MySQL turns off network access by default.

---

