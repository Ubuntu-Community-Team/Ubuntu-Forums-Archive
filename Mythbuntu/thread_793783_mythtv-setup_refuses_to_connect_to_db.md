---
title: "mythtv-setup refuses to connect to db"
date: 2008-05-14
forum: Mythbuntu
---

### Post by zoiks on 2008-05-14
I've tried to be careful to follow the directions, but I can't get past running sudo mythtv-setup.

```
mythbox@coral:~$ sudo mythtv-setup.real

```
(English chosen)
(message box says no UPnP backends found)

```
2008-05-14 00:24:55.481 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-14 00:24:55.487 XScreenSaver support enabled
2008-05-14 00:24:55.487 DPMS is active.
2008-05-14 00:24:55.487 Empty LocalHostName.
2008-05-14 00:24:55.487 Using localhost value of coral
2008-05-14 00:24:55.493 New DB connection, total: 1
2008-05-14 00:24:55.496 Unable to connect to database!
2008-05-14 00:24:55.496 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-05-14 00:24:55.546 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QServerSocket: failed to bind or listen to the socket
2008-05-14 00:24:55.597 MCP::InitUPnP() - HttpServer Create Error
2008-05-14 00:24:55.597 Deleting UPnP client...
2008-05-14 00:24:55.597 No UPnP backends found
2008-05-14 00:24:55.600 Primary screen 0.
2008-05-14 00:24:55.600 Using screen 0, 1024x768 at 0,0
2008-05-14 00:24:55.601 Switching to square mode (blue)
2008-05-14 00:24:55.624 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-05-14 00:24:55.624 lirc_init failed for mythtv, see preceding
messages
2008-05-14 00:24:55.624 JoystickMenuClient Error: Joystick disabled -
Failed to read /home/mythbox/.mythtv/joystickmenurc
2008-05-14 00:24:57.000 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2008-05-14 00:24:57.000 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...
2008-05-14 00:24:57.000 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2008-05-14 00:24:57.000 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...
2008-05-14 00:25:36.142 Writing settings file
/home/mythbox/.mythtv/mysql.txt
2008-05-14 00:25:36.146 Closing DB connection named 'DBManager0'
2008-05-14 00:25:36.152 Unable to connect to database!
2008-05-14 00:25:36.152 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-05-14 00:25:36.202 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-05-14 00:25:36.252 Cannot login to database?
2008-05-14 00:25:36.252 Cannot login to database?
2008-05-14 00:25:36.253 Primary screen 0.
2008-05-14 00:25:36.253 Using screen 0, 1024x768 at 0,0
2008-05-14 00:25:36.254 Switching to square mode (blue)
2008-05-14 00:25:36.259 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-05-14 00:25:36.259 lirc_init failed for mythtv, see preceding
messages
2008-05-14 00:25:36.259 JoystickMenuClient Error: Joystick disabled -
Failed to read /home/mythbox/.mythtv/joystickmenurc
2008-05-14 00:25:36.465 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2008-05-14 00:25:36.465 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...
2008-05-14 00:25:36.465 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...
2008-05-14 00:28:16.391 User cancelled database configuration
2008-05-14 00:28:16.401 Failed to init MythContext, exiting.

```

In the setup screens I chose:
localhost
no ping no port
mythconverg
mythtv
<randomly generated password from installation>


I had seen other posts about manually creating mythconverg: I did that.

```
mythbox@coral:~$ mysql -u root -p mythconverg
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 76260
Server version: 5.0.51a-3ubuntu5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 

```


I've tried to be careful to follow instructions. The mythtv mysql password is still the randomly chosen one from the install. I'm not knowledgeable in mysql so I can't decipher what's going on with the database. FWIW I've been using MythTV for several years, compiling from scratch on a SuSE-based system (which is still running great in the living room), and this is the first time I've had trouble running mythtv-setup.

Also, mysql.err and mysql.log are both blank.

One more thing, my hard drives are getting hit hard, and my mythbackend.log is growing big time. It's now up to **784MB**. It's filling up with this junk, repeated over and over:

```
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2008-05-14 01:04:44.753 Unable to connect to database!
2008-05-14 01:04:44.754 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-05-14 01:04:44.807 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-05-14 01:04:44.857 Cannot login to database?
2008-05-14 01:04:44.858 Cannot login to database?

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
Database password: [xxxxxxxx]  
[console is not interactive, using default 'xxxxxxxx']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2008-05-14 01:04:44.876 Unable to connect to database!
2008-05-14 01:04:44.877 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-05-14 01:04:44.930 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...

```

Any clues? I could really use some help here.

---

### Post by volkswagner on 2008-05-14
Can you log into mysql with user mythtv as you did with root?

Verify the password in /etc/mythtv/mysql.txt

Check out response number five in the following thread.

