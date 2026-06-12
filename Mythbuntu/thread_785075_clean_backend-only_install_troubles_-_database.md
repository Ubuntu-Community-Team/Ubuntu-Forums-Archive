---
title: "clean backend-only install troubles - database"
date: 2008-05-07
forum: Mythbuntu
---

### Post by pasta514 on 2008-05-07
I have a machine I want to be my backend only.  It is current hardware.  AthlonX2, 4GB RAM, 2x HDD, ATI card.  Nothing special.

Here is what I did:
1) boot alternate CD; normal installation
2) manually partitioned the disks
3) installed base system
4) installed: openSSH, samba and mythtv Backend master
5) set user login and password
6) set mysql root password
7) reboot, then install ATI proprietary driver, then reboot
8) synaptic update

then at a terminal tried 'mythtv-setup'
it asked me to join the required group, so I did
then I get to the setup screens and regardless of what I try the result is the same
'cannot to database?' <--- it's asked ME?? :confused:
'no UPnP backends found'

for hostname I tried localhost, the assignedname, assignedname.domain, and the static IP of the backend.




```
2008-05-06 23:29:19.484 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-06 23:29:19.502 XScreenSaver support enabled
2008-05-06 23:29:19.503 DPMS is active.
2008-05-06 23:29:19.504 Empty LocalHostName.
2008-05-06 23:29:19.505 Using localhost value of sipper
2008-05-06 23:29:19.520 New DB connection, total: 1
2008-05-06 23:29:19.521 Unable to connect to database!
2008-05-06 23:29:19.522 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.112' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-05-06 23:29:19.575 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QServerSocket: failed to bind or listen to the socket
2008-05-06 23:29:19.628 MCP::InitUPnP() - HttpServer Create Error
2008-05-06 23:29:19.628 Deleting UPnP client...
2008-05-06 23:29:19.629 No UPnP backends found
2008-05-06 23:29:19.636 Primary screen 0.
2008-05-06 23:29:19.636 Using screen 0, 1280x1024 at 0,0
2008-05-06 23:29:19.640 Switching to square mode (blue)
2008-05-06 23:29:19.810 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-05-06 23:29:19.811 lirc_init failed for mythtv, see preceding messages
2008-05-06 23:29:19.811 JoystickMenuClient Error: Joystick disabled - Failed to 
read /home/papa/.mythtv/joystickmenurc
```

also, fwiw:

```
(zenity:15454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(zenity:15454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(zenity:15454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```

do I need to install something else?

---

### Post by superm1 on 2008-05-07
> **pasta514 said:**
> I have a machine I want to be my backend only.  It is current hardware.  AthlonX2, 4GB RAM, 2x HDD, ATI card.  Nothing special.

Here is what I did:
1) boot alternate CD; normal installation
2) manually partitioned the disks
3) installed base system
4) installed: openSSH, samba and mythtv Backend master
5) set user login and password
6) set mysql root password
7) reboot, then install ATI proprietary driver, then reboot
8) synaptic update

then at a terminal tried 'mythtv-setup'
it asked me to join the required group, so I did
then I get to the setup screens and regardless of what I try the result is the same
'cannot to database?' <--- it's asked ME?? :confused:
'no UPnP backends found'

for hostname I tried localhost, the assignedname, assignedname.domain, and the static IP of the backend.




```
2008-05-06 23:29:19.484 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-06 23:29:19.502 XScreenSaver support enabled
2008-05-06 23:29:19.503 DPMS is active.
2008-05-06 23:29:19.504 Empty LocalHostName.
2008-05-06 23:29:19.505 Using localhost value of sipper
2008-05-06 23:29:19.520 New DB connection, total: 1
2008-05-06 23:29:19.521 Unable to connect to database!
2008-05-06 23:29:19.522 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.112' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-05-06 23:29:19.575 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QServerSocket: failed to bind or listen to the socket
2008-05-06 23:29:19.628 MCP::InitUPnP() - HttpServer Create Error
2008-05-06 23:29:19.628 Deleting UPnP client...
2008-05-06 23:29:19.629 No UPnP backends found
2008-05-06 23:29:19.636 Primary screen 0.
2008-05-06 23:29:19.636 Using screen 0, 1280x1024 at 0,0
2008-05-06 23:29:19.640 Switching to square mode (blue)
2008-05-06 23:29:19.810 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-05-06 23:29:19.811 lirc_init failed for mythtv, see preceding messages
2008-05-06 23:29:19.811 JoystickMenuClient Error: Joystick disabled - Failed to 
read /home/papa/.mythtv/joystickmenurc
```also, fwiw:

```
(zenity:15454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(zenity:15454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(zenity:15454): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```do I need to install something else?
I suspect the selection of a mysql-root-password during install fsck'ed with things, which would be a bug.

Try this:

```
sudo dpkg-reconfigure mythtv-database
```

---

