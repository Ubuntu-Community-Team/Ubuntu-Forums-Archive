---
title: "Help reinstalling mythtv"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by jba6511 on 2007-05-29
Once upon a time I had mythtv working except for the remote. I was playing around with the settings trying to run it in a window and I ended up changing the resolution so that I could no longer see anything. I tried to uninstall and reinstall and everything would go back to the way it was. I was told to use sudo apt-get --purge mythtv, which I did and then I searched for the remaining mythtv files to delete by hand. Those I found were locked to I changed permissions and deleted. Now I went to reinstall mythtv and I can not get the backend process to run that the front connects to. I have pasted the output from the log. I believe everything right now is a big mess. If someone could tell me a way to completely remove everything mythtv from my system or help me sort out this mess. I tried freevo as well and did not like it. Would like to go back to mythtv but do not know if it is going to work short of doing a reinstall of ubuntu. Help please, I;m begging.




[PHP]blake@Ubuntu-Desktop:~$ more /var/log/mythtv/mythbackend.log
2007-05-29 18:45:34.104 Using runtime prefix = /usr
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:45:34.231 New DB connection, total: 1
2007-05-29 18:45:34.235 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:45:34.258 Current Schema Version: 1160
Starting up as the master server.
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:45:34.290 New DB connection, total: 2
2007-05-29 18:45:34.292 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:45:34.296 EITHelper: localtime offset -4:00:00 
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:45:34.313 New DB connection, total: 3
2007-05-29 18:45:34.314 Connected to database 'mythconverg' at host: localhost
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:45:34.697 New DB scheduler connection
2007-05-29 18:45:34.958 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:45:34.969 Main::Starting HttpServer
2007-05-29 18:45:34.985 Main::Registering HttpStatus Extension
2007-05-29 18:45:35.005 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-05-29 18:45:35.009 Enabled verbose msgs:  important general
2007-05-29 18:45:35.010 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2007-05-29 18:45:35.011 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2007-05-29 18:45:35.105 DB Error (Clear setting):
Query was:
DELETE FROM settings WHERE value = 'upnp:UDN:urn:schemas-upnp-org:device:MediaSe
rver:1' AND hostname = 'Ubuntu-Desktop' ;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:35.111 DB Error (Save new setting on host):
Query was:
INSERT INTO settings ( value, data, hostname ) VALUES ( 'upnp:UDN:urn:schemas-up
np-org:device:MediaServer:1', '5e16f4fb-bc89-4fe0-8a6e-addaa0774d44', 'Ubuntu-De
sktop' );
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:36.125 DB Error (Clear setting):
Query was:
DELETE FROM settings WHERE value = 'upnp:UDN:urn:schemas-upnp-org:device:MediaSe
rver:1' AND hostname = 'Ubuntu-Desktop' ;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:36.129 DB Error (Save new setting on host):
Query was:
INSERT INTO settings ( value, data, hostname ) VALUES ( 'upnp:UDN:urn:schemas-up
np-org:device:MediaServer:1', 'a050b274-0f4b-4cc2-975e-e386be9d6f8a', 'Ubuntu-De
sktop' );
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:37.008 Reschedule requested for id -1.
2007-05-29 18:45:37.013 DB Error (UpdateMatches):
Query was:
DELETE FROM recordmatch WHERE recordid = -1 OR -1 = -1;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:37.016 DB Error (CheckTooMany):
Query was:
SELECT recordid,title,maxepisodes,maxnewest FROM record;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:37.018 DB Error (AddNotListed):
Query was:
SELECT record.recordid, record.type, record.chanid, record.starttime, record.sta
rtdate, record.endtime, record.enddate, record.startoffset, record.endoffset, re
cord.title, record.subtitle, record.description, channel.channum, channel.callsi
gn, channel.name FROM record  INNER JOIN channel ON (channel.chanid = record.cha
nid)  LEFT JOIN recordmatch on record.recordid = recordmatch.recordid WHERE (typ
e = 1 OR type = 2 OR type = 5 OR type = 7)  AND recordmatch.chanid IS NULL
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:37.018 Scheduled 0 items in 0.0 = 0.01 match + 0.00 place
2007-05-29 18:45:37.020 Seem to be woken up by USER
2007-05-29 18:45:37.144 DB Error (Clear setting):
Query was:
DELETE FROM settings WHERE value = 'upnp:UDN:urn:schemas-upnp-org:device:MediaSe
rver:1' AND hostname = 'Ubuntu-Desktop' ;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:37.149 DB Error (Save new setting on host):
Query was:
INSERT INTO settings ( value, data, hostname ) VALUES ( 'upnp:UDN:urn:schemas-up
np-org:device:MediaServer:1', 'fba96480-cba9-423d-9a95-c765aa14e998', 'Ubuntu-De
sktop' );
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:38.161 DB Error (Clear setting):
Query was:
DELETE FROM settings WHERE value = 'upnp:UDN:urn:schemas-upnp-org:device:MediaSe
rver:1' AND hostname = 'Ubuntu-Desktop' ;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:38.161 DB Error (Save new setting on host):
Query was:
INSERT INTO settings ( value, data, hostname ) VALUES ( 'upnp:UDN:urn:schemas-up
np-org:device:MediaServer:1', 'f71ef479-9e51-4f42-a57d-b69fb3fe2178', 'Ubuntu-De
sktop' );
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:39.173 DB Error (Clear setting):
Query was:
DELETE FROM settings WHERE value = 'upnp:UDN:urn:schemas-upnp-org:device:MediaSe
rver:1' AND hostname = 'Ubuntu-Desktop' ;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:39.173 DB Error (Save new setting on host):
Query was:
INSERT INTO settings ( value, data, hostname ) VALUES ( 'upnp:UDN:urn:schemas-up
np-org:device:MediaServer:1', 'a7aa4d26-873e-4a80-8050-ec59999e518e', 'Ubuntu-De
sktop' );
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:44.282 DB Error (JobQueue::CleanupOldJobsInQueue: Error deletin
g old finished jobs.):
Query was:
DELETE FROM jobqueue WHERE (status in (272, 288, 320) AND statustime < '2007-05-
27T18:45:44') OR (status in (304) AND statustime < '2007-05-25T18:45:44')
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:44.290 DB Error (HouseKeeper Cleaning Recorded Tables):
Query was:
SELECT DISTINCT p.chanid, p.starttime FROM recordedprogram p LEFT JOIN recorded 
r ON p.chanid = r.chanid AND p.starttime = r.progstart WHERE r.chanid IS NULL;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:44.292 DB Error (Error in JobQueue::GetJobs(), Unable to query 
list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.sta
tus, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, rec
orded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inser
ttime, j.chanid, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:45:44.978 DB Error (Error in JobQueue::GetJobs(), Unable to query 
list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.sta
tus, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, rec
orded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inser
ttime, j.chanid, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-29 18:49:29.929 Using runtime prefix = /usr
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:49:29.953 New DB connection, total: 1
2007-05-29 18:49:29.957 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:49:29.959 Current Schema Version: 1160
Starting up as the master server.
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:49:29.967 New DB connection, total: 2
2007-05-29 18:49:29.967 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:49:29.969 EITHelper: localtime offset -4:00:00 
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:49:29.975 New DB connection, total: 3
2007-05-29 18:49:29.975 Connected to database 'mythconverg' at host: localhost
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:49:30.265 New DB scheduler connection
2007-05-29 18:49:30.266 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:49:30.269 Main::Starting HttpServer
2007-05-29 18:49:30.272 Main::Registering HttpStatus Extension
2007-05-29 18:49:30.277 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-05-29 18:49:30.278 Enabled verbose msgs:  important general
/home/blake/Tv Recordings//nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/home/blake/Tv Recordings/' exists and that both 
the directory and that file are writeable by this user.
2007-05-29 18:52:37.234 Using runtime prefix = /usr
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:52:37.333 New DB connection, total: 1
2007-05-29 18:52:37.343 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:52:37.356 Current Schema Version: 1160
Starting up as the master server.
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:52:37.396 New DB connection, total: 2
2007-05-29 18:52:37.403 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:52:37.405 EITHelper: localtime offset -4:00:00 
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:52:37.420 New DB connection, total: 3
2007-05-29 18:52:37.426 Connected to database 'mythconverg' at host: localhost
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:52:37.860 New DB scheduler connection
2007-05-29 18:52:37.862 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:52:37.865 Main::Starting HttpServer
2007-05-29 18:52:37.868 Main::Registering HttpStatus Extension
2007-05-29 18:52:37.873 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-05-29 18:52:38.141 Enabled verbose msgs:  important general
/home/blake/Tv Recordings//nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/home/blake/Tv Recordings/' exists and that both 
the directory and that file are writeable by this user.
2007-05-29 18:54:46.917 Using runtime prefix = /usr
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:54:46.935 New DB connection, total: 1
2007-05-29 18:54:46.939 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:54:46.941 Current Schema Version: 1160
Starting up as the master server.
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:54:46.948 New DB connection, total: 2
2007-05-29 18:54:46.948 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:54:46.950 EITHelper: localtime offset -4:00:00 
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:54:46.954 New DB connection, total: 3
2007-05-29 18:54:46.955 Connected to database 'mythconverg' at host: localhost
QSettings: error creating /home/mythtv/.qt
QSettings::sync: filename is null/empty
2007-05-29 18:54:47.101 New DB scheduler connection
2007-05-29 18:54:47.102 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:54:47.105 Main::Starting HttpServer
2007-05-29 18:54:47.107 Main::Registering HttpStatus Extension
2007-05-29 18:54:47.111 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-05-29 18:54:47.114 Enabled verbose msgs:  important general
/home/blake/Tv Recordings//nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/home/blake/Tv Recordings/' exists and that both 
the directory and that file are writeable by this user.
2007-05-29 18:59:37.305 Using runtime prefix = /usr
2007-05-29 18:59:37.478 New DB connection, total: 1
2007-05-29 18:59:37.527 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:59:37.591 Current Schema Version: 1160
Starting up as the master server.
2007-05-29 18:59:37.864 New DB connection, total: 2
2007-05-29 18:59:37.902 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:59:38.014 EITHelper: localtime offset -4:00:00 
2007-05-29 18:59:38.099 New DB connection, total: 3
2007-05-29 18:59:38.404 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:59:38.972 New DB scheduler connection
2007-05-29 18:59:39.050 Connected to database 'mythconverg' at host: localhost
2007-05-29 18:59:39.072 Main::Starting HttpServer
2007-05-29 18:59:39.421 Main::Registering HttpStatus Extension
2007-05-29 18:59:39.684 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-05-29 18:59:39.997 Enabled verbose msgs:  important general
/home/blake/Tv Recordings//nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/home/blake/Tv Recordings/' exists and that both 
the directory and that file are writeable by this user.
Mutex destroy failure: Device or resource busy
2007-05-29 18:59:41.086 Reschedule requested for id -1.
2007-05-29 22:02:39.656 Using runtime prefix = /usr
2007-05-29 22:02:39.678 New DB connection, total: 1
2007-05-29 22:02:39.791 Connected to database 'mythconverg' at host: localhost
2007-05-29 22:02:39.806 Current Schema Version: 1160
Starting up as the master server.
2007-05-29 22:02:39.913 New DB connection, total: 2
2007-05-29 22:02:40.198 Connected to database 'mythconverg' at host: localhost
2007-05-29 22:02:40.208 EITHelper: localtime offset -4:00:00 
2007-05-29 22:02:40.216 New DB connection, total: 3
2007-05-29 22:02:40.217 Connected to database 'mythconverg' at host: localhost
2007-05-29 22:02:40.369 New DB scheduler connection
2007-05-29 22:02:40.456 Connected to database 'mythconverg' at host: localhost
2007-05-29 22:02:40.463 Main::Starting HttpServer
2007-05-29 22:02:40.468 Main::Registering HttpStatus Extension
2007-05-29 22:02:40.472 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-05-29 22:02:40.475 Enabled verbose msgs:  important general
/home/blake/Tv Recordings//nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/home/blake/Tv Recordings/' exists and that both 
the directory and that file are writeable by this user.
2007-05-29 22:16:46.665 Using runtime prefix = /usr
2007-05-29 22:16:46.685 New DB connection, total: 1
2007-05-29 22:16:46.690 Connected to database 'mythconverg' at host: localhost
2007-05-29 22:16:46.692 Current Schema Version: 1160
Starting up as the master server.
2007-05-29 22:16:46.696 New DB connection, total: 2
2007-05-29 22:16:46.697 Connected to database 'mythconverg' at host: localhost
2007-05-29 22:16:46.699 EITHelper: localtime offset -4:00:00 
2007-05-29 22:16:46.702 New DB connection, total: 3
2007-05-29 22:16:46.703 Connected to database 'mythconverg' at host: localhost
2007-05-29 22:16:46.852 New DB scheduler connection
2007-05-29 22:16:46.853 Connected to database 'mythconverg' at host: localhost
2007-05-29 22:16:46.854 Main::Starting HttpServer
2007-05-29 22:16:46.857 Main::Registering HttpStatus Extension
2007-05-29 22:16:46.861 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-05-29 22:16:46.862 Enabled verbose msgs:  important general
/home/blake/Tv Recordings//nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/home/blake/Tv Recordings/' exists and that both 
the directory and that file are writeable by this user.
[/PHP]

---

### Post by tgm4883 on 2007-05-29
when you removed mythtv, did you also remove the database?

---

### Post by jba6511 on 2007-05-30
was it called something like mythtv-common-database or mythtv-database? If it can be removed in synaptic I did. On a windows machine right now so I will look later but I removed everything from synaptic that was mythtv related.

---

### Post by tgm4883 on 2007-05-30
Yea I think thats it.  You need to make sure you purged those too.  If you don't have any other sql databases you can also remove and purge mysql

---

### Post by jba6511 on 2007-05-30
Thanks will try that.

---

### Post by tgm4883 on 2007-05-30
sudo apt-get remove --purge mysql

---

### Post by jba6511 on 2007-05-30
I purged everything and reinstalled the mysql packages cause I was not sure if I needed them or not and they had the ubuntu logo by them. I have not installed anything except for hellanzb, screenlets, gnome-compiz-manager, beryl, avant windwo navigator, and ntfs-3g. I did not want to mess with those files until I got confirmation from someone here.

---

### Post by jba6511 on 2007-05-30
blake@Ubuntu-Desktop:~$ sudo apt-get remove --purge mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mysql
blake@Ubuntu-Desktop:~$

---

### Post by tgm4883 on 2007-05-30
sorry, 

sudo apt-get remove --purge mysql-server

---

### Post by jba6511 on 2007-05-30
blake@Ubuntu-Desktop:~$ sudo apt-get remove --purge mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-server is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Guess I do not need to worry about that then. Will try to reinstall now and report how it goes

---

### Post by jba6511 on 2007-05-30
well here is the new error log. Looks cleaner anyways:

[PHP]blake@Ubuntu-Desktop:~$ ps -p `cat /var/run/mythtv/mythbackend.pid`
  PID TTY          TIME CMD
blake@Ubuntu-Desktop:~$  more /var/log/mythtv/mythbackend.log
2007-05-30 12:32:41.412 Using runtime prefix = /usr
2007-05-30 12:32:41.459 New DB connection, total: 1
2007-05-30 12:32:41.585 Connected to database 'mythconverg' at host: localhost
2007-05-30 12:32:41.674 Current Schema Version: 1160
Starting up as the master server.
2007-05-30 12:32:42.404 New DB connection, total: 2
2007-05-30 12:32:42.416 Connected to database 'mythconverg' at host: localhost
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2007-05-30 12:32:42.467 DB Error (Error in JobQueue::GetJobs(), Unable to query 
list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.sta
tus, j.statustime, j.hostname, j.args, j.comment, r.endtime FROM jobqueue j, rec
orded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inser
ttime, j.chanid, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2007-05-30 12:32:42.467 Main::Starting HttpServer
2007-05-30 12:32:42.500 Main::Registering HttpStatus Extension
2007-05-30 12:32:42.507 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-05-30 12:32:42.508 Enabled verbose msgs:  important general
/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '' exists and that both 
the directory and that file are writeable by this user.
2007-05-30 12:36:31.356 Using runtime prefix = /usr
2007-05-30 12:36:31.377 New DB connection, total: 1
2007-05-30 12:36:31.381 Connected to database 'mythconverg' at host: localhost
2007-05-30 12:36:31.384 Current Schema Version: 1160
Starting up as the master server.
2007-05-30 12:36:31.388 New DB connection, total: 2
2007-05-30 12:36:31.389 Connected to database 'mythconverg' at host: localhost
2007-05-30 12:36:31.391 EITHelper: localtime offset -4:00:00 
2007-05-30 12:36:31.394 New DB connection, total: 3
2007-05-30 12:36:31.395 Connected to database 'mythconverg' at host: localhost
2007-05-30 12:36:31.542 New DB scheduler connection
2007-05-30 12:36:31.543 Connected to database 'mythconverg' at host: localhost
2007-05-30 12:36:31.545 Main::Starting HttpServer
2007-05-30 12:36:31.548 Main::Registering HttpStatus Extension
2007-05-30 12:36:31.551 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-05-30 12:36:31.552 Enabled verbose msgs:  important general
/home/blake/Tv Recordings//nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/home/blake/Tv Recordings/' exists and that both 
the directory and that file are writeable by this user.
[/PHP]

---

### Post by tgm4883 on 2007-05-30
did you run mythtv-setup?

---

### Post by jba6511 on 2007-05-30
yeah I ran the mythtv-backend setup, and all of my previously enter info was still there. I then filled the database when it asked and then went that was complete, ran the command to see if the backend server was running, which it is not. Apparently, all of the purging and removal of files I did according to this thread did no good if it saved the configuration info still. However, I am getting fewer errors (I think only 2). Can anyone look at the log and see what is wrong? It says something about not configuring the capture card but it is already setup and ready to go.

---

### Post by jba6511 on 2007-05-31
please someone??? I am begging here.

---

### Post by rhpot1991 on 2007-05-31
Are you sure the database is there and your mythtv user(or whatever you setup) has access to it?  I would try removing the tuner card from your mythtv setup and re-adding it.  I would be worried about the data lying around still, seems you didn't purge some of the mythpackages.  Fire up Synaptec search for mythtv and completely remove all of the packages then start from scratch.

---

### Post by jba6511 on 2007-05-31
maybe I am leaving a package or to as I have tried that. I am at school right now but I will list all of the packages I remove completely from syanptic later tonight.

---

### Post by jba6511 on 2007-05-31
the packages I completely removed using synaptic are:

libmyth-0.20
mythtv
mythtv-backend
mythtv-common
mythtv-database
mythtv-frontend

am I missing something else?

---

### Post by rhpot1991 on 2007-05-31
Looks about right, only other things are plugins but you might not have any installed.

---

### Post by jba6511 on 2007-05-31
no plugins installed. I have marked these for complete removal and then I still find a few folders left behind after the uninstallation. Synaptic asks me for my password when I first start it but do I maybe need to be root in order to completely remove everything? Just a newbie thinking out loud.

for example, I just searched my filesystem for myth and found stuff like mythtv-backend in my /etc/default after the uninstall

---

### Post by tgm4883 on 2007-05-31
> **jba6511 said:**
> the packages I completely removed using synaptic are:

libmyth-0.20
mythtv
mythtv-backend
mythtv-common
mythtv-database
mythtv-frontend

am I missing something else?

you purged those too right?

---

### Post by rhpot1991 on 2007-05-31
I believe that "complete removal" or whatever it is in Synaptec purges the files associated with a package.

---

### Post by tgm4883 on 2007-05-31
> **rhpot1991 said:**
> I believe that "complete removal" or whatever it is in Synaptec purges the files associated with a package.

Ha, I knew that, didn't see that he said completely removed.

---

### Post by jba6511 on 2007-05-31
any idea why those files are left behind then. I have 28 related to mythtv left after complete removal. It has to be one of these that is holding my configuration settings right? I have attached a screenshot of whats left over.

---

### Post by jba6511 on 2007-06-01
maybe someone can answer this today

---

### Post by tgm4883 on 2007-06-01
> **jba6511 said:**
> maybe someone can answer this today

Some of those are cache files for apt.  Some are log files.  What I would do if I were you is this.

```
sudo apt-get install mythtv-backend mythtv-frontend
```

Let it install, then do

```
sudo apt-get remove --purge mythtv-backend mythtv-frontend mythtv-database mysql-server libmyth-0.20 libmyth-0.20-dev mytharchive-data mytharchive mythbrowser mythcontrols mythdvd mythflix mythgallery mythgame mythmusic mythnews mythphone mythplugins mythtv mythtv-backend-master mythtv-common mythtv-doc mythtv-themes mythvideo mythweather mythweb ubuntu-mythtv-frontend
```

Then bust on over to the community documents and follow the guide there to install

---

### Post by jba6511 on 2007-06-01
Followed the advice from above and below is the output after purging the documents. Some directories and files were not removed, so what should be done about these:

(Reading database ... 135493 files and directories currently installed.)
Removing mythtv-frontend ...
Purging configuration files for mythtv-frontend ...
Removing mythtv-backend ...
Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
Purging configuration files for mythtv-backend ...
dpkg - warning: while removing mythtv-backend, directory `/var/lib/mythtv/recordings' not empty so not removed.
dpkg - warning: while removing mythtv-backend, directory `/var/lib/mythtv' not empty so not removed.
Removing libmyth-0.20 ...
Purging configuration files for libmyth-0.20 ...
Removing mysql-server ...
Removing mythtv-common ...
Purging configuration files for mythtv-common ...
dpkg - warning: while removing mythtv-common, directory `/etc/mythtv' not empty so not removed.

---

### Post by rhpot1991 on 2007-06-01
> **jba6511 said:**
> Followed the advice from above and below is the output after purging the documents. Some directories and files were not removed, so what should be done about these:

(Reading database ... 135493 files and directories currently installed.)
Removing mythtv-frontend ...
Purging configuration files for mythtv-frontend ...
Removing mythtv-backend ...
Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
Purging configuration files for mythtv-backend ...
dpkg - warning: while removing mythtv-backend, directory `/var/lib/mythtv/recordings' not empty so not removed.
dpkg - warning: while removing mythtv-backend, directory `/var/lib/mythtv' not empty so not removed.
Removing libmyth-0.20 ...
Purging configuration files for libmyth-0.20 ...
Removing mysql-server ...
Removing mythtv-common ...
Purging configuration files for mythtv-common ...
dpkg - warning: while removing mythtv-common, directory `/etc/mythtv' not empty so not removed.

I would go ahead and remove the directories it didn't want to remove.  I would guess that it had files in there that dkpg didn't install and therefor it doesn't want to remove something that is needed.  But, you are installing again so nothing should be effected.  Try killing all those directories then installing based on the directions on the mythtv wiki, they are quite good.

---

### Post by jba6511 on 2007-06-01
yeah I used the guide before and got it running . WIll try manually deleting the files and see if it works.

---

### Post by jba6511 on 2007-06-01
Ok that seemed to have erased all of the previous settings. Now when I click on frontend for the mythtv, nothing happens. I know it takes awhile to load by I have tried twice waiting 15 minutes in between and nothing loads. My comp froze up once but that is all. When mythtv was working it did not take nearly this long. Can I do anything about this?

---

### Post by tgm4883 on 2007-06-01
Try starting it from the command line, then we can see any errors.

---

### Post by jba6511 on 2007-06-02
[PHP]blake@Ubuntu-Desktop:~$ mythfrontend
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-06-01 23:59:45.788 Using runtime prefix = /usr
2007-06-01 23:59:45.794 Gnome-Screensaver support enabled
2007-06-01 23:59:45.794 DPMS is active.
2007-06-01 23:59:45.803 New DB connection, total: 1
2007-06-01 23:59:45.806 Connected to database 'mythconverg' at host: localhost
2007-06-01 23:59:45.806 Total desktop dim: 1280x1024, with 1 screen[s].
2007-06-01 23:59:45.808 Using screen 0, 1280x1024 at 0,0
2007-06-01 23:59:45.812 Current Schema Version: 1114
2007-06-01 23:59:45.812 Newest Schema Version : 1160
2007-06-01 23:59:45.813 New DB connection, total: 2
2007-06-01 23:59:45.813 Connected to database 'mythconverg' at host: localhost
2007-06-01 23:59:45.814 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-06-01 23:59:45.814 New DB connection, total: 3
2007-06-01 23:59:45.814 Connected to database 'mythconverg' at host: localhost
2007-06-01 23:59:45.815 Upgrading to schema version 1115
2007-06-01 23:59:45.815 DB Error (Performing database upgrade): 
Query was: ALTER TABLE tvchain ADD COLUMN endtime DATETIME NOT NULL default '0000-00-00 00:00:00'; 
Error was: Driver error was [2/1060]:
QMYSQL3: Unable to execute query
Database error was:
Duplicate column name 'endtime'
 
new version: 1115
2007-06-01 23:59:45.815 Database Schema upgrade FAILED, unlocking.
2007-06-01 23:59:45.815 Couldn't upgrade database to new schema, exiting.
blake@Ubuntu-Desktop:~$ 
[/PHP]

---

### Post by tgm4883 on 2007-06-02
Well at least we are getting somewhere.  Let me do some searching.

---

### Post by jba6511 on 2007-06-02
thanks. I appreciate the time you are taking to help me with this

---

### Post by jba6511 on 2007-06-02
well fixed the first part of the errors myself. Now I need to get the rest working. Here is the error log now:

[PHP]2007-06-02 01:22:47.988 Using runtime prefix = /usr
2007-06-02 01:22:48.000 Gnome-Screensaver support enabled
2007-06-02 01:22:48.000 DPMS is active.
2007-06-02 01:22:48.037 New DB connection, total: 1
2007-06-02 01:22:48.040 Connected to database 'mythconverg' at host: localhost
2007-06-02 01:22:48.040 Total desktop dim: 1280x1024, with 1 screen[s].
2007-06-02 01:22:48.042 Using screen 0, 1280x1024 at 0,0
2007-06-02 01:22:48.068 Current Schema Version: 1114
2007-06-02 01:22:48.069 Newest Schema Version : 1160
2007-06-02 01:22:48.069 New DB connection, total: 2
2007-06-02 01:22:48.069 Connected to database 'mythconverg' at host: localhost
2007-06-02 01:22:48.069 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2007-06-02 01:22:48.070 New DB connection, total: 3
2007-06-02 01:22:48.070 Connected to database 'mythconverg' at host: localhost
2007-06-02 01:22:48.071 Upgrading to schema version 1115
2007-06-02 01:22:48.071 DB Error (Performing database upgrade): 
Query was: ALTER TABLE tvchain ADD COLUMN endtime DATETIME NOT NULL default '0000-00-00 00:00:00'; 
Error was: Driver error was [2/1060]:
QMYSQL3: Unable to execute query
Database error was:
Duplicate column name 'endtime'
 
new version: 1115
2007-06-02 01:22:48.071 Database Schema upgrade FAILED, unlocking.
2007-06-02 01:22:48.071 Couldn't upgrade database to new schema, exiting.
blake@Ubuntu-Desktop:~$ 
[/PHP]

---

### Post by jba6511 on 2007-06-02
I tried reparing mythtv database following this thread here: 
[http://ubuntuforums.org/showthread.php?t=413944&page=2](http://ubuntuforums.org/showthread.php?t=413944&page=2)

however, once I enter mysqlcheck -r mythconverg -umthtv -pmythtv

I got an access denied error about mythtv and local host. I checked and I am a memeber of the group and followed instructions to add myself and reset the password but neither worked. Any ideas? I am thinking if I could repair the database then I should be set.


NEVERMIND -got the repair command to work but still having troubles. Here is the latest log. Notice the duplicate entry at the bottom
blake@Ubuntu-Desktop:~$ ps -p `cat /var/run/mythtv/mythbackend.pid`
  PID TTY          TIME CMD
blake@Ubuntu-Desktop:~$ more /var/log/mythtv/mythbackend.log
2007-06-02 02:13:31.656 Using runtime prefix = /usr
2007-06-02 02:13:31.671 New DB connection, total: 1
2007-06-02 02:13:31.675 Connected to database 'mythconverg' at host: localhost
2007-06-02 02:13:31.678 Current Schema Version: 1114
2007-06-02 02:13:31.678 Newest Schema Version : 1160
2007-06-02 02:13:31.680 New DB connection, total: 2
2007-06-02 02:13:31.680 Connected to database 'mythconverg' at host: localhost
2007-06-02 02:13:31.681 Setting Lock for Database Schema upgrade. If you see a l
ong pause here it means the Schema is already locked and is being upgraded by an
other Myth process.
2007-06-02 02:13:31.682 New DB connection, total: 3
2007-06-02 02:13:31.682 Connected to database 'mythconverg' at host: localhost
2007-06-02 02:13:31.683 Upgrading to schema version 1115
2007-06-02 02:13:31.684 DB Error (Performing database upgrade): 
Query was: ALTER TABLE tvchain ADD COLUMN endtime DATETIME NOT NULL default '000
0-00-00 00:00:00'; 
Error was: Driver error was [2/1060]:
QMYSQL3: Unable to execute query
Database error was:
Duplicate column name 'endtime'
 
new version: 1115
2007-06-02 02:13:31.684 Database Schema upgrade FAILED, unlocking.
2007-06-02 02:13:31.685 Couldn't upgrade database to new schema

---

### Post by jba6511 on 2007-06-02
any ideas how to correct this?

---

### Post by jba6511 on 2007-06-03
still unresolved and so close...

---

### Post by rhpot1991 on 2007-06-03
Looks like the DB user that you entered doesn't have the proper access to the mythconverge database.  I think it needs grant permissions on the DB.  I will double check this when I get my main mythbox put back together, its in pieces testing for bad hardware in another machine currently.

---

### Post by jba6511 on 2007-06-03
thanks, please let me know if this is the case and how I can correct it.

---

### Post by superm1 on 2007-06-03
> **jba6511 said:**
> thanks, please let me know if this is the case and how I can correct it.

Okay - so given that error, you can either manually go into the table and delete the duplicate column, or drop the database and put it back in.  


I would say dropping the database is the better bet, because if there is one column corrupted, there are likely more.

By far the easiest way to drop and add the database is this:

```
sudo apt-get remove --purge mysql-server-5.0 mythtv-database
sudo apt-get install mysql-server-5.0 mythtv-database
```

It will ask you after the first command if its okay to drop.  You hit yet and do the second.

If you have valuable data that you need, it can be backed up as well.  Your call.

---

### Post by jba6511 on 2007-06-03
thanks that worked and now I can run mythtv. any way to watch mythtv in a window and not in fullscreen view? Again, thanks for everyone's help.

---

### Post by superm1 on 2007-06-03
> **jba6511 said:**
> thanks that worked and now I can run mythtv. any way to watch mythtv in a window and not in fullscreen view? Again, thanks for everyone's help.
Go into settings appearance.  Change the resolution to the size of the window you want.  Choose to run the frontend in a window.

As for AV being out of sync - did you select video as a timebase in the frontend settings?  (If so turn this off).  Are you watching hidef stuff or not?

---

### Post by jba6511 on 2007-06-03
i fixed the sync problem As far as the resolution of the window, can someone explicitly tell me the option names and what they set them to? I tried this before and ended up messing up myth so I am hesistant to do it again. How about a screenshot of this to clarify for me please?

---

### Post by superm1 on 2007-06-03
I circled the 3 things to change
The first is your width (like 800 or 1024 typically)
The second is your height (like 600 or 768 typically)

The third is that checkbox at the bottom to run in a window.

---

### Post by jba6511 on 2007-06-03
thanks - could not be any clearer.

---

