---
title: "mySQL won't start, following power a failure"
date: 2012-10-28
forum: Mythbuntu
---

### Post by neutron68 on 2012-10-28
This isn't Mythbuntu, but mySQL is used across all the mythtv distros, so there is likely someone that knows mySQL better than I.

The mySQL on my friend's Knoppmyth R5.5 machine won't start, following a power failure.
The machine starts and runs, but since mySQL isn't running, mythtv can't do anything.

Since SSH still works fine, I looked around his machine via SSH.
I can see that mythtv keeps trying to connect to the database (over and over) and fails.
The Mythtv backend log shows:
```
Cannot login to database?

Would you like to configure the database connection now? [yes]
[console is not interactive, using default 'yes']
Database host name: [localhost]
[console is not interactive, using default 'localhost']
Should I test connectivity to this host using the ping command? [yes]
[console is not interactive, using default 'yes']
Database non-default port: [0]
[console is not interactive, using default '0']
Database name: [mythconverg]
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]
[console is not interactive, using default 'mythtv']
Database password: [mythtv]
[console is not interactive, using default 'mythtv']
Unique identifier for this machine (if empty, the local host name will be used)$
[console is not interactive, using default '']
```

I looked at his syslog file a day or 2 after the power failure.
It looks like power died around 3pm on Oct.3.  When power came back at 5pm (17:04 hours), it booted and mysql detected the crash:

```
Oct  3 17:04:11 mythtv mysqld_safe[3262]: started
Oct  3 17:04:11 mythtv mysqld[3265]: 121003 17:04:11  InnoDB: Database was not shut down normally!
Oct  3 17:04:11 mythtv mysqld[3265]: InnoDB: Starting crash recovery.
Oct  3 17:04:11 mythtv mysqld[3265]: InnoDB: Reading tablespace information from the .ibd files...
Oct  3 17:04:11 mythtv mysqld[3265]: InnoDB: Restoring possible half-written data pages from the doublewrite
Oct  3 17:04:11 mythtv mysqld[3265]: InnoDB: buffer...
Oct  3 17:04:11 mythtv mysqld[3265]: 121003 17:04:11  InnoDB: Starting log scan based on checkpoint at
Oct  3 17:04:11 mythtv mysqld[3265]: InnoDB: log sequence number 0 111426.
Oct  3 17:04:11 mythtv mysqld[3265]: InnoDB: Doing recovery: scanned up to log sequence number 0 111426
Oct  3 17:04:11 mythtv mysqld[3265]: 121003 17:04:11  InnoDB: Started; log sequence number 0 111426
Oct  3 17:04:11 mythtv mysqld[3265]: 121003 17:04:11 [Note] /usr/sbin/mysqld: ready for connections.
Oct  3 17:04:11 mythtv mysqld[3265]: Version: '5.0.32-Debian_7etch1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution
Oct  3 17:04:12 mythtv /etc/mysql/debian-start[3302]: Upgrading MySQL tables if necessary.
Oct  3 17:04:12 mythtv ntpdate[2803]: step time server 64.73.32.134 offset 0.232328 sec
Oct  3 17:04:13 mythtv /etc/mysql/debian-start[3348]: Checking for crashed MySQL tables.
```

