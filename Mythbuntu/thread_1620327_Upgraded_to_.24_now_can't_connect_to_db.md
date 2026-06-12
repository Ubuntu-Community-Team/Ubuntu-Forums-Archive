---
title: "Upgraded to .24 now can't connect to db"
date: 2010-11-12
forum: Mythbuntu
---

### Post by jayman8547 on 2010-11-12
As the title says, cant't remote connect to db, or on the backend for that matter.

Setup:
4 Individual machines - Backend, 3 Front ends.  Started upgrade on one of the front ends first (not thinking) then went to backend.  Upgraded by enabling auto-builds then using ppa? repo then system update.  Backend failed to update the first time.  Asked me if I wanted to do a partial upgrade and I said yes.  System just froze at calculating disk space.  After a half hour or so I killed the update and did a command line update && upgrade.  Updated some of the packages but not all.  Rebooted system and did a synaptic upgrade and all seemed good.  Still could not connect from a frontend.  Did command line update && upgrade again and it told me it couldn't upgrade 4 packages.  After a few reboots and backend restarts I did another update && upgrade and this time it did a full upgrade like it had not done one previously...

Anyways, now when I go into mcc on any machine and test connection it fails.  Security code is set to 0000 on all machines, ip's are correct, etc.  System was running and stable for 2+ years before tonight upgrading to .24.  All front ends updated seamlessly.  Also I can log into mysql db manually.

Please Help!!!

---

### Post by tgm4883 on 2010-11-12
Is the backend started? Post your backend logs.

---

### Post by jayman8547 on 2010-11-12
Pretty sure backend is running

The log file is filled with

2010-11-12 10:07:56.283 MainServer::ANN Monitor
2010-11-12 10:07:56.313 adding: tzcheck as a client (events: 0)

and mythcommflag is taking the system to 80-90%

Never posted a log before, easiest way?

---

### Post by tgm4883 on 2010-11-12
```
pastebinit /var/log/mythtv/mythbackend.log
```

Then post the URL here

---

### Post by jayman8547 on 2010-11-12
Get an error


> # pastebinit /var/log/mythtv/mythbackend.log
Traceback (most recent call last):
  File "/usr/bin/pastebinit", line 279, in <module>
    page = url_opener.open(website, params) #Send the informations and be redirected to the final page
  File "/usr/lib/python2.6/urllib.py", line 209, in open
    return getattr(self, name)(url, data)
  File "/usr/lib/python2.6/urllib.py", line 348, in open_http
    h.send(data)
  File "/usr/lib/python2.6/httplib.py", line 759, in send
    self.sock.sendall(str)
  File "<string>", line 1, in sendall
IOError: [Errno socket error] [Errno 104] Connection reset by peer

---

### Post by tgm4883 on 2010-11-13
Hmm, Thats no deal. You could try using Mythbuntu-log-grabber which is part of MCC. If that doesn't work I would just attach your log in a post here.

---

### Post by jayman8547 on 2010-11-13
Tried posting mythbackend.log but it is huge.  There are 6 files all 15mb plus the current one at 3mb.  That;s why pastebinit probably didn't work.  

Now log is filled with

