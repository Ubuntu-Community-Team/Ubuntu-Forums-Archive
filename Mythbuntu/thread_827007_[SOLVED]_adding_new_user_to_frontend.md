---
title: "[SOLVED] adding new user to frontend"
date: 2008-06-12
forum: Mythbuntu
---

### Post by elj4176 on 2008-06-12
I have a laptop that I use as a frontend when I want to watch something. It is a general use laptop so it is not a dedicated FE.

My wifes laptop died the other day so I added her as a user on mine. When she tries to run mythtv nothing happens in the gui. So I tried from the command line. It appears to connect to the DB and start mythfrontend.real but that's it.
I checked /var/log/mythtv/mythfrontend.log and there is nothing to indicate a problem other than it says 
starting mythfrontned.real
but then nothing else after that. 

I log out of her user account and log into mine and it works fine. Log back into her account and it doesn't work. Do I need to add her to a certain group or change permissions somewhere to make this work?
Thanks!

---

### Post by superm1 on 2008-06-12
Add her to the mythtv group and logout.  If you started it as normal mythfrontend (not mythfrontend.real), this would have already happened...

If that doesn't do the trick, run it with either strace or with -v all

---

### Post by elj4176 on 2008-06-12
She is already in the mythtv group. Here is what I get when I run mythfrontend -strace

kim@pils:~$ mythfrontend -strace
2008-06-12 18:24:28.255 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-12 18:24:28.696 XScreenSaver support enabled
2008-06-12 18:24:28.696 DPMS is active.
2008-06-12 18:24:28.696 Empty LocalHostName.
2008-06-12 18:24:28.697 Using localhost value of pils
2008-06-12 18:24:28.697 Testing network connectivity to notmydomain.com
2008-06-12 18:24:28.959 New DB connection, total: 1
2008-06-12 18:27:38.074 Unable to connect to database!
2008-06-12 18:27:38.074 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on 'notmydomain.com' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-06-12 18:30:47.364 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...

2008-06-12 18:30:47.616 UPnPautoconf() - Found one UPnP backend

I know the mysql server is running and working under my account. Any other ideas?
Thanks! I appreciate the help.

---

### Post by elj4176 on 2008-06-12
Nevermind. The /home/kim/.mythtv/mysql.txt needed to be corrected. The hostname was wrong - not using the IP.

---

