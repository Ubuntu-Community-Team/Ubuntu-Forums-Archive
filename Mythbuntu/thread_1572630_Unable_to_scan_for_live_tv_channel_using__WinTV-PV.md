---
title: "Unable to scan for live tv channel using  WinTV-PVR-150"
date: 2010-09-11
forum: Mythbuntu
---

### Post by okorkie on 2010-09-11
AS the title indicates, I am unable to scan or receive live TV when configuring MythTV.

In the 'Input connections' section, I have 5 entries:

V4L: /dev/video0 (Tuner 1) >
V4L: /dev/video0 (S-Video 1) > None
V4L: /dev/video0 (Composite 1) > None
V4L: /dev/video0 (S-Video 2) > None
V4L: /dev/video0 (Composite 2) > None

When I select Tuner 1 (I assume this is the correct input - I am using the RF or COAX port on my WinTV-PVR-150 MCE), it says:

Capture device: [V4L:/dev/video0]
Input: Tuner 1

Then if I try to 'Scan for Channels', it comes back with 'Failed to find any channels'.  I am using my Comcast analog feed and is set to us-cable.

Any suggestion is greatly appreciated.

Thanks

---

### Post by klc5555 on 2010-09-11
> **okorkie said:**
> AS the title indicates, I am unable to scan or receive live TV when configuring MythTV.

In the 'Input connections' section, I have 5 entries:

V4L: /dev/video0 (Tuner 1) >
V4L: /dev/video0 (S-Video 1) > None
V4L: /dev/video0 (Composite 1) > None
V4L: /dev/video0 (S-Video 2) > None
V4L: /dev/video0 (Composite 2) > None

When I select Tuner 1 (I assume this is the correct input - I am using the RF or COAX port on my WinTV-PVR-150 MCE), it says:

Capture device: [V4L:/dev/video0]
Input: Tuner 1

Then if I try to 'Scan for Channels', it comes back with 'Failed to find any channels'.  I am using my Comcast analog feed and is set to us-cable.

Any suggestion is greatly appreciated.

Thanks

It's been a couple of years since I set one of the cards up, but you seem to have the pvr-150 set up as v4l-analog in the capture-card section of the backend setup. [V4L:/dev/video0] It is an MPEG2 hardware encoding device and should be set up that way. [MPEG:/dev/video0]

You still may not be able to scan for analog channels, as there are channel scanning bugs which are not due to be fixed until 0.24. But the 150 doesn't really need to scan to be able to find analog channels: it knows the frequencies required for particular analog channels. In a worst case scenario, once the Input Source has been set up and bound to the tuner in Input Connections, the channels can be added manually one-at-a-time in the Channel Editor. As long as the channel's  number is added to the two places in the form that require it ("Channel Number", and "Frequency or Channel"), mythtv should be able to tell the 150 to tune a specific channel, and the 150 should be able to find it. 

You might also want to add an appropriate name and callsign for each channel as you're adding it in the Editor ("WTTW", "KZOP" or whatever), and the xmltvid number of the channel if you're using Schedules Direct to get your channel schedules information. But these can always be added later from the onscreen menu while you're actually watching the channel in question in live tv.

