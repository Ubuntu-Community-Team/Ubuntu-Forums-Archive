---
title: "[SOLVED] Can't run MythTV -- no db created?"
date: 2007-11-04
forum: Mythbuntu
---

### Post by couzin2000 on 2007-11-04
I've been through every thread in this Forum, and I cannot find an answer that will work.

I have a brand new system,** Ubuntu Gutsy** and **MythTV** installed with the **Mythbuntu control center**.
I was having networking problems and I've fixed them all - completely, so everything is accessible, without problems.
I was having graphic problems, because I couldn't get the Tv-out to work on my grafx card - but **Mythbuntu control center** fixed it. *Now I have tv out*.

Now, I start[FONT="Courier New"] MythTV backend[/FONT] from my Admin panel, and I get a blue screen asking me to type in the host, the user name, password, db name, db type. I do that, and then it wants to run mythfilldatabase, to which I answer yes. This all goes on without any error messages or warnings - butI have a feeling it should. But let me finish the point first.
THEN I run[FONT="Courier New"] MythFrontEnd[/FONT] from Applications. I get the exact same deal.

What I understand from that is that there is no database created for MythTV (should be called [FONT="Courier New"]mythconverg[/FONT]). So even if I try to connect, which it probably is doing, MythTV won't find the database, which is* to my knowledge* necessary.

So how come I don't have that db? Did something go wrong during install?
I need this up and running soon. Anyone wanna take a stab at helping me fixing this?

---

### Post by superm1 on 2007-11-04
> **couzin2000 said:**
> I've been through every thread in this Forum, and I cannot find an answer that will work.

I have a brand new system,** Ubuntu Gutsy** and **MythTV** installed with the **Mythbuntu control center**.
I was having networking problems and I've fixed them all - completely, so everything is accessible, without problems.
I was having graphic problems, because I couldn't get the Tv-out to work on my grafx card - but **Mythbuntu control center** fixed it. *Now I have tv out*.

Now, I start[FONT=Courier New] MythTV backend[/FONT] from my Admin panel, and I get a blue screen asking me to type in the host, the user name, password, db name, db type. I do that, and then it wants to run mythfilldatabase, to which I answer yes. This all goes on without any error messages or warnings - butI have a feeling it should. But let me finish the point first.
THEN I run[FONT=Courier New] MythFrontEnd[/FONT] from Applications. I get the exact same deal.

What I understand from that is that there is no database created for MythTV (should be called [FONT=Courier New]mythconverg[/FONT]). So even if I try to connect, which it probably is doing, MythTV won't find the database, which is* to my knowledge* necessary.

So how come I don't have that db? Did something go wrong during install?
I need this up and running soon. Anyone wanna take a stab at helping me fixing this?
Did you have mysql server installed before hand? 

Do you have a ~/.mythtv/mysql.txt?  If so, get rid of it and try to start mythtv setup from the system->administration menu.

---

### Post by uopjohnson on 2007-11-04
First of all have you run mythtv-setup?  You can do this by clicking on the big button in the control center under mythtv setup.  If you haven't then do this first.  You need to go through all the pages in order to get mythtv setup. 

If you have already run this then from here you should do is decide if you have a DB created or if you are just having issues connecting to it.  To see if you have created a database run:
```
tail /etc/mythtv/mysql.txt
```

that will show you something like:
```
DBPassword=abcDEF123
```

Now try and connect to mysql:
```
mysql -u mythtv -p
```
when it asks for your password enter what was show above in DBPassword.
If that works type:
```
show databases;
```
if one of the DBs listed is mythconverg then you are doing well.  If you get nothing then you will need to re-create the DB.

If mythconverge is shown then do:
```
use mythconverg;
show tables;

```
should list about 75 tables.  

If you succeed with all fo these steps and see all of the tables then your problem is with connecting to the db.  post back with results.

---

### Post by couzin2000 on 2007-11-07
Superm1:> Did you have mysql server installed before hand?
Do you have a ~/.mythtv/mysql.txt? If so, get rid of it and try to start mythtv setup from the system->administration menu.
I didn't have it installed, but it did install once I ran the MythTV install. However, I didn't find the file you specified -- I assume that's a *good* thing.
uopjohnson:> tail /etc/mythtv/mysql.txt
Ran that just now, this is what I get:```
DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=geddylee

```
My understanding is that this means I DO have a db, the password is geddylee.
So I ran the next command,> mysql -u mythtv -p and I got this as a result: ```
ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)
```
Now this is something I can't get my head wrapped around... the backend and front ends are both local. Same disk. Yet, no access... do I need some sort of root access *other* than the one that pops up at the beginning?
Otherwise, what are my options here - reinstallation? I'd rather not, but if I have no choice...