### Post by pasta514 on 2008-05-08
> **superm1 said:**
> I suspect the selection of a mysql-root-password during install fsck'ed with things, which would be a bug.

Try this:

```
sudo dpkg-reconfigure mythtv-database
```

That did not help.

I then reset the root password following these instructions.  
```
http://www.cyberciti.biz/tips/recover-mysql-root-password.html
> 
Step # 1 : Stop mysql service
# /etc/init.d/mysql stop

Step # 2: Start to MySQL server w/o password:
# mysqld_safe --skip-grant-tables &

Step # 3: Connect to mysql server using mysql client:
# mysql -u root
mysql>

Step # 4: Setup new MySQL root user password
mysql> use mysql;
mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD") where User='root';
mysql> flush privileges;
mysql> quit

Step # 5: Stop MySQL Server:
# /etc/init.d/mysql stop

Step # 6: Start MySQL server and test it
# /etc/init.d/mysql start
# mysql -u root -p



```
Looks like root password update worked... but the problem still looks the same as before:

output from this is the same as before:
```
sudo dpkg-reconfigure mythtv-database
```

here's another take on it:
```
papa@sipper:/etc/mysql/conf.d$ mythbackend
2008-05-07 22:38:33.062 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-07 22:38:33.063 Using localhost value of sipper
2008-05-07 22:38:33.079 New DB connection, total: 1
2008-05-07 22:38:33.086 Unable to connect to database!
2008-05-07 22:38:33.086 Driver error was [1/1049]:
QMYSQL3: Unable to connect
Database error was:
Unknown database 'mythconverg'

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-05-07 22:38:33.138 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QServerSocket: failed to bind or listen to the socket
2008-05-07 22:38:33.189 MCP::InitUPnP() - HttpServer Create Error
2008-05-07 22:38:33.189 Deleting UPnP client...
2008-05-07 22:38:33.190 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [yes]  

```

:confused:

---

### Post by superm1 on 2008-05-08
> **pasta514 said:**
> That did not help.

I then reset the root password following these instructions.  
```
http://www.cyberciti.biz/tips/recover-mysql-root-password.html


```Looks like root password update worked... but the problem still looks the same as before:

output from this is the same as before:
```
sudo dpkg-reconfigure mythtv-database
```here's another take on it:
```
papa@sipper:/etc/mysql/conf.d$ mythbackend
2008-05-07 22:38:33.062 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-07 22:38:33.063 Using localhost value of sipper
2008-05-07 22:38:33.079 New DB connection, total: 1
2008-05-07 22:38:33.086 Unable to connect to database!
2008-05-07 22:38:33.086 Driver error was [1/1049]:
QMYSQL3: Unable to connect
Database error was:
Unknown database 'mythconverg'

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-05-07 22:38:33.138 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QServerSocket: failed to bind or listen to the socket
2008-05-07 22:38:33.189 MCP::InitUPnP() - HttpServer Create Error
2008-05-07 22:38:33.189 Deleting UPnP client...
2008-05-07 22:38:33.190 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [yes]  

```:confused:
What's the output from the dpkg-reconfigure command?

That's where the database gets made..

---

### Post by pasta514 on 2008-05-08
> **pasta514 said:**
> :confused:

I did this:
```

$ cd /usr/share/mythtv/sql
$ mysql -u root <mc.sql -p
$ sudo /etc/init.d/mysql restart
$ mysql -u root mythconverg -p

```

hoped for the best, but still the same
```

papa@sipper:/$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
papa@sipper:/$ mysql -u root mythconverg -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 7
Server version: 5.0.51a-3ubuntu5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> quit
Bye
papa@sipper:/$ sudo dpkg-reconfigure mythtv-database 
Failed to connect to database: Access denied for user 'root'@'sipper.zenserver.mshome' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
papa@sipper:/$ 

```

**but wait!!!**  something did change.  I went to MCC and hit LAUNCH MYTHTV SETUP and it told me it needed to update my database, then it went into the backend setup program.  

I will get back to this tomorrow.

---

### Post by pasta514 on 2008-05-08
> **superm1 said:**
> What's the output from the dpkg-reconfigure command?

That's where the database gets made..

```
papa@sipper:/$ sudo dpkg-reconfigure mythtv-database 
Failed to connect to database: Access denied for user 'root'@'sipper.zenserver.mshome' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
papa@sipper:/$
```

---

### Post by Svenson14 on 2008-06-04
I am having the same problem.
I have looked around at different forums.

I've tried reconfiguring the Database but it gives the same error
```
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
```

Im running the newest version of Ubuntu, and I'll admit im a noob, so try to spell things out for me as far as code go.

I have MythTV all on one system (don't have a separate display or any other connections to any other computers)

What can I do? Is it Mysql?

---

### Post by studiodaz on 2008-06-05
got the same problem.

using alt CD mythbuntu 8.04

---