```
2010-11-13 00:24:32.378 [mpeg2video @ 0x7f6f07ba95c0]ac-tex damaged at 105 67
2010-11-13 00:24:43.062 [mpeg2video @ 0x7f6f07ba95c0]00 motion_type at 119 67
2010-11-13 00:24:55.136 [mpeg2video @ 0x7f6f07ba95c0]00 motion_type at 98 67
2010-11-13 00:25:05.249 [mpeg2video @ 0x7f6f07ba95c0]end mismatch left=50 4DCCF2
2010-11-13 00:25:05.918 [mpeg2video @ 0x7f6f07ba95c0]ac-tex damaged at 61 67
2010-11-13 00:25:08.181 [mpeg2video @ 0x7f6f07ba95c0]ac-tex damaged at 106 67
2010-11-13 00:25:25.795 [mpeg2video @ 0x7f6f07ba95c0]end mismatch left=42 3249A4
2010-11-13 00:25:33.529 [mpeg2video @ 0x7f6f07ba95c0]end mismatch left=189 521D30
2010-11-13 00:25:38.226 [mpeg2video @ 0x7f6f07ba95c0]ac-tex damaged at 87 67
2010-11-13 00:25:55.230 [mpeg2video @ 0x7f6f07ba95c0]slice mismatch
2010-11-13 00:25:56.374 [mpeg2video @ 0x7f6f07ba95c0]end mismatch left=122 3A1A7A
2010-11-13 00:25:57.854 [mpeg2video @ 0x7f6f07ba95c0]slice mismatch
2010-11-13 00:26:06.840 [mpeg2video @ 0x7f6f07ba95c0]ac-tex damaged at 90 67
2010-11-13 00:26:07.027 [mpeg2video @ 0x7f6f07ba95c0]invalid mb type in B Frame at 109 67
2010-11-13 00:26:11.274 [mpeg2video @ 0x7f6f07ba95c0]00 motion_type at 94 67
```

I have an hd homerun and hd pvr on the system.

---

### Post by jayman8547 on 2010-11-13
solved the performance issues and log files filling up.  There was a mythcommflag job running that was spiking all the resources. 

Still can't connect to the db remotely though through mcc.

---

### Post by jayman8547 on 2010-11-13
remote login try to my sql database returns 

```
ERROR 1044 (42000): Access denied for user 'mythtv'@'%' to database 'mythconverg                                         e'

```

---

### Post by jayman8547 on 2010-11-13
Turning in for the night.

running 

mysql -u mythtv -p mythconverg

on the backend I can log in to the db fine.  

Running 

mysql -h 192.168.1.150 -D mythconverge -u mythtv -p

remotely I get the access denied error.

I changed permissions on the db for all users to get access and still nothing.

I need to get this back up ASAP!  Any help would be appreciated!!

---

### Post by uncle hammy on 2010-11-13
> **jayman8547 said:**
> remote login try to my sql database returns 

```
ERROR 1044 (42000): Access denied for user 'mythtv'@'%' to database 'mythconverg                                         e'

```
```

mysql -uroot -pMYUSERPASS
GRANT ALL ON mythconverg.* to 'mythtv'@'%' identified by 'MY MYTHTV PASS AS DEFINED IN GENERAL SETTINGS';
FLUSH PRIVILEGES;

```

---

### Post by tgm4883 on 2010-11-13
> **uncle hammy said:**
> ```

mysql -uroot -pMYUSERPASS
GRANT ALL ON mythconverg.* to 'mythtv'@'%' identified by 'MY MYTHTV PASS AS DEFINED IN GENERAL SETTINGS';
FLUSH PRIVILEGES;

```

Also check that the mythtv service is set to enabled in mythbuntu control centre

---

### Post by jayman8547 on 2010-11-13
> **uncle hammy said:**
> ```

mysql -uroot -pMYUSERPASS
GRANT ALL ON mythconverg.* to 'mythtv'@'%' identified by 'MY MYTHTV PASS AS DEFINED IN GENERAL SETTINGS';
FLUSH PRIVILEGES;

```

when I type mysql -uroot -p I assume root is the root user?  I get 

```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
```

even when I try for mythtv user as well as my username.  I am using the password in mysql.txt correct?

Mysql is enabled in the backend mcc

Seems I changed the permissions on the db...

---

### Post by uncle hammy on 2010-11-13
> **jayman8547 said:**
> I am using the password in mysql.txt correct?
No, read my post again.  You are using your password for your user that you set when you installed Mythbuntu.

```
mysql -uroot -pMY USER'S PASSWORD!
```

You are using the mysql.txt password when you set the privileges for mythtv.

```
GRANT ALL ON mythconverg.* to 'mythtv'@'%' IDENTIFIED BY 'MYSQL.TXT PASSWORD';
```

---