[http://ubuntuforums.org/showthread.php?t=611899&highlight=mythtv+backend+will]("http://ubuntuforums.org/showthread.php?t=611899&highlight=mythtv+backend+will")


If you still get no joy, you can also force the change of password for any user by following these steps.

[http://www.cyberciti.biz/faq/mysql-change-root-password/]("http://www.cyberciti.biz/faq/mysql-change-root-password/")

---

### Post by zoiks on 2008-05-14
> **volkswagner said:**
> Can you log into mysql with user mythtv as you did with root?

Verify the password in /etc/mythtv/mysql.txt

Check out response number five in the following thread.

[http://ubuntuforums.org/showthread.php?t=611899&highlight=mythtv+backend+will]("http://ubuntuforums.org/showthread.php?t=611899&highlight=mythtv+backend+will")


If you still get no joy, you can also force the change of password for any user by following these steps.

[http://www.cyberciti.biz/faq/mysql-change-root-password/]("http://www.cyberciti.biz/faq/mysql-change-root-password/")

Thanks for the response.

OK, first I checked ~/.mythtv/mysql.txt and the password that was in there was the one I set during the installation process for the mysql user mythtv.

In any event, I then did

```
mythbox@coral:~$ rm ~/.mythtv/mysql.txt

```

Next, I did the following:

```
mythbox@coral:~$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 28435
Server version: 5.0.51a-3ubuntu5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> SET PASSWORD FOR 'mythtv' = PASSWORD('**password**');
ERROR 1133 (42000): Can't find any matching row in the user table
mysql>

```
(BTW I think the SET PASSWORD statement in the linked post is missing a semicolon. I wonder how many newbies are choking on that one.)

It looks like the mythtv user in the mysql database wasn't even created yet. I don't know the access details I should be giving the mythtv user, so how should I correctly create the mythtv user in mysql?

Obviously, no joy yet.

---

### Post by superm1 on 2008-05-14
> **zoiks said:**
> Thanks for the response.

OK, first I checked ~/.mythtv/mysql.txt and the password that was in there was the one I set during the installation process for the mysql user mythtv.

In any event, I then did

```
mythbox@coral:~$ rm ~/.mythtv/mysql.txt

```Next, I did the following:

```
mythbox@coral:~$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 28435
Server version: 5.0.51a-3ubuntu5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> SET PASSWORD FOR 'mythtv' = PASSWORD('**password**');
ERROR 1133 (42000): Can't find any matching row in the user table
mysql>

```(BTW I think the SET PASSWORD statement in the linked post is missing a semicolon. I wonder how many newbies are choking on that one.)

It looks like the mythtv user in the mysql database wasn't even created yet. I don't know the access details I should be giving the mythtv user, so how should I correctly create the mythtv user in mysql?

Obviously, no joy yet.
OK so it sounds like the mythtv-database wasn't fully prepped. 

Reconfigure it with

```

sudo dpkg-reconfigure mythtv-database
```

Make sure that you enter the proper root user and pass when you do so.  That should make the user and such.

---

### Post by zoiks on 2008-05-14
FWIW, I tried as mysql root:

```
mysql> SELECT Host, User, Password FROM mysql.user;
+-----------+------------------+-------------------------------------------+
| Host      | User             | Password                                  |
+-----------+------------------+-------------------------------------------+
| localhost | root             | *xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx6D6D | 
| coral     | root             | *xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx6D6D | 
| 127.0.0.1 | root             | *xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx6D6D | 
| localhost |                  |                                           | 
| coral     |                  |                                           | 
| localhost | debian-sys-maint | *xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx0F44 | 
| localhost | mythtv           | *xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx2FFC | 
+-----------+------------------+-------------------------------------------+
7 rows in set (0.00 sec)

mysql> 

```

---

### Post by zoiks on 2008-05-14
> **superm1 said:**
> OK so it sounds like the mythtv-database wasn't fully prepped. 

Reconfigure it with

```

sudo dpkg-reconfigure mythtv-database
```

Make sure that you enter the proper root user and pass when you do so.  That should make the user and such.

Alright, tried this:

```
mythbox@coral:~$ sudo dpkg-reconfigure mythtv-database
[sudo] password for mythbox: 
 * Starting MySQL database server mysqld                                 [ OK ] 
mythbox@coral:~$ 
mythbox@coral:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 90505
Server version: 5.0.51a-3ubuntu5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> SET PASSWORD FOR 'mythbox' = PASSWORD('xxxxxxxx');
ERROR 1133 (42000): Can't find any matching row in the user table
mysql> 

```

Still no go.

---

### Post by zoiks on 2008-05-14
> **zoiks said:**
> Alright, tried this:

```
mythbox@coral:~$ sudo dpkg-reconfigure mythtv-database
[sudo] password for mythbox: 
 * Starting MySQL database server mysqld                                 [ OK ] 
mythbox@coral:~$ 
mythbox@coral:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 90505
Server version: 5.0.51a-3ubuntu5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> SET PASSWORD FOR 'mythbox' = PASSWORD('xxxxxxxx');
ERROR 1133 (42000): Can't find any matching row in the user table
mysql> 

```

Still no go.

Oops. The mysql line above contains the wrong user (s/mythbox/mythtv/).

I ran mythtv-setup, and now I have the proper setup screen which I am now attempting to complete.

So that means success, so far. Thanks for the help!

---

### Post by shao.lo on 2011-11-26
I know this is an old thread, but since I just had similar issues I thought I'd add my experience here in case anyone else has same problem.

I installed mythv on Oneric and no matter what I tried, I always got the connection error described in this thread.  As a last resort, I rebooted.  Mythtv came right up after that.

So, if you have the same frustrating error and none of the above suggestions works for you. Try rebooting.

---

