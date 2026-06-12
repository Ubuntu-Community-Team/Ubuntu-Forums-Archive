---
title: "Master Backend Server?"
date: 2007-10-07
forum: Mythbuntu
---

### Post by mwacky on 2007-10-07
Upgraded from Feisty to Gusty, then added Mythbuntu by launching from website.

Capture Card (lspci):
```
00:11.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:11.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)


```
Had tried MythTV before but have always received this error when trying to watch tv:

> Could not connect to the master backend server -- is it running?  Is the IP address set for it in the setup program correct?

Seems like I have everything set in the Backend and Frontend Setup properly, looks good from the Mythbuntu Control Centre.  
 
Has decent video for an older card, but has no sound with TV Time which I believe is related to [Launchpad Bug #29789]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/29789").  The sound problem shouldn't stop mythtv from running or have a problem with the backend server, right?

---

### Post by superm1 on 2007-10-07
> **mwacky said:**
> Upgraded from Feisty to Gusty, then added Mythbuntu by launching from website.

Capture Card (lspci):
```
00:11.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:11.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)


```Had tried MythTV before but have always received this error when trying to watch tv:



Seems like I have everything set in the Backend and Frontend Setup properly, looks good from the Mythbuntu Control Centre.  
 
Has decent video for an older card, but has no sound with TV Time which I believe is related to [Launchpad Bug #29789]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/29789").  The sound problem shouldn't stop mythtv from running or have a problem with the backend server, right?

First:
Checkout /var/log/mythtv/mythbackend.log.  Check for any errors with permissions or startup.

Next:
Also check and make sure you **don't** have a ~/.mythtv/mysql.txt.  Make sure you **don't** have a /home/mythtv/.mythtv/mysql.txt too.  If you have either, get rid of it.

Lastly:
Configure the backend by going into mythbuntu control centre, and choosing the mythtv-setup button.

---

### Post by mwacky on 2007-10-08
> First:
Checkout /var/log/mythtv/mythbackend.log.  Check for any errors with permissions or startup.

Nothing in the log


> Next:
Also check and make sure you **don't** have a ~/.mythtv/mysql.txt.  Make sure you **don't** have a /home/mythtv/.mythtv/mysql.txt too.  If you have either, get rid of it.

```
mwacker@Barney:~$ ls /home/mwacker/.mythtv/
channels  mysql.txt  themecache
mwacker@Barney:~$ sudo rm /home/mwacker/.mythtv/mysql.txt 
```


> Lastly:
Configure the backend by going into mythbuntu control centre, and choosing the mythtv-setup button.

After running MythTv Setup from Control Center it became stuck on *Configuring Automatic Login* and attempt to send a bug report, but failed doing that.

Then ran updates and received this message:

```

MythTV-Database reconfigure required

The mythtv-database package was upgraded or installed, but was unable to contact a MySQL server.
If you were in the process of dist-upgrading, this is normal as mysql-server is stopped for a portion of the upgrade.
If this is a fresh package installation, verify that mysql-server is installed and running.  Once you have verified the server is running, you can reconfigure the package by running 'sudo dpkg-reconfigure mythtv-database'.
If your root password or location of the MySQL server are non standard, you can also update them via 'sudo dpkg-reconfigure mythtv-database'.
```

Will restart and see if the setup works and make sure mysql is running.

---

### Post by mwacky on 2007-10-08
> Will restart and see if the setup works and make sure mysql is running.
Well still receiving the same error but looked at the latest log:

```

2007-10-07 18:11:59.783 Using runtime prefix = /usr
2007-10-07 18:11:59.933 New DB connection, total: 1
2007-10-07 18:11:59.956 Unable to connect to database!
2007-10-07 18:11:59.957 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-07 18:12:00.020 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-07 18:12:00.075 Failed to init MythContext, exiting.
2007-10-08 19:13:06.075 Using runtime prefix = /usr
2007-10-08 19:13:06.409 New DB connection, total: 1
2007-10-08 19:13:06.436 Unable to connect to database!
2007-10-08 19:13:06.438 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-08 19:13:06.500 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-08 19:13:06.568 Failed to init MythContext, exiting.

```

I can look at MySql with Webmin and see the mythtv user, tried giving user full permissions.

---

### Post by superm1 on 2007-10-09
> **mwacky said:**
> Well still receiving the same error but looked at the latest log:

```

2007-10-07 18:11:59.783 Using runtime prefix = /usr
2007-10-07 18:11:59.933 New DB connection, total: 1
2007-10-07 18:11:59.956 Unable to connect to database!
2007-10-07 18:11:59.957 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-07 18:12:00.020 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-07 18:12:00.075 Failed to init MythContext, exiting.
2007-10-08 19:13:06.075 Using runtime prefix = /usr
2007-10-08 19:13:06.409 New DB connection, total: 1
2007-10-08 19:13:06.436 Unable to connect to database!
2007-10-08 19:13:06.438 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-10-08 19:13:06.500 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-10-08 19:13:06.568 Failed to init MythContext, exiting.

```I can look at MySql with Webmin and see the mythtv user, tried giving user full permissions.
Did you follow what I said and rm ~/.mythtv/mysql.txt?

As long as you don't touch the mythtv password, it is all read from /etc/mythtv/mysql.txt

---

### Post by mwacky on 2007-10-09
> **superm1 said:**
> Did you follow what I said and rm ~/.mythtv/mysql.txt?

As long as you don't touch the mythtv password, it is all read from /etc/mythtv/mysql.txt

Yes, after I delete mysql.txt MythTV frontend sends me through the setup again. If I do not change to the proper password, I am just sent through the setup again and again.  But if I do change the password for the mythtv user, I get the same IP error for the backend server and mysql.txt is created again.  Unfortunately I have altered the mythtv password.  How can I reset the mythtv user password without having setup create mysql.txt?

Thanks!

---

### Post by superm1 on 2007-10-09
> **mwacky said:**
> Yes, after I delete mysql.txt MythTV frontend sends me through the setup again. If I do not change to the proper password, I am just sent through the setup again and again.  But if I do change the password for the mythtv user, I get the same IP error for the backend server and mysql.txt is created again.  Unfortunately I have altered the mythtv password.  How can I reset the mythtv user password without having setup create mysql.txt?

Thanks!

If the root password is different than the generated password initially, run this:

```
sudo dpkg-reconfigure mythtv-database
```

This will populate the db properly.

You can update the password that is supposed to be used via ( in the fe and be ) via

```
sudo dpkg-reconfigure mythtv-common
```

---

### Post by mwacky on 2007-10-09
Thanks for all your help!

After you mentioned /etc/mythtv/mysql.txt held all the passwords.  I changed to the proper password in this file, deleted from /home/user/.mythtv and ran today's updates.  After restarting, I now have my first working MythTV setup!!!  I'm so happy, even though video and audio quality aren't great on this dinosaur capture card and box, I have finally made it work!!

---

### Post by CaptainPatent on 2007-10-11
I'm a bit confused here. I was having an identical problem to mwacky (frontend giving a "could not connect to the database" error). I also messed around with the mysql password so I figured I was in the same boat. I have gotten to the same point that mwacky described where every time you run the frontend it goes through setup and always says it cannot connect to the database.
I deleted ~/.mythtv/mysql.txt and the  /home/mythtv/.mythtv/ directory didn't exist so that should have been ok
I made sure I had the correct password I entered for the mysql database by looking at the /etc/mythtv/mysql.txt file and then I ran

```
sudo dpkg-reconfigure mythtv-database
```

After trying to run that I get the error message:

```
Failed to connect to database: Access denied for user 'mythtv'@'localhost' (using password: YES) at -e line 5, <> line 1,
failed to create database (incorrect admin username/password?)
It's also possible mysql-server wasn't running. After install is complete you will need to make sure mysql-server is running and that you supplied correct information. Try: sudo dpkg-reconfigure mythtv-database.
```

I've tried setting up the password to be the administrator account along with two other username/password combinations of my own. Does the mysql database need to have the same password as the administrator account, or is this just an administrator account for mysql itself? (I noticed by default it was a random combination)

I'm now in a position though that the frontend won't run (just  goes through setup and says "could not connect to mysql database)

---

### Post by CaptainPatent on 2007-10-12
Ha, Nevermind I got it figured out.

---

### Post by palmnut on 2007-10-15
> **superm1 said:**
> Next:
Also check and make sure you **don't** have a ~/.mythtv/mysql.txt.  Make sure you **don't** have a /home/mythtv/.mythtv/mysql.txt too.  If you have either, get rid of it.

If you're running Myth split between two machines, would you do this on the backend, frontend or both machines?

I'm running the backend on one laptop and am trying to run the front end on another over the network; alas I'm having troubel accessing both the MySQL DB reliably (sometimes it opens, mosttimes it fails) and the backend server at all. The irony is that I can get it to work perfectly if I access it from Windoze using MyTV Player on the wife's machine. This is annoying, so I'm clutching at straws.

---

### Post by superm1 on 2007-10-15
> **palmnut said:**
> If you're running Myth split between two machines, would you do this on the backend, frontend or both machines?

I'm running the backend on one laptop and am trying to run the front end on another over the network; alas I'm having troubel accessing both the MySQL DB reliably (sometimes it opens, mosttimes it fails) and the backend server at all. The irony is that I can get it to work perfectly if I access it from Windoze using MyTV Player on the wife's machine. This is annoying, so I'm clutching at straws.
You shouldn't have ~/.mythtv/mysql.txt or /home/mythtv/.mythtv/mysql.txt on *any* machines.

On the frontend, you will have to call
dpkg-reconfigure mythtv-common to update the systemwide mysql.txt

---

### Post by oobe-feisty on 2007-10-20
> **CaptainPatent said:**
> Ha, Nevermind I got it figured out.

did it ever occur to you that other people might want to know what happened other people read these threads in order to resolve there own problems

---

### Post by rothgar on 2007-10-21
I sorta have the same issue.

my frontend/backend connects just fine when all the IP addresses are set to 127.0.0.1.  I can go into mythtv-setup and change the IP address of the backend to 192.168.2.20 (the IP of my machine) and everything works fine.  But when I go to the frontend -> setup -> general and change the IP there to 192.168.2.20 I cannot connect. I commented out bind-address in /et/mysql/my.cnf and I set the mysql permissions to allow all IP addresses 
> $ mysql -u root mythconverg
mysql> grant all on mythconverg.* to mythtv@"%" identified by "mythtv";
mysql> flush privileges;

and I deleted the mysql.txt file.  I still cannot connect if I try to connect to 192.168.2.20.  Anything else I am supposed to do?  If I delete the mysql.txt file does the mythtv password change?

---

### Post by arrhn on 2008-12-14
If you still have problems connecting but all the user-password combinations seem to work when you try them by hand, search in /var for an old mysql.txt and delete it.  I found one in /var/lib/mythtv/.mythtv that was being read by mythtv-backend instead of the intended one in /etc/mythtv.

---

