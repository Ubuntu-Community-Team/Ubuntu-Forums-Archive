---
title: "MythTV doesn't create tables on installation"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by thefeffa on 2007-04-21
I'm following the [backend frontend desktop guide]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop?highlight=%28mythtv%29") for Feisty MythTV, but after the mythtv packages are loaded, the MythTV tables aren't created in MySQL. I didn't realize it at first, because as I ran mythtv-setup from the System menu, it moved through the setup pages but it never saved my information. Finally, I ran it from the terminal and I saw a lot of errors, including the following examples near the end of my errors:

> 2007-04-21 08:30:53.428 DB Error (Insert Keybinding):
Query was:
INSERT INTO keybindings (context, action, description, keylist, hostname) VALUES ( 'Global', '9', '9', '9', 'optimus' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.keybindings' doesn't exist

2007-04-21 08:30:54.727 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-04-21 08:30:54.879 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-21 08:39:17.655 DB Error (Clear setting):
Query was:
DELETE FROM settings WHERE value = 'Language' AND hostname = 'optimus' ;
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.settings' doesn't exist

2007-04-21 08:39:17.656 DB Error (Save new setting on host):
Query was:
INSERT INTO settings ( value, data, hostname ) VALUES ( 'Language', '', 'optimus' );
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.settings' doesn't exist

2007-04-21 08:39:44.472 DB Error (checkStoragePaths):
Query was:
SELECT data FROM settings WHERE value='RecordFilePrefix' AND hostname = 'optimus';
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.settings' doesn't exist

2007-04-21 08:39:44.473 DB Error (checkChannelPresets):
Query was:
SELECT cardid, startchan, sourceid, inputname FROM cardinput;
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.cardinput' doesn't exist


These tables don't look like they were created in MySQL. I added the keybindings table by hand, but then got wise and decided to see if anyone had already come across this problem or if there was a script that I could run to create all the tables (maybe this got missed by my package installer?)

Thanks!

P.S. I've had mythtv running on this same setup in Edgy.

---

### Post by thefeffa on 2007-04-21
Okay, I got it figured out. Because of the way the guide is set up, I was supposed to skip certainly sections. One section I inadvertently skipped was this one:

> First, you need to edit the mysql configuration to allow outside hosts to connect:

$ sudo nano /etc/mysql/my.cnf

Look for the line that reads:

    *

      bind-address= 127.0.0.1
         

and comment out that line by placing a # at the beginning.

Then, restart mysql:

$ sudo /etc/init.d/mysql restart


That got it working.

---

### Post by superm1 on 2007-04-21
for Gutsy, it will be planned as a debconf step to do this for you (and secure your root password at the same time).  Glad you figured it out though.

---

### Post by isionous on 2007-06-10
When I run "sudo /etc/init.d/mysql restart", I get the following:

 * Stopping MySQL database server mysqld                                                          [fail] 
 * Starting MySQL database server mysqld                                                          [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

How do I fix this so it tries mythtv@jmegner-desktop1 instead of debian-sys-maint@localhost?  Or is there some problem with passwords and it really needs to be debian-sys-maint?

---

### Post by superm1 on 2007-06-10
> **isionous said:**
> When I run "sudo /etc/init.d/mysql restart", I get the following:

 * Stopping MySQL database server mysqld                                                          [fail] 
 * Starting MySQL database server mysqld                                                          [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

How do I fix this so it tries mythtv@jmegner-desktop1 instead of debian-sys-maint@localhost?  Or is there some problem with passwords and it really needs to be debian-sys-maint?
Somehow you lost the administration user for mysql.  If this is a fresh install, purge the mysql server and reinstall it.
```
sudo apt-get remove --purge mythtv-database mysql-server-5.0
sudo apt-get install mythtv-database mysql-server-5.0
```

---

### Post by isionous on 2007-06-18
Thanks, doing the --purges on everything mysql and mythtv related helped.

---

### Post by Fred_geek on 2007-07-10
I was getting so frustrated trying to figure out why the way the tutorial said didn't work lol 
The purging and reinstallation really worked for me, 
Everything myth and mysql related worked

---

### Post by superm1 on 2007-07-10
> **Fred_geek said:**
> I was getting so frustrated trying to figure out why the way the tutorial said didn't work lol 
The purging and reinstallation really worked for me, 
Everything myth and mysql related worked

I still haven't identified the cause of this, but I have something in the gutsy packages that should hopefully work around it.

---

