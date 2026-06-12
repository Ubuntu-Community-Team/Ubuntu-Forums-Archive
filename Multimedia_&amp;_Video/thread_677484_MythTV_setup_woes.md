---
title: "MythTV setup woes"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by twin_57103 on 2008-01-24
Hi folks, been trying to setup MythTV for a new TV tuner, and it isn't going very well.  I'm hoping someone out there can help.  I've been trying to follow the guide at [https://help.ubuntu.com/community/MythTV?]("https://help.ubuntu.com/community/MythTV?")  

My problem is with the initial setup phase - cannot connect to database errors.  I've confirmed that my my user account is part of the MythTV group.  I've tried a couple variations on the password - the generated one from the initial setup (I copied the screens into a text document) and also "mythtv".  Regardless, I get stuck on the database configuration screen (screen shot attached)

I've run the setup utilities (mythtv-database and mythtv-common), but no help so far.  When I try "mysql -u root mysql" I get 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Computer: dual-boot Ubuntu 7.10/Windows XP; Dell Dimension 4700, 1.5 Gb RAM, 3.0 GHz; TV tuner is KWorld PlusTV 115

I am probably missing something simple - I'd appreciate any thoughts you have!

---

### Post by lime4x4 on 2008-01-24
Is this on a box running the front-end and back-end?

---

### Post by twin_57103 on 2008-01-24
Everything's on one computer - nothing networked.  Front-end and back-end are on this system.

---

### Post by lime4x4 on 2008-01-24
is the back-end running? I installed mythbuntu on a seperate box then installed mythtv front-end only on a gutsy box and i had the same problem trying to connect remotley to a myth back-end server and it turned out to be i had the password wrong

---

### Post by twin_57103 on 2008-01-24
Do I need to manually start and/or configure the back-end?  I may well have the password wrong, but I've tried everything that I can think of and it hasn't worked.

---

### Post by lime4x4 on 2008-01-24
when u installed myth back-end you should've been asked to configure it right then. Atleast on the mythbuntu install i had to configure the back-end server as it was being installed

---

### Post by twin_57103 on 2008-01-24
It looks like this is (part of) the problem.  The backend doesn't appear to be running - I tried to restart it with "sudo /etc/init.d/mythtv-backend restart" and got "Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed."

Here's the output from running "mythbackend"
2008-01-24 22:09:41.360 Using runtime prefix = /usr
2008-01-24 22:09:41.372 New DB connection, total: 1
2008-01-24 22:09:41.376 Unable to connect to database!
2008-01-24 22:09:41.376 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-24 22:09:41.433 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-24 22:09:41.490 Failed to init MythContext, exiting.

I tried to check the log: 
more /var/log/mythtv/mythbackend.lo
/var/log/mythtv/mythbackend.lo: No such file or directory

Any ideas?  Is there a way to manually reconfigure it?  I am thinking about removing and reinstalling mythTV entirely.  Thanks for all the help already!

---

### Post by lime4x4 on 2008-01-25
I would. use this command to completly remove a package

sudo apt-get remove --purge "package name"

That should remove everything including the config files

---

### Post by twin_57103 on 2008-01-25
Thanks.  I'll give it a try later.

---

### Post by wgandhi on 2008-04-21
I had the exact same problem. I made it past the setup of the backend by adding the myth database to the mysql server.
I ran this command:
mysql -u root -p < /usr/share/mythtv/sql/mc.sql

Later I did the backend setup from the menus. Everything worked. Onto setting up the front end next..

-Wish

ps: I tried Windows Vista first.. It did not recognize my WIFI card and hardy did. Must be a first for me..

---