Be sure to read the myth wiki entry on this card: [http://www.mythtv.org/wiki/Hauppauge_PVR-150](http://www.mythtv.org/wiki/Hauppauge_PVR-150)

---

### Post by axelsvag on 2010-09-12
Maybe I am totally wrong but I thought the search function for analogue card was broken since 0.22. I had to put the frequency manually to make it work.

---

### Post by grandpaken on 2010-09-13
> **okorkie said:**
> AS the title indicates, I am unable to scan or receive live TV when configuring MythTV.



Capture device: [V4L:/dev/video0]
Input: Tuner 1

Then if I try to 'Scan for Channels', it comes back with 'Failed to find any channels'.  I am using my Comcast analog feed and is set to us-cable.

Any suggestion is greatly appreciated.

Thanks

   My PVR-150 is setup as IVTV MPeg on Tuner 1 and scanning works in .23 fixes...at least it did 2 weeks ago when I rescanned my cable connection.

---

### Post by lank23 on 2010-09-13
won't work now that the channels are digital, unless you have it connected right out of the cable box on channel 3 / 4  .

---

### Post by grandpaken on 2010-09-13
> **lank23 said:**
> won't work now that the channels are digital, unless you have it connected right out of the cable box on channel 3 / 4  .

  That really depends on your cable company.  Most still have SD  channels when connected right to the 
cable as well as clear QAM.  Although I've heard of a few, there aren't many who are 100% digital other than FIOS type providers.  In some cases, like mine, only SD cable is available...no boxes,HD, pay for view, internet, phone or DVR's.

---

### Post by klc5555 on 2010-09-13
> **lank23 said:**
> won't work now that the channels are digital, unless you have it connected right out of the cable box on channel 3 / 4  .

Many places Comcast still broadcasts (at least) the VHF locals ch. 2-13 in analog. For the rest you're right, he'll need the STB or DTA on ch. 3/4, and scanning becomes moot.

---

### Post by lank23 on 2010-09-13
I have the same card with FIOS, and all of them are digital that I care to watch.

I think that all of the cable company's from big to small will have to broadcast in digital in the near future if the powers to be get there way.

---

### Post by okorkie on 2010-09-15
Hi,

I am using a Comcast feed which still have analog feeds.  The reason I know this is that my TV in the bedroom has a direct connection to the RF.

The Mythbuntu PC is on my main TV that has a Scientific Atlanta STB.  

I will try to a couple of things and see what I come up with. 

Thanks so far!

---

### Post by tgm4883 on 2010-09-15
Yea, looks like you have it set up as a V4L tuner instead of a Hardware encoder

---

### Post by okorkie on 2010-09-15
Under the Capture Card, then once I see the following:

Card type:
Video device:  /dev/video0
Probed info:  Hauppauge WinTV PVR-150
Default input: Tuner 1

You are correct, it was setup to Analog V4L capture card.. however my choices for the card type are:

-analog V4L capture card
- Mjpeg capture card (Matrox G200, DC10)
- IVTV MPEG-2 Encoder card
- H.264 encoder card (HD-PVR)
- DVB DTV capture card
- Fireware cable box
- USB MPEG-4 encoder box (Plextor ConvertX)
- HDHomeRun DTV tuner box
- Network Recorder
- Import Recorder

I'm not sure which to choose, but I did tryp IVTV MPEG-2 encoder card, but I couldn't get it to work and watch live TV.  Maybe I'm missing a step somewhere.

---

### Post by tgm4883 on 2010-09-15
> **okorkie said:**
> Under the Capture Card, then once I see the following:

Card type:
Video device:  /dev/video0
Probed info:  Hauppauge WinTV PVR-150
Default input: Tuner 1

You are correct, it was setup to Analog V4L capture card.. however my choices for the card type are:

-analog V4L capture card
- Mjpeg capture card (Matrox G200, DC10)
- IVTV MPEG-2 Encoder card
- H.264 encoder card (HD-PVR)
- DVB DTV capture card
- Fireware cable box
- USB MPEG-4 encoder box (Plextor ConvertX)
- HDHomeRun DTV tuner box
- Network Recorder
- Import Recorder

I'm not sure which to choose, but I did tryp IVTV MPEG-2 encoder card, but I couldn't get it to work and watch live TV.  Maybe I'm missing a step somewhere.

IVTV MPEG-2 Encoder card is correct. If you can't watch LiveTV after that you will need to post your backend logs from /var/log/mythtv/mythbackend.log

---

### Post by okorkie on 2010-09-16
Here is the log:

vgc-ra710g@vgc-ra710g-desktop:~$ cat /var/log/mythtv/myth
mythbackend.log   mythfrontend.log  mythwelcome.log   
vgc-ra710g@vgc-ra710g-desktop:~$ cat /var/log/mythtv/mythbackend.log
2010-09-15 18:55:31.473 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-09-15 18:55:31.596 Using runtime prefix = /usr
2010-09-15 18:55:31.735 Using configuration directory = /home/mythtv/.mythtv
2010-09-15 18:55:32.211 Empty LocalHostName.
2010-09-15 18:55:32.317 Using localhost value of vgc-ra710g-desktop
2010-09-15 18:55:33.282 New DB connection, total: 1
2010-09-15 18:55:33.572 Connected to database 'mythconverg' at host: localhost
2010-09-15 18:55:33.699 Closing DB connection named 'DBManager0'
2010-09-15 18:55:33.741 Connected to database 'mythconverg' at host: localhost
2010-09-15 18:55:34.187 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-15 18:55:34.637 MythBackend: Starting up as the master server.
2010-09-15 18:55:35.325 New DB connection, total: 2
2010-09-15 18:55:35.468 Connected to database 'mythconverg' at host: localhost
2010-09-15 18:55:36.243 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2010-09-15 18:55:36.469 ChannelBase(1) Error: InitializeInputs():
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2010-09-15 18:55:36.534 MythBackend, Error: No valid capture cards are defined in the database.
            Perhaps you should re-read the installation instructions?
2010-09-15 18:55:36.608 New DB connection, total: 3
2010-09-15 18:55:36.656 Connected to database 'mythconverg' at host: localhost
2010-09-15 18:55:38.522 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-09-15 18:55:38.572 Main::Registering HttpStatus Extension
2010-09-15 18:55:38.606 Enabled verbose msgs:  important general
2010-09-15 18:55:39.030 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-15 18:56:58.340 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-15 18:57:24.008 MainServer::ANN Monitor
2010-09-15 18:57:24.561 adding: vgc-ra710g-desktop as a client (events: 0)
2010-09-15 18:57:24.797 MainServer::ANN Monitor
2010-09-15 18:57:24.948 adding: vgc-ra710g-desktop as a client (events: 1)
QSqlQuery::exec: database not open
2010-09-15 19:05:54.109 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:05:54.261 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-09-15 19:05:54.728 No error type from QSqlError?  Strange...
2010-09-15 19:05:55.027 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:

No error type from QSqlError?  Strange...
QSqlQuery::exec: database not open
2010-09-15 19:05:56.673 No error type from QSqlError?  Strange...
QSqlQuery::exec: database not open
2010-09-15 19:05:56.989 No error type from QSqlError?  Strange...
2010-09-15 19:05:57.202 Unable to connect to database!
2010-09-15 19:05:57.272 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:05:57.472 No error type from QSqlError?  Strange...
2010-09-15 19:06:00.565 Unable to connect to database!
2010-09-15 19:06:00.591 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:06:00.866 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:06:01.307 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-09-15 19:06:01.348 No error type from QSqlError?  Strange...
2010-09-15 19:06:01.375 Unable to connect to database!
2010-09-15 19:06:01.466 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:06:01.706 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:06:01.872 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-09-15 19:06:01.897 No error type from QSqlError?  Strange...
2010-09-15 19:06:55.341 Unable to connect to database!
2010-09-15 19:06:55.362 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:06:55.652 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:06:55.861 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-09-15 19:06:56.246 No error type from QSqlError?  Strange...
2010-09-15 19:06:56.419 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:

No error type from QSqlError?  Strange...
2010-09-15 19:07:00.963 Unable to connect to database!
2010-09-15 19:07:00.999 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:07:01.688 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:07:01.870 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-09-15 19:07:01.936 No error type from QSqlError?  Strange...
2010-09-15 19:07:56.672 Unable to connect to database!
2010-09-15 19:07:56.683 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:07:56.760 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:07:56.825 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-09-15 19:07:56.833 No error type from QSqlError?  Strange...
2010-09-15 19:07:56.863 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:

No error type from QSqlError?  Strange...
2010-09-15 19:08:01.106 Unable to connect to database!
2010-09-15 19:08:01.133 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:08:01.392 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:08:01.834 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-09-15 19:08:02.097 No error type from QSqlError?  Strange...
2010-09-15 19:08:02.371 Unable to connect to database!
2010-09-15 19:08:02.552 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:08:03.080 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:08:03.230 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-09-15 19:08:03.349 No error type from QSqlError?  Strange...
2010-09-15 19:08:57.204 Unable to connect to database!
2010-09-15 19:08:57.328 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:08:57.574 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:08:57.901 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-09-15 19:08:58.152 No error type from QSqlError?  Strange...
2010-09-15 19:08:58.289 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:

No error type from QSqlError?  Strange...
2010-09-15 19:09:01.389 Unable to connect to database!
2010-09-15 19:09:01.556 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:09:02.068 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:09:03.049 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-09-15 19:09:03.182 No error type from QSqlError?  Strange...
2010-09-15 19:09:58.606 Unable to connect to database!
2010-09-15 19:09:58.648 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:09:58.931 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:09:59.089 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-09-15 19:09:59.097 No error type from QSqlError?  Strange...
2010-09-15 19:09:59.106 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:

No error type from QSqlError?  Strange...
2010-09-15 19:10:02.319 Unable to connect to database!
2010-09-15 19:10:02.652 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:10:03.008 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:10:03.132 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-09-15 19:10:03.173 No error type from QSqlError?  Strange...
2010-09-15 19:10:03.215 Unable to connect to database!
2010-09-15 19:10:03.256 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:10:03.439 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:10:03.623 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-09-15 19:10:03.672 No error type from QSqlError?  Strange...
2010-09-15 19:10:59.227 Unable to connect to database!
2010-09-15 19:10:59.368 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-09-15 19:10:59.279 Unable to connect to database!
QSqlQuery::exec: database not open
2010-09-15 19:10:59.567 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:10:59.684 No error type from QSqlError?  Strange...
QSqlQuery::exec: database not open
2010-09-15 19:10:59.717 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:10:59.867 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-09-15 19:10:59.950 No error type from QSqlError?  Strange...
2010-09-15 19:10:59.892 Unable to connect to database!
2010-09-15 19:11:00.099 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
2010-09-15 19:11:00.000 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:

No error type from QSqlError?  Strange...
QSqlQuery::exec: database not open
2010-09-15 19:11:00.274 No error type from QSqlError?  Strange...
2010-09-15 19:11:00.416 Unable to connect to database!
2010-09-15 19:11:00.457 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:11:00.599 No error type from QSqlError?  Strange...
2010-09-15 19:11:02.749 Unable to connect to database!
2010-09-15 19:11:02.912 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:11:03.211 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:11:03.611 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-09-15 19:11:03.760 No error type from QSqlError?  Strange...
2010-09-15 19:12:00.809 Unable to connect to database!
2010-09-15 19:12:01.674 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:12:02.142 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:12:02.284 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-09-15 19:12:02.392 No error type from QSqlError?  Strange...
2010-09-15 19:12:02.654 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:

No error type from QSqlError?  Strange...
2010-09-15 19:12:03.306 Unable to connect to database!
2010-09-15 19:12:03.376 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:12:03.615 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:12:03.748 Error preparing query: SELECT MIN(id),dirname FROM storagegroup WHERE hostname = :HOSTNAME AND groupname NOT IN ( 'DB Backups', 'Videos', 'Trailers', 'Coverart', 'Fanart', 'Screenshots', 'Banners' ) GROUP BY dirname;
2010-09-15 19:12:03.765 No error type from QSqlError?  Strange...
2010-09-15 19:12:05.146 AutoExpire: ERROR: Filesystem Info cache is empty, unable to calculate necessary parameters.
2010-09-15 19:12:05.190 Unable to connect to database!
2010-09-15 19:12:05.212 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:12:05.462 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:12:05.537 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-09-15 19:12:05.545 No error type from QSqlError?  Strange...
2010-09-15 19:12:05.554 Unable to connect to database!
2010-09-15 19:12:05.562 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:12:05.645 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:12:05.828 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-09-15 19:12:05.886 No error type from QSqlError?  Strange...
2010-09-15 19:12:05.986 Unable to connect to database!
2010-09-15 19:12:06.061 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:12:06.711 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:12:06.926 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' DAY)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-09-15 19:12:07.055 No error type from QSqlError?  Strange...
2010-09-15 19:12:07.159 Unable to connect to database!
2010-09-15 19:12:07.193 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:12:07.435 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:12:07.609 Error preparing query: SELECT recordid, maxepisodes, title FROM record WHERE maxepisodes > 0 ORDER BY recordid ASC, maxepisodes DESC
2010-09-15 19:12:07.661 No error type from QSqlError?  Strange...
2010-09-15 19:12:07.702 Unable to connect to database!
2010-09-15 19:12:07.792 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:12:07.984 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:12:08.217 Error preparing query: SELECT MIN(id),dirname FROM storagegroup WHERE hostname = :HOSTNAME AND groupname NOT IN ( 'DB Backups', 'Videos', 'Trailers', 'Coverart', 'Fanart', 'Screenshots', 'Banners' ) GROUP BY dirname;
2010-09-15 19:12:08.267 No error type from QSqlError?  Strange...
2010-09-15 19:12:08.325 AutoExpire: ERROR: Filesystem Info cache is empty, unable to determine what Recordings to expire
2010-09-15 19:13:03.654 Unable to connect to database!
2010-09-15 19:13:03.900 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:13:04.225 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:13:04.467 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-09-15 19:13:04.508 No error type from QSqlError?  Strange...
2010-09-15 19:13:04.644 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:

No error type from QSqlError?  Strange...
2010-09-15 19:13:05.979 Unable to connect to database!
2010-09-15 19:13:06.047 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:13:06.405 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:13:06.655 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-09-15 19:13:06.788 No error type from QSqlError?  Strange...
2010-09-15 19:14:04.717 Unable to connect to database!
2010-09-15 19:14:04.759 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:14:04.868 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:14:04.934 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
2010-09-15 19:14:04.988 No error type from QSqlError?  Strange...
2010-09-15 19:14:05.009 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:

No error type from QSqlError?  Strange...
2010-09-15 19:14:05.989 Unable to connect to database!
2010-09-15 19:14:06.058 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:14:06.365 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:14:06.540 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
2010-09-15 19:14:06.615 No error type from QSqlError?  Strange...
2010-09-15 19:14:06.624 Unable to connect to database!
2010-09-15 19:14:06.632 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2010-09-15 19:14:06.973 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:14:07.197 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-09-15 19:14:07.281 No error type from QSqlError?  Strange...
2010-09-15 19:15:05.483 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:15:06.292 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:16:05.653 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:17:05.134 MainServer::ANN Monitor
2010-09-15 19:17:05.179 adding: vgc-ra710g-desktop as a client (events: 0)
QSqlQuery::exec: database not open
2010-09-15 19:20:07.573 No error type from QSqlError?  Strange...
QSqlQuery::exec: database not open
2010-09-15 19:20:08.293 No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:20:09.149 Error preparing query: SELECT chanid, starttime, lastupdatetime, recusage, hostname FROM inuseprograms
QSqlQuery::prepare: database not open
2010-09-15 19:20:10.814 No error type from QSqlError?  Strange...
2010-09-15 19:20:11.054 Error preparing query: SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j LEFT JOIN recorded r   ON j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
QSqlQuery::exec: database not open
2010-09-15 19:20:14.051 No error type from QSqlError?  Strange...
2010-09-15 19:20:14.282 No error type from QSqlError?  Strange...
2010-09-15 19:20:15.822 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:

No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
2010-09-15 19:20:19.972 Error preparing query: SELECT recorded.chanid, starttime,   endtime,            title,           subtitle,    description,        hostname,        channum,     name,               callsign,        seriesid,    programid,          recorded.recpriority,         progstart,          progend,         filesize,    recgroup,           storagegroup,    basename FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recgroup = 'LiveTV' AND endtime < DATE_ADD(starttime, INTERVAL '2' MINUTE) AND endtime <= DATE_ADD(NOW(), INTERVAL '-1' MINUTE)  AND deletepending = 0 ORDER BY autoexpire DESC, starttime ASC
2010-09-15 19:20:20.706 No error type from QSqlError?  Strange...
2010-09-15 19:20:30.917 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-09-15 19:20:31.007 Using runtime prefix = /usr
2010-09-15 19:20:31.083 Using configuration directory = /home/mythtv/.mythtv
2010-09-15 19:20:31.386 Empty LocalHostName.
2010-09-15 19:20:31.409 Using localhost value of vgc-ra710g-desktop
2010-09-15 19:20:31.855 New DB connection, total: 1
2010-09-15 19:20:31.908 Unable to connect to database!
2010-09-15 19:20:31.979 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-09-15 19:21:14.823 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-09-15 19:21:16.205 Using runtime prefix = /usr
2010-09-15 19:21:16.252 Using configuration directory = /home/mythtv/.mythtv
2010-09-15 19:21:16.704 Empty LocalHostName.
2010-09-15 19:21:16.781 Using localhost value of vgc-ra710g-desktop
2010-09-15 19:21:17.030 New DB connection, total: 1
2010-09-15 19:21:17.496 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:21:17.576 Closing DB connection named 'DBManager0'
2010-09-15 19:21:17.652 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:21:18.491 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-15 19:21:18.577 MythBackend: Starting up as the master server.
2010-09-15 19:21:19.455 New DB connection, total: 2
2010-09-15 19:21:19.524 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:21:19.928 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2010-09-15 19:21:19.959 ChannelBase(1) Error: InitializeInputs():
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2010-09-15 19:21:19.987 MythBackend, Error: No valid capture cards are defined in the database.
            Perhaps you should re-read the installation instructions?
2010-09-15 19:21:20.090 New DB connection, total: 3
2010-09-15 19:21:20.132 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:21:20.402 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-09-15 19:21:20.431 Main::Registering HttpStatus Extension
2010-09-15 19:21:20.440 Enabled verbose msgs:  important general
2010-09-15 19:21:20.638 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-15 19:22:13.637 MainServer::ANN Monitor
2010-09-15 19:22:13.741 adding: vgc-ra710g-desktop as a client (events: 0)
2010-09-15 19:22:13.775 MainServer::ANN Monitor
2010-09-15 19:22:13.824 adding: vgc-ra710g-desktop as a client (events: 1)
2010-09-15 19:22:40.814 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-15 19:26:43.470 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
2010-09-15 19:26:43.487 MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
2010-09-15 19:26:57.226 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
2010-09-15 19:26:57.251 MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
2010-09-15 19:27:01.037 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
2010-09-15 19:27:01.048 MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
2010-09-15 19:27:03.374 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
2010-09-15 19:27:03.397 MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
2010-09-15 19:27:16.087 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
2010-09-15 19:27:16.112 MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
2010-09-15 19:27:21.058 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
2010-09-15 19:27:21.066 MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
2010-09-15 19:37:59.476 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-09-15 19:37:59.490 Using runtime prefix = /usr
2010-09-15 19:37:59.532 Using configuration directory = /home/mythtv/.mythtv
2010-09-15 19:37:59.548 Empty LocalHostName.
2010-09-15 19:37:59.556 Using localhost value of vgc-ra710g-desktop
2010-09-15 19:37:59.584 New DB connection, total: 1
2010-09-15 19:37:59.601 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:37:59.606 Closing DB connection named 'DBManager0'
2010-09-15 19:37:59.615 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:37:59.626 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-15 19:37:59.633 MythBackend: Starting up as the master server.
2010-09-15 19:37:59.643 New DB connection, total: 2
2010-09-15 19:37:59.648 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:37:59.704 New DB connection, total: 3
2010-09-15 19:37:59.731 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:37:59.744 Channel(/dev/video0): SetChannelByString(Please add), Error: CheckChannel failed.
            Please verify the channel in the 'mythtv-setup' Channel Editor.
2010-09-15 19:37:59.747 ChannelBase(1) Error: Setting start channel 'Please add' failed,
            and we failed to find any suitible channels on any input.
2010-09-15 19:37:59.769 New DB scheduler connection
2010-09-15 19:37:59.781 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:37:59.831 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-09-15 19:37:59.847 Main::Registering HttpStatus Extension
2010-09-15 19:37:59.855 Enabled verbose msgs:  important general
2010-09-15 19:37:59.866 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-15 19:38:02.812 Reschedule requested for id -1.
2010-09-15 19:38:03.056 Scheduled 0 items in 0.2 = 0.05 match + 0.20 place
2010-09-15 19:38:03.071 Seem to be woken up by USER
2010-09-15 19:38:09.384 MainServer::ANN Monitor
2010-09-15 19:38:09.391 adding: vgc-ra710g-desktop as a client (events: 0)
2010-09-15 19:38:09.400 MainServer::ANN Monitor
2010-09-15 19:38:09.408 adding: vgc-ra710g-desktop as a client (events: 1)
2010-09-15 19:38:09.417 Reschedule requested for id -1.
2010-09-15 19:38:09.497 Scheduled 0 items in 0.1 = 0.01 match + 0.07 place
2010-09-15 19:38:46.249 MainServer::ANN Monitor
2010-09-15 19:38:46.252 adding: vgc-ra710g-desktop as a client (events: 0)
2010-09-15 19:38:46.261 MainServer::ANN Monitor
2010-09-15 19:38:46.268 adding: vgc-ra710g-desktop as a client (events: 1)
2010-09-15 19:38:50.172 MainServer::ANN Playback
2010-09-15 19:38:50.204 adding: vgc-ra710g-desktop as a client (events: 0)
2010-09-15 19:38:50.214 TVRec(1): Changing from None to WatchingLiveTV
2010-09-15 19:38:50.224 GetChannelData() failed because it could not
            find channel number 'Please add' in DB for source '1'.
2010-09-15 19:38:50.229 ChannelBase(1): IsTunable(Tuner 1,Please add) Failed to find channel in DB on input '2'
2010-09-15 19:38:50.237 ChannelBase(1) Error: Setting start channel 'Please add' failed,
            and we failed to find any suitible channels on any input.
2010-09-15 19:38:50.246 TVRec(1): HW Tuner: 1->1
2010-09-15 19:38:50.261 Channel(/dev/video0): SetChannelByString(Please add), Error: CheckChannel failed.
            Please verify the channel in the 'mythtv-setup' Channel Editor.
2010-09-15 19:38:50.262 TVRec(1) Error: Failed to set channel to Please add. Reverting to kState_None
2010-09-15 19:38:50.271 TVRec(1): Changing from WatchingLiveTV to None
2010-09-15 19:38:59.305 MainServer::ANN Playback
2010-09-15 19:38:59.332 adding: vgc-ra710g-desktop as a client (events: 0)
2010-09-15 19:38:59.342 TVRec(1): Changing from None to WatchingLiveTV
2010-09-15 19:38:59.351 GetChannelData() failed because it could not
            find channel number 'Please add' in DB for source '1'.
2010-09-15 19:38:59.357 ChannelBase(1): IsTunable(Tuner 1,Please add) Failed to find channel in DB on input '2'
2010-09-15 19:38:59.365 ChannelBase(1) Error: Setting start channel 'Please add' failed,
            and we failed to find any suitible channels on any input.
2010-09-15 19:38:59.411 TVRec(1): HW Tuner: 1->1
2010-09-15 19:38:59.435 Channel(/dev/video0): SetChannelByString(Please add), Error: CheckChannel failed.
            Please verify the channel in the 'mythtv-setup' Channel Editor.
2010-09-15 19:38:59.439 TVRec(1) Error: Failed to set channel to Please add. Reverting to kState_None
2010-09-15 19:38:59.447 TVRec(1): Changing from WatchingLiveTV to None
2010-09-15 19:39:19.812 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-15 19:43:19.288 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-09-15 19:43:19.289 Using runtime prefix = /usr
2010-09-15 19:43:19.312 Using configuration directory = /home/mythtv/.mythtv
2010-09-15 19:43:19.321 Empty LocalHostName.
2010-09-15 19:43:19.329 Using localhost value of vgc-ra710g-desktop
2010-09-15 19:43:19.349 New DB connection, total: 1
2010-09-15 19:43:19.360 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:43:19.363 Closing DB connection named 'DBManager0'
2010-09-15 19:43:19.371 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:43:19.382 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-15 19:43:19.388 MythBackend: Starting up as the master server.
2010-09-15 19:43:19.399 New DB connection, total: 2
2010-09-15 19:43:19.404 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:43:19.415 New DB connection, total: 3
2010-09-15 19:43:19.420 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:43:19.434 Channel(/dev/video0): SetChannelByString(Please add), Error: CheckChannel failed.
            Please verify the channel in the 'mythtv-setup' Channel Editor.
2010-09-15 19:43:19.437 ChannelBase(1) Error: Setting start channel 'Please add' failed,
            and we failed to find any suitible channels on any input.
2010-09-15 19:43:19.457 New DB scheduler connection
2010-09-15 19:43:19.462 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:43:19.486 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-09-15 19:43:19.495 Main::Registering HttpStatus Extension
2010-09-15 19:43:19.503 Enabled verbose msgs:  important general
2010-09-15 19:43:19.514 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-15 19:43:22.476 Reschedule requested for id -1.
2010-09-15 19:43:22.579 Scheduled 0 items in 0.1 = 0.02 match + 0.08 place
2010-09-15 19:43:22.602 Seem to be woken up by USER
2010-09-15 19:43:28.785 MainServer::ANN Monitor
2010-09-15 19:43:28.805 adding: vgc-ra710g-desktop as a client (events: 0)
2010-09-15 19:43:28.814 MainServer::ANN Monitor
2010-09-15 19:43:28.822 adding: vgc-ra710g-desktop as a client (events: 1)
2010-09-15 19:43:28.832 Reschedule requested for id -1.
2010-09-15 19:43:28.916 Scheduled 0 items in 0.1 = 0.01 match + 0.07 place
2010-09-15 19:43:29.479 New DB connection, total: 4
2010-09-15 19:43:29.488 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:43:43.513 MainServer::ANN Monitor
2010-09-15 19:43:43.533 adding: vgc-ra710g-desktop as a client (events: 0)
2010-09-15 19:43:43.543 MainServer::ANN Monitor
2010-09-15 19:43:43.549 adding: vgc-ra710g-desktop as a client (events: 1)
2010-09-15 19:43:47.681 MainServer::ANN Playback
2010-09-15 19:43:47.701 adding: vgc-ra710g-desktop as a client (events: 0)
2010-09-15 19:43:47.712 TVRec(1): Changing from None to WatchingLiveTV
2010-09-15 19:43:47.763 GetChannelData() failed because it could not
            find channel number 'Please add' in DB for source '1'.
2010-09-15 19:43:47.768 ChannelBase(1): IsTunable(Tuner 1,Please add) Failed to find channel in DB on input '2'
2010-09-15 19:43:47.776 ChannelBase(1) Error: Setting start channel 'Please add' failed,
            and we failed to find any suitible channels on any input.
2010-09-15 19:43:47.785 TVRec(1): HW Tuner: 1->1
2010-09-15 19:43:47.800 Channel(/dev/video0): SetChannelByString(Please add), Error: CheckChannel failed.
            Please verify the channel in the 'mythtv-setup' Channel Editor.
2010-09-15 19:43:47.801 TVRec(1) Error: Failed to set channel to Please add. Reverting to kState_None
2010-09-15 19:43:47.832 TVRec(1): Changing from WatchingLiveTV to None
2010-09-15 19:44:39.476 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-15 19:48:22.545 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-09-15 19:48:22.546 Using runtime prefix = /usr
2010-09-15 19:48:22.567 Using configuration directory = /home/mythtv/.mythtv
2010-09-15 19:48:22.576 Empty LocalHostName.
2010-09-15 19:48:22.584 Using localhost value of vgc-ra710g-desktop
2010-09-15 19:48:22.605 New DB connection, total: 1
2010-09-15 19:48:22.617 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:48:22.625 Closing DB connection named 'DBManager0'
2010-09-15 19:48:22.634 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:48:22.645 Current MythTV Schema Version (DBSchemaVer): 1254
2010-09-15 19:48:22.652 MythBackend: Starting up as the master server.
2010-09-15 19:48:22.662 New DB connection, total: 2
2010-09-15 19:48:22.667 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:48:22.679 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2010-09-15 19:48:22.684 ChannelBase(1) Error: InitializeInputs():
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2010-09-15 19:48:22.692 MythBackend, Error: No valid capture cards are defined in the database.
            Perhaps you should re-read the installation instructions?
2010-09-15 19:48:22.702 New DB connection, total: 3
2010-09-15 19:48:22.709 Connected to database 'mythconverg' at host: localhost
2010-09-15 19:48:22.721 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-09-15 19:48:22.725 Main::Registering HttpStatus Extension
2010-09-15 19:48:22.733 Enabled verbose msgs:  important general
2010-09-15 19:48:22.744 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-09-15 19:48:35.560 MainServer::ANN Monitor
2010-09-15 19:48:35.564 adding: vgc-ra710g-desktop as a client (events: 0)
2010-09-15 19:48:35.573 MainServer::ANN Monitor
2010-09-15 19:48:35.580 adding: vgc-ra710g-desktop as a client (events: 1)
2010-09-15 19:48:55.375 MainServer::ANN Monitor
2010-09-15 19:48:55.391 adding: vgc-ra710g-desktop as a client (events: 0)
2010-09-15 19:48:55.401 MainServer::ANN Monitor
2010-09-15 19:48:55.408 adding: vgc-ra710g-desktop as a client (events: 1)

---

### Post by tgm4883 on 2010-09-17
```
2010-09-15 19:48:22.684 ChannelBase(1) Error: InitializeInputs():
Could not get inputs for the capturecard.
Perhaps you have forgotten to bind video
sources to your card's inputs?
2010-09-15 19:48:22.692 MythBackend, Error: No valid capture cards are defined in the database.
Perhaps you should re-read the installation instructions?
```

Logs are great :)

