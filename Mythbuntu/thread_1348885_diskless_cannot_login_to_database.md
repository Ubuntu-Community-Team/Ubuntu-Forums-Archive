---
title: "diskless cannot login to database"
date: 2009-12-07
forum: Mythbuntu
---

### Post by map7 on 2009-12-07
I'm running Mythbuntu 9.10 64bit on my server and I'm trying to setup some diskless clients.  I've had Mythbuntu 8.04 working with diskless clients before but I've hit a brick wall with 9.10.  Here is what I've tried:

Mythtv-backend setup
Setup backend & database IP in mythtv-setup to point to my servers static IP of: 10.1.1.10.
Entered a security pin of '1234'

Setup mysql
Changed my.cnf to remark out bind & also tried setting bind-address to 10.1.1.10 not sure which is correct here.

```
$ sudo dpkg-reconfigure mythtv-common
```
Set the mysql host to: 10.1.1.10

```
$ sudo dpkg-reconfigure mythtv-database
```
Answer 'yes' to allow remote

Changed mysql database permissions with these commands:

Log into mysql as root and perform the following:

```

root@mythserver-desktop:/etc/mysql# mysql -u root mysql -p

mysql> grant all on mythconverg.* to 'mythtv'@'%' identified by '<my myth password from mysql.txt>';
Query OK, 0 rows affected (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql> exit

```

I can get a remote frontend working using my notebook (ubuntu 9.10 64bit)

My diskless system does boot up but when I start mythfrontend it first asks for the language, I select 'English' then it has the error 'Cannot login to database'.  I then tried to setup the link manually and it still doesn't work.

I can access the database from my diskless frontend through the command line with the command:
```
$ mysql -h 10.1.1.10 -u mythtv -p mythconverg
```

I've created my diskless image with command:
```
  $ sudo ltsp-build-client --mythbuntu --mythbuntu-user-credentials "mythclient":"mythclient" --copy-package-lists --copy-sourceslist --accept-unsigned-packages --arch i386
```

Here is the output I get when running mythfrontend from the clients terminal
```
$ mythfrontend
2009-12-08 08:12:30.580 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-12-08 08:12:30.614 Using runtime prefix = /usr
2009-12-08 08:12:30.614 Using configuration directory = /home/mythclient/.mythtv
2009-12-08 08:12:31.356 Unable to read configuration file mysql.txt
2009-12-08 08:12:31.357 Empty LocalHostName.
2009-12-08 08:12:31.357 Using localhost value of 00a0d1437afa
2009-12-08 08:12:31.364 New DB connection, total: 1
2009-12-08 08:12:31.365 Unable to connect to database!
2009-12-08 08:12:31.365 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


2009-12-08 08:12:31.513 UPnPautoconf() - Found one UPnP backend
2009-12-08 08:12:31.652 MythXMLClient::GetConnectionInfo Failed - (606) Action Not Authorized
2009-12-08 08:12:31.652 Testing network connectivity to '10.1.1.10'
2009-12-08 08:12:31.657 Closing DB connection named 'DBManager0'
2009-12-08 08:12:46.671 Unable to connect to database!
2009-12-08 08:12:46.671 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'10.1.1.100' (using password: YES)

2009-12-08 08:12:46.671 Cannot login to database?
2009-12-08 08:12:46.682 Primary screen: 0.
2009-12-08 08:12:46.682 Using screen 0, 1280x800 at 0,0
2009-12-08 08:12:46.724 Using theme base resolution of 1280x720
2009-12-08 08:12:46.766 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
                        eno: No such file or directory (2)
2009-12-08 08:12:46.768 JoystickMenuThread Error: Joystick disabled - Failed to read /home/mythclient/.mythtv/joystickmenurc
2009-12-08 08:12:46.794 Using the Qt painter
2009-12-08 08:12:59.123 User cancelled database configuration
2009-12-08 08:12:59.125 Failed to init MythContext, exiting.
2009-12-08 08:12:59.125 Deleting UPnP client...

```

---

### Post by map7 on 2009-12-08
Thanks to wagnerrp & iamlindoro on IRC I got a solution to this problem.  It was two things:

The bind-address in my.cnf must be equal to your mysql server in my case this was
bind-address=10.1.1.10

Second was the grant command was wrong.  It should be:
mysql> grant all on mythconverg.* to 'mythtv'@'10.1.1.100' identified by 'mythtv';

Assuming my client got IP 10.1.1.100.  The password is 'mythtv' no matter what your password is in mysql.txt.  The client use username:mythtv, password:mythtv to connect.

---