---

### Post by uopjohnson on 2007-11-07
Sounds like your password might have gotten mangled, lots of ways for that to happen.  The password for mysql has nothing to do with your user password on your system.
try:
```
 
mysql -u root mysql

```
The default password is blank, so you should just be able to get in to the mysql as root.  
If you get into mysql you will see the mysql> prompt.  If you have an error you will need to recover your root mysql password.  You can google for 'reset mysql root password' for info and let me know if you need more detailed instructions.  You can probably get some pretty good instructions from the general forum.  

If you see the prompt type
```

UPDATE user SET Password=PASSWORD('geddylee') WHERE user='mythtv'; FLUSH PRIVILEGES;

```
That will change your password to what myth thinks it should be.  Now you can probably run mythtv-setup.

---

### Post by little_penguin on 2007-11-09
It's frustrating, I feel your pain! I had the same problems for ages, I was unable to log in as the root user for sql server, regardless of the password I'd set, but then I discovered there was also an sql configuration file on my system called debian.cnf which contained details which gave me access to the sql setup:

etc/mysql/debian.cnf 

user:
- debian-sys-maint
- and a password

I went into phpmyadmin by typing localhost in a browser, entered the above data and was then able to reset/change passwords for the mythtv database users. The installation of mythtv worked after that.

I have a hybrid Ubuntu/Kubuntu installation with KDE, rather than pure Ubuntu, and maybe the debian.cnf is Kubuntu only, not sure.

---

### Post by couzin2000 on 2007-11-09
uopjohnson:
```
mysql -u root mysql
```
didn't work for me at all. I got this:> sebastien@sebastien-desktop:~$ mysql -u mythtv -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)
sebastien@sebastien-desktop:~$
instead.

little_penguin:
I went in using ```
sudo gedit /etc/mysql/debian.cnf
```and got the password that you mentioned. However, I'm pretty sure I looked into Synaptic and can't find *any* single package that registers at **mysqlphpadmin**. When I type in "**localhost**" into Firefox, I get to a http root folder with "**apache2-default**" and "**mythweb**" as possible choices. I know my Apache server works now, but as for the mythweb folder I can't get in. No sign of **mysqlphpadmin** anywhere. Am I missing something here?

I know I can retrieve the password now, so what should I do with it now?

Thanks for all the help by the way... so far the most progress I've made!

---

### Post by uopjohnson on 2007-11-09
you are probably loking for phpmyadmin, but I wouldn't take that route yet.  It looks like you ran the wrong command.  
mysql -u mythtv -p means log into mysql usering the user  (-u) mythtv and a password to be input later(-p) mysql-u root means log into mysql as the user root with no password.  Did you run the right command and paste the wrong one?

---

### Post by little_penguin on 2007-11-10
Apologies for the typo, yes  phpmyadmin is what I meant to write :) You apparently don't have it installed then, but try uopjohnson's suggestions first.

If you still can't connect to the database, install the packages listed under item 2 of this guide: 

