---
title: "backend server connection problem"
date: 2007-11-02
forum: Mythbuntu
---

### Post by barcesat on 2007-11-02
Hi,
i'm trying to put my tv listings through a XMLTV file. i have an external grabber which woks great (in wine).

when i try to fill the database using this command: 

```
mythbuntu@mythbuntu:~$ mythfilldatabase --file 1 -1 /home/mythbuntu/.wine/drive_c/Program\ Files/MegaEPG/xml/epgdata.xml
```

i get that error (at the end) that i can't connect to the backend server (which runs on the same computer - frontend-backend configuration).

```
mythbuntu@mythbuntu:~$ mythfilldatabase --file 1 -1 /home/mythbuntu/.wine/drive_c/Program\ Files/MegaEPG/xml/epgdata.xml
### bypassing grabbers, reading directly from file
2007-11-02 11:11:43.825 Using runtime prefix = /usr
2007-11-02 11:11:43.840 New DB connection, total: 1
2007-11-02 11:11:43.845 Connected to database 'mythconverg' at host: localhost
2007-11-02 11:11:44.373 New DB connection, total: 2
2007-11-02 11:11:44.373 Connected to database 'mythconverg' at host: localhost
2007-11-02 11:11:44.949 Updating icons for sourceid: 1
2007-11-02 11:11:44.951 New DB connection, total: 3
2007-11-02 11:11:44.952 Connected to database 'mythconverg' at host: localhost
removing existing program: isr2 &#1492;&#1502;&#1492;&#1508;&#1499;&#1504;&#1497;&#1501; 2007-11-02T00:40:00 - 2007-11-02T01:10:00
inserting new program    : isr2 &#1492;&#1502;&#1492;&#1508;&#1499;&#1504;&#1497;&#1501; ?' ??? 2 00:40:00 2007 - ?' ??? 2 01:10:00 2007

2007-11-02 11:11:49.827 New DB connection, total: 4
2007-11-02 11:11:49.828 Connected to database 'mythconverg' at host: localhost
removing existing program: ng &#1502;&#1510;&#1512;&#1497;&#1501;: &#1492;&#1502;&#1500;&#1498; &#1514;&#1493;&#1514; &#1502;&#1514;&#1490;&#1500;&#1492; (&#1512;&#1493;) 2007-11-02T01:00:00 - 2007-11-02T02:00:00
inserting new program    : ng &#1502;&#1510;&#1512;&#1497;&#1501;: &#1492;&#1502;&#1500;&#1498; &#1514;&#1493;&#1514; &#1502;&#1514;&#1490;&#1500;&#1492; (&#1512;&#1493;) ?' ??? 2 01:00:00 2007 - ?' ??? 2 02:00:00 2007

removing existing program: ng &#1502;&#1510;&#1512;&#1497;&#1501;: &#1492;&#1502;&#1500;&#1498; &#1514;&#1493;&#1514; &#1502;&#1514;&#1490;&#1500;&#1492; (&#1512;&#1493;) 2007-11-02T04:00:00 - 2007-11-02T05:00:00
inserting new program    : ng &#1502;&#1510;&#1512;&#1497;&#1501;: &#1492;&#1502;&#1500;&#1498; &#1514;&#1493;&#1514; &#1502;&#1514;&#1490;&#1500;&#1492; (&#1512;&#1493;) ?' ??? 2 04:00:00 2007 - ?' ??? 2 05:00:00 2007

removing existing program: ng &#1502;&#1500;&#1495;&#1502;&#1493;&#1514; &#1492;&#1490;&#1500;&#1491;&#1497;&#1488;&#1496;&#1493;&#1512;&#1497;&#1501; (&#1512;&#1493;) 2007-11-03T17:00:00 - 2007-11-03T18:00:00
inserting new program    : ng &#1502;&#1500;&#1495;&#1502;&#1493;&#1514; &#1492;&#1490;&#1500;&#1491;&#1497;&#1488;&#1496;&#1493;&#1512;&#1497;&#1501; (&#1512;&#1493;) ?' ??? 3 17:00:00 2007 - ?' ??? 3 18:00:00 2007

removing existing program: ng &#1514;&#1497;&#1488;&#1493;&#1512;&#1497;&#1514; &#1492;&#1511;&#1513;&#1512; - &#1514;&#1511;&#1512;&#1497;&#1514; &#1512;&#1493;&#1494;&#1493;&#1493;&#1500; 2007-11-03T22:00:00 - 2007-11-03T23:00:00
inserting new program    : ng &#1514;&#1497;&#1488;&#1493;&#1512;&#1497;&#1514; &#1492;&#1511;&#1513;&#1512; - &#1514;&#1511;&#1512;&#1497;&#1514; &#1512;&#1493;&#1494;&#1493;&#1493;&#1500; ?' ??? 3 22:00:00 2007 - ?' ??? 3 23:00:00 2007

Updated programs: 17  Unchanged programs: 3283
2007-11-02 11:11:54.248 Adjusting program database end times.
2007-11-02 11:11:54.302     0 replacements made
2007-11-02 11:11:54.302 Marking generic episodes.
2007-11-02 11:11:54.346     Found 0
2007-11-02 11:11:54.347 Marking repeats.
2007-11-02 11:11:54.370     Found 0
2007-11-02 11:11:54.370 Unmarking new episode rebroadcast repeats.
2007-11-02 11:11:54.413     Found 0
2007-11-02 11:11:54.498 Marking episode first showings.
2007-11-02 11:11:56.433     Found 2042
2007-11-02 11:11:56.433 Marking episode last showings.
2007-11-02 11:11:58.382     Found 2042
2007-11-02 11:11:58.397 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2007-11-02 11:11:58.404 Connecting to backend server: localhost:6543 (try 1 of 5)
2007-11-02 11:11:58.404 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2007-11-02 11:11:58.404 Error rescheduling id -1 in ScheduledRecording::signalChange
2007-11-02 11:11:58.405 Connecting to backend server: localhost:6543 (try 1 of 5)
2007-11-02 11:11:58.405 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2007-11-02 11:11:58.406 mythfilldatabase run complete.
2007-11-02 11:11:58.431 DataDirect: Deleting temporary files

```

