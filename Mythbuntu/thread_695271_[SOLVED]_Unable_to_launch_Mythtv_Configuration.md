---
title: "[SOLVED] Unable to launch Mythtv Configuration"
date: 2008-02-12
forum: Mythbuntu
---

### Post by karlec on 2008-02-12
I have not been able to launch MythTv configuration from the MCC.  I am getting the following
```
2008-02-12 21:24:37.433 Using runtime prefix = /usr, libdir = /usr/lib
2008-02-12 21:24:37.453 XScreenSaver support enabled
2008-02-12 21:24:37.454 DPMS is active.
2008-02-12 21:24:37.464 Empty LocalHostName.
2008-02-12 21:24:37.464 Using localhost value of jMyth
2008-02-12 21:24:37.473 New DB connection, total: 1
2008-02-12 21:24:37.477 Unable to connect to database!
2008-02-12 21:24:37.477 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-02-12 21:24:37.528 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
................................................................................
2008-02-12 21:24:40.202 UPnPautoconf() - No UPnP backends found
2008-02-12 21:24:40.202 No UPnP backends found
2008-02-12 21:24:40.207 Total desktop dim: 1280x1024, with 1 screen[s].
2008-02-12 21:24:40.209 Using screen 0, 1280x1024 at 0,0
2008-02-12 21:24:40.228 Switching to square mode (blue)
2008-02-12 21:24:40.285 Using the Qt painter
2008-02-12 21:24:40.293 Joystick disabled.
mythtv: could not connect to socket
mythtv: Connection refused
2008-02-12 21:24:40.294 lirc_init failed for mythtv, see preceding messages
2008-02-12 21:24:43.424 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2008-02-12 21:24:43.424 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...
2008-02-12 21:24:43.424 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2008-02-12 21:24:43.424 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...
2008-02-12 21:24:48.799 Writing settings file /home/myth/.mythtv/mysql.txt
2008-02-12 21:24:48.800 Closing DB connection named 'DBManager0'
2008-02-12 21:24:48.819 Unable to connect to database!
2008-02-12 21:24:48.819 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-02-12 21:24:48.870 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-02-12 21:24:48.920 Cannot login to database?
2008-02-12 21:24:48.920 Cannot login to database?
2008-02-12 21:24:48.921 Total desktop dim: 1280x1024, with 1 screen[s].
2008-02-12 21:24:48.922 Using screen 0, 1280x1024 at 0,0
2008-02-12 21:24:48.925 Switching to square mode (blue)
2008-02-12 21:24:48.933 Using the Qt painter
mythtv: could not connect to socket
mythtv: Connection refused
2008-02-12 21:24:48.934 lirc_init failed for mythtv, see preceding messages
2008-02-12 21:24:48.935 Joystick disabled.
2008-02-12 21:24:49.593 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2008-02-12 21:24:49.593 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...

```

This is on Hardy.

---

### Post by superm1 on 2008-02-12
What'd you do?  upgrading?  Fresh install?  What steps led up to this?

---

### Post by karlec on 2008-02-12
It is a fresh install of Hardy first, then the Mythbuntu packages.

---

### Post by superm1 on 2008-02-13
Hm well that's not good :)

Did you modify anything by hand configuration wise?

---

### Post by karlec on 2008-02-13
I set up everything else on the MCC and installed a few packages, but nothing really involved.

---

### Post by superm1 on 2008-02-13
Well can you check and see if the password defined in /etc/mythtv/mysql.txt is working, or where the issue is coming from?  As of hardy the passwords in ~/.mythtv should all be symlinked to /etc/mythtv/mysql.txt, so hopefully that isn't where the issue developed, but it's possible that something is getting overlooked.

---

### Post by karlec on 2008-02-13
Thanks again for responding.  I'll check when I get home tonight.

---

### Post by karlec on 2008-02-14
Ok I decided to start from scratch again and reinstall.

Now I am getting the following message when I try to set-up the system roles to Primary Backend/FrontEnd/Ubuntu Desktop::
```
E:Unable to correct problems, you have held broken packages.
```

---

### Post by superm1 on 2008-02-15
Can you see if this is still persisting?  It shouldn't be after you run apt-get update/apt-get upgrade

---

### Post by karlec on 2008-02-16
I am still getting the same message.

---

### Post by superm1 on 2008-02-16
Open up synaptic and look for it's broken packages filter.  See if you can resolve them there.

---

### Post by karlec on 2008-02-18
Nothing is coming up in the broken package filter in Synaptic.  The other part of the message was to:

```
 Check your repository list for universe, multiverse, main.  Perform packagelist update as well
``` 

I I have run both update and upgrade commands, and checked  my sources lists.  Nothing unusual there either that I could tell.

```
 # deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha amd64 (20080201.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://packages.medibuntu.org/ hardy free non-free
```

---

### Post by mckemie on 2008-07-15
I've just installed mythbuntu 8.04.1 and encountered seemingly the same problem "cannot (EVER) login to database".  I've browsed through this thread and do not see a solution.  What am I missing?

---

### Post by t-tbone on 2008-07-24
Same here.  Fresh install on 8.0.4 and the database can't connect.

---

### Post by scru on 2008-07-25
Same issue (Cannot login to Database).

---

### Post by drkm_4_frm on 2008-07-27
Can some one tell how this is solved?

---

### Post by pmorton on 2008-07-29
-

---

### Post by pmorton on 2008-07-29
Same issue. Does anyone know what's wrong?

---

### Post by pmorton on 2008-07-31
Solved, pace linuxgrrl (see [http://ubuntuforums.org/showthread.php?t=75963](http://ubuntuforums.org/showthread.php?t=75963))
 
sudo apt-get install libqt3-mt-mysq

---

### Post by nanobug on 2008-08-11
that is a thread from 2005 and it didn't solve anything.  kind of jumped the gun there.

---

### Post by jfacemyer on 2008-08-13
I don't know if it's the right way to do it, but I fixed the problem by adding the mysql user and database (the setup interface was trying to use "mythtv" as both the user and password for the mysql database "mythconverg").

```
mysql -u root -p
(enter password)
CREATE DATABASE mythconverg;
GRANT ALL ON mythconverg.* TO 'mythtv'@'localhost' IDENTIFIED BY 'mythtv';
```

Hope that helps.

---

### Post by PapaGoose on 2008-08-31
Just as an aside, I had very similar problems when trying to get alternate front ends to remotely connect to the backend. On your back end machine, log into mysql and run 

```
grant all on mythconverg.* to '<username>'@'<frontend IP>' identified by '<password>';

```

from the SQL prompt so that your specific frontend has privileges to remotely connect. Of course, this also implies that you need to have assigned static IPs to both your back end and your front end.

I also ran

```
set password for '<username>'@'<front end IP>' = OLD_PASSWORD('<password>');
```

not sure if this last one did anything, it probably won't if everything else is up to date, but my setup works fine now

---

### Post by jrlrocks on 2008-09-17
THANK YOU THANK YOU!

2 very long days hunting for an answer came to an emd!
:popcorn: time!

---

### Post by CadetD on 2009-07-27
Yes! Yes! Thanks.

---