### Post by nickrout on 2010-11-13
```
sudo dpkg-reconfigure mythtv-common   
                                                                         
sudo dpkg-reconfigure mythtv-database
```

---

### Post by jayman8547 on 2010-11-13
uncle hammy - did that, tried testing mysql setting in mcc, no mas.

Then did Nickrout's and rebooted, rechecked in mcc, still no mas.

I did find I had a secondary backend running on one of my frontends.  I had to create a secondary backend because otherwise mythbuntu does not create mythfrontend.log.  I just clean installed that particular frontend last week so I had a secondary backend running since then and during the upgrade.

When I start the frontends I tail the log files and it seems they are connecting to the db?

```
Starting mythfrontend.real..
2010-11-13 21:21:58.241 mythfrontend version: branches/release-0-24-fixes [27174] www.mythtv.org
2010-11-13 21:21:58.241 Using runtime prefix = /usr
2010-11-13 21:21:58.242 Using configuration directory = /home/jayman8547/.mythtv
2010-11-13 21:21:58.244 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2010-11-13 21:21:58.703 Empty LocalHostName.
2010-11-13 21:21:58.703 Using localhost value of mustafaar
2010-11-13 21:21:58.704 Testing network connectivity to '192.168.1.150'
2010-11-13 21:21:58.843 New DB connection, total: 1
2010-11-13 21:21:58.846 Connected to database 'mythconverg' at host: 192.168.1.150
2010-11-13 21:21:58.867 Closing DB connection named 'DBManager0'
2010-11-13 21:21:58.869 Connected to database 'mythconverg' at host: 192.168.1.150
2010-11-13 21:21:58.874 Current locale EN_US
2010-11-13 21:21:58.875 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2010-11-13 21:21:59.109 ScreenSaverX11Private: XScreenSaver support enabled
2010-11-13 21:21:59.112 DPMS is disabled.
2010-11-13 21:21:59.151 Desktop video mode: 1920x1080 60.000 Hz
2010-11-13 21:21:59.223 Enabled verbose msgs:  important general
2010-11-13 21:21:59.233 Loading en_us translation for module mythfrontend
2010-11-13 21:21:59.263 LIRC: Successfully initialized '/dev/lircd' using '/home/jayman8547/.mythtv/lircrc' config
2010-11-13 21:21:59.263 JoystickMenuThread: Joystick disabled - Failed to read /home/jayman8547/.mythtv/joystickmenurc
2010-11-13 21:21:59.372 Using Frameless Window
2010-11-13 21:21:59.372 Using Full Screen Window
2010-11-13 21:22:00.141 Using the OpenGL painter
2010-11-13 21:22:00.272 OpenGL: OpenGL vendor  : NVIDIA Corporation
2010-11-13 21:22:00.273 OpenGL: OpenGL renderer: ION/PCI/SSE2
2010-11-13 21:22:00.273 OpenGL: OpenGL version : 3.3.0 NVIDIA 260.19.06
2010-11-13 21:22:00.273 OpenGL: Max texture size: 8192 x 8192
2010-11-13 21:22:00.273 OpenGL: Max texture units: 4
2010-11-13 21:22:00.273 OpenGL: Direct rendering: Yes
2010-11-13 21:22:00.273 OpenGL: Initialised MythRenderOpenGL
2010-11-13 21:22:00.619 Current MythTV Schema Version (DBSchemaVer): 1264
2010-11-13 21:22:02.309 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2010-11-13 21:22:02.309 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2010-11-13 21:22:02.313 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2010-11-13 21:22:02.313 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2010-11-13 21:22:02.964 Registering Internal as a media playback plugin.
2010-11-13 21:22:03.039 Loading en_us translation for module mytharchive
2010-11-13 21:22:03.054 Registering WebBrowser as a media playback plugin.
2010-11-13 21:22:03.055 Loading en_us translation for module mythbrowser
2010-11-13 21:22:03.133 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-11-13 21:22:03.134 Loading en_us translation for module mythgallery
2010-11-13 21:22:03.160 Loading en_us translation for module mythgame
2010-11-13 21:22:03.216 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-11-13 21:22:03.336 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-11-13 21:22:03.355 Loading en_us translation for module mythmusic
2010-11-13 21:22:03.366 Loading en_us translation for module mythnetvision
2010-11-13 21:22:03.381 Loading en_us translation for module mythnews
2010-11-13 21:22:03.404 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-11-13 21:22:03.404 MythVideo database schema is old. Waiting to see if DB is being upgraded.
2010-11-13 21:22:04.405 New DB connection, total: 2
2010-11-13 21:22:04.407 Connected to database 'mythconverg' at host: 192.168.1.150
2010-11-13 21:22:04.416 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-11-13 21:22:05.424 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-11-13 21:22:06.431 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-11-13 21:22:06.432 Timed out waiting.
2010-11-13 21:22:06.459 SG(DB Backups) Error: FindNextDirMostFree: '/multimedia/Myth/db_backups' does not exist!
2010-11-13 21:22:06.465 Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
2010-11-13 21:23:06.584 Database Backup complete.
2010-11-13 21:23:06.585 Backed up database to file: '/tmp/mythconverg-1264-20101113212206.sql.gz'
ICE default IO error handler doing an exit(), pid = 1931, errno = 32

```