i also get error messages from within the frontend that it can't connect to the backend server.
how can i fix it?

thanks in advance,
ziv

---

### Post by superm1 on 2007-11-02
> **barcesat said:**
> Hi,
i'm trying to put my tv listings through a XMLTV file. i have an external grabber which woks great (in wine).

when i try to fill the database using this command: 

```
mythbuntu@mythbuntu:~$ mythfilldatabase --file 1 -1 /home/mythbuntu/.wine/drive_c/Program\ Files/MegaEPG/xml/epgdata.xml
```i get that error (at the end) that i can't connect to the backend server (which runs on the same computer - frontend-backend configuration).

```
mythbuntu@mythbuntu:~$ mythfilldatabase --file 1 -1 /home/mythbuntu/.wine/drive_c/Program\ Files/MegaEPG/xml/epgdata.xml
### bypassing grabbers, reading directly from file
2007-11-02 11:11:43.825 Using runtime prefix = /usr
2007-11-02 11:11:43.840 New DB connection, total: 1
2007-11-02 11:11:43.845 Connected to database 'mythconverg' at host: localhost
2007-11-02 11:11:44.373 New DB connection, total: 2
2007-11-02 11:11:44.373 Connected to database 'mythconverg' at host: localhost
2007-11-02 11:11:44.949 Updating icons for sourceid: 1
2007-11-02 11:11:44.951 New DB connection, total: 3
2007-11-02 11:11:44.952 Connected to database 'mythconverg' at host: localhost
removing existing program: isr2 &#1492;&#1502;&#1492;&#1508;&#1499;&#1504;&#1497;&#1501; 2007-11-02T00:40:00 - 2007-11-02T01:10:00
inserting new program    : isr2 &#1492;&#1502;&#1492;&#1508;&#1499;&#1504;&#1497;&#1501; ?' ??? 2 00:40:00 2007 - ?' ??? 2 01:10:00 2007

2007-11-02 11:11:49.827 New DB connection, total: 4
2007-11-02 11:11:49.828 Connected to database 'mythconverg' at host: localhost
removing existing program: ng &#1502;&#1510;&#1512;&#1497;&#1501;: &#1492;&#1502;&#1500;&#1498; &#1514;&#1493;&#1514; &#1502;&#1514;&#1490;&#1500;&#1492; (&#1512;&#1493;) 2007-11-02T01:00:00 - 2007-11-02T02:00:00
inserting new program    : ng &#1502;&#1510;&#1512;&#1497;&#1501;: &#1492;&#1502;&#1500;&#1498; &#1514;&#1493;&#1514; &#1502;&#1514;&#1490;&#1500;&#1492; (&#1512;&#1493;) ?' ??? 2 01:00:00 2007 - ?' ??? 2 02:00:00 2007

removing existing program: ng &#1502;&#1510;&#1512;&#1497;&#1501;: &#1492;&#1502;&#1500;&#1498; &#1514;&#1493;&#1514; &#1502;&#1514;&#1490;&#1500;&#1492; (&#1512;&#1493;) 2007-11-02T04:00:00 - 2007-11-02T05:00:00
inserting new program    : ng &#1502;&#1510;&#1512;&#1497;&#1501;: &#1492;&#1502;&#1500;&#1498; &#1514;&#1493;&#1514; &#1502;&#1514;&#1490;&#1500;&#1492; (&#1512;&#1493;) ?' ??? 2 04:00:00 2007 - ?' ??? 2 05:00:00 2007

removing existing program: ng &#1502;&#1500;&#1495;&#1502;&#1493;&#1514; &#1492;&#1490;&#1500;&#1491;&#1497;&#1488;&#1496;&#1493;&#1512;&#1497;&#1501; (&#1512;&#1493;) 2007-11-03T17:00:00 - 2007-11-03T18:00:00
inserting new program    : ng &#1502;&#1500;&#1495;&#1502;&#1493;&#1514; &#1492;&#1490;&#1500;&#1491;&#1497;&#1488;&#1496;&#1493;&#1512;&#1497;&#1501; (&#1512;&#1493;) ?' ??? 3 17:00:00 2007 - ?' ??? 3 18:00:00 2007

removing existing program: ng &#1514;&#1497;&#1488;&#1493;&#1512;&#1497;&#1514; &#1492;&#1511;&#1513;&#1512; - &#1514;&#1511;&#1512;&#1497;&#1514; &#1512;&#1493;&#1494;&#1493;&#1493;&#1500; 2007-11-03T22:00:00 - 2007-11-03T23:00:00
inserting new program    : ng &#1514;&#1497;&#1488;&#1493;&#1512;&#1497;&#1514; &#1492;&#1511;&#1513;&#1512; - &#1514;&#1511;&#1512;&#1497;&#1514; &#1512;&#1493;&#1494;&#1493;&#1493;&#1500; ?' ??? 3 22:00:00 2007 - ?' ??? 3 23:00:00 2007

Updated programs: 17  Unchanged programs: 3283
2007-11-02 11:11:54.248 Adjusting program database end times.
2007-11-02 11:11:54.302     0 replacements made
2007-11-02 11:11:54.302 Marking generic episodes.
2007-11-02 11:11:54.346     Found 0
2007-11-02 11:11:54.347 Marking repeats.
2007-11-02 11:11:54.370     Found 0
2007-11-02 11:11:54.370 Unmarking new episode rebroadcast repeats.
2007-11-02 11:11:54.413     Found 0
2007-11-02 11:11:54.498 Marking episode first showings.
2007-11-02 11:11:56.433     Found 2042
2007-11-02 11:11:56.433 Marking episode last showings.
2007-11-02 11:11:58.382     Found 2042
2007-11-02 11:11:58.397 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2007-11-02 11:11:58.404 Connecting to backend server: localhost:6543 (try 1 of 5)
2007-11-02 11:11:58.404 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2007-11-02 11:11:58.404 Error rescheduling id -1 in ScheduledRecording::signalChange
2007-11-02 11:11:58.405 Connecting to backend server: localhost:6543 (try 1 of 5)
2007-11-02 11:11:58.405 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2007-11-02 11:11:58.406 mythfilldatabase run complete.
2007-11-02 11:11:58.431 DataDirect: Deleting temporary files

```i also get error messages from within the frontend that it can't connect to the backend server.
how can i fix it?