[http://hyams.webhop.net/mythtv/myth_ubuntu.html]("http://hyams.webhop.net/mythtv/myth_ubuntu.html")

It's written for Ubuntu Edgy, but it worked for me on Feisty.

---

### Post by couzin2000 on 2007-11-10
uopjohnson: yep, I think I might have pasted the wrong command instead. I just retried your command, with 2 different usernames, but neither of them are allowed access. Haven't tried root, though... yet.

little_penguin: yeah, I thought it might have been something like that. Well, yeah, I looked for phpmyadmin, but I don't have it installed. 
I went to your link, but seeing as though all of this is for Edgy, and I'm using Gutsy, there's not much point. Besides, most of the packages are already installed by default with my Ubuntu, or aren't available anymore. I did install (through Synaptic) **libapache2-mod-auth-mysql**, but I haven't seen any change, even after reboot.

Any other suggestions? At this point, I'm willing to bet it IS a password problem, but can't be modified yet because of some restricted, root-type access I need to either mysql or some other app I can't see the name of.

[COLOR="DarkRed"]Scratch that - phpmyadmin **is** installed but I can't see it when I go to **localhost**. Myabe it's *not running* or something?[/COLOR]

---

### Post by uopjohnson on 2007-11-10
There is a difference between the root mysql user and the root system users, which I think is confusing you.  There is actually no correlation between mysql accounts and accounts on your computer.  Go ahead and try mysql -u root and see if you can get into the db.  If not then you will just need to reset your mysql root account which isn't too hard to do.

---

### Post by couzin2000 on 2007-11-10
> There is a difference between the root mysql user and the root system users, which I think is confusing you.You could say that.
> Go ahead and try mysql -u root and see if you can get into the db. If not then you will just need to reset your mysql root account which isn't too hard to do.Looks like I'm gonna have to ask you how to do just that.

ON another note, the password I put into the MythTV setup was different than the one I found in the file little_penguin was talking about. Is this supposed to be the same password? I'm not sure whether I should be resetting, or just trying to modify the passwords. Either way, the solution for me involves not reinstalling the whole thing - most of this stuff isn't broken, and *if it ain't broke*...

[COLOR="Red"]EDIT: Looks like I can get in as **root**... now what?[/COLOR]

---

### Post by couzin2000 on 2007-11-10
Here's what I got entering **showdatabases;** :
```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| mysql              | 
+--------------------+
2 rows in set (0.02 sec)

```
No mythconverg in sight... I'm guessing what follows is to create the db... Shouldn't this have been done already by MythTV? Why do I have to go through with this myself? Is there a function to create the db from MythTV?

---

### Post by uopjohnson on 2007-11-10
OK you need to create the DB and check to be sure the mythtv use has been created in mysql.  Lets do the second thing first:
```
mysql -u root mysql
mysql> select Host,User from user;

```
should give you something like:
```

+-----------+------------------+
| Host      | User             |
+-----------+------------------+
| %         | mythtv           | 
| 127.0.0.1 | root             | 
| localhost | debian-sys-maint | 
| localhost | mythtv           | 
| localhost | root             | 
+-----------+------------------+
6 rows in set (0.01 sec)

```
if you see a couple User entries for mythtv then you are in good shape.  If you see no mythtv entries then do this.
```

mysql> grant all on mythconverg.* to mythtv@% identified by 'PASSWORD';

```

Now that you have a mythtv use you can create the mythtv database:
```
mysql> create database mythconverg;
```

Then you need to edit /etc/mythtv/mysql.txt with your new password.
```
sudo gedit /etc/mythtv/mysql.txt
```

Then you can run the mythbuntu control center and click on the mythtv-setup button. 

Let me know where that doesn't work.

---

### Post by couzin2000 on 2007-11-11
```
mysql -u root mysql
mysql> select Host,User from user;
```
didn't work at all, either way. The first line gives me an Access Denied result, so I login as **root** (with **-p**) and then I try your second line. I get this:
```
mysql> select Host,User from user;
ERROR 1046 (3D000): No database selected
mysql>
```
Not sure where that leaves me, since I can't execute any of the lines you're sending me.  I tried **help** but I can't seem to find any other command than **use** to select the db I wanna see.

One dramatinc thought here: could this be a different version than what MythTV is used to, or is built for? How do I know which version MythTV is supposed to be using, and which version of MySQL I'm using?

[COLOR="Red"]EDIT: found the version info:
```
mysql> status
--------------
mysql  Ver 14.12 Distrib 5.0.45, for pc-linux-gnu (i486) using readline 5.2

Connection id:          143
Current database:
Current user:           root@localhost
SSL:                    Not in use
Current pager:          stdout
Using outfile:          ''
Using delimiter:        ;
Server version:         5.0.45-Debian_1ubuntu3-log Debian etch distribution
Protocol version:       10
Connection:             Localhost via UNIX socket
Server characterset:    latin1
Db     characterset:    latin1
Client characterset:    latin1
Conn.  characterset:    latin1
UNIX socket:            /var/run/mysqld/mysqld.sock
Uptime:                 17 hours 59 min 57 sec

Threads: 1  Questions: 50  Slow queries: 0  Opens: 23  Flush tables: 1  Open tables: 17  Queries per second avg: 0.001

```[/COLOR]

---

### Post by uopjohnson on 2007-11-11
No worries about the version, myth supports mysql 4 and 5 (which you are running).  If you log into mysql as root type 
```
use mysql;
```
to select the mysql database to use and then you can continue starting with mysql> select Host,User from user;

---

### Post by couzin2000 on 2007-11-11
Got in using root, changed the db used to mysql, then ran **select Host, user** thingy, then I ran this:
```
mysql> grant all on mythconverg.* to mythtv@% identified by 'PASSWORD';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '% identified by 'PASSWORD'' at line 1
mysql>
```
Did I make a mistake?

---

### Post by uopjohnson on 2007-11-12
nope my fault again.  I should start testing these commands and stop trying to give them from memory.  You need to quote the username and host (%) so the right command is:
```
mysql> grant all on mythconverg.* to 'mythtv'@'%' identified by 'PASSWORD';

```

---

### Post by couzin2000 on 2007-11-12
Alrighty... I just went through every step, like you posted. Here's what I get:

```
sebastien@sebastien-desktop:~$ mysql -u root mysql -p
Enter password: 
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 10
Server version: 5.0.45-Debian_1ubuntu3-log Debian etch distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> grant all on mythconverg.* to 'mythtv'@'%' identified by 'PASSWORD';
Query OK, 0 rows affected (0.00 sec)

mysql> select Host,User from user;
+-------------------+------------------+
| Host              | User             |
+-------------------+------------------+
| %                 | mythtv           | 
| 127.0.0.1         | root             | 
| localhost         | debian-sys-maint | 
| localhost         | root             | 
| sebastien-desktop | root             | 
+-------------------+------------------+
5 rows in set (0.00 sec)

mysql> create database mythconverg;
ERROR 1007 (HY000): Can't create database 'mythconverg'; database exists
mysql>
```

I'm not sure that this is normal... should I be* seeing* the** mythconverg** db in that last listing?
What am I doing wrong here... I'm going outta my mind because I'm not used to waiting around while posts appear for me to fix the problem... I'm an "experienced noob", but still... this is driving me nuts!

[COLOR="Red"]EDIT: when I try to run the Myth control center, and run MythTV Setup, I get this message:
```
2007-11-12 21:03:45.208 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:45.258 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:45.308 Database not open while trying to load setting: Style
2007-11-12 21:03:45.309 Unable to connect to database!
2007-11-12 21:03:45.309 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:45.359 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:45.409 Database not open while trying to load setting: Theme
2007-11-12 21:03:45.409 Switching to square mode (blue)
2007-11-12 21:03:45.409 Unable to connect to database!
2007-11-12 21:03:45.410 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:45.460 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:45.510 Database not open while trying to load setting: GuiOffsetX
2007-11-12 21:03:45.510 Unable to connect to database!
2007-11-12 21:03:45.510 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:45.561 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:45.611 Database not open while trying to load setting: GuiOffsetY
2007-11-12 21:03:45.611 Unable to connect to database!
2007-11-12 21:03:45.611 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:45.661 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:45.711 Database not open while trying to load setting: GuiResolution
2007-11-12 21:03:45.712 Unable to connect to database!
2007-11-12 21:03:45.712 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:45.762 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:45.812 Database not open while trying to load setting: GuiWidth
2007-11-12 21:03:45.812 Unable to connect to database!
2007-11-12 21:03:45.812 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:45.863 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:45.913 Database not open while trying to load setting: GuiHeight
2007-11-12 21:03:45.916 Unable to connect to database!
2007-11-12 21:03:45.916 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:45.966 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:46.016 Database not open while trying to load setting: MenuTheme
2007-11-12 21:03:46.016 Unable to connect to database!
2007-11-12 21:03:46.016 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:46.067 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:46.117 Database not open while trying to load setting: QtFontBig
2007-11-12 21:03:46.117 Unable to connect to database!
2007-11-12 21:03:46.117 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:46.167 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:46.217 Database not open while trying to load setting: QtFontMedium
2007-11-12 21:03:46.218 Unable to connect to database!
2007-11-12 21:03:46.218 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:46.268 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:46.318 Database not open while trying to load setting: QtFontSmall
2007-11-12 21:03:46.328 Unable to connect to database!
2007-11-12 21:03:46.328 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:46.379 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:46.429 Database not open while trying to load setting: ThemePainter
2007-11-12 21:03:46.429 Using the Qt painter
2007-11-12 21:03:46.429 Unable to connect to database!
2007-11-12 21:03:46.429 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:46.480 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:46.530 Database not open while trying to load setting: HideMouseCursor
2007-11-12 21:03:46.530 Unable to connect to database!
2007-11-12 21:03:46.530 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:46.580 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:46.630 Database not open while trying to load setting: RunFrontendInWindow
mythtv: could not open config file /home/sebastien/.mythtv/lircrc
mythtv: No such file or directory
Failed to read lirc config /home/sebastien/.mythtv/lircrc for mythtv
2007-11-12 21:03:46.935 Joystick disabled.
2007-11-12 21:03:46.939 Unable to connect to database!
2007-11-12 21:03:46.939 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:46.991 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:47.041 Unable to connect to database!
2007-11-12 21:03:47.041 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:47.091 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:47.142 Unable to connect to database!
2007-11-12 21:03:47.142 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:47.192 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:47.242 Unable to connect to database!
2007-11-12 21:03:47.242 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:47.293 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:47.343 Unable to connect to database!
2007-11-12 21:03:47.343 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:47.396 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:47.446 Unable to connect to database!
2007-11-12 21:03:47.446 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:47.496 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:47.547 Unable to connect to database!
2007-11-12 21:03:47.547 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:47.597 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:47.647 Unable to connect to database!
2007-11-12 21:03:47.648 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:47.698 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:47.748 Unable to connect to database!
2007-11-12 21:03:47.748 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:47.798 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:47.851 Unable to connect to database!
2007-11-12 21:03:47.851 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:47.901 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:47.951 Unable to connect to database!
2007-11-12 21:03:47.952 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:48.002 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:48.052 Unable to connect to database!
2007-11-12 21:03:48.052 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:48.102 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:48.153 Unable to connect to database!
2007-11-12 21:03:48.153 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:48.203 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:48.254 Unable to connect to database!
2007-11-12 21:03:48.254 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:48.304 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:48.354 Unable to connect to database!
2007-11-12 21:03:48.354 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:48.404 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:48.455 Unable to connect to database!
2007-11-12 21:03:48.455 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:48.505 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:48.556 Unable to connect to database!
2007-11-12 21:03:48.556 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:48.606 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:48.656 Unable to connect to database!
2007-11-12 21:03:48.656 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:48.707 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:48.757 Unable to connect to database!
2007-11-12 21:03:48.757 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:48.807 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:48.857 Unable to connect to database!
2007-11-12 21:03:48.858 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:48.908 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:48.958 Unable to connect to database!
2007-11-12 21:03:48.958 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:49.008 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:49.059 Unable to connect to database!
2007-11-12 21:03:49.059 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:49.109 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:49.159 Unable to connect to database!
2007-11-12 21:03:49.160 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:49.210 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:49.260 Unable to connect to database!
2007-11-12 21:03:49.260 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:49.311 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:49.361 Unable to connect to database!
2007-11-12 21:03:49.361 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-12 21:03:49.411 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-12 21:03:49.462 Database not open while trying to load setting: Language

```What could this be??[/COLOR]

---

### Post by uopjohnson on 2007-11-12
I aggree with you this is getting a bit ridiculous and you may want to consider a re-install as at this point you would probably be done with that several times over.  It looks like your database has already been created, but your user has not.  Now you have create the user with the grant ALL on statement above.  If the mythconverg database is already up then your next step is to edit /etc/mythtv/mysql.txt with the password you used above in place of PASSWORD as in:
```
identified by 'PASSWORD';
```
Once you have changed that password try running mythtv-setup from the control center again.

Looking at your edit above the probablem is that you now have the wrong password in /etc/mythtv/mysql.txt.  That is what the line 'Access denied for user 'mythtv'@'localhost' (using password: YES)' means.

---

### Post by couzin2000 on 2007-11-12
> then your next step is to edit /etc/mythtv/mysql.txt with the password you used above in place of PASSWORD
soon as I read **PASSWORD** I figured out my mistake. Wrong Password. I just replaced the pass in both instances and voilà!
**[COLOR="Red"]IT WORKS!![/COLOR]**
Thanks so much... I owe you one for that.
Now, onto my laptop, which will become a separate frontend. Keep this in your subscriptions, cause I'll be back here next week asking questions again. THANKS AGAIN!

---

### Post by pasta514 on 2007-11-13
[QUOTE=uopjohnson;3747726]OK you need to create the DB and check to be sure the mythtv use has been created in mysql.  Lets do the second thing first:
```
mysql -u root mysql
mysql> select Host,User from user;

```
should give you something like:
```

+-----------+------------------+
| Host      | User             |
+-----------+------------------+
| %         | mythtv           | 
| 127.0.0.1 | root             | 
| localhost | debian-sys-maint | 
| localhost | mythtv           | 
| localhost | root             | 
+-----------+------------------+
6 rows in set (0.01 sec)

```

excuse me there Jon.  I am following through this most useful thread trying to get frontend on a different machine to connect.  At this point I get this output
```
papa@sipper:~$ mysql -u root mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 75
Server version: 5.0.45-Debian_1ubuntu3-log Debian etch distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> select Host,User from user;
+----------------------------+------------------+
| Host                       | User             |
+----------------------------+------------------+
| %                          | mythtv           | 
| 127.0.0.1                  | root             | 
| cubert.itri.brighton.ac.uk | root             | 
| localhost                  | debian-sys-maint | 
| localhost                  | mythtv           | 
| localhost                  | root             | 
+----------------------------+------------------+
6 rows in set (0.00 sec)
mysql>
``` 
Just curious what is this item? and why is it here?
```
| cubert.itri.brighton.ac.uk | root             | 
```Is it part of schedules direct?

Thanks,

---

### Post by Zero7 on 2007-11-13
Deleted. Starting another thread.

---

### Post by pasta514 on 2007-11-13
deleted

---

### Post by pasta514 on 2007-11-13
> **pasta514 said:**
> [QUOTE=uopjohnson;3747726]OK you need to create the DB and check to be sure the mythtv use has been created in mysql.  Lets do the second thing first:
```

mysql> select Host,User from user;
+----------------------------+------------------+
| Host                       | User             |
+----------------------------+------------------+
| %                          | mythtv           | 
| 127.0.0.1                  | root             | 
| cubert.itri.brighton.ac.uk | root             | 
| localhost                  | debian-sys-maint | 
| localhost                  | mythtv           | 
| localhost                  | root             | 
+----------------------------+------------------+
6 rows in set (0.00 sec)
mysql>
``` 
Just curious what is this item? and why is it here?
```
| cubert.itri.brighton.ac.uk | root             | 
```Is it part of schedules direct?

Thanks,

found the answer myself:
[http://ubuntuforums.org/showthread.php?t=590229](http://ubuntuforums.org/showthread.php?t=590229)

---

### Post by couzin2000 on 2007-11-14
So now that I've got the backend working properly with a frontend on the same system, I need to know - the setup for my remote front end needs certain info, right?

So I assume that the IP to be put in during the MythTV setup is an *internal ip* (such as **192.168.0.101**, fo example). Is there a port specification too? Would I have to unlock those ports on my router, behind the firewall, or would that just be opening the firewall's ports? I'm guessing I don't have to do anything while I'm on the LAN. As soon as I affect the ports on my router, this will open the WAN ports, right?

Then, same user, same password, and I should be good to go, right?

---

### Post by Nox_UK on 2007-11-16
btw, i'm getting all this on a new install too...  also 7.10
Nox

---

### Post by couzin2000 on 2007-12-04
Anybody wanna help out with this video problem, or should I just start another thread?

---

### Post by uopjohnson on 2007-12-04
What video problem?  Did I miss a post?

---

### Post by couzin2000 on 2007-12-07
You're right -- sorry, my mistake. I guess I mustve posted and had a bug or something.

The problem is such: I now have complete access to MythTV, except that I have no video or audio playback. I think this may be related to the MythVideo plugin config, because the Music plugin works fine and I do hear audio.
The database works, and I can access the web to update the movie data. However, when I select a video in the list and hit Play, nothing happens. I get zero interaction. I can still navigate through the list, but no video.

I've looked through the threads to find something about a command-line app that I can run instead of Mplayer, but it's funny... I can run the movies from the desktop quite nicely in MPlayer, just not within Myth.

Anyone have an idea what this could be?

Thanks (and sorry about the last post)

---

### Post by uopjohnson on 2007-12-08
Do you mean that mythvideo isn't working or that you can't see video you've recorded with mythtv?  
If you go into settings -> general -> media settings -> playback?  something like that.  You are looking for the box to put in the default media player.  replace whatever is there with Internal.  That will use the internal myth video player and limit the number of problems you may be having.

---

### Post by couzin2000 on 2008-01-02
I do not have any video playback when I try to watch previously downloaded movies and/or  tv shows. Most of my stuff is in Xvid or Divx format. Could this be a conflicting codec, or could it be a lack of?
I've tried typing that in, but neither works. Both the mplayer command or internal command both don't work.
Anything else? I did start another thread about this... here: [http://ubuntuforums.org/showthread.php?t=621483](http://ubuntuforums.org/showthread.php?t=621483)
Help out if you can!

---

