---
title: "mythconverg not created during install"
date: 2008-05-11
forum: Mythbuntu
---

### Post by bignickel on 2008-05-11
Hi, I've just installed mythbuntu on my Apple TV using the alternate install disk.  I've installed the frontend and backend on this machine (I'm not capturing, just using it as a media playback machine).

The problem is that I don't think the mythconverg database was created during installation.  If I run mythtv-setup after I select language it says "No UPnP Backends found".  After I accepts the defaults for the database it says "Cannot login to database?

If I try to login to the mysql database I get this:

```
tim@atv:~$ mysql -u root -p mythconverg
Enter password: 
ERROR 1049 (42000): Unknown database 'mythconverg'

```

I tried do a full reinstall and got the same problem.  What am I doing wrong?

---

### Post by Nikas on 2008-05-11
Try to add the database manually:

```
mysql -u root -p < /usr/share/mythtv/sql/mc.sql
```

Run mythtv-setup after that.

---

### Post by bignickel on 2008-05-11
Tack så mycket, it was just because I was running mythtv setup under my own account, and I didn't have permissions for mythconverg.

---

### Post by pjman on 2008-05-13
I'm having a similar problem. I was able to create mythconverg by running

```
mysql -u root -p < /usr/share/mythtv/sql/mc.sql
```

but the mythtv user doesn't have access to the mythconverg database. 

Does anyone know the mysql command to give access to mythtv?

---

### Post by falcon15500 on 2008-05-15
```
grant all on mythconverg.* to "user"@"localhost" identified by "password";
```

Should work...  Leave the "s in there and sub in mythtv for user and the correct password.

---

### Post by reslip on 2008-05-16
I ran into this same problem during install and I have already filled out a bugzilla report. From this thread...

[http://ubuntuforums.org/showthread.php?t=772482](http://ubuntuforums.org/showthread.php?t=772482)

In short, I fixed the issue by running

sudo dpkg-reconfigure mythtv-database

This should create the user, password, and database tables for mythtv.

---

### Post by doogy2004 on 2008-06-09
> **reslip said:**
> I ran into this same problem during install and I have already filled out a bugzilla report. From this thread...

[http://ubuntuforums.org/showthread.php?t=772482](http://ubuntuforums.org/showthread.php?t=772482)

In short, I fixed the issue by running

sudo dpkg-reconfigure mythtv-database

This should create the user, password, and database tables for mythtv.

Thanks,
I ran exactly that and now it works like a charm.

Thank you

---

### Post by kwisher on 2008-07-19
> **Nikas said:**
> Try to add the database manually:

```
mysql -u root -p < /usr/share/mythtv/sql/mc.sql
```

Run mythtv-setup after that.

I'm having similar issues connecting to the backend database. When I use the above code it returns:

```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

Any advise would be appreciated.

---

### Post by prkfriryce on 2009-02-09
> **reslip said:**
> I ran into this same problem during install and I have already filled out a bugzilla report. From this thread...

[http://ubuntuforums.org/showthread.php?t=772482](http://ubuntuforums.org/showthread.php?t=772482)

In short, I fixed the issue by running

sudo dpkg-reconfigure mythtv-database

This should create the user, password, and database tables for mythtv.

thanks that also fixed the missing mythconverg db

---

### Post by klc5555 on 2009-02-10
> **pjman said:**
> I'm having a similar problem. I was able to create mythconverg by running

```
mysql -u root -p < /usr/share/mythtv/sql/mc.sql
```

but the mythtv user doesn't have access to the mythconverg database. 

Does anyone know the mysql command to give access to mythtv?

Substitute "-u mythtv" where you have been trying "-u root". In the lunatic Ubuntu world, the emasculated "root" user doesn't get access to the mythconverg database. I think I must have wasted a couple of hours figuring that out the first time I had to restore a mythconverg on a Mythbuntu machine.

---

### Post by dlgaier on 2009-02-11
I'm having problems similar to those above.  I keep getting an:

ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)

I have gone through the troubleshooting link at [https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)
and tried all the sections there.  I have also checked that mysql is working, I have checked that the username and password are correct at /etc/mythtv/mysql.txt, I have run the 'sudo dpkg-reconfigure mythtv-common" and "sudo dpkg-reconfigure mythtv-database' several times.  I get the same 'access denied to user' and 'failed to create database (incorrect admin username/password?).  I feel like I'm starting to go in circles - any suggestions on how to get past this stumbling block?

Some details of the installation-
Started with Ubuntu 7.10 running on an AMD64
Installed mythtv according to instructions at the following site:
[https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop),
but keep running into the problems above during the Mythtv Setup part.

Any suggestions on what I'm doing wrong?  Thanks!

---

### Post by nickrout on 2009-02-11
> **dlgaier said:**
> 
Some details of the installation-
Started with Ubuntu 7.10 running on an AMD64
Installed mythtv according to instructions at the following site:
[https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop),
but keep running into the problems above during the Mythtv Setup part.

Any suggestions on what I'm doing wrong?  Thanks!

Well using about three versions ago would be a poor start!

---

### Post by klc5555 on 2009-02-12
> **dlgaier said:**
> I'm having problems similar to those above.  I keep getting an:

ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)

I have gone through the troubleshooting link at [https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)
and tried all the sections there.  I have also checked that mysql is working, I have checked that the username and password are correct at /etc/mythtv/mysql.txt, I have run the 'sudo dpkg-reconfigure mythtv-common" and "sudo dpkg-reconfigure mythtv-database' several times.  I get the same 'access denied to user' and 'failed to create database (incorrect admin username/password?).  I feel like I'm starting to go in circles - any suggestions on how to get past this stumbling block?

Some details of the installation-
Started with Ubuntu 7.10 running on an AMD64
Installed mythtv according to instructions at the following site:
[https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop),
but keep running into the problems above during the Mythtv Setup part.

Any suggestions on what I'm doing wrong?  Thanks!

I've got idea what you've done wrong to this point ...but at least unlike the previous snarky reply I can tell you how to create a new little stumpy mythconverg, after which (hopefully) you may proceed with the backend setup.

In Mythbuntu, root can't access the mythconverg database. But root does pull up the mysql prompt ("mysql>") where you enter the command to create a new mythconverg database.

The relevant snippet from the Mythtv manual:

[http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance)
---------------------------------------------------------
To restore: (assuming that you've dropped the database)

$ mysql -u root
  mysql>create database mythconverg;
  mysql>exit
$ mysql -u mythtv -pmythtv mythconverg < mythtv_backup.sql

---------------------------------------------------------

It's the first 3 commands that pertain to you (since you've got nothing yet to restore) Don't forget the semicolon (";") in the "create" line. This being 'Buntu, you may have to "sudo" the first line (I can't quite remember, it's been nearly a year since I last needed to create a blank mythconverg database).

If you can create a mythconverg, but still can't proceed with the setup, troubleshooting can start from there. 

Good luck!

---

### Post by dlgaier on 2009-02-12
Ok - thanks for the help, but I'm not sure I got too far.  Here's what happened:

Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 10
Server version: 5.0.45-Debian_1ubuntu3.4-log Debian etch distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> create database mythconverg;
Query OK, 1 row affected (0.09 sec)

mysql> exit
Bye

I then restarted the mysql server just in case it needed to reload this new database:

 * Stopping MySQL database server mysqld                            [ OK ] 
 * Starting MySQL database server mysqld                            [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Does that last line mean there are still problems?  Because when I tried to run the mythtv setup again, I got a window that kept repeating this (which I had actually gotten before):

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-02-12 21:10:52.606 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-02-12 21:10:52.658 Database not open while trying to load setting: TVVidModeResolution
2009-02-12 21:10:52.659 Unable to connect to database!
2009-02-12 21:10:52.659 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

But I know that mysql is running because of the line:
mysql     9613  0.3  4.8 160672 21568 pts/0    Sl   20:49   0:00 /usr/sbin/mysql

Any other suggestions?  Do I need to find the manual for mysql?

Thanks.

---

### Post by nickrout on 2009-02-12
> **dlgaier said:**
> 

Any other suggestions?  Do I need to find the manual for mysql?

Thanks.

I would think using an up to date version would be the best start.

But ```
sudo dpkg-reconfigure mythtv-database 
```should fix it. Really it should, but perhaps it only works properly in recent versions?

---

### Post by klc5555 on 2009-02-13
> **dlgaier said:**
> Ok - thanks for the help, but I'm not sure I got too far.  Here's what happened:

Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 10
Server version: 5.0.45-Debian_1ubuntu3.4-log Debian etch distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> create database mythconverg;
Query OK, 1 row affected (0.09 sec)

mysql> exit
Bye

I then restarted the mysql server just in case it needed to reload this new database:

 * Stopping MySQL database server mysqld                            [ OK ] 
 * Starting MySQL database server mysqld                            [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Does that last line mean there are still problems?  Because when I tried to run the mythtv setup again, I got a window that kept repeating this (which I had actually gotten before):

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-02-12 21:10:52.606 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2009-02-12 21:10:52.658 Database not open while trying to load setting: TVVidModeResolution
2009-02-12 21:10:52.659 Unable to connect to database!
2009-02-12 21:10:52.659 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

But I know that mysql is running because of the line:
mysql     9613  0.3  4.8 160672 21568 pts/0    Sl   20:49   0:00 /usr/sbin/mysql

Any other suggestions?  Do I need to find the manual for mysql?

Thanks.

OK. MySQL is running and you have a mythconverg database. And this database is fine --it gets checked every time the backend starts. If the mythtv user cannot connect to it, it is likely because, in your attempts to reconfigure MySQL the MySQL root password has been altered, and the mythtv user is trying to pass the old password to it. Or, the password the mythtv _frontend_ has (in the "General" screen of the frontend setup) has been altered, without the actual root MySQL password having been changed, so there's a password mismatch between the front and backends. If the MySQL root password did get altered, and neither you nor mythtv know what it is now, it can still be reset (googling "lost mysql password" brings up no end of tutorials), but since you have no data yet to lose in your current installation, it would doubtless require less time to blow your current faulty installation away and reinstall from scratch.

Or, finally, there have been a couple of 7.10 installs I have seen where the networking and hosts installation is not quite perfect, and a combined frontend/backend machine didn't know that 127.0.0.1 was, in fact, 'localhost' (and therefore couldn't connect to the database at 'localhost'). Once I added the IP/hosts information in manually for localhost (in the desktop>system>network), the installations worked.

So I'd check for the obvious password mismatch errors (and the networking error), and if nothing, then cut your lost time and reinstall from scratch from the CD. Whatever the original installation mistake was, all the post-hoc package and configuration mucking with MySQL may have rendered your current installation unsalvageable, or at least not time effective to salvage. 

That being said, I like version 7.10 better than anything which has come later. My myth master backend machine runs version 7.10 because later Mythbunu versions choke on it, and because once I got 7.10 properly configured, it was and is rock-stable and runs myth 0.21 very smoothly. But nickrout is correct insofar as pointing out that 7.10 is due to drop out of support come October or so, and while the Mythtv 0.21 backports run quite well and keep 7.10 compatible with any 0.21 system, fixes are not being applied much (if at all) to these 0.21 backports.You may find yourself later doing patchwork of a sort that is not usual for Ubuntu to keep your 7.10+0.21 installation at 100 percent. 

Cheers! :)

---

### Post by dlgaier on 2009-02-22
Ok, I finally have this part working.  Here's what I THINK happened...

1) I set the network address to the local IP address of the machine on my network instead of the 127.0.0.1 or whatever the default value was.  Not sure this really made any difference, but since I intend to add at least one front-end machine in the future I figured it couldn't hurt.  Unfortunately this didn't seem to fix the problem, but included it here for completeness.

2) While working with mysql, I realized I was able to log in as root, but not as mythtv.  I'm not sure I really should be able to do this, but it got me thinking - maybe the mythtv account either didn't exist or was damaged, so I did some reading on the [www.mysql.com](www.mysql.com) website.

3) I logged into mysql as root, and did a '> CREATE USER' for 'mythtv'@'localhost', using the password that the setup kept telling me was the one for mythtv (i.e. the 'reconfigure mythtv-database' command).

4) Because I had created the mythconverg database with the root account, I had to then '> GRANT' mythtv the access rights to this database.

Once I did those things, I didn't have any more problems with accessing the database.  I have finished most of the remaining setup, but still can't seem to watch live TV - I get a blank screen for a few seconds, then it goes back to the menu.  I must have some settings wrong, so it's back to the troubleshooting section.

Anyway, thanks for the suggestions - they got me heading in the right direction.

---

### Post by nickrout on 2009-02-22
as for getting livetv, there will be stuff in the logs that will give a clue.

The log is /var/log/mythtv/mythfrontend.log

---

### Post by dlgaier on 2009-02-22
> **nickrout said:**
> as for getting livetv, there will be stuff in the logs that will give a clue.

The log is /var/log/mythtv/mythfrontend.log


Yea - just looked there - as best I can tell the error was about the program not having the proper permission to open a file in the recording directory - something about (fd -1)?  My gut feeling is that the file permissions on the directories are not set correctly, but I'm checking into that now ...

---