thanks in advance,
ziv
Please see /var/log/mythtv/mythbackend.log

---

### Post by barcesat on 2007-11-02
```
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-02 14:08:06.377 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-02 14:08:06.471 Failed to init MythContext, exiting.
2007-11-02 14:11:40.020 Using runtime prefix = /usr
2007-11-02 14:11:40.082 New DB connection, total: 1
2007-11-02 14:11:40.089 Unable to connect to database!
2007-11-02 14:11:40.090 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)
```

i see "access denied", i see "driver error" & Database not open"

what is the problem actually?

---

### Post by superm1 on 2007-11-02
> **barcesat said:**
> ```
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-02 14:08:06.377 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-02 14:08:06.471 Failed to init MythContext, exiting.
2007-11-02 14:11:40.020 Using runtime prefix = /usr
2007-11-02 14:11:40.082 New DB connection, total: 1
2007-11-02 14:11:40.089 Unable to connect to database!
2007-11-02 14:11:40.090 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)
```i see "access denied", i see "driver error" & Database not open"

what is the problem actually?
First
```
rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf
```

When you installed, did you set a root mysql password?  If so, you need to
```
sudo dpkg-reconfigure mythtv-database
sudo dpkg-reconfigure mythtv-common
```

Did you change your mysql mythtv password? If so you need to
```
sudo dpkg-reconfigure mythtv-common
```

---

### Post by barcesat on 2007-11-02
OK i did it... and restarted the backend from the terminal. but i see that there are still some problems there