---

### Post by jayman8547 on 2010-11-13
PS - Also ran 

```
mysqlcheck -u root -p --repair mythconverg
```

and found no errors

I used nmap to check open ports both locally and remotely and 3306 is open on both.

I can get in to the backend setup fine as well and finds all the settings which means it's connecting to the db - right?  It's just when I go into mcc -> mysql and test security I get a big fat X.  All codes are set to 0000

---

### Post by nickrout on 2010-11-14
> **jayman8547 said:**
> PS - Also ran 

```
mysqlcheck -u root -p --repair mythconverg
```

and found no errors

I used nmap to check open ports both locally and remotely and 3306 is open on both.

I can get in to the backend setup fine as well and finds all the settings which means it's connecting to the db - right?  It's just when I go into mcc -> mysql and test security I get a big fat X.  All codes are set to 0000

the log in your previous post seems to show a connection - so is the frontend working?

---

### Post by jayman8547 on 2010-11-14
Frontends seem to connect but hang at a blank screen.  Happens on 2 that I tried it on.  The logs in both are pretty much verbatim - that it seems to find the db and login, exits the db, logs in again then can't make some database backup directory then eventually exits.

I needed my system back up so last night I just rebuilt one from the ground up.  I lost my recordings but after 16 plus hours invested in troubleshooting the past 2 days I had to do something...

---

### Post by nickrout on 2010-11-14
> **jayman8547 said:**
> Frontends seem to connect but hang at a blank screen.  Happens on 2 that I tried it on.  The logs in both are pretty much verbatim - that it seems to find the db and login, exits the db, logs in again then can't make some database backup directory then eventually exits.

I needed my system back up so last night I just rebuilt one from the ground up.  I lost my recordings but after 16 plus hours invested in troubleshooting the past 2 days I had to do something...

how did you lose your recordings?

---

### Post by jayman8547 on 2010-11-14
Still have the recordings on hard drive, sorry.  Just lost the db link.  Which leads me to - Is there a way I can get the new db to see them as recordings again?  I was just going to copy them into my main video dump, rename and watch.

EDIT - just found the mythfind_orphans script but seems to be outdated.

---

### Post by nickrout on 2010-11-14
> **jayman8547 said:**
> Still have the recordings on hard drive, sorry.  Just lost the db link.  Which leads me to - Is there a way I can get the new db to see them as recordings again?  I was just going to copy them into my main video dump, rename and watch.

EDIT - just found the mythfind_orphans script but seems to be outdated.


Did you not backup the database?

[http://www.gossamer-threads.com/lists/mythtv/users/459359#459359](http://www.gossamer-threads.com/lists/mythtv/users/459359#459359)

---