My friend manually restarted around noon on Oct.4 and mysql compained some more:
```
Oct  4 12:23:01 mythtv mysqld_safe[3232]: started
Oct  4 12:23:01 mythtv mysqld[3235]: 121004 12:23:01  InnoDB: Database was not shut down normally!
Oct  4 12:23:01 mythtv mysqld[3235]: InnoDB: Starting crash recovery.
Oct  4 12:23:01 mythtv mysqld[3235]: InnoDB: Reading tablespace information from the .ibd files...
Oct  4 12:23:01 mythtv mysqld[3235]: InnoDB: Restoring possible half-written data pages from the doublewrite
Oct  4 12:23:01 mythtv mysqld[3235]: InnoDB: buffer...
Oct  4 12:23:01 mythtv mysqld[3235]: 121004 12:23:01  InnoDB: Starting log scan based on checkpoint at
Oct  4 12:23:01 mythtv mysqld[3235]: InnoDB: log sequence number 0 111426.
Oct  4 12:23:01 mythtv mysqld[3235]: InnoDB: Doing recovery: scanned up to log sequence number 0 111426
Oct  4 12:23:01 mythtv mysqld[3235]: 121004 12:23:01  InnoDB: Started; log sequence number 0 111426
Oct  4 12:23:01 mythtv mysqld[3235]: 121004 12:23:01 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect file format 'db'
Oct  4 12:23:01 mythtv mysqld_safe[3246]: ended
Oct  4 12:23:05 mythtv ntpdate[2771]: step time server 38.229.71.1 offset -0.019226 sec
Oct  4 12:23:07 mythtv kernel: eth0: no IPv6 routers present
Oct  4 12:23:13 mythtv kernel: Clocksource tsc unstable (delta = 3917961016 ns)
Oct  4 12:23:15 mythtv /etc/init.d/mysql[3381]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Oct  4 12:23:15 mythtv /etc/init.d/mysql[3381]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Oct  4 12:23:15 mythtv /etc/init.d/mysql[3381]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Oct  4 12:23:15 mythtv /etc/init.d/mysql[3381]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Oct  4 12:23:15 mythtv /etc/init.d/mysql[3381]:
```

