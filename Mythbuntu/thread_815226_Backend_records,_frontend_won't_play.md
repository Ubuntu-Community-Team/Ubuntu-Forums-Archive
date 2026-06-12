---
title: "Backend records, frontend won't play"
date: 2008-06-01
forum: Mythbuntu
---

### Post by UltramaticOrange on 2008-06-01
Basic setup:
P4 2.4GHZ (socket 478.)
1GB of PC2700
HD-5500
ATI TV Wonder (not yet configured)

So, I've found people with the same problem, but no solution offered up. In my personal experience, this usually means that the solution is pretty simple, but after a few days, it still alludes me.

Everything seems to be setup okay until I go to try and watch TV. When I do, I'm presented with a black screen and no method to exit back to the main menu (except to `kill <pid>` the frontend process). When I enter the recording directory I have an mpg file which I can open and play fine in VLC. The file also opens and plays in MPlayer with the error "AO:[pulse] Failed to connect to server: Connection refused"

Backend log:
```
2008-05-31 04:10:21.487 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-31 04:10:21.695 Empty LocalHostName.
2008-05-31 04:10:21.724 Using localhost value of magicvoice
2008-05-31 04:10:21.856 New DB connection, total: 1
2008-05-31 04:10:21.890 Connected to database 'mythconverg' at host: localhost
2008-05-31 04:10:21.892 Closing DB connection named 'DBManager0'
2008-05-31 04:10:21.894 Connected to database 'mythconverg' at host: localhost
2008-05-31 04:10:21.927 New DB connection, total: 2
2008-05-31 04:10:21.936 Connected to database 'mythconverg' at host: localhost
2008-05-31 04:10:21.979 Current Schema Version: 1214
Starting up as the master server.
2008-05-31 04:10:22.164 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2008-05-31 04:10:22.296 ChannelBase(1) Error: InitializeInputs(): 
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-05-31 04:10:22.363 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-05-31 04:10:22.414 Main::Registering HttpStatus Extension
2008-05-31 04:10:22.414 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-05-31 04:10:22.415 Enabled verbose msgs:  important general
2008-05-31 04:10:22.506 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
2008-05-31 04:11:42.314 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-31 04:12:23.772 MainServer::HandleAnnounce Monitor
2008-05-31 04:12:23.782 adding: magicvoice as a client (events: 0)
2008-05-31 04:12:23.816 MainServer::HandleAnnounce Monitor
2008-05-31 04:12:23.817 adding: magicvoice as a client (events: 1)
2008-05-31 21:13:17.445 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-31 21:30:19.708 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-31 21:30:19.752 Empty LocalHostName.
2008-05-31 21:30:19.753 Using localhost value of magicvoice
2008-05-31 21:30:19.765 New DB connection, total: 1
2008-05-31 21:30:19.782 Connected to database 'mythconverg' at host: localhost
2008-05-31 21:30:19.785 Closing DB connection named 'DBManager0'
2008-05-31 21:30:19.786 Connected to database 'mythconverg' at host: localhost
2008-05-31 21:30:19.789 New DB connection, total: 2
2008-05-31 21:30:19.790 Connected to database 'mythconverg' at host: localhost
2008-05-31 21:30:19.794 Current Schema Version: 1214
Starting up as the master server.
2008-05-31 21:30:19.827 New DB connection, total: 3
2008-05-31 21:30:19.828 Connected to database 'mythconverg' at host: localhost
2008-05-31 21:30:20.055 New DB scheduler connection
2008-05-31 21:30:20.057 Connected to database 'mythconverg' at host: localhost
Schedules Direct Digital is defined, but isn't attached to a cardinput.
Schedules Direct Broadcast is defined, but isn't attached to a cardinput.
2008-05-31 21:30:20.099 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-05-31 21:30:20.099 Main::Registering HttpStatus Extension
2008-05-31 21:30:20.100 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-05-31 21:30:20.101 Enabled verbose msgs:  important general
2008-05-31 21:30:20.105 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-31 21:30:20.110 SG(Default) Error: Group 'Default' wants to use directory '/home/mythos/mythos/', but this directory is not writeable.
2008-05-31 21:30:23.067 Reschedule requested for id -1.
2008-05-31 21:30:23.138 Scheduled 0 items in 0.1 = 0.01 match + 0.06 place
2008-05-31 21:30:23.147 Seem to be woken up by USER
2008-05-31 21:31:40.071 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
2008-05-31 21:46:44.137 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
2008-05-31 21:59:51.538 MainServer::HandleAnnounce Monitor
2008-05-31 21:59:51.541 adding: magicvoice as a client (events: 0)
2008-05-31 21:59:51.543 MainServer::HandleAnnounce Monitor
2008-05-31 21:59:51.543 adding: magicvoice as a client (events: 1)
2008-05-31 21:59:51.545 Reschedule requested for id -1.
2008-05-31 21:59:51.575 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
QDateTime::fromString: Parameter out of range
2008-05-31 22:01:47.689 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
2008-05-31 22:16:47.729 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-05-31 22:31:47.758 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
QSqlQuery::exec: database not open
2008-05-31 22:42:30.201 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2008-05-31 22:42:30.528 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
No error type from QSqlError?  Strange...
2008-05-31 22:42:47.824 Unable to connect to database!
2008-05-31 22:42:47.862 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-05-31 22:42:47.916 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2008-05-31 22:42:47.970 Unable to connect to database!
2008-05-31 22:42:47.971 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-05-31 22:42:48.024 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2008-05-31 22:43:30.856 Unable to connect to database!
2008-05-31 22:43:31.967 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-05-31 22:43:34.070 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2008-05-31 22:43:34.143 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
No error type from QSqlError?  Strange...
2008-05-31 22:43:48.078 Unable to connect to database!
2008-05-31 22:43:48.166 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-05-31 22:43:48.220 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QSqlQuery::prepare: database not open
QSqlQuery::exec: database not open
2008-05-31 22:44:34.157 Connected to database 'mythconverg' at host: localhost
2008-05-31 22:46:06.255 MainServer::HandleAnnounce Monitor
2008-05-31 22:46:06.283 adding: magicvoice as a client (events: 0)
2008-05-31 22:46:06.284 MainServer::HandleAnnounce Monitor
2008-05-31 22:46:06.285 adding: magicvoice as a client (events: 1)
2008-05-31 22:46:06.411 MainServer::HandleAnnounce Playback
2008-05-31 22:46:06.412 adding: magicvoice as a client (events: 0)
2008-05-31 22:46:06.486 TVRec(1): Changing from None to WatchingLiveTV
2008-05-31 22:46:06.640 TVRec(1): HW Tuner: 1->1
2008-05-31 22:46:08.192 TFW, Error: Opening file '/home/mythos/mythos/2021_20080531224606.nuv'.
			eno: Permission denied (13)
2008-05-31 22:46:08.194 TVRec(1) Error: RingBuffer '/home/mythos/mythos/2021_20080531224606.nuv' not open...
2008-05-31 22:46:08.194 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2008-05-31 22:46:08.195 TVRec(1) Error: Failed to create RingBuffer 2
2008-05-31 22:46:08.213 TVRec(1): Changing from WatchingLiveTV to None
2008-05-31 22:46:08.219 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-31 22:46:08.220 MythSocket(82891a0:-1): writeStringList: Error, socket went unconnected.
2008-05-31 22:46:48.278 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-31 22:48:33.738 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-31 22:48:33.911 Empty LocalHostName.
2008-05-31 22:48:33.930 Using localhost value of magicvoice
2008-05-31 22:48:34.086 New DB connection, total: 1
2008-05-31 22:48:34.124 Connected to database 'mythconverg' at host: localhost
2008-05-31 22:48:34.127 Closing DB connection named 'DBManager0'
2008-05-31 22:48:34.129 Connected to database 'mythconverg' at host: localhost
2008-05-31 22:48:34.173 New DB connection, total: 2
2008-05-31 22:48:34.208 Connected to database 'mythconverg' at host: localhost
2008-05-31 22:48:34.291 Current Schema Version: 1214
Starting up as the master server.
2008-05-31 22:48:34.677 New DB connection, total: 3
2008-05-31 22:48:34.682 Connected to database 'mythconverg' at host: localhost
2008-05-31 22:48:34.859 New DB scheduler connection
2008-05-31 22:48:34.875 Connected to database 'mythconverg' at host: localhost
Schedules Direct Digital is defined, but isn't attached to a cardinput.
Schedules Direct Broadcast is defined, but isn't attached to a cardinput.
2008-05-31 22:48:35.117 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-05-31 22:48:35.173 Main::Registering HttpStatus Extension
2008-05-31 22:48:35.176 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-05-31 22:48:35.281 Enabled verbose msgs:  important general
2008-05-31 22:48:35.431 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-31 22:48:35.628 SG(Default) Error: Group 'Default' wants to use directory '/home/mythos/mythos/', but this directory is not writeable.
2008-05-31 22:48:37.907 Reschedule requested for id -1.
2008-05-31 22:48:38.294 Scheduled 0 items in 0.4 = 0.18 match + 0.20 place
2008-05-31 22:48:38.302 Seem to be woken up by USER
QDateTime::fromString: Parameter out of range
2008-05-31 22:49:09.549 MainServer::HandleAnnounce Monitor
2008-05-31 22:49:09.554 adding: magicvoice as a client (events: 0)
2008-05-31 22:49:09.556 MainServer::HandleAnnounce Monitor
2008-05-31 22:49:09.557 adding: magicvoice as a client (events: 1)
2008-05-31 22:49:09.563 MainServer::HandleAnnounce Playback
2008-05-31 22:49:09.581 adding: magicvoice as a client (events: 0)
2008-05-31 22:49:09.584 TVRec(1): Changing from None to WatchingLiveTV
2008-05-31 22:49:09.592 TVRec(1): HW Tuner: 1->1
2008-05-31 22:49:10.805 TFW, Error: Opening file '/home/mythos/mythos/2021_20080531224909.nuv'.
			eno: Permission denied (13)
2008-05-31 22:49:10.808 TVRec(1) Error: RingBuffer '/home/mythos/mythos/2021_20080531224909.nuv' not open...
2008-05-31 22:49:10.809 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2008-05-31 22:49:10.810 TVRec(1) Error: Failed to create RingBuffer 2
2008-05-31 22:49:10.813 TVRec(1): Changing from WatchingLiveTV to None
2008-05-31 22:49:10.814 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-31 22:49:54.910 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-05-31 23:04:55.137 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-31 23:09:48.428 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-31 23:09:48.437 Empty LocalHostName.
2008-05-31 23:09:48.449 Using localhost value of magicvoice
2008-05-31 23:09:48.461 New DB connection, total: 1
2008-05-31 23:09:48.472 Connected to database 'mythconverg' at host: localhost
2008-05-31 23:09:48.475 Closing DB connection named 'DBManager0'
2008-05-31 23:09:48.479 Connected to database 'mythconverg' at host: localhost
2008-05-31 23:09:48.488 New DB connection, total: 2
2008-05-31 23:09:48.489 Connected to database 'mythconverg' at host: localhost
2008-05-31 23:09:48.493 Current Schema Version: 1214
Starting up as the master server.
2008-05-31 23:09:48.527 New DB connection, total: 3
2008-05-31 23:09:48.528 Connected to database 'mythconverg' at host: localhost
2008-05-31 23:09:48.777 New DB scheduler connection
2008-05-31 23:09:48.779 Connected to database 'mythconverg' at host: localhost
Schedules Direct Digital is defined, but isn't attached to a cardinput.
Schedules Direct Broadcast is defined, but isn't attached to a cardinput.
2008-05-31 23:09:48.847 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-05-31 23:09:48.847 Main::Registering HttpStatus Extension
2008-05-31 23:09:48.848 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-05-31 23:09:48.849 Enabled verbose msgs:  important general
2008-05-31 23:09:48.852 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-31 23:09:48.931 SG(Default) Error: Group 'Default' wants to use directory '/home/mythos/mythos/', but this directory is not writeable.
2008-05-31 23:09:51.801 Reschedule requested for id -1.
2008-05-31 23:09:51.835 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-05-31 23:09:51.843 Seem to be woken up by USER
QDateTime::fromString: Parameter out of range
2008-05-31 23:11:08.804 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
2008-05-31 23:26:08.860 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
2008-05-31 23:39:58.620 MainServer::HandleAnnounce Monitor
2008-05-31 23:39:58.625 adding: magicvoice as a client (events: 0)
2008-05-31 23:39:58.627 MainServer::HandleAnnounce Monitor
2008-05-31 23:39:58.627 adding: magicvoice as a client (events: 1)
2008-05-31 23:39:58.629 Reschedule requested for id -1.
2008-05-31 23:39:58.736 Scheduled 0 items in 0.1 = 0.01 match + 0.10 place
QDateTime::fromString: Parameter out of range
2008-05-31 23:41:13.426 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
2008-05-31 23:56:13.470 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
2008-06-01 00:03:40.617 MainServer::HandleAnnounce Monitor
2008-06-01 00:03:40.621 adding: magicvoice as a client (events: 0)
2008-06-01 00:03:40.623 MainServer::HandleAnnounce Monitor
2008-06-01 00:03:40.623 adding: magicvoice as a client (events: 1)
2008-06-01 00:03:40.632 MainServer::HandleAnnounce Playback
2008-06-01 00:03:40.633 adding: magicvoice as a client (events: 0)
2008-06-01 00:03:40.635 TVRec(1): Changing from None to WatchingLiveTV
2008-06-01 00:03:40.644 TVRec(1): HW Tuner: 1->1
2008-06-01 00:03:41.824 TFW, Error: Opening file '/home/mythos/mythos/2004_20080601000340.nuv'.
			eno: Permission denied (13)
2008-06-01 00:03:41.826 TVRec(1) Error: RingBuffer '/home/mythos/mythos/2004_20080601000340.nuv' not open...
2008-06-01 00:03:41.826 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2008-06-01 00:03:41.827 TVRec(1) Error: Failed to create RingBuffer 2
2008-06-01 00:03:41.830 TVRec(1): Changing from WatchingLiveTV to None
2008-06-01 00:03:41.831 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 10:05:31.689 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-01 10:05:31.753 Empty LocalHostName.
2008-06-01 10:05:31.822 Using localhost value of magicvoice
2008-06-01 10:05:32.045 New DB connection, total: 1
2008-06-01 10:05:32.130 Connected to database 'mythconverg' at host: localhost
2008-06-01 10:05:32.174 Closing DB connection named 'DBManager0'
2008-06-01 10:05:32.177 Connected to database 'mythconverg' at host: localhost
2008-06-01 10:05:32.207 New DB connection, total: 2
2008-06-01 10:05:32.221 Connected to database 'mythconverg' at host: localhost
2008-06-01 10:05:32.292 Current Schema Version: 1214
Starting up as the master server.
2008-06-01 10:05:32.609 New DB connection, total: 3
2008-06-01 10:05:32.612 Connected to database 'mythconverg' at host: localhost
2008-06-01 10:05:32.897 New DB scheduler connection
2008-06-01 10:05:33.101 Connected to database 'mythconverg' at host: localhost
Schedules Direct Digital is defined, but isn't attached to a cardinput.
Schedules Direct Broadcast is defined, but isn't attached to a cardinput.
2008-06-01 10:05:33.410 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-06-01 10:05:33.532 Main::Registering HttpStatus Extension
2008-06-01 10:05:33.552 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-06-01 10:05:33.553 Enabled verbose msgs:  important general
2008-06-01 10:05:33.715 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 10:05:33.887 SG(Default) Error: Group 'Default' wants to use directory '/home/mythos/mythos/', but this directory is not writeable.
2008-06-01 10:05:36.266 Reschedule requested for id -1.
2008-06-01 10:05:36.341 Scheduled 0 items in 0.1 = 0.02 match + 0.06 place
2008-06-01 10:05:36.348 Seem to be woken up by USER
QDateTime::fromString: Parameter out of range
2008-06-01 10:06:26.312 MainServer::HandleAnnounce Monitor
2008-06-01 10:06:26.316 adding: magicvoice as a client (events: 0)
2008-06-01 10:06:26.318 MainServer::HandleAnnounce Monitor
2008-06-01 10:06:26.318 adding: magicvoice as a client (events: 1)
2008-06-01 10:06:26.320 Reloading backend settings
2008-06-01 10:06:53.268 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 10:08:09.534 Reschedule requested for id 0.
2008-06-01 10:08:09.653 Scheduled 0 items in 0.1 = 0.02 match + 0.10 place
QDateTime::fromString: Parameter out of range
2008-06-01 10:11:09.252 Reloading backend settings
2008-06-01 10:11:16.688 MainServer::HandleAnnounce Playback
2008-06-01 10:11:16.692 adding: magicvoice as a client (events: 0)
2008-06-01 10:11:16.738 TVRec(1): Changing from None to WatchingLiveTV
2008-06-01 10:11:16.834 TVRec(1): HW Tuner: 1->1
2008-06-01 10:11:18.261 TFW, Error: Opening file '/home/mythos/mythos/2004_20080601101117.nuv'.
			eno: Permission denied (13)
2008-06-01 10:11:18.263 TVRec(1) Error: RingBuffer '/home/mythos/mythos/2004_20080601101117.nuv' not open...
2008-06-01 10:11:18.263 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2008-06-01 10:11:18.264 TVRec(1) Error: Failed to create RingBuffer 2
2008-06-01 10:11:18.267 TVRec(1): Changing from WatchingLiveTV to None
2008-06-01 10:11:18.272 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 10:58:24.651 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-01 10:58:24.679 Empty LocalHostName.
2008-06-01 10:58:24.680 Using localhost value of magicvoice
2008-06-01 10:58:24.692 New DB connection, total: 1
2008-06-01 10:58:24.700 Connected to database 'mythconverg' at host: localhost
2008-06-01 10:58:24.702 Closing DB connection named 'DBManager0'
2008-06-01 10:58:24.703 Connected to database 'mythconverg' at host: localhost
2008-06-01 10:58:24.706 New DB connection, total: 2
2008-06-01 10:58:24.707 Connected to database 'mythconverg' at host: localhost
2008-06-01 10:58:24.711 Current Schema Version: 1214
Starting up as the master server.
2008-06-01 10:58:24.741 New DB connection, total: 3
2008-06-01 10:58:24.742 Connected to database 'mythconverg' at host: localhost
2008-06-01 10:58:24.874 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2008-06-01 10:58:24.877 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2008-06-01 10:58:24.898 New DB scheduler connection
2008-06-01 10:58:24.900 Connected to database 'mythconverg' at host: localhost
Schedules Direct Analog is defined, but isn't attached to a cardinput.
Schedules Direct Broadcast is defined, but isn't attached to a cardinput.
2008-06-01 10:58:25.002 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-06-01 10:58:25.003 Main::Registering HttpStatus Extension
2008-06-01 10:58:25.003 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-06-01 10:58:25.004 Enabled verbose msgs:  important general
2008-06-01 10:58:25.007 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 10:58:25.056 SG(Default) Error: Group 'Default' wants to use directory '/home/mythos/mythos/', but this directory is not writeable.
2008-06-01 10:58:27.910 Reschedule requested for id -1.
2008-06-01 10:58:27.973 Scheduled 0 items in 0.1 = 0.03 match + 0.03 place
2008-06-01 10:58:27.988 Seem to be woken up by USER
2008-06-01 10:59:44.927 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 11:14:44.982 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 11:29:45.371 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 11:31:33.009 MainServer::HandleAnnounce Monitor
2008-06-01 11:31:33.013 adding: magicvoice as a client (events: 0)
2008-06-01 11:31:33.014 MainServer::HandleAnnounce Monitor
2008-06-01 11:31:33.015 adding: magicvoice as a client (events: 1)
2008-06-01 11:31:33.017 Reschedule requested for id -1.
2008-06-01 11:31:33.125 Scheduled 0 items in 0.1 = 0.01 match + 0.10 place
2008-06-01 11:33:01.938 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-01 11:33:02.111 Empty LocalHostName.
2008-06-01 11:33:02.130 Using localhost value of magicvoice
2008-06-01 11:33:02.277 New DB connection, total: 1
2008-06-01 11:33:02.367 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:33:02.370 Closing DB connection named 'DBManager0'
2008-06-01 11:33:02.373 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:33:02.423 New DB connection, total: 2
2008-06-01 11:33:02.436 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:33:02.516 Current Schema Version: 1214
Starting up as the master server.
2008-06-01 11:33:02.787 New DB connection, total: 3
2008-06-01 11:33:02.790 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:33:02.958 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2008-06-01 11:33:02.991 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2008-06-01 11:33:03.022 New DB scheduler connection
2008-06-01 11:33:03.024 Connected to database 'mythconverg' at host: localhost
Schedules Direct Analog is defined, but isn't attached to a cardinput.
Schedules Direct Broadcast is defined, but isn't attached to a cardinput.
2008-06-01 11:33:03.300 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-06-01 11:33:03.361 Main::Registering HttpStatus Extension
2008-06-01 11:33:03.362 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-06-01 11:33:03.363 Enabled verbose msgs:  important general
2008-06-01 11:33:03.473 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 11:33:03.578 SG(Default) Error: Group 'Default' wants to use directory '/home/mythos/mythos/', but this directory is not writeable.
2008-06-01 11:33:06.173 Reschedule requested for id -1.
2008-06-01 11:33:06.290 Scheduled 0 items in 0.1 = 0.07 match + 0.05 place
2008-06-01 11:33:06.298 Seem to be woken up by USER
2008-06-01 11:33:35.759 MainServer::HandleAnnounce Monitor
2008-06-01 11:33:35.764 adding: magicvoice as a client (events: 0)
2008-06-01 11:33:35.766 MainServer::HandleAnnounce Monitor
2008-06-01 11:33:35.767 adding: magicvoice as a client (events: 1)
2008-06-01 11:33:35.773 MainServer::HandleAnnounce Playback
2008-06-01 11:33:35.791 adding: magicvoice as a client (events: 0)
2008-06-01 11:33:35.794 TVRec(1): Changing from None to WatchingLiveTV
2008-06-01 11:33:35.802 TVRec(1): HW Tuner: 1->1
2008-06-01 11:33:37.015 TFW, Error: Opening file '/home/mythos/mythos/1021_20080601113335.mpg'.
			eno: Permission denied (13)
2008-06-01 11:33:37.025 TVRec(1) Error: RingBuffer '/home/mythos/mythos/1021_20080601113335.mpg' not open...
2008-06-01 11:33:37.025 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2008-06-01 11:33:37.026 TVRec(1) Error: Failed to create RingBuffer 1
2008-06-01 11:33:37.027 TVRec(1): Changing from WatchingLiveTV to None
2008-06-01 11:33:37.027 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 11:34:23.185 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 11:39:02.902 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-01 11:39:02.904 Empty LocalHostName.
2008-06-01 11:39:02.906 Using localhost value of magicvoice
2008-06-01 11:39:02.919 New DB connection, total: 1
2008-06-01 11:39:02.926 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:39:02.928 Closing DB connection named 'DBManager0'
2008-06-01 11:39:02.952 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:39:02.960 New DB connection, total: 2
2008-06-01 11:39:02.961 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:39:02.965 Current Schema Version: 1214
Starting up as the master server.
2008-06-01 11:39:03.005 New DB connection, total: 3
2008-06-01 11:39:03.006 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:39:03.129 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2008-06-01 11:39:03.131 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2008-06-01 11:39:03.133 New DB scheduler connection
2008-06-01 11:39:03.134 Connected to database 'mythconverg' at host: localhost
Schedules Direct Analog is defined, but isn't attached to a cardinput.
Schedules Direct Broadcast is defined, but isn't attached to a cardinput.
2008-06-01 11:39:03.213 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-06-01 11:39:03.214 Main::Registering HttpStatus Extension
2008-06-01 11:39:03.215 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-06-01 11:39:03.216 Enabled verbose msgs:  important general
2008-06-01 11:39:03.219 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 11:39:06.155 Reschedule requested for id -1.
2008-06-01 11:39:06.190 Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2008-06-01 11:39:06.197 Seem to be woken up by USER
2008-06-01 11:39:39.573 MainServer::HandleAnnounce Monitor
2008-06-01 11:39:39.575 adding: magicvoice as a client (events: 0)
2008-06-01 11:39:39.577 MainServer::HandleAnnounce Monitor
2008-06-01 11:39:39.578 adding: magicvoice as a client (events: 1)
2008-06-01 11:39:39.584 MainServer::HandleAnnounce Playback
2008-06-01 11:39:39.585 adding: magicvoice as a client (events: 0)
2008-06-01 11:39:39.588 TVRec(1): Changing from None to WatchingLiveTV
2008-06-01 11:39:39.598 TVRec(1): HW Tuner: 1->1
2008-06-01 11:39:40.748 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-06-01 11:39:41.241 Finished recording Unknown: channel 1021
2008-06-01 11:39:42.430 Finished recording Unknown: channel 1021
2008-06-01 11:39:42.649 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-06-01 11:39:42.964 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-01 11:39:42.973 Empty LocalHostName.
2008-06-01 11:39:42.973 Using localhost value of magicvoice
2008-06-01 11:39:42.986 New DB connection, total: 1
2008-06-01 11:39:42.993 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:39:42.997 Closing DB connection named 'DBManager0'
2008-06-01 11:39:42.998 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:39:43.001 New DB connection, total: 2
2008-06-01 11:39:43.002 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:39:43.008 Current Schema Version: 1214
2008-06-01 11:39:43.027 Preview Error: Previewer file '/home/mythos/mythos/1021_20080601113939.mpg' is not valid.
2008-06-01 11:39:43.030 Preview Error: Run() file not local: '/home/mythos/mythos/1021_20080601113939.mpg'
2008-06-01 11:39:43.039 Preview Error: Preview process not ok.
			fileinfo(/home/mythos/mythos/1021_20080601113939.mpg.png) exists: 0 readable: 0 size: 0
2008-06-01 11:39:58.712 TVRec(1): Changing from WatchingLiveTV to None
2008-06-01 11:39:58.970 Finished recording Unknown: channel 1021
2008-06-01 11:40:23.157 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 11:42:23.186 Expiring 0 MBytes for 1021 @ Sun Jun 1 11:39:39 2008 => Unknown
2008-06-01 11:55:23.216 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-01 12:10:23.252 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

```


