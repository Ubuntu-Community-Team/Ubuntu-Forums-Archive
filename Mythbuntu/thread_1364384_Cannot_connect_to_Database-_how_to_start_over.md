---
title: "Cannot connect to Database- how to start over?"
date: 2009-12-25
forum: Mythbuntu
---

### Post by purduephotog on 2009-12-25
This has been a long, long day.  

I just received a couple of new disks and the wife would like to watch them.  I put them into the Mythbuntu setup and booted the system.  It comes up "Cannot connect to database".  All fields are empty.

I would really like to get this system back up and running.  When I follow some of the suggestions here [https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

I get nowhere- for various issues.

When I run the mythtvconfig I get this:
```
2009-12-25 19:37:32.483 Using runtime prefix = /usr
2009-12-25 19:37:32.490 XScreenSaver support enabled
2009-12-25 19:37:32.491 DPMS is disabled.
2009-12-25 19:37:32.491 Empty LocalHostName.
2009-12-25 19:37:32.491 Using localhost value of mythbuntu
2009-12-25 19:37:32.499 New DB connection, total: 1
2009-12-25 19:37:32.503 Unable to connect to database!
2009-12-25 19:37:32.503 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-12-25 19:37:32.554 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
................................................................................
2009-12-25 19:37:35.112 UPnPautoconf() - No UPnP backends found
2009-12-25 19:37:35.112 No UPnP backends found
2009-12-25 19:37:35.114 Primary screen 0.
2009-12-25 19:37:35.114 Using screen 0, 1024x768 at 0,0
2009-12-25 19:37:35.114 No theme dir: /home/hirsch/.mythtv/themes/blue
2009-12-25 19:37:35.115 Switching to square mode (blue)
2009-12-25 19:37:35.128 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-12-25 19:37:35.128 lirc_init failed for mythtv, see preceding messages
2009-12-25 19:37:35.129 JoystickMenuClient Error: Joystick disabled - Failed to read /home/hirsch/.mythtv/joystickmenurc

```

At this point, I don't give a damn if I have to re-find all 300+ dvds on the unit.  I just want it working and I don't feel the need to dick around with the TOSlink for 3 weeks again so I am not truly interested in upgrading yet.

If you can provide me a simple, how to reset the stupid thing and start over, I'd be most grateful.

---

### Post by iponeverything on 2009-12-26
What do you see when you do:

```
sudo /etc/init.d/mysql restart

```


What shows up in the latest mysql log in:

/var/log/mysql

```
ls -ltr 

```

will show you newest one at the bottom.

---

### Post by purduephotog on 2009-12-26
[sudo] password for hirsch: 
 * Stopping MySQL database server mysqld
   ...done.
 * Starting MySQL database server mysqld
   ...done.
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
hirsch@mythbuntu:~$ 

As for /var/log/mysql - there's nothing in it (as of this morning and after the afore mentioned restart)

---

### Post by iponeverything on 2009-12-26
Can you log into the database with:

```

sudo mysql -u root

```

It that does not work see:
[http://www.mythtv.org/wiki/Reset_MySQL_root_Password](http://www.mythtv.org/wiki/Reset_MySQL_root_Password)

change the password for mysql mythtv account:

[http://ubuntuforums.org/showthread.php?t=360401](http://ubuntuforums.org/showthread.php?t=360401)

Put the correct password in:
```
/etc/mythtv/mysql.txt

```

---

