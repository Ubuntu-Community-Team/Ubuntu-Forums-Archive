---
title: "Need help getting mythbuntu to work"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by tech9 on 2008-01-04
After installing mythbuntu and using this command...
```
sudo apt-get install mythtv mythtv-themes
```I followed the myth community link ...

                                 [https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop)
 (followed step by step)

I am receiving the following error...

```

AMD@AMD-desktop:~$ more /var/log/mythtv/mythbackend.log
2008-01-03 19:30:50.400 Using runtime prefix = /usr
2008-01-03 19:30:50.727 New DB connection, total: 1
2008-01-03 19:30:50.767 Unable to connect to database!
2008-01-03 19:30:50.769 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-03 19:30:50.852 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-03 19:30:50.904 Failed to init MythContext, exiting.
2008-01-03 19:33:57.821 Using runtime prefix = /usr
2008-01-03 19:33:58.063 New DB connection, total: 1
2008-01-03 19:33:58.069 Unable to connect to database!
2008-01-03 19:33:58.070 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-03 19:33:58.124 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-03 19:33:58.175 Failed to init MythContext, exiting.
2008-01-03 19:35:52.650 Using runtime prefix = /usr
2008-01-03 19:35:52.677 New DB connection, total: 1
2008-01-03 19:35:52.683 Unable to connect to database!
2008-01-03 19:35:52.684 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-03 19:35:52.738 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-03 19:35:52.789 Failed to init MythContext, exiting.
2008-01-03 19:40:32.651 Using runtime prefix = /usr
2008-01-03 19:40:32.928 New DB connection, total: 1
2008-01-03 19:40:32.934 Unable to connect to database!
2008-01-03 19:40:32.935 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-03 19:40:32.989 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-03 19:40:33.041 Failed to init MythContext, exiting.
2008-01-03 19:47:45.297 Using runtime prefix = /usr
2008-01-03 19:47:45.808 New DB connection, total: 1
2008-01-03 19:47:45.814 Unable to connect to database!
2008-01-03 19:47:45.815 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-03 19:47:45.869 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-03 19:47:45.920 Failed to init MythContext, exiting.
2008-01-03 20:38:02.458 Using runtime prefix = /usr
2008-01-03 20:38:02.745 New DB connection, total: 1
2008-01-03 20:38:02.757 Unable to connect to database!
2008-01-03 20:38:02.784 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-03 20:38:03.107 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-03 20:38:03.372 Failed to init MythContext, exiting.
2008-01-03 20:41:22.044 Using runtime prefix = /usr
2008-01-03 20:41:22.506 New DB connection, total: 1
2008-01-03 20:41:22.512 Unable to connect to database!
2008-01-03 20:41:22.513 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-03 20:41:22.568 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-03 20:41:22.619 Failed to init MythContext, exiting.
2008-01-03 20:42:24.233 Using runtime prefix = /usr
2008-01-03 20:42:24.253 New DB connection, total: 1
2008-01-03 20:42:24.259 Unable to connect to database!
2008-01-03 20:42:24.260 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-03 20:42:24.314 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-03 20:42:24.365 Failed to init MythContext, exiting.
2008-01-03 20:45:38.294 Using runtime prefix = /usr
2008-01-03 20:45:38.320 New DB connection, total: 1
2008-01-03 20:45:38.337 Unable to connect to database!
2008-01-03 20:45:38.338 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-01-03 20:45:38.393 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-01-03 20:45:38.444 Failed to init MythContext, exiting.

```I realize that the user name and password is being denied, so the steps that took after that was to purge the sql DB and reinstall it...

```

sudo apt-get remove --purge mythtv-database mysql-server-5.0
sudo apt-get install mysql-server-5.0 mythtv-database

```

then I gave the same password that mythbuntu  provides...

and still getting errors.

Can someone help me please?

Thanks!

---

### Post by finneces on 2008-01-05
I have the exact same problem and have been trying for days to get passed it.  I found these myth mysql instructions but it didt help me:
[http://www.mythtv.org/docs/mythtv-HOWTO-6.html](http://www.mythtv.org/docs/mythtv-HOWTO-6.html)

I would really like to get this working.  Please let me know if you figure it out!

---

### Post by finneces on 2008-01-05
Try this:

in your user home directory you can find ~/.mythtv/mysql.txt
or also in /etc/mythtv/mysql.txt.   Make sure they both have the same password.  Then set that password in mysql:

```

mysql -u root -p
enter password

mysql> SET PASSWORD FOR 'mythtv'@'localhost' = PASSWORD('RjD3jan');
Query OK, 0 rows affected (0.00 sec)

mysql> quit
Bye

```

Then test if you can enter mysql with that password:
```
mysql -u mythtv -pRjD3jan
```

You might also need to set up the access priveledges for mythtv:

```
$ mysql -u root -p mythconverg
mysql> grant all on mythconverg.* to mythtv@"%.mydomain.com" identified by "mythtv";
mysql> flush privileges;
```

That did the trick for me!
Now my problem is Im running out of memory.  I knew the day would come when 512 would no longer be enough!

---

### Post by tech9 on 2008-01-07
> **finneces said:**
> Try this:

in your user home directory you can find ~/.mythtv/mysql.txt
or also in /etc/mythtv/mysql.txt.   Make sure they both have the same password.  Then set that password in mysql:

```

mysql -u root -p
enter password

mysql> SET PASSWORD FOR 'mythtv'@'localhost' = PASSWORD('RjD3jan');
Query OK, 0 rows affected (0.00 sec)

mysql> quit
Bye

```Then test if you can enter mysql with that password:
```
mysql -u mythtv -pRjD3jan
```You might also need to set up the access priveledges for mythtv:

```
$ mysql -u root -p mythconverg
mysql> grant all on mythconverg.* to mythtv@"%.mydomain.com" identified by "mythtv";
mysql> flush privileges;
```That did the trick for me!
Now my problem is Im running out of memory.  I knew the day would come when 512 would no longer be enough!

Hey Thanks finneces,

 I will try this when I get home! I will let you know if this works for me too!

Thanks again :)