Frontend log:
```
Starting mythfrontend.real..
2008-05-31 04:10:40.133 New DB connection, total: 2
2008-05-31 04:10:40.133 Connected to database 'mythconverg' at host: localhost
2008-05-31 04:10:40.138 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-05-31 04:10:40.138 Enabled verbose msgs:  important general
2008-05-31 04:10:41.268 Unable to parse themeinfo.xml for glass-wide
2008-05-31 04:10:41.269 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-31 04:10:42.835 Unable to parse themeinfo.xml for glass-wide
2008-05-31 04:10:42.835 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-31 04:10:45.001 Writing settings file /home/mythos/.mythtv/mysql.txt
2008-05-31 04:10:45.002 Closing DB connection named 'DBManager1'
2008-05-31 04:10:45.002 Closing DB connection named 'DBManager0'
2008-05-31 04:10:45.003 Connected to database 'mythconverg' at host: localhost
2008-05-31 04:10:45.115 Primary screen 0.
2008-05-31 04:10:45.116 Using screen 0, 1920x1080 at 0,0
2008-05-31 04:10:45.119 Switching to square mode (Mythbuntu-8.04)
2008-05-31 04:10:45.179 Using the Qt painter
2008-05-31 04:10:45.182 lirc init success using configuration file: /home/mythos/.mythtv/lircrc
2008-05-31 04:10:45.182 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythos/.mythtv/joystickmenurc
2008-05-31 04:12:16.945 Specified base font 'medium' does not exist for font clock
2008-05-31 04:12:16.946 Specified base font 'medium' does not exist for font small
2008-05-31 04:12:16.946 Specified base font 'medium' does not exist for font medium
2008-05-31 04:12:16.946 Specified base font 'medium' does not exist for font large
2008-05-31 04:12:16.950 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-05-31 04:12:17.176 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-05-31 04:12:17.448 Registering Internal as a media playback plugin.
2008-05-31 04:12:17.512 Upgrading to MythArchive schema version 1001
2008-05-31 04:12:17.523 Connected to database 'mythconverg' at host: localhost
2008-05-31 04:12:17.638 Inserting MythFlix initial database information.
2008-05-31 04:12:17.638 Upgrading to MythFlix schema version 1000
2008-05-31 04:12:17.647 Upgrading to MythFlix schema version 1001
2008-05-31 04:12:17.816 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-05-31 04:12:17.842 Setting Up MythMovies Database Tables
2008-05-31 04:12:17.851 MythMovies Database Setup Complete
2008-05-31 04:12:18.168 Upgrading to MythMusic schema version 1007
2008-05-31 04:12:18.173 Upgrading to MythMusic schema version 1008
2008-05-31 04:12:18.192 Upgrading to MythMusic schema version 1009
2008-05-31 04:12:18.197 Upgrading to MythMusic schema version 1010
2008-05-31 04:12:18.202 Updating music_albumart image types
2008-05-31 04:12:18.206 Upgrading to MythMusic schema version 1011
2008-05-31 04:12:18.208 Upgrading to MythMusic schema version 1012
2008-05-31 04:12:18.232 Upgrading to MythMusic schema version 1013
2008-05-31 04:12:18.275 Failed to run 'cdrecord --scanbus'
2008-05-31 04:12:18.279 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-05-31 04:12:18.282 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-05-31 04:12:18.429 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP: Creating autogen directory entry for this host
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-05-31 04:12:18.994 Inserting MythWeather initial database information.
2008-05-31 04:12:18.994 Upgrading to MythWeather schema version 1000
2008-05-31 04:12:23.770 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-31 04:12:23.771 Using protocol version 40
2008-05-31 04:12:26.141 Deleting UPnP client...
2008-05-31 04:12:26.142 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2008-05-31 22:45:55.719 New DB connection, total: 2
2008-05-31 22:45:55.720 Connected to database 'mythconverg' at host: localhost
2008-05-31 22:45:55.748 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-05-31 22:45:55.748 Enabled verbose msgs:  important general
2008-05-31 22:45:56.172 Unable to parse themeinfo.xml for glass-wide
2008-05-31 22:45:56.173 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-31 22:45:56.723 Unable to parse themeinfo.xml for glass-wide
2008-05-31 22:45:56.723 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-31 22:45:57.499 Primary screen 0.
2008-05-31 22:45:57.501 Using screen 0, 1920x1080 at 0,0
2008-05-31 22:45:57.504 Switching to square mode (Mythbuntu-8.04)
2008-05-31 22:45:57.550 Using the Qt painter
2008-05-31 22:45:57.550 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythos/.mythtv/joystickmenurc
2008-05-31 22:45:57.572 lirc init success using configuration file: /home/mythos/.mythtv/lircrc
2008-05-31 22:46:00.546 Specified base font 'medium' does not exist for font clock
2008-05-31 22:46:00.547 Specified base font 'medium' does not exist for font small
2008-05-31 22:46:00.547 Specified base font 'medium' does not exist for font medium
2008-05-31 22:46:00.547 Specified base font 'medium' does not exist for font large
2008-05-31 22:46:00.551 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-05-31 22:46:00.805 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-05-31 22:46:00.971 Registering Internal as a media playback plugin.
2008-05-31 22:46:01.205 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-05-31 22:46:01.563 Failed to run 'cdrecord --scanbus'
2008-05-31 22:46:01.567 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-05-31 22:46:01.572 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-05-31 22:46:01.654 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-05-31 22:46:06.254 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-31 22:46:06.255 Using protocol version 40
2008-05-31 22:46:06.409 TV: Attempting to change from None to WatchingLiveTV
2008-05-31 22:46:06.410 Using protocol version 40
2008-05-31 22:46:08.217 GetEntryAt(-1) failed.
2008-05-31 22:46:08.218 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2008-05-31 22:46:08.219 TV Error: LiveTV not successfully started
2008-05-31 22:46:08.219 TV Error: LiveTV not successfully started
2008-05-31 22:46:08.308 TV: Deleting TV Chain in destructor
2008-05-31 22:46:08.352 DPMS Deactivated 
2008-05-31 22:46:08.353 DPMS Reactivated.
2008-05-31 22:46:20.784 Deleting UPnP client...
Starting mythfrontend.real..
2008-05-31 22:48:53.568 New DB connection, total: 2
2008-05-31 22:48:53.568 Connected to database 'mythconverg' at host: localhost
2008-05-31 22:48:53.571 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-05-31 22:48:53.571 Enabled verbose msgs:  important general
2008-05-31 22:48:53.617 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-05-31 22:48:54.646 Unable to parse themeinfo.xml for glass-wide
2008-05-31 22:48:54.646 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-31 22:48:56.112 Unable to parse themeinfo.xml for glass-wide
2008-05-31 22:48:56.129 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-31 22:48:57.559 Primary screen 0.
2008-05-31 22:48:57.560 Using screen 0, 1920x1080 at 0,0
2008-05-31 22:48:57.563 Switching to square mode (Mythbuntu-8.04)
2008-05-31 22:48:57.587 Using the Qt painter
2008-05-31 22:48:57.589 lirc init success using configuration file: /home/mythos/.mythtv/lircrc
2008-05-31 22:48:57.590 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythos/.mythtv/joystickmenurc
2008-05-31 22:49:00.456 Specified base font 'medium' does not exist for font clock
2008-05-31 22:49:00.457 Specified base font 'medium' does not exist for font small
2008-05-31 22:49:00.457 Specified base font 'medium' does not exist for font medium
2008-05-31 22:49:00.457 Specified base font 'medium' does not exist for font large
2008-05-31 22:49:00.459 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-05-31 22:49:00.727 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-05-31 22:49:00.894 Registering Internal as a media playback plugin.
2008-05-31 22:49:01.113 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-05-31 22:49:01.443 Failed to run 'cdrecord --scanbus'
2008-05-31 22:49:01.447 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-05-31 22:49:01.450 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-05-31 22:49:01.519 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-05-31 22:49:09.547 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-31 22:49:09.549 Using protocol version 40
2008-05-31 22:49:09.561 TV: Attempting to change from None to WatchingLiveTV
2008-05-31 22:49:09.562 Using protocol version 40
2008-05-31 22:49:10.815 GetEntryAt(-1) failed.
2008-05-31 22:49:10.817 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2008-05-31 22:49:10.817 TV Error: LiveTV not successfully started
2008-05-31 22:49:10.818 TV Error: LiveTV not successfully started
2008-05-31 22:49:10.826 TV: Deleting TV Chain in destructor
2008-05-31 22:49:10.834 DPMS Deactivated 
2008-05-31 22:49:10.836 DPMS Reactivated.
2008-05-31 22:59:21.542 Deleting UPnP client...
Starting mythfrontend.real..
2008-06-01 00:03:21.847 New DB connection, total: 2
2008-06-01 00:03:21.847 Connected to database 'mythconverg' at host: localhost
2008-06-01 00:03:21.851 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-06-01 00:03:21.851 Enabled verbose msgs:  important general
2008-06-01 00:03:21.982 Unable to parse themeinfo.xml for glass-wide
2008-06-01 00:03:21.982 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-01 00:03:22.191 Unable to parse themeinfo.xml for glass-wide
2008-06-01 00:03:22.191 The theme (glass-wide) is missing a themeinfo.xml file

2008-06-01 00:03:22.521 Primary screen 0.
2008-06-01 00:03:22.522 Using screen 0, 1920x1080 at 0,0
2008-06-01 00:03:22.525 Switching to square mode (Mythbuntu-8.04)
2008-06-01 00:03:22.546 Using the Qt painter
2008-06-01 00:03:22.548 lirc init success using configuration file: /home/mythos/.mythtv/lircrc
2008-06-01 00:03:22.548 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythos/.mythtv/joystickmenurc
2008-06-01 00:03:24.645 Specified base font 'medium' does not exist for font clock
2008-06-01 00:03:24.645 Specified base font 'medium' does not exist for font small
2008-06-01 00:03:24.645 Specified base font 'medium' does not exist for font medium
2008-06-01 00:03:24.645 Specified base font 'medium' does not exist for font large
2008-06-01 00:03:24.647 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-06-01 00:03:24.857 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-06-01 00:03:24.944 Registering Internal as a media playback plugin.
2008-06-01 00:03:25.040 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-06-01 00:03:25.099 Failed to run 'cdrecord --scanbus'
2008-06-01 00:03:25.103 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-06-01 00:03:25.106 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-06-01 00:03:25.164 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-06-01 00:03:40.615 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-06-01 00:03:40.616 Using protocol version 40
2008-06-01 00:03:40.630 TV: Attempting to change from None to WatchingLiveTV
2008-06-01 00:03:40.631 Using protocol version 40
2008-06-01 00:03:41.832 GetEntryAt(-1) failed.
2008-06-01 00:03:41.834 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2008-06-01 00:03:41.835 TV Error: LiveTV not successfully started
2008-06-01 00:03:41.835 TV Error: LiveTV not successfully started
2008-06-01 00:03:41.869 TV: Deleting TV Chain in destructor
2008-06-01 00:03:41.876 DPMS Deactivated 
2008-06-01 00:03:41.877 DPMS Reactivated.
ICE default IO error handler doing an exit(), pid = 6567, errno = 11
Starting mythfrontend.real..
2008-06-01 10:05:52.953 New DB connection, total: 2
2008-06-01 10:05:52.962 Connected to database 'mythconverg' at host: localhost
2008-06-01 10:05:52.965 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-06-01 10:05:52.966 Enabled verbose msgs:  important general
2008-06-01 10:05:53.890 Unable to parse themeinfo.xml for glass-wide
2008-06-01 10:05:53.890 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-01 10:05:55.548 Unable to parse themeinfo.xml for glass-wide
2008-06-01 10:05:55.548 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-01 10:05:57.414 Primary screen 0.
2008-06-01 10:05:57.414 Using screen 0, 1920x1080 at 0,0
2008-06-01 10:05:57.417 Switching to square mode (Mythbuntu-8.04)
2008-06-01 10:05:57.447 Using the Qt painter
2008-06-01 10:05:57.449 lirc init success using configuration file: /home/mythos/.mythtv/lircrc
2008-06-01 10:05:57.450 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythos/.mythtv/joystickmenurc
2008-06-01 10:06:00.644 Specified base font 'medium' does not exist for font clock
2008-06-01 10:06:00.644 Specified base font 'medium' does not exist for font small
2008-06-01 10:06:00.645 Specified base font 'medium' does not exist for font medium
2008-06-01 10:06:00.645 Specified base font 'medium' does not exist for font large
2008-06-01 10:06:00.647 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-06-01 10:06:00.914 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-06-01 10:06:01.080 Registering Internal as a media playback plugin.
2008-06-01 10:06:01.301 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-06-01 10:06:01.660 Failed to run 'cdrecord --scanbus'
2008-06-01 10:06:01.663 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-06-01 10:06:01.667 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-06-01 10:06:01.736 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-06-01 10:06:26.295 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-06-01 10:06:26.311 Using protocol version 40
2008-06-01 10:06:26.331 Received a remote 'Clear Cache' request
2008-06-01 10:06:27.189 Unable to parse themeinfo.xml for glass-wide
2008-06-01 10:06:27.189 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-01 10:06:31.346 Received a remote 'Clear Cache' request
2008-06-01 10:06:35.006 Unable to parse themeinfo.xml for glass-wide
2008-06-01 10:06:35.006 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-01 10:06:37.749 Received a remote 'Clear Cache' request
2008-06-01 10:06:42.000 Loading from: /usr/share/mythtv/themes/default/appear-ui.xml
2008-06-01 10:07:30.709 Received a remote 'Clear Cache' request
2008-06-01 10:07:35.594 Unable to parse themeinfo.xml for glass-wide
2008-06-01 10:07:35.594 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-01 10:07:51.769 Received a remote 'Clear Cache' request
2008-06-01 10:08:09.533 Received a remote 'Clear Cache' request
2008-06-01 10:08:20.268 Failed to run 'cdrecord --scanbus'
2008-06-01 10:08:20.304 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-06-01 10:08:20.314 Failed to run 'cdrecord --scanbus -dev=ATAPI'

(gksudo:6304): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:6304): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:6304): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Reading package lists... Done
Building dependency tree       
Reading state information... Done
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:205: GtkWarning: gtk_file_folder_unix_get_info: assertion `strcmp (dirname, folder_unix->filename) == 0' failed
  gtk.main()
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS2008-06-01 10:11:09.258 Received a remote 'Clear Cache' request
2008-06-01 10:11:16.686 TV: Attempting to change from None to WatchingLiveTV
2008-06-01 10:11:16.687 Using protocol version 40
2008-06-01 10:11:18.269 GetEntryAt(-1) failed.
2008-06-01 10:11:18.270 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2008-06-01 10:11:18.271 TV Error: LiveTV not successfully started
2008-06-01 10:11:18.292 TV Error: LiveTV not successfully started
2008-06-01 10:11:18.380 TV: Deleting TV Chain in destructor
2008-06-01 10:11:18.398 DPMS Deactivated 
2008-06-01 10:11:18.399 DPMS Reactivated.
2008-06-01 10:11:21.437 Deleting UPnP client...
Starting mythfrontend.real..
2008-06-01 11:33:21.301 New DB connection, total: 2
2008-06-01 11:33:21.301 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:33:21.308 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-06-01 11:33:21.309 Enabled verbose msgs:  important general
2008-06-01 11:33:22.504 Unable to parse themeinfo.xml for glass-wide
2008-06-01 11:33:22.505 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-01 11:33:23.830 Unable to parse themeinfo.xml for glass-wide
2008-06-01 11:33:23.830 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-01 11:33:25.770 Primary screen 0.
2008-06-01 11:33:25.771 Using screen 0, 1920x1080 at 0,0
2008-06-01 11:33:25.774 Switching to square mode (Mythbuntu-8.04)
2008-06-01 11:33:25.804 Using the Qt painter
2008-06-01 11:33:25.806 lirc init success using configuration file: /home/mythos/.mythtv/lircrc
2008-06-01 11:33:25.807 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythos/.mythtv/joystickmenurc
2008-06-01 11:33:28.866 Specified base font 'medium' does not exist for font clock
2008-06-01 11:33:28.866 Specified base font 'medium' does not exist for font small
2008-06-01 11:33:28.866 Specified base font 'medium' does not exist for font medium
2008-06-01 11:33:28.866 Specified base font 'medium' does not exist for font large
2008-06-01 11:33:28.869 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-06-01 11:33:29.138 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-06-01 11:33:29.311 Registering Internal as a media playback plugin.
2008-06-01 11:33:29.549 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-06-01 11:33:29.894 Failed to run 'cdrecord --scanbus'
2008-06-01 11:33:29.898 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-06-01 11:33:29.901 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-06-01 11:33:29.970 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-06-01 11:33:35.757 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-06-01 11:33:35.759 Using protocol version 40
2008-06-01 11:33:35.771 TV: Attempting to change from None to WatchingLiveTV
2008-06-01 11:33:35.772 Using protocol version 40
2008-06-01 11:33:37.029 GetEntryAt(-1) failed.
2008-06-01 11:33:37.030 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2008-06-01 11:33:37.030 TV Error: LiveTV not successfully started
2008-06-01 11:33:37.031 TV Error: LiveTV not successfully started
2008-06-01 11:33:37.121 TV: Deleting TV Chain in destructor
2008-06-01 11:33:37.127 DPMS Deactivated 
2008-06-01 11:33:37.128 DPMS Reactivated.
2008-06-01 11:34:07.336 Deleting UPnP client...
Starting mythfrontend.real..
2008-06-01 11:39:31.844 New DB connection, total: 2
2008-06-01 11:39:31.844 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:39:31.847 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-06-01 11:39:31.847 Enabled verbose msgs:  important general
2008-06-01 11:39:31.980 Unable to parse themeinfo.xml for glass-wide
2008-06-01 11:39:31.980 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-01 11:39:32.193 Unable to parse themeinfo.xml for glass-wide
2008-06-01 11:39:32.193 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-01 11:39:32.520 Primary screen 0.
2008-06-01 11:39:32.521 Using screen 0, 1920x1080 at 0,0
2008-06-01 11:39:32.524 Switching to square mode (Mythbuntu-8.04)
2008-06-01 11:39:32.545 Using the Qt painter
2008-06-01 11:39:32.547 lirc init success using configuration file: /home/mythos/.mythtv/lircrc
2008-06-01 11:39:32.547 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythos/.mythtv/joystickmenurc
2008-06-01 11:39:34.736 Specified base font 'medium' does not exist for font clock
2008-06-01 11:39:34.736 Specified base font 'medium' does not exist for font small
2008-06-01 11:39:34.736 Specified base font 'medium' does not exist for font medium
2008-06-01 11:39:34.736 Specified base font 'medium' does not exist for font large
2008-06-01 11:39:34.738 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-06-01 11:39:34.951 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-06-01 11:39:35.036 Registering Internal as a media playback plugin.
2008-06-01 11:39:35.136 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-06-01 11:39:35.195 Failed to run 'cdrecord --scanbus'
2008-06-01 11:39:35.199 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-06-01 11:39:35.202 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-06-01 11:39:35.261 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-06-01 11:39:39.570 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-06-01 11:39:39.572 Using protocol version 40
2008-06-01 11:39:39.583 TV: Attempting to change from None to WatchingLiveTV
2008-06-01 11:39:39.584 Using protocol version 40
2008-06-01 11:39:40.806 New DB connection, total: 3
2008-06-01 11:39:40.807 Connected to database 'mythconverg' at host: localhost
2008-06-01 11:39:40.820 DPMS Deactivated 
2008-06-01 11:39:40.857 NVP: Disabling Audio, params(-1,2,44100)
2008-06-01 11:39:40.937 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-06-01 11:39:41.040 OSD Theme Dimensions W: 640 H: 480
2008-06-01 11:39:42.531 TV: Changing from None to WatchingLiveTV
2008-06-01 11:39:42.540 Realtime priority would require SUID as root.
2008-06-01 11:39:42.635 Video timing method: USleep with busy wait
2008-06-01 11:39:43.783 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2008-06-01 11:39:45.626 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2008-06-01 11:39:45.626 VideoOutputXv: ProcessFrameXvMC: Called without frame
2008-06-01 11:39:45.628 AFD: Opened codec 0x8668dc0, id(MPEG2VIDEO_XVMC) type(Video)
2008-06-01 11:39:45.628 AFD: codec AC3 has 6 channels
2008-06-01 11:39:45.629 AFD: Opened codec 0x85531e0, id(AC3) type(Audio)
2008-06-01 11:39:45.637 Opening audio device 'default'. ch 2(2) sr 48000
2008-06-01 11:39:45.637 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-06-01 11:39:45.716 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2008-06-01 11:39:45.718 NVP: Enabling Audio
2008-06-01 11:39:45.729 XvMC: picture structure FRAME
2008-06-01 11:39:46.158 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:39:47.489 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:39:48.819 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:39:50.151 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:39:51.481 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:39:52.812 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:39:54.142 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:39:55.474 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:39:56.804 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:39:58.135 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:39:58.663 TV: Attempting to change from WatchingLiveTV to None
2008-06-01 11:39:59.465 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:00.795 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:02.126 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:03.456 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:04.787 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:06.117 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:07.447 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:08.778 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:10.108 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:11.438 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:12.769 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:14.099 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:15.429 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:16.760 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:18.090 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:19.420 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:20.751 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:22.081 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:23.411 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:24.742 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:26.072 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:27.403 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:28.733 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:30.063 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:31.394 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:32.724 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:34.054 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:35.385 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:36.715 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:38.045 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:39.376 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:40.706 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:42.036 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:43.367 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:44.697 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:46.027 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:47.358 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:48.688 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:50.019 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:51.349 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:52.679 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:54.010 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:55.340 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:56.670 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:58.001 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:40:59.331 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:00.661 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:01.992 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:03.322 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:04.652 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:05.983 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:07.313 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:08.643 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:09.974 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:11.304 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:12.634 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:13.965 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:15.295 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:16.625 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:17.956 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:19.286 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:20.616 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:21.947 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:23.277 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:24.608 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:25.938 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:27.268 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:28.599 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:29.929 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:31.259 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:32.590 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:33.920 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:35.250 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:36.581 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:37.911 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:39.241 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:40.572 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:41.902 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:43.233 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:44.563 NVP: Prebuffer wait timed out 10 times.
2008-06-01 11:41:45.893 NVP: Prebuffer wait timed out 10 times.

```

Thanks in advance.

---

### Post by UltramaticOrange on 2008-06-01
Switched from nvidia-glx to nvidia-glx-legacy fixed the problem.

digital channels are breaking up a bit. Any advice?

---