```

mythbuntu@mythbuntu:~$ mythbackend
2007-11-02 17:14:55.522 Using runtime prefix = /usr
2007-11-02 17:14:55.540 New DB connection, total: 1
2007-11-02 17:14:55.545 Connected to database 'mythconverg' at host: localhost
2007-11-02 17:14:55.574 Current Schema Version: 1160
Starting up as the master server.
2007-11-02 17:14:55.585 New DB connection, total: 2
2007-11-02 17:14:55.586 Connected to database 'mythconverg' at host: localhost
2007-11-02 17:14:55.630 EITHelper: localtime offset 2:00:00 
2007-11-02 17:14:55.663 TVRec(1) Error: Start channel from DB is empty, setting to '' instead.
2007-11-02 17:14:55.664 TVRec(1) Error: Start channel invalid, setting to '' on input Composite 1 instead.
2007-11-02 17:14:55.664 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2007-11-02 17:14:55.666 New DB connection, total: 3
2007-11-02 17:14:55.693 Connected to database 'mythconverg' at host: localhost
2007-11-02 17:14:55.938 Channel(/dev/video0): SetChannelByString(3), Error: CheckChannel failed.
                        Please verify the channel in the 'mythtv-setup' Channel Editor.
2007-11-02 17:14:55.938 TVRec(1) Error: Setting start channel '3' failed, 
                        and no other channels were found on input.
2007-11-02 17:14:55.989 New DB scheduler connection
2007-11-02 17:14:55.989 Connected to database 'mythconverg' at host: localhost
2007-11-02 17:14:57.406 Main::Registering HttpStatus Extension
2007-11-02 17:14:57.406 mythbackend version: 0.20.20070821-1 www.mythtv.org
2007-11-02 17:14:57.406 Enabled verbose msgs:  important general
/var/lib/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/var/lib/mythtv/recordings' exists and that both 
the directory and that file are writeable by this user.

```

---

### Post by superm1 on 2007-11-02
> **barcesat said:**
> OK i did it... and restarted the backend from the terminal. but i see that there are still some problems there

```

mythbuntu@mythbuntu:~$ mythbackend
2007-11-02 17:14:55.522 Using runtime prefix = /usr
2007-11-02 17:14:55.540 New DB connection, total: 1
2007-11-02 17:14:55.545 Connected to database 'mythconverg' at host: localhost
2007-11-02 17:14:55.574 Current Schema Version: 1160
Starting up as the master server.
2007-11-02 17:14:55.585 New DB connection, total: 2
2007-11-02 17:14:55.586 Connected to database 'mythconverg' at host: localhost
2007-11-02 17:14:55.630 EITHelper: localtime offset 2:00:00 
2007-11-02 17:14:55.663 TVRec(1) Error: Start channel from DB is empty, setting to '' instead.
2007-11-02 17:14:55.664 TVRec(1) Error: Start channel invalid, setting to '' on input Composite 1 instead.
2007-11-02 17:14:55.664 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2007-11-02 17:14:55.666 New DB connection, total: 3
2007-11-02 17:14:55.693 Connected to database 'mythconverg' at host: localhost
2007-11-02 17:14:55.938 Channel(/dev/video0): SetChannelByString(3), Error: CheckChannel failed.
                        Please verify the channel in the 'mythtv-setup' Channel Editor.
2007-11-02 17:14:55.938 TVRec(1) Error: Setting start channel '3' failed, 
                        and no other channels were found on input.
2007-11-02 17:14:55.989 New DB scheduler connection
2007-11-02 17:14:55.989 Connected to database 'mythconverg' at host: localhost
2007-11-02 17:14:57.406 Main::Registering HttpStatus Extension
2007-11-02 17:14:57.406 mythbackend version: 0.20.20070821-1 www.mythtv.org
2007-11-02 17:14:57.406 Enabled verbose msgs:  important general
/var/lib/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/var/lib/mythtv/recordings' exists and that both 
the directory and that file are writeable by this user.

```

File exactly what it says.  Adjust the permissions for /var/lib/mythtv/recordings so that mythtv:mythtv can read and write to it.

```
sudo chown mythtv:mythtv /var/lib/mythtv/recordings -R
```

---

### Post by barcesat on 2007-11-03
still the exact same message... :\

---

### Post by superm1 on 2007-11-03
> **barcesat said:**
> still the exact same message... :\
Well did you restart the backend service afterard?

```
sudo /etc/init.d/mythtv-backend restart
```


Also, what is the output of this

```
ls -lah /var/lib/mythtv/recordings
```

---

### Post by Chewiesw on 2008-01-31
Hi 
I am experiencing a similar problem with the 

mythfilldatabase --file 1 -1 /home/mythbuntu/.... command. Everything seem to work but there is no program data, when using live tv or the program guide. Everything  did work until I had a power failure and since then I have been able to succesfully update.

Cheers

---