T9

---

### Post by tech9 on 2008-01-10
> **finneces said:**
> Try this:

in your user home directory you can find ~/.mythtv/mysql.txt
or also in /etc/mythtv/mysql.txt.   Make sure they both have the same password.  Then set that password in mysql:

```

mysql -u root -p
enter password

mysql> SET PASSWORD FOR 'mythtv'@'localhost' = PASSWORD('RjD3jan');
Query OK, 0 rows affected (0.00 sec)

mysql> quit
Bye

```Then test if you can enter mysql with that password:
```
mysql -u mythtv -pRjD3jan
```You might also need to set up the access priveledges for mythtv:

```
$ mysql -u root -p mythconverg
mysql> grant all on mythconverg.* to mythtv@"%.mydomain.com" identified by "mythtv";
mysql> flush privileges;
```That did the trick for me!
Now my problem is Im running out of memory.  I knew the day would come when 512 would no longer be enough!

Hi finneces,

I made sure that the password in both ~/.mythtv/mysql.txt
and /etc/mythtv/mysql.txt. are the same... then when I enter this command after entering...

mysql -u root -p
enter password

mysql> SET PASSWORD FOR 'mythtv'@'localhost' = PASSWORD('mypassword');

I get this error...

ERROR 1133 (42000): Can't find any matching row in the user table

I feel like I am getting close... or at least can get into mysql to enter these commands.

Do you know why I am getting this error
Thank you for all of your help! :)

---

### Post by finneces on 2008-01-11
> **tech9 said:**
>  
ERROR 1133 (42000): Can't find any matching row in the user table



It looks like the database is not setup.  After I did the install of the mythtv package I found a program called "MythTV Backend Setup".  under System -> Administration .  If you run that it will set up the mysql database, then try making sure that the passwords are correct and so on.

Good luck, and let me know if it works!

Matt

---

### Post by tech9 on 2008-01-11
> **finneces said:**
> It looks like the database is not setup.  After I did the install of the mythtv package I found a program called "MythTV Backend Setup".  under System -> Administration .  If you run that it will set up the mysql database, then try making sure that the passwords are correct and so on.

Good luck, and let me know if it works!

Matt

Hi Matt :)

   Ok, I have launched the mythtv backend setup and a message states that it needed to close. Then it opened a window and shot all the above errors that I have in my first post. Finally, it loads the mythtv front-end automatically. I go through the prompts to select English. Make sure the password is the same in the next setup screen as it is in the mysql.txt in both the /etc/mythtv and .mythtv under my home. Then I click finish go back into mythbuntu setup to test the sql connection and it fails. 

I have tried uninstalling all instances of mythtv and mythbuntu under synaptic; then reinstalled, but I end up with the same mysql errors.

I even tried uninstalling and reinstalling mysql, so that I could enter "mypassword" into the mysql DB
```

sudo apt-get remove --purge mythtv-database mysql-server-5.0
sudo apt-get install mysql-server-5.0 mythtv-database

```

do you have any more suggestions? Thank you so much for helping me :)

---

### Post by floquet on 2008-01-11
Hi tech9 

I'm experiencing the same error. It appeared since the update manager updated me to mysql 5.0.45-1ubuntu3.1. There should be some sort of incompatibility, but I still have not found it.

So anyone knows how to revert back to previous versions of mysql?

---

### Post by floquet on 2008-01-11
I've managed it to work again. It seems that there was some problems with the root password in mysql.

I completely reinstalled the mysql-server in synaptic. In the reinstallation it asked me for the root password. I entered the 'bffwpaie' default password for mythtv.

After this I reinstaled mythtv (it was removed when I un-installed mysql-server), and then it work again.

Regards,

---

### Post by benanzo on 2008-01-11
It's been awhile since I've had to set up my MythTV box, but I seem to remember encountering this error if I launched the frontend as my normal user instead of the 'mythtv' user.  Make sure the username is correct in mythtv-setup.  Either that or allow your normal user to access the mythconverg db.  I just used Webmin to add myself to the db and set up my password.  (But don't run Webmin all the time...shut it off when you're not using it.)

webmin.com

---

### Post by tech9 on 2008-01-14
Thank you all for the replies. So, I got to the point where I was frustrated enough to uninstall everything related to mythbuntu and mythtv. I even deleted the mysql folder as root, but now when I try to install everything clean. I am getting sql erros stating that it can't find /mysql/my.cnf and user.frm. I was thinking that installing mysql would just re-create everything, but I guess not. Well, I don't know if I am ambitious enough to start all over at this point with a clean rebuild and try installing mythbuntu again. I have never had so much problems installing and configure an app in linux.

---

