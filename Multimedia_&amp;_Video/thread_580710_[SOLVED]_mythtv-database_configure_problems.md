---
title: "[SOLVED] mythtv-database configure problems"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by Blairboy on 2007-10-19
Ok, I had a working backend and connect to it from the same computer and through a frontend on a laptop as well.  I upgraded to gutsy and mythtv-database is whining at me now with an error I don't know how to fix.

```
Setting up mythtv-database (0.20.2-0ubuntu10) ...
Failed to execute SQL: GRANT ALL PRIVILEGES ON mythtv.* TO root@localhost IDENTIFIED BY 'password'\nAccess denied for user 'root'@'%' to database 'mythtv' at -e line 8, <> line 1.
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 255

```

Everything is fine with the database and I can connect to it through command line and through phpmyadmin.  Any ideas on how to remedy this?  I miss my mythtv.  :(

---

### Post by Blairboy on 2007-10-19
Nobody has any ideas or experiencing the same problem?

---

### Post by Blairboy on 2007-10-19
I'm now thoroughly confused.  Here's a line from mythfrontend:

```
2007-10-19 02:21:59.968 Connected to database 'mythtv' at host: 192.168.1.107

```

But it then says this during the same session:

```
2007-10-19 02:22:41.561 Connection timed out.
                        You probably should modify the Master Server
                        settings in the setup program and set the
                        proper IP address.

```

---

### Post by superm1 on 2007-10-19
Okay a few things.

If mythtv-database is borking out on you like that, did you set a root mysql-password?  If so, you need to do this:

```
sudo dpkg-reconfigure mythtv-database
```

And pop in that password that you set for the root user.

As for connecting to the master database, click system-administration- "MythTV setup".  Double check that the IPs listed in the general tab are correct.

If those are correct, then take a look over at ```
/var/log/mythtv/mythbackend.log
``` for what's happening.

---

### Post by Blairboy on 2007-10-19
I have a root password set up and I had it in myth prior to the upgrade.  It was connecting fine.

I ran ```
sudo dpkg-reconfigure mythtv-database 
``` again and typed in the ip address and password and enabled remote connections.

I restarted the backend and opened the frontend.  this is what the backend log had to allow:

```
2007-10-19 10:20:08.417 Failed to init MythContext, exiting.
2007-10-19 10:24:39.982 Using runtime prefix = /usr
2007-10-19 10:24:40.016 New DB connection, total: 1
2007-10-19 10:24:40.025 Unable to connect to database!
2007-10-19 10:24:40.029 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-19 10:24:40.082 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-19 10:24:40.133 Failed to init MythContext, exiting.
```

I'm not sure why its trying to connect with the mythtv user, because root is set as the user in the backend setup, frontend setup, /etc/mythtv/mysql.txt, and ~/home/user/.mythtv/mysql.txt.

---

### Post by Blairboy on 2007-10-19
Anybody know where myth is getting the incorrect user from?  Because its supposed to be using root to connect to the database, but the backend log says that its trying to use mythtv as the mysql user.

---

### Post by superm1 on 2007-10-19
*sigh*

Okay lets see if i can hammer out an explanation here.

**mythtv-database**
When you first install mythtv, mythtv-database is installed.  The purpose of this package (in gutsy) is to create a new database, new user, and prefill that database with some data.

That new user is the mysql 'mythtv' user.  This is the *only* time that that root password is used.  So when you dpkg-reconfigure mythtv-database, you are providing information to *create* that new user, not the information that user uses.

**mythtv-common**
The information that is actually used to connect to the database is handled by mythtv-common.  When you dpkg-reconfigure mythtv-common, you provide the information about the user created when mythtv-database was installed.

**mysql.txt**
Okay there are three places this file can be found.  REMOVE ~/.mythtv/mysql.txt, /home/mythtv/.mythtv/mysql.txt.  You don't want either of those.  Just use the systemwide /etc/mythtv/mysql.txt  You are asking for trouble otherwise.  When you dpkg-reconfigure mythtv-common, this information is placed into /etc/mythtv/mysql.txt.  If you don't know the information for your mythtv user in mysql, you will need to reset his password manually.

---

### Post by Blairboy on 2007-10-19
Awesome.  Removed the two files, dpkg-reconfigured common/database, restarted the backend and it worked.  I do have one other issue to resolve though (yes, I know, I'm a pain in the ***).  I have 2 dvd drives and I was able to rip with either of them prior to the upgrade.  Now the dvd importer doesn't recognize the dvd-rw drive, which worked fine before.  The confusing thing is that if I tell myth to eject the drive, it has the info for the dvd displayed.  I even tried changing the dvd settings to /dev/hdc, but still no dice.  Any ideas?

Thanks so much for the help by the way.

---

### Post by superm1 on 2007-10-19
> **Blairboy said:**
> Awesome.  Removed the two files, dpkg-reconfigured common/database, restarted the backend and it worked.  I do have one other issue to resolve though (yes, I know, I'm a pain in the ***).  I have 2 dvd drives and I was able to rip with either of them prior to the upgrade.  Now the dvd importer doesn't recognize the dvd-rw drive, which worked fine before.  The confusing thing is that if I tell myth to eject the drive, it has the info for the dvd displayed.  I even tried changing the dvd settings to /dev/hdc, but still no dice.  Any ideas?

Thanks so much for the help by the way.
No ideas there.  Check where it's trying to rip to and permissions, only two items I could think would have changed on the upgrade.

---

### Post by Blairboy on 2007-10-19
I can rip with the other drive, so the paths are fine.  I can play the dvd with the dvd-rw drive, but it just doesn't come up when I open the rip dialog, whereas it recognizes it with the other drive.

---