With the thought that his mythconverg database files might be corrupted, I did try and repair the mySQL tables following this forum post:
[http://forum.linhes.org/viewtopic.php?f=21&t=20885](http://forum.linhes.org/viewtopic.php?f=21&t=20885)

1. /etc/init.d/mythtv-backend stop 
2. /etc/init.d/mysql stop 
3. cd /var/lib/mysql/mythconverg 
4. myisamchk -f -r *.MYI 
     During this part, it says it's fixing database records.  Then it finishes.
5. /etc/init.d/mysql start 
     At this point, I always get the  "Starting MySQL database server: mysqld. . . . . . . . . . . failed!" message.

When I compare my friend's database file folder (/var/lib/mysql/mythconverg) with the same folder in my still-functioning R5.5 machine, it looks like all the database files are there.

I found 2 posts from Ubuntu users with the exact same symptoms.  In both cases, the users reinstalled mySQL - they never figured out how to replace the 1 or 2 needed files, etc.
[http://askubuntu.com/questions/139859/mysql-service-do-not-launch](http://askubuntu.com/questions/139859/mysql-service-do-not-launch)
[http://www.edugeek.net/forums/nix/97829-mysql-headaches.html](http://www.edugeek.net/forums/nix/97829-mysql-headaches.html)

The mySQL version in Knoppmyth R5.5 is version 5.0.32 from 2008.

I searched for and found archive repositories at:  [http://archive.debian.org/debian/dists/](http://archive.debian.org/debian/dists/)

Knoppmyth R5.5 was created mainly from the Debian etch branch, so I was pretty sure I could pull "vintage 2008" apt-get files from:
[http://archive.debian.org/debian/dists/etch/](http://archive.debian.org/debian/dists/etch/)

I inserted the following lines in my /etc/apt/sources.list:
```
deb http://archive.debian.org/debian/ etch main
deb-src http://archive.debian.org/debian/ etch main
```

I was able to successfully have the "apt-get update" command talk to it and get an update list of packages!

Next, I was able to fetch mysql-server-5.0 from the etch archive, but it won't finish installing...no idea why.
I've tried several times.

FIRST TIME:
```
root@mythtv:~# apt-get install mysql-server-5.0
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libmysqlclient15off mysql-client-5.0 mysql-common
Suggested packages:
  tinyca
Recommended packages:
  mailx
The following packages will be upgraded:
  libmysqlclient15off mysql-client-5.0 mysql-common mysql-server-5.0
4 upgraded, 0 newly installed, 0 to remove and 122 not upgraded.
Need to get 34.4MB of archives.
After unpacking 311kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://archive.debian.org etch/main mysql-common 5.0.32-7etch12 [55.9kB]
Get:2 http://archive.debian.org etch/main libmysqlclient15off 5.0.32-7etch12 [1795kB]
Get:3 http://archive.debian.org etch/main mysql-client-5.0 5.0.32-7etch12 [7194kB]
Get:4 http://archive.debian.org etch/main mysql-server-5.0 5.0.32-7etch12 [25.4MB]
Fetched 34.4MB in 1m59s (288kB/s)
Preconfiguring packages ...
(Reading database ... 92282 files and directories currently installed.)
Preparing to replace mysql-common 5.0.32-7etch1 (using .../mysql-common_5.0.32-7etch12_all.deb) ...
Unpacking replacement mysql-common ...
Preparing to replace libmysqlclient15off 5.0.32-7etch1 (using .../libmysqlclient15off_5.0.32-7etch12_i386.deb) ...
Unpacking replacement libmysqlclient15off ...
Preparing to replace mysql-client-5.0 5.0.32-7etch1 (using .../mysql-client-5.0_5.0.32-7etch12_i386.deb) ...
Unpacking replacement mysql-client-5.0 ...
Setting up mysql-common (5.0.32-7etch12) ...
(Reading database ... 92282 files and directories currently installed.)
Preparing to replace mysql-server-5.0 5.0.32-7etch1 (using .../mysql-server-5.0_5.0.32-7etch12_i386.deb) ...
Stopping MySQL database server: mysqld.
Stopping MySQL database server: mysqld.
Unpacking replacement mysql-server-5.0 ...
Setting up libmysqlclient15off (5.0.32-7etch12) ...
Setting up mysql-client-5.0 (5.0.32-7etch12) ...
Setting up mysql-server-5.0 (5.0.32-7etch12) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld . . . . . . . . . . . . . . failed!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@mythtv:~#
```

MOST RECENT TIME:
```
root@mythtv:/var/lib/mysql/mythconverg# apt-get install mysql-server-5.0
Reading package lists... Done
Building dependency tree... Done
mysql-server-5.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 122 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.32-7etch12) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld . . . . . . . . . . . . . . failed!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@mythtv:/var/lib/mysql/mythconverg#
```

Of note, I tried to restore an automatic backup of the mythconverg database file.  
They get automatically backed up to /var/backups/

The catch-22 is that since mysql won't run, I can't use mysql to restore the backup!

I started by using gunzip to unzip the more recent, clean mythconverg.sql.gz file.
Then...
```
root@mythtv:/var/lib/mysql/mythconverg# mysql -u mythtv -pmythtv mythconverg < /var/backups/mythconverg.sql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

I'm trying, but I keep hitting brick walls...

I reloaded it several times and it just won't start?!
Anyone see anything familiar with what mySQL is doing?

Eric

---

### Post by Rotak on 2012-10-29
First thing I recognized is your command to restore the database backup. Try to use the mysql command like this:
```
mysql -u mythtv -p mythconverg .....
```I don't believe you can use "-p[PASSWORD]". If you want to do this, I think you need to use "--password=[YOURPASS]". If you use "-p" only, it will ask you to enter the password before the action starts.

Other things that may cause mysql to fail starting/installing are:

[LIST]
[*]Insufficient disk space.
Make sure you have enough disk space left ```
df -h
```
[*]Mysql being unable to (re-)create the sock file.
So, stop myth-backend and mysql and delete /var/run/mysql/mysqld.sock.
[/LIST]

Both issues can also lead to failure of installing the dpkg packages.

---

### Post by neutron68 on 2012-10-29
Those are reasonable thoughts.

1.  I tried all variations of the password command and all had the same result, where mySQL didn't start up:
-pPASSWORD
--password=PASSWORD
-p (password to be entered when prompted)
Of note, mySQL won't start, when you simply type mySQL as root.

2.  Checking disk space was my first check - not a problem.
The root (boot) partition is 20GB and is 65% free.

3.  There is no /var/run/mysqld/mysqld.sock file to delete.
(In 2008, Knoppmyth used the /var/run/mysqld directory rather than the /var/run/mysql directory for the mysqld.sock file.)

I'm open to other thoughts.

Thanks,
Eric

---

### Post by Rotak on 2012-10-29
Did you try to run "mysqld_safe"? It may show or log additional error messages.

---

### Post by nickrout on 2012-10-29
> 01 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect file format 'db'


This is mysql's own privilege tables I think, not the mythconverg database. Fix thos tables, not mythconverg.

---

### Post by neutron68 on 2012-10-29
> **nickrout said:**
> This is mysql's own privilege tables I think, not the mythconverg database. Fix thos tables, not mythconverg.
So, I should change to the mysql directory and rerun the fix command?
```
cd /var/lib/mysql/mysql 
myisamchk -f -r *.MYI 
```
If different, please specify.

Thanks.
Eric

---

### Post by nickrout on 2012-10-29
> **neutron68 said:**
> So, I should back up one directory level and rerun the fix command?
```
cd /var/lib/mysql/ 
myisamchk -f -r *.MYI 
```
If different, please specify.

Thanks.
Eric/var/lib/mysql/mysql

---

### Post by neutron68 on 2012-10-29
It looks like you were answering as I was correcting the directory in my post. :)

Good.  We're on the same page (and directory) :)

Eric

---

### Post by neutron68 on 2012-11-04
It's fixed!

I was able to connect to an archived repository from 2008 and pull the same version of the mysql-server-5.0.
Unfortunately, the dpkg process did NOT fully complete, so I wasn't able to reinstall mysql-server-5.0.
It turns out that reinstalling mysql-server-5.0 would not have helped in this case, anyway.

I finally got hold of my friend Brad to look at this with me.  He was able to get mysql started and forced a rebuild of the damaged database.
He looked at the error messages and saw that the "db" table (part of the "mysql" database) was the corrupted one - not the mythtv "mythconverg" database.

Here is Brad's description of what he had to do to fix the database problems.
> 
It was fairly easy to fix once the exact problem was understood.

I didn't cut any log or error snippets, but the key error message ended up being:  ```
[ERROR] Fatal error: Can't open and lock privilege tables: Incorrect file format 'db'
```

mySQL stores data on disk organized fairly logically - /var/lib/mysql is the base directory, and sub-directories are different databases, with the file groups in those directories being individual table information (generally).

The mySQL privilege information determines what users have access to which data, and is stored in the "mysql" database in the "db" table.  The confusing part was that the error was complaining about an incorrect file format ('db'), which led me to think that somehow the format of a table was changed to something inappropriate.

However, what the error actually is trying to say is "table 'db' has an incorrect file format" - in other words, it's corrupted.

So, I started the mySQL server on a separate VTTY in a mode that essentially bypassed the privilege/user mechanism (and related tables):  ```
mysqld --skip-grant &
```

From there, I could start the mySQL command line console on another VTTY.  Because the privilege/user mechanism had been bypassed, I checked to see that the user table was OK by manually inserting a new user.

From the mysql command line console, first ```
use user;
``` then ```
insert into user values('localhost','maint','','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
``` verified that mySQL and the user table was functioning as expected.

However an error similar to the original error above appeared on the VTTY that mysqld was launched from, as well as a warning indicated on command execution within the command line interface (but no specifics).

From the command line console, ```
a repair table db;
``` showed that it was damaged/corrupt, and normal repair methods weren't going to work.

Although this is generally used as a last resort, I opted to take a more blunt approach and force it to try and recreate the MYI information from the FRM file - ```
repair table db use_frm;
```

Ultimately, that is what brought some level of functionality back.  Although, deleting the "db" table and restoring/recreating it would have allowed things to start again, it would likely have smashed the MythTV functionality and required a lot more forensic rebuilding than I had time or patience to do.
All is working again on the Knoppmyth R5.5 machine.  In the end, it was a corrupted mysql database file!  The trick was getting mysql to start up in a broken state!

I hope this helps someone else!
Eric

---