---

### Post by okorkie on 2010-09-22
Hello,

Ok, I am still stuck and I have no idea of what the problem is.. At this point I'm close to renting a DVR from Comcast :-(

I figure I would give it one last shot at trying to get this working.  I have posted a video on YouTube of myself going through each of the steps in the configuration process and is about 4 minutes and 45 seconds in length.  Here is the link:

[http://www.youtube.com/watch?v=UooUEVzG910](http://www.youtube.com/watch?v=UooUEVzG910)

Again, any help is greatly appreciated!

---

### Post by saedelaere on 2010-10-08
I don't know if you really need mythTV to watch TV with the . PVR-150. In case you want to try an alternative have a look at [TV-Viewer]("http://tv-viewer.sourceforge.net/") If you have problems with segfaults you will need to install ActiveTCL, which is described in this [howto]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Howto#Replacing_included_Tcl.2FTk_packages_with_ActiveTcl").

Regards

---

### Post by Furry_Fighter_20x66 on 2010-10-09
I am not sure what's going on with your database there. It might be part of your issues.

Anyway, if you want to test the card to make sure it is working you can do the following:

in a terminal : mplayer /dev/video0

open a second terminal and you can use the following to change inputs and channels. (You may also have to install the ivtv-utils from the package manager)

to change input:
v4l2-ctl -t (number)
where (number) is 0 to 3 or 4 or so for the other inputs

to change channels:
ivtv-tune -c (number)

Now if you get everything working here, your card is working great.

For the setup of the tuner in MythTV, you will have to add in the command for changing channels in the input settings. it's simple. Just follow my screenshot for where to place it. I get the channel listings from Schedules Direct and set them that way. I have never had to set them manually and I am not sure how but at least I hope this was able to help you in some small way.

---

