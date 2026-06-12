---
title: "MythTV No Live TV"
date: 2009-01-04
forum: Mythbuntu
---

### Post by nisbet on 2009-01-04
I just installed Mythbuntu on my HP m7560n, it has a Conexant Falcon II TV tuner and I installed ivtv drivers.  When setting up MythTV everything seemed to be going fine, it even scanned the channels and detected signal on channels 2-75 (which is correct), but when I tried to activate live tv the screen goes blank for about 60 seconds and then returns to the main menu.  Any thoughts on what might be going on here?

---

### Post by murbanci on 2009-01-04
Can you post the output of the logs.  /var/log/mythtv/mythfrontend.log and mythbackend.log

---

### Post by nisbet on 2009-01-04
Mythbackend Log:
2009-01-04 17:58:41.032 Using runtime prefix = /usr
2009-01-04 17:58:41.089 Empty LocalHostName.
2009-01-04 17:58:41.106 Using localhost value of Griffindor
2009-01-04 17:58:41.215 New DB connection, total: 1
2009-01-04 17:58:41.251 Connected to database 'mythconverg' at host: localhost
2009-01-04 17:58:41.312 Closing DB connection named 'DBManager0'
2009-01-04 17:58:41.316 Connected to database 'mythconverg' at host: localhost
2009-01-04 17:58:41.318 New DB connection, total: 2
2009-01-04 17:58:41.321 Connected to database 'mythconverg' at host: localhost
2009-01-04 17:58:41.365 Current Schema Version: 1214
Starting up as the master server.
2009-01-04 17:58:41.470 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 17:58:42.599 ChannelBase(1) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-01-04 17:58:42.843 New DB connection, total: 3
2009-01-04 17:58:42.865 Connected to database 'mythconverg' at host: localhost
2009-01-04 17:58:42.953 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-04 17:58:42.960 Main::Registering HttpStatus Extension
2009-01-04 17:58:42.992 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 17:58:42.994 Enabled verbose msgs:  important general
2009-01-04 17:58:43.065 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 17:59:12.010 MainServer::HandleAnnounce Monitor
2009-01-04 17:59:12.014 adding: Griffindor as a client (events: 0)
2009-01-04 17:59:12.015 MainServer::HandleAnnounce Monitor
2009-01-04 17:59:12.016 adding: Griffindor as a client (events: 1)
2009-01-04 18:00:02.821 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 18:15:03.009 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 18:18:07.954 MainServer::HandleAnnounce Monitor
2009-01-04 18:18:07.956 adding: Griffindor as a client (events: 0)
2009-01-04 18:18:07.957 MainServer::HandleAnnounce Monitor
2009-01-04 18:18:07.958 adding: Griffindor as a client (events: 1)
2009-01-04 18:21:14.146 MainServer::HandleAnnounce Monitor
2009-01-04 18:21:14.148 adding: Griffindor as a client (events: 0)
2009-01-04 18:21:14.149 MainServer::HandleAnnounce Monitor
2009-01-04 18:21:14.150 adding: Griffindor as a client (events: 1)
2009-01-04 18:23:51.007 Using runtime prefix = /usr
2009-01-04 18:23:51.065 Empty LocalHostName.
2009-01-04 18:23:51.072 Using localhost value of Griffindor
2009-01-04 18:23:51.166 New DB connection, total: 1
2009-01-04 18:23:51.209 Connected to database 'mythconverg' at host: localhost
2009-01-04 18:23:51.262 Closing DB connection named 'DBManager0'
2009-01-04 18:23:51.303 Connected to database 'mythconverg' at host: localhost
2009-01-04 18:23:51.306 New DB connection, total: 2
2009-01-04 18:23:51.308 Connected to database 'mythconverg' at host: localhost
2009-01-04 18:23:51.373 Current Schema Version: 1214
Starting up as the master server.
2009-01-04 18:23:51.528 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 18:23:52.687 ChannelBase(1) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-01-04 18:23:52.728 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-04 18:23:52.729 Main::Registering HttpStatus Extension
2009-01-04 18:23:52.729 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 18:23:52.730 Enabled verbose msgs:  important general
2009-01-04 18:23:52.748 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 18:24:15.950 MainServer::HandleAnnounce Monitor
2009-01-04 18:24:15.951 adding: Griffindor as a client (events: 0)
2009-01-04 18:24:15.952 MainServer::HandleAnnounce Monitor
2009-01-04 18:24:15.953 adding: Griffindor as a client (events: 1)
2009-01-04 18:25:12.697 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 18:37:04.289 MainServer::HandleAnnounce Monitor
2009-01-04 18:37:04.291 adding: Griffindor as a client (events: 0)
2009-01-04 18:37:04.292 MainServer::HandleAnnounce Monitor
2009-01-04 18:37:04.292 adding: Griffindor as a client (events: 1)
2009-01-04 18:41:26.194 Using runtime prefix = /usr
2009-01-04 18:41:26.344 Empty LocalHostName.
2009-01-04 18:41:26.344 Using localhost value of Griffindor
2009-01-04 18:41:26.351 New DB connection, total: 1
2009-01-04 18:41:26.357 Connected to database 'mythconverg' at host: localhost
2009-01-04 18:41:26.379 Closing DB connection named 'DBManager0'
2009-01-04 18:41:26.382 Connected to database 'mythconverg' at host: localhost
2009-01-04 18:41:26.396 New DB connection, total: 2
2009-01-04 18:41:26.397 Connected to database 'mythconverg' at host: localhost
2009-01-04 18:41:26.405 Current Schema Version: 1214
Starting up as the master server.
2009-01-04 18:41:26.411 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 18:41:26.412 ChannelBase(1) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-01-04 18:41:26.423 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-04 18:41:26.423 Main::Registering HttpStatus Extension
2009-01-04 18:41:26.431 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 18:41:26.438 Enabled verbose msgs:  important general
2009-01-04 18:41:26.447 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 18:41:37.598 MainServer::HandleAnnounce Monitor
2009-01-04 18:41:37.601 adding: Griffindor as a client (events: 0)
2009-01-04 18:41:37.602 MainServer::HandleAnnounce Monitor
2009-01-04 18:41:37.602 adding: Griffindor as a client (events: 1)
2009-01-04 18:42:46.416 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 18:43:05.742 MainServer::HandleAnnounce Monitor
2009-01-04 18:43:05.748 adding: Griffindor as a client (events: 0)
2009-01-04 18:43:05.750 MainServer::HandleAnnounce Monitor
2009-01-04 18:43:05.751 adding: Griffindor as a client (events: 1)
2009-01-04 18:57:46.497 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 19:04:13.774 MainServer::HandleAnnounce Monitor
2009-01-04 19:04:13.780 adding: Griffindor as a client (events: 0)
2009-01-04 19:04:13.781 MainServer::HandleAnnounce Monitor
2009-01-04 19:04:13.781 adding: Griffindor as a client (events: 1)
2009-01-04 19:04:13.782 Reloading backend settings
2009-01-04 19:08:42.802 Using runtime prefix = /usr
2009-01-04 19:08:42.831 Empty LocalHostName.
2009-01-04 19:08:42.832 Using localhost value of Griffindor
2009-01-04 19:08:42.839 New DB connection, total: 1
2009-01-04 19:08:42.854 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:08:42.856 Closing DB connection named 'DBManager0'
2009-01-04 19:08:42.867 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:08:42.870 New DB connection, total: 2
2009-01-04 19:08:42.871 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:08:42.873 Current Schema Version: 1214
Starting up as the master server.
2009-01-04 19:08:42.895 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 19:08:42.920 ChannelBase(1) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-01-04 19:08:42.922 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 19:08:42.923 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2009-01-04 19:08:42.935 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-04 19:08:42.936 Main::Registering HttpStatus Extension
2009-01-04 19:08:42.936 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 19:08:42.937 Enabled verbose msgs:  important general
2009-01-04 19:08:42.939 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 19:08:55.282 MainServer::HandleAnnounce Monitor
2009-01-04 19:08:55.288 adding: Griffindor as a client (events: 0)
2009-01-04 19:08:55.289 MainServer::HandleAnnounce Monitor
2009-01-04 19:08:55.290 adding: Griffindor as a client (events: 1)
2009-01-04 19:09:13.583 MainServer::HandleAnnounce Monitor
2009-01-04 19:09:13.592 adding: Griffindor as a client (events: 0)
2009-01-04 19:09:13.593 MainServer::HandleAnnounce Monitor
2009-01-04 19:09:13.594 adding: Griffindor as a client (events: 1)
2009-01-04 19:10:02.928 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 19:16:58.366 Using runtime prefix = /usr
2009-01-04 19:16:58.533 Empty LocalHostName.
2009-01-04 19:16:58.534 Using localhost value of Griffindor
2009-01-04 19:16:58.541 New DB connection, total: 1
2009-01-04 19:16:58.546 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:16:58.547 Closing DB connection named 'DBManager0'
2009-01-04 19:16:58.548 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:16:58.553 New DB connection, total: 2
2009-01-04 19:16:58.554 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:16:58.558 Current Schema Version: 1214
Starting up as the master server.
2009-01-04 19:16:58.567 New DB connection, total: 3
2009-01-04 19:16:58.568 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:16:58.618 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 19:16:58.621 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-01-04 19:16:58.636 New DB scheduler connection
2009-01-04 19:16:58.637 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:16:58.651 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-04 19:16:58.652 Main::Registering HttpStatus Extension
2009-01-04 19:16:58.659 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 19:16:58.667 Enabled verbose msgs:  important general
2009-01-04 19:16:58.676 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 19:17:01.646 Reschedule requested for id -1.
2009-01-04 19:17:01.671 Scheduled 0 items in 0.0 = 0.00 match + 0.02 place
2009-01-04 19:17:01.679 Seem to be woken up by USER
2009-01-04 19:17:04.950 MainServer::HandleAnnounce Monitor
2009-01-04 19:17:04.953 adding: Griffindor as a client (events: 0)
2009-01-04 19:17:04.954 MainServer::HandleAnnounce Monitor
2009-01-04 19:17:04.955 adding: Griffindor as a client (events: 1)
2009-01-04 19:17:04.956 Reschedule requested for id -1.
2009-01-04 19:17:04.982 Scheduled 0 items in 0.0 = 0.02 match + 0.01 place
2009-01-04 19:17:23.532 MainServer::HandleAnnounce Monitor
2009-01-04 19:17:23.538 adding: Griffindor as a client (events: 0)
2009-01-04 19:17:23.539 MainServer::HandleAnnounce Monitor
2009-01-04 19:17:23.540 adding: Griffindor as a client (events: 1)
2009-01-04 19:17:28.005 MainServer::HandleAnnounce Playback
2009-01-04 19:17:28.018 adding: Griffindor as a client (events: 0)
2009-01-04 19:17:28.021 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 19:17:28.025 TVRec(1): HW Tuner: 1->1
2009-01-04 19:17:29.165 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-01-04 19:17:29.166 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 19:17:29.184 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 19:17:29.189 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-01-04 19:18:09.196 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 19:18:09.204 Finished recording Unknown: channel 1002
2009-01-04 19:18:12.615 MainServer::HandleAnnounce Playback
2009-01-04 19:18:12.619 adding: Griffindor as a client (events: 0)
2009-01-04 19:18:12.621 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 19:18:12.626 TVRec(1): HW Tuner: 1->1
2009-01-04 19:18:13.678 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-01-04 19:18:13.679 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 19:18:13.695 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 19:18:13.699 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-01-04 19:18:18.645 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 19:18:53.702 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 19:18:53.710 Finished recording Unknown: channel 1002
2009-01-04 19:26:08.669 Using runtime prefix = /usr
2009-01-04 19:26:08.828 Empty LocalHostName.
2009-01-04 19:26:08.829 Using localhost value of Griffindor
2009-01-04 19:26:08.835 New DB connection, total: 1
2009-01-04 19:26:08.841 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:26:08.847 Closing DB connection named 'DBManager0'
2009-01-04 19:26:08.849 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:26:08.850 New DB connection, total: 2
2009-01-04 19:26:08.852 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:26:08.854 Current Schema Version: 1214
Starting up as the master server.
2009-01-04 19:26:08.875 New DB connection, total: 3
2009-01-04 19:26:08.877 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:26:08.919 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 19:26:08.920 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-01-04 19:26:08.921 New DB scheduler connection
2009-01-04 19:26:08.922 Connected to database 'mythconverg' at host: localhost
Cable is defined, but isn't attached to a cardinput.
2009-01-04 19:26:08.933 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-04 19:26:08.934 Main::Registering HttpStatus Extension
2009-01-04 19:26:08.943 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 19:26:08.951 Enabled verbose msgs:  important general
2009-01-04 19:26:08.960 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 19:26:11.927 Reschedule requested for id -1.
2009-01-04 19:26:11.960 Scheduled 0 items in 0.0 = 0.02 match + 0.02 place
2009-01-04 19:26:11.966 Seem to be woken up by USER
2009-01-04 19:26:14.889 MainServer::HandleAnnounce Monitor
2009-01-04 19:26:14.893 adding: Griffindor as a client (events: 0)
2009-01-04 19:26:14.894 MainServer::HandleAnnounce Monitor
2009-01-04 19:26:14.895 adding: Griffindor as a client (events: 1)
2009-01-04 19:26:14.896 Reschedule requested for id -1.
2009-01-04 19:26:14.906 MythSocket(8909200:-1): writeStringList: Error, socket went unconnected.
2009-01-04 19:26:14.917 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-01-04 19:26:28.927 Expiring 0 MBytes for 1002 @ Sun Jan 4 19:17:28 2009 => Unknown
2009-01-04 19:26:28.936 Expiring 0 MBytes for 1002 @ Sun Jan 4 19:18:12 2009 => Unknown
2009-01-04 19:26:39.871 MainServer::HandleAnnounce Monitor
2009-01-04 19:26:39.877 adding: Griffindor as a client (events: 0)
2009-01-04 19:26:39.878 MainServer::HandleAnnounce Monitor
2009-01-04 19:26:39.878 adding: Griffindor as a client (events: 1)
2009-01-04 19:26:39.883 MainServer::HandleAnnounce Playback
2009-01-04 19:26:39.884 adding: Griffindor as a client (events: 0)
2009-01-04 19:26:39.885 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 19:26:39.888 TVRec(1): HW Tuner: 1->1
2009-01-04 19:26:39.921 New DB connection, total: 4
2009-01-04 19:26:39.923 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:26:40.974 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-01-04 19:26:40.975 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 19:26:40.994 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 19:26:40.996 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-01-04 19:27:21.002 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 19:27:21.018 Finished recording Unknown: channel 1002
2009-01-04 19:27:27.590 MainServer::HandleAnnounce Playback
2009-01-04 19:27:27.595 adding: Griffindor as a client (events: 0)
2009-01-04 19:27:27.596 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 19:27:27.601 TVRec(1): HW Tuner: 1->1
2009-01-04 19:27:28.660 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-01-04 19:27:28.661 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 19:27:28.677 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 19:27:28.679 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-01-04 19:27:28.942 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 19:28:08.685 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 19:28:08.691 Finished recording Unknown: channel 1002
2009-01-04 19:28:28.958 Expiring 0 MBytes for 1002 @ Sun Jan 4 19:26:39 2009 => Unknown
2009-01-04 19:28:54.525 Reschedule requested for id 0.
2009-01-04 19:28:54.553 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2009-01-04 19:32:35.842 Using runtime prefix = /usr
2009-01-04 19:32:36.000 Empty LocalHostName.
2009-01-04 19:32:36.001 Using localhost value of Griffindor
2009-01-04 19:32:36.008 New DB connection, total: 1
2009-01-04 19:32:36.018 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:32:36.020 Closing DB connection named 'DBManager0'
2009-01-04 19:32:36.021 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:32:36.023 New DB connection, total: 2
2009-01-04 19:32:36.025 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:32:36.028 Current Schema Version: 1214
Starting up as the master server.
2009-01-04 19:32:36.042 New DB connection, total: 3
2009-01-04 19:32:36.050 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:32:36.191 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 19:32:36.192 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-01-04 19:32:36.194 New DB scheduler connection
2009-01-04 19:32:36.195 Connected to database 'mythconverg' at host: localhost
Cable is defined, but isn't attached to a cardinput.
2009-01-04 19:32:36.206 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-04 19:32:36.207 Main::Registering HttpStatus Extension
2009-01-04 19:32:36.214 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 19:32:36.222 Enabled verbose msgs:  important general
2009-01-04 19:32:36.232 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 19:32:39.199 Reschedule requested for id -1.
2009-01-04 19:32:39.222 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-01-04 19:32:39.226 Seem to be woken up by USER
2009-01-04 19:32:42.010 MainServer::HandleAnnounce Monitor
2009-01-04 19:32:42.014 adding: Griffindor as a client (events: 0)
2009-01-04 19:32:42.015 MainServer::HandleAnnounce Monitor
2009-01-04 19:32:42.016 adding: Griffindor as a client (events: 1)
2009-01-04 19:32:42.017 Reschedule requested for id -1.
2009-01-04 19:32:42.040 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-01-04 19:32:54.465 MainServer::HandleAnnounce Monitor
2009-01-04 19:32:54.468 adding: Griffindor as a client (events: 0)
2009-01-04 19:32:54.469 MainServer::HandleAnnounce Monitor
2009-01-04 19:32:54.469 adding: Griffindor as a client (events: 1)
2009-01-04 19:32:54.474 MainServer::HandleAnnounce Playback
2009-01-04 19:32:54.475 adding: Griffindor as a client (events: 0)
2009-01-04 19:32:54.477 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 19:32:54.480 TVRec(1): HW Tuner: 1->1
2009-01-04 19:32:55.561 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-01-04 19:32:55.562 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 19:32:55.580 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 19:32:55.584 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-01-04 19:32:56.199 Expiring 0 MBytes for 1002 @ Sun Jan 4 19:27:27 2009 => Unknown
2009-01-04 19:33:35.589 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 19:33:35.594 Finished recording Unknown: channel 1002
2009-01-04 19:33:56.205 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 19:36:56.218 Expiring 0 MBytes for 1002 @ Sun Jan 4 19:32:54 2009 => Unknown
2009-01-04 19:49:02.089 Using runtime prefix = /usr
2009-01-04 19:49:02.115 Empty LocalHostName.
2009-01-04 19:49:02.116 Using localhost value of Griffindor
2009-01-04 19:49:02.123 New DB connection, total: 1
2009-01-04 19:49:02.129 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:49:02.139 Closing DB connection named 'DBManager0'
2009-01-04 19:49:02.151 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:49:02.153 New DB connection, total: 2
2009-01-04 19:49:02.154 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:49:02.162 Current Schema Version: 1214
Starting up as the master server.
2009-01-04 19:49:02.170 New DB connection, total: 3
2009-01-04 19:49:02.181 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:49:02.320 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 19:49:02.325 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-01-04 19:49:02.326 New DB scheduler connection
2009-01-04 19:49:02.327 Connected to database 'mythconverg' at host: localhost
Cable is defined, but isn't attached to a cardinput.
2009-01-04 19:49:02.339 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-04 19:49:02.340 Main::Registering HttpStatus Extension
2009-01-04 19:49:02.340 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 19:49:02.341 Enabled verbose msgs:  important general
2009-01-04 19:49:02.351 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 19:49:05.332 Reschedule requested for id -1.
2009-01-04 19:49:05.352 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-01-04 19:49:05.355 Seem to be woken up by USER
2009-01-04 19:49:09.578 MainServer::HandleAnnounce Monitor
2009-01-04 19:49:09.589 adding: Griffindor as a client (events: 0)
2009-01-04 19:49:09.590 MainServer::HandleAnnounce Monitor
2009-01-04 19:49:09.591 adding: Griffindor as a client (events: 1)
2009-01-04 19:49:09.592 Reschedule requested for id -1.
2009-01-04 19:49:09.595 MythSocket(a16b888:-1): writeStringList: Error, socket went unconnected.
2009-01-04 19:49:09.613 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-01-04 19:50:22.334 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 19:50:44.905 MainServer::HandleAnnounce Monitor
2009-01-04 19:50:44.907 adding: Griffindor as a client (events: 0)
2009-01-04 19:50:44.908 MainServer::HandleAnnounce Monitor
2009-01-04 19:50:44.908 adding: Griffindor as a client (events: 1)
2009-01-04 19:50:44.914 MainServer::HandleAnnounce Playback
2009-01-04 19:50:44.915 adding: Griffindor as a client (events: 0)
2009-01-04 19:50:44.916 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 19:50:44.924 TVRec(1): HW Tuner: 1->1
2009-01-04 19:50:46.005 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-01-04 19:50:46.006 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 19:50:46.023 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 19:50:46.026 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-01-04 19:51:26.032 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 19:51:26.038 Finished recording Unknown: channel 1002
2009-01-04 19:52:22.345 Expiring 0 MBytes for 1002 @ Sun Jan 4 19:50:44 2009 => Unknown
2009-01-04 19:55:59.366 Using runtime prefix = /usr
2009-01-04 19:55:59.391 Empty LocalHostName.
2009-01-04 19:55:59.392 Using localhost value of Griffindor
2009-01-04 19:55:59.398 New DB connection, total: 1
2009-01-04 19:55:59.404 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:55:59.405 Closing DB connection named 'DBManager0'
2009-01-04 19:55:59.406 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:55:59.408 New DB connection, total: 2
2009-01-04 19:55:59.409 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:55:59.411 Current Schema Version: 1214
Starting up as the master server.
2009-01-04 19:55:59.418 New DB connection, total: 3
2009-01-04 19:55:59.419 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:55:59.555 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 19:55:59.561 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-01-04 19:55:59.576 New DB scheduler connection
2009-01-04 19:55:59.578 Connected to database 'mythconverg' at host: localhost
Cable is defined, but isn't attached to a cardinput.
2009-01-04 19:55:59.608 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-04 19:55:59.609 Main::Registering HttpStatus Extension
2009-01-04 19:55:59.615 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 19:55:59.622 Enabled verbose msgs:  important general
2009-01-04 19:55:59.631 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 19:56:01.825 MainServer::HandleAnnounce Monitor
2009-01-04 19:56:01.831 adding: Griffindor as a client (events: 0)
2009-01-04 19:56:01.832 MainServer::HandleAnnounce Monitor
2009-01-04 19:56:01.832 adding: Griffindor as a client (events: 1)
2009-01-04 19:56:02.600 Reschedule requested for id -1.
2009-01-04 19:56:02.619 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-01-04 19:56:02.623 Seem to be woken up by USER
2009-01-04 19:56:16.980 MainServer::HandleAnnounce Monitor
2009-01-04 19:56:16.982 adding: Griffindor as a client (events: 0)
2009-01-04 19:56:16.983 MainServer::HandleAnnounce Monitor
2009-01-04 19:56:16.984 adding: Griffindor as a client (events: 1)
2009-01-04 19:56:16.989 MainServer::HandleAnnounce Playback
2009-01-04 19:56:16.991 adding: Griffindor as a client (events: 0)
2009-01-04 19:56:16.992 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 19:56:16.997 TVRec(1): HW Tuner: 1->1
2009-01-04 19:56:18.078 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-01-04 19:56:18.079 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 19:56:18.097 NVR(/dev/video0): Won't work with the streaming interface, falling back
2009-01-04 19:56:18.100 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
VIDIOCGMBUF:: Invalid argument
2009-01-04 19:56:58.104 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 19:56:58.109 Finished recording Unknown: channel 1002
2009-01-04 19:57:19.602 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 19:57:55.750 Reloading backend settings
2009-01-04 19:58:19.616 Expiring 0 MBytes for 1002 @ Sun Jan 4 19:56:17 2009 => Unknown
2009-01-04 20:12:19.635 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 20:14:43.799 Using runtime prefix = /usr
2009-01-04 20:14:43.875 Empty LocalHostName.
2009-01-04 20:14:43.885 Using localhost value of Griffindor
2009-01-04 20:14:43.959 New DB connection, total: 1
2009-01-04 20:14:43.985 Connected to database 'mythconverg' at host: localhost
2009-01-04 20:14:44.022 Closing DB connection named 'DBManager0'
2009-01-04 20:14:44.095 Connected to database 'mythconverg' at host: localhost
2009-01-04 20:14:44.098 New DB connection, total: 2
2009-01-04 20:14:44.099 Connected to database 'mythconverg' at host: localhost
2009-01-04 20:14:44.150 Current Schema Version: 1214
Starting up as the master server.
2009-01-04 20:14:45.238 New DB connection, total: 3
2009-01-04 20:14:45.250 Connected to database 'mythconverg' at host: localhost
2009-01-04 20:14:45.376 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 20:14:45.419 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-01-04 20:14:45.436 New DB scheduler connection
2009-01-04 20:14:45.445 Connected to database 'mythconverg' at host: localhost
Cable is defined, but isn't attached to a cardinput.
2009-01-04 20:14:45.537 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-04 20:14:45.586 Main::Registering HttpStatus Extension
2009-01-04 20:14:45.596 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 20:14:45.599 Enabled verbose msgs:  important general
2009-01-04 20:14:45.674 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 20:14:48.451 Reschedule requested for id -1.
2009-01-04 20:14:48.590 Scheduled 0 items in 0.1 = 0.06 match + 0.08 place
2009-01-04 20:14:48.595 Seem to be woken up by USER
2009-01-04 20:15:30.144 MainServer::HandleAnnounce Monitor
2009-01-04 20:15:30.148 adding: Griffindor as a client (events: 0)
2009-01-04 20:15:30.149 MainServer::HandleAnnounce Monitor
2009-01-04 20:15:30.150 adding: Griffindor as a client (events: 1)
2009-01-04 20:15:30.153 MainServer::HandleAnnounce Playback
2009-01-04 20:15:30.164 adding: Griffindor as a client (events: 0)
2009-01-04 20:15:30.170 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 20:15:30.177 TVRec(1): HW Tuner: 1->1
2009-01-04 20:15:31.332 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-01-04 20:15:31.334 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 20:15:31.352 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 20:15:31.354 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-01-04 20:16:05.453 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 20:16:11.360 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 20:16:11.371 Finished recording Unknown: channel 1002
2009-01-04 20:18:05.475 Expiring 0 MBytes for 1002 @ Sun Jan 4 20:15:30 2009 => Unknown
2009-01-04 20:31:05.500 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 20:42:02.805 MainServer::HandleAnnounce Monitor
2009-01-04 20:42:02.808 adding: Griffindor as a client (events: 0)
2009-01-04 20:42:02.809 MainServer::HandleAnnounce Monitor
2009-01-04 20:42:02.809 adding: Griffindor as a client (events: 1)
2009-01-04 20:42:02.815 MainServer::HandleAnnounce Playback
2009-01-04 20:42:02.816 adding: Griffindor as a client (events: 0)
2009-01-04 20:42:02.818 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 20:42:02.825 TVRec(1): HW Tuner: 1->1
2009-01-04 20:42:03.899 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-01-04 20:42:03.900 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 20:42:03.915 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 20:42:03.917 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-01-04 20:42:43.921 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 20:42:43.926 Finished recording Unknown: channel 1002
2009-01-04 20:44:05.523 Expiring 0 MBytes for 1002 @ Sun Jan 4 20:42:02 2009 => Unknown
2009-01-04 20:50:22.047 Using runtime prefix = /usr
2009-01-04 20:50:22.082 Empty LocalHostName.
2009-01-04 20:50:22.093 Using localhost value of Griffindor
2009-01-04 20:50:22.099 New DB connection, total: 1
2009-01-04 20:50:22.105 Connected to database 'mythconverg' at host: localhost
2009-01-04 20:50:22.107 Closing DB connection named 'DBManager0'
2009-01-04 20:50:22.113 Connected to database 'mythconverg' at host: localhost
2009-01-04 20:50:22.115 New DB connection, total: 2
2009-01-04 20:50:22.116 Connected to database 'mythconverg' at host: localhost
2009-01-04 20:50:22.118 Current Schema Version: 1214
Starting up as the master server.
2009-01-04 20:50:22.144 New DB connection, total: 3
2009-01-04 20:50:22.151 Connected to database 'mythconverg' at host: localhost
2009-01-04 20:50:22.297 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 20:50:22.301 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-01-04 20:50:22.302 New DB scheduler connection
2009-01-04 20:50:22.303 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2009-01-04 20:50:22.313 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-04 20:50:22.313 Main::Registering HttpStatus Extension
2009-01-04 20:50:22.314 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 20:50:22.315 Enabled verbose msgs:  important general
2009-01-04 20:50:22.316 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 20:50:24.424 MainServer::HandleAnnounce Monitor
2009-01-04 20:50:24.430 adding: Griffindor as a client (events: 0)
2009-01-04 20:50:24.439 MainServer::HandleAnnounce Monitor
2009-01-04 20:50:24.447 adding: Griffindor as a client (events: 1)
2009-01-04 20:50:24.457 MythSocket(b2502c50:-1): writeStringList: Error, socket went unconnected.
2009-01-04 20:50:25.307 Reschedule requested for id -1.
2009-01-04 20:50:25.344 Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2009-01-04 20:50:25.348 Seem to be woken up by USER
2009-01-04 20:50:39.002 MainServer::HandleAnnounce Monitor
2009-01-04 20:50:39.012 adding: Griffindor as a client (events: 0)
2009-01-04 20:50:39.013 MainServer::HandleAnnounce Monitor
2009-01-04 20:50:39.014 adding: Griffindor as a client (events: 1)
2009-01-04 20:50:39.019 MainServer::HandleAnnounce Playback
2009-01-04 20:50:39.020 adding: Griffindor as a client (events: 0)
2009-01-04 20:50:39.021 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 20:50:39.024 TVRec(1): HW Tuner: 1->1
2009-01-04 20:50:40.106 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-01-04 20:50:40.107 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 20:50:40.124 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 20:50:40.125 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-01-04 20:51:20.131 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 20:51:20.138 Finished recording Unknown: channel 2002
2009-01-04 20:51:42.308 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 20:52:42.319 Expiring 0 MBytes for 2002 @ Sun Jan 4 20:50:39 2009 => Unknown
2009-01-04 21:03:35.964 Using runtime prefix = /usr
2009-01-04 21:03:35.991 Empty LocalHostName.
2009-01-04 21:03:35.992 Using localhost value of Griffindor
2009-01-04 21:03:35.999 New DB connection, total: 1
2009-01-04 21:03:36.004 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:03:36.005 Closing DB connection named 'DBManager0'
2009-01-04 21:03:36.016 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:03:36.028 New DB connection, total: 2
2009-01-04 21:03:36.030 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:03:36.042 Current Schema Version: 1214
Starting up as the master server.
2009-01-04 21:03:36.057 New DB connection, total: 3
2009-01-04 21:03:36.058 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:03:36.192 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 21:03:36.196 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-01-04 21:03:36.197 New DB scheduler connection
2009-01-04 21:03:36.198 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2009-01-04 21:03:36.208 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-04 21:03:36.209 Main::Registering HttpStatus Extension
2009-01-04 21:03:36.209 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 21:03:36.210 Enabled verbose msgs:  important general
2009-01-04 21:03:36.211 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 21:03:37.844 MainServer::HandleAnnounce Monitor
2009-01-04 21:03:37.849 adding: Griffindor as a client (events: 0)
2009-01-04 21:03:37.856 MainServer::HandleAnnounce Monitor
2009-01-04 21:03:37.863 adding: Griffindor as a client (events: 1)
2009-01-04 21:03:39.202 Reschedule requested for id -1.
2009-01-04 21:03:39.221 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-01-04 21:03:39.225 Seem to be woken up by USER
2009-01-04 21:05:20.766 Using runtime prefix = /usr
2009-01-04 21:05:20.792 Empty LocalHostName.
2009-01-04 21:05:20.793 Using localhost value of Griffindor
2009-01-04 21:05:20.799 New DB connection, total: 1
2009-01-04 21:05:20.805 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:05:20.806 Closing DB connection named 'DBManager0'
2009-01-04 21:05:20.807 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:05:20.809 New DB connection, total: 2
2009-01-04 21:05:20.810 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:05:20.812 Current Schema Version: 1214
Starting up as the master server.
2009-01-04 21:05:20.820 New DB connection, total: 3
2009-01-04 21:05:20.821 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:05:20.956 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2009-01-04 21:05:20.963 ChannelBase(2) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2009-01-04 21:05:20.966 New DB scheduler connection
2009-01-04 21:05:20.967 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2009-01-04 21:05:20.979 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-04 21:05:20.980 Main::Registering HttpStatus Extension
2009-01-04 21:05:20.981 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 21:05:20.987 Enabled verbose msgs:  important general
2009-01-04 21:05:20.995 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 21:05:23.972 Reschedule requested for id -1.
2009-01-04 21:05:23.988 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-01-04 21:05:23.992 Seem to be woken up by USER
2009-01-04 21:05:25.911 MainServer::HandleAnnounce Monitor
2009-01-04 21:05:25.917 adding: Griffindor as a client (events: 0)
2009-01-04 21:05:25.918 MainServer::HandleAnnounce Monitor
2009-01-04 21:05:25.922 adding: Griffindor as a client (events: 1)
2009-01-04 21:05:25.931 Reschedule requested for id -1.
2009-01-04 21:05:25.997 Scheduled 0 items in 0.1 = 0.06 match + 0.01 place
2009-01-04 21:05:39.196 MainServer::HandleAnnounce Monitor
2009-01-04 21:05:39.205 adding: Griffindor as a client (events: 0)
2009-01-04 21:05:39.206 MainServer::HandleAnnounce Monitor
2009-01-04 21:05:39.206 adding: Griffindor as a client (events: 1)
2009-01-04 21:05:39.210 MainServer::HandleAnnounce Playback
2009-01-04 21:05:39.211 adding: Griffindor as a client (events: 0)
2009-01-04 21:05:39.213 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 21:05:39.217 TVRec(1): HW Tuner: 1->1
2009-01-04 21:05:40.299 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-01-04 21:05:40.300 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 21:05:40.316 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 21:05:40.319 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-01-04 21:06:20.320 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 21:06:20.328 Finished recording Unknown: channel 2002
2009-01-04 21:06:40.973 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 21:08:40.986 Expiring 0 MBytes for 2002 @ Sun Jan 4 21:05:39 2009 => Unknown
2009-01-04 21:21:39.244 MainServer::HandleAnnounce Monitor
2009-01-04 21:21:39.248 adding: Griffindor as a client (events: 0)
2009-01-04 21:21:39.249 MainServer::HandleAnnounce Monitor
2009-01-04 21:21:39.250 adding: Griffindor as a client (events: 1)
2009-01-04 21:21:41.011 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 21:22:53.176 MainServer::HandleAnnounce Playback
2009-01-04 21:22:53.180 adding: Griffindor as a client (events: 0)
2009-01-04 21:22:53.181 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 21:22:53.184 TVRec(1): HW Tuner: 1->1
2009-01-04 21:22:54.257 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-01-04 21:22:54.257 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 21:22:54.275 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 21:22:54.277 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-01-04 21:23:34.282 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 21:23:34.286 Finished recording Unknown: channel 2002
2009-01-04 21:25:24.601 MainServer::HandleAnnounce Monitor
2009-01-04 21:25:24.607 adding: Griffindor as a client (events: 0)
2009-01-04 21:25:24.608 MainServer::HandleAnnounce Monitor
2009-01-04 21:25:24.608 adding: Griffindor as a client (events: 1)
2009-01-04 21:26:41.027 Expiring 0 MBytes for 2002 @ Sun Jan 4 21:22:53 2009 => Unknown
2009-01-04 21:35:58.505 MainServer::HandleAnnounce Monitor
2009-01-04 21:35:58.506 adding: Griffindor as a client (events: 0)
2009-01-04 21:35:58.507 MainServer::HandleAnnounce Monitor
2009-01-04 21:35:58.508 adding: Griffindor as a client (events: 1)
2009-01-04 21:36:41.044 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 21:39:04.498 MainServer::HandleAnnounce Monitor
2009-01-04 21:39:04.501 adding: Griffindor as a client (events: 0)
2009-01-04 21:39:04.502 MainServer::HandleAnnounce Monitor
2009-01-04 21:39:04.503 adding: Griffindor as a client (events: 1)
2009-01-04 21:39:04.508 MainServer::HandleAnnounce Playback
2009-01-04 21:39:04.511 adding: Griffindor as a client (events: 0)
2009-01-04 21:39:04.513 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 21:39:04.520 TVRec(1): HW Tuner: 1->1
2009-01-04 21:39:05.593 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2009-01-04 21:39:05.594 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 21:39:05.611 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 21:39:05.612 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-01-04 21:39:45.619 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 21:39:45.626 Finished recording Unknown: channel 2002
2009-01-04 21:42:41.074 Expiring 0 MBytes for 2002 @ Sun Jan 4 21:39:04 2009 => Unknown
2009-01-04 21:51:38.827 MainServer::HandleAnnounce Monitor
2009-01-04 21:51:39.379 adding: Griffindor as a client (events: 0)
2009-01-04 21:51:39.382 MainServer::HandleAnnounce Monitor
2009-01-04 21:51:39.383 adding: Griffindor as a client (events: 1)
2009-01-04 21:51:41.087 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min





**mythfrontend log:**

Starting mythfrontend.real..
2009-01-04 17:58:55.285 New DB connection, total: 2
2009-01-04 17:58:55.285 Connected to database 'mythconverg' at host: localhost
2009-01-04 17:58:55.287 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 17:58:55.287 Enabled verbose msgs:  important general
2009-01-04 17:58:59.125 Writing settings file /home/mark/.mythtv/mysql.txt
2009-01-04 17:58:59.125 Closing DB connection named 'DBManager1'
2009-01-04 17:58:59.125 Closing DB connection named 'DBManager0'
2009-01-04 17:58:59.126 Connected to database 'mythconverg' at host: localhost
2009-01-04 17:58:59.135 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 17:58:59.136 Primary screen 0.
2009-01-04 17:58:59.137 Using screen 0, 800x600 at 0,0
2009-01-04 17:58:59.138 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 17:58:59.138 Switching to square mode (Mythbuntu-8.04)
2009-01-04 17:58:59.427 Using the Qt painter
2009-01-04 17:58:59.428 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 17:58:59.429 Connected to database 'mythconverg' at host: localhost
2009-01-04 17:58:59.429 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 17:58:59.804 Specified base font 'medium' does not exist for font clock
2009-01-04 17:58:59.805 Specified base font 'medium' does not exist for font small
2009-01-04 17:58:59.805 Specified base font 'medium' does not exist for font medium
2009-01-04 17:58:59.805 Specified base font 'medium' does not exist for font large
2009-01-04 17:58:59.806 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 17:59:00.095 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 17:59:00.168 Registering Internal as a media playback plugin.
2009-01-04 17:59:00.303 Upgrading to MythArchive schema version 1001
2009-01-04 17:59:00.458 Inserting MythFlix initial database information.
2009-01-04 17:59:00.458 Upgrading to MythFlix schema version 1000
2009-01-04 17:59:00.496 Upgrading to MythFlix schema version 1001
2009-01-04 17:59:00.883 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 17:59:01.070 Setting Up MythMovies Database Tables
2009-01-04 17:59:01.266 MythMovies Database Setup Complete
2009-01-04 17:59:03.312 Upgrading to MythMusic schema version 1007
2009-01-04 17:59:03.357 Upgrading to MythMusic schema version 1008
2009-01-04 17:59:03.556 Upgrading to MythMusic schema version 1009
2009-01-04 17:59:03.582 Upgrading to MythMusic schema version 1010
2009-01-04 17:59:03.608 Updating music_albumart image types
2009-01-04 17:59:03.610 Upgrading to MythMusic schema version 1011
2009-01-04 17:59:03.611 Upgrading to MythMusic schema version 1012
2009-01-04 17:59:03.635 Upgrading to MythMusic schema version 1013
2009-01-04 17:59:03.825 Failed to run 'cdrecord --scanbus'
2009-01-04 17:59:03.829 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-04 17:59:03.831 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-04 17:59:03.857 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.4:5060 NAT address 192.168.1.4
SIP: Cannot register; proxy, username or password not set
2009-01-04 17:59:04.015 Inserting MythWeather initial database information.
2009-01-04 17:59:04.015 Upgrading to MythWeather schema version 1000
2009-01-04 17:59:04.270 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 17:59:12.000 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 17:59:12.010 Using protocol version 40
2009-01-04 17:59:33.494 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2009-01-04 17:59:36.689 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/video-ui.xml
Destroying SipFsm object 
2009-01-04 17:59:48.439 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-04 18:16:53.262 New DB connection, total: 2
2009-01-04 18:16:53.263 Connected to database 'mythconverg' at host: localhost
2009-01-04 18:16:53.264 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 18:16:53.264 Enabled verbose msgs:  important general
2009-01-04 18:16:53.397 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-01-04 18:16:53.613 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 18:16:53.614 Primary screen 0.
2009-01-04 18:16:53.614 Using screen 0, 1680x1050 at 0,0
2009-01-04 18:16:53.614 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 18:16:53.615 Switching to square mode (Mythbuntu-8.04)
2009-01-04 18:16:53.627 Using the Qt painter
2009-01-04 18:16:53.628 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 18:16:53.628 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 18:16:53.930 Removing stale cache dir: /home/mark/.mythtv/themecache/Mythbuntu-8.04.800.600
2009-01-04 18:17:54.437 Specified base font 'medium' does not exist for font clock
2009-01-04 18:17:54.437 Specified base font 'medium' does not exist for font small
2009-01-04 18:17:54.437 Specified base font 'medium' does not exist for font medium
2009-01-04 18:17:54.437 Specified base font 'medium' does not exist for font large
2009-01-04 18:17:54.438 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 18:17:54.573 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 18:17:54.620 Registering Internal as a media playback plugin.
2009-01-04 18:17:54.800 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 18:17:54.827 Failed to run 'cdrecord --scanbus'
2009-01-04 18:17:54.832 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-04 18:17:54.836 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-04 18:17:54.859 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2009-01-04 18:17:54.937 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 18:18:07.953 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 18:18:07.953 Using protocol version 40
2009-01-04 18:18:13.242 Deleting UPnP client...
2009-01-04 18:18:13.242 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2009-01-04 18:21:09.239 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-01-04 18:21:09.266 New DB connection, total: 2
2009-01-04 18:21:09.267 Connected to database 'mythconverg' at host: localhost
2009-01-04 18:21:09.268 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 18:21:09.268 Enabled verbose msgs:  important general
2009-01-04 18:21:09.602 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 18:21:09.603 Primary screen 0.
2009-01-04 18:21:09.603 Using screen 0, 1680x1050 at 0,0
2009-01-04 18:21:09.604 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 18:21:09.604 Switching to square mode (Mythbuntu-8.04)
2009-01-04 18:21:09.618 Using the Qt painter
2009-01-04 18:21:09.618 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 18:21:09.619 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 18:21:10.479 Specified base font 'medium' does not exist for font clock
2009-01-04 18:21:10.480 Specified base font 'medium' does not exist for font small
2009-01-04 18:21:10.480 Specified base font 'medium' does not exist for font medium
2009-01-04 18:21:10.480 Specified base font 'medium' does not exist for font large
2009-01-04 18:21:10.481 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 18:21:10.609 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 18:21:10.633 Registering Internal as a media playback plugin.
2009-01-04 18:21:10.761 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 18:21:10.787 Failed to run 'cdrecord --scanbus'
2009-01-04 18:21:10.790 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-04 18:21:10.794 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-04 18:21:10.813 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2009-01-04 18:21:10.876 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 18:21:14.145 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 18:21:14.146 Using protocol version 40
2009-01-04 18:21:16.089 Deleting UPnP client...
2009-01-04 18:21:16.090 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2009-01-04 18:24:06.335 New DB connection, total: 2
2009-01-04 18:24:06.336 Connected to database 'mythconverg' at host: localhost
2009-01-04 18:24:06.337 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 18:24:06.337 Enabled verbose msgs:  important general
2009-01-04 18:24:09.202 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 18:24:09.203 Primary screen 0.
2009-01-04 18:24:09.203 Using screen 0, 1680x1050 at 0,0
2009-01-04 18:24:09.204 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 18:24:09.204 Switching to square mode (Mythbuntu-8.04)
2009-01-04 18:24:09.243 Using the Qt painter
2009-01-04 18:24:09.244 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 18:24:09.245 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 18:24:11.096 Specified base font 'medium' does not exist for font clock
2009-01-04 18:24:11.097 Specified base font 'medium' does not exist for font small
2009-01-04 18:24:11.097 Specified base font 'medium' does not exist for font medium
2009-01-04 18:24:11.097 Specified base font 'medium' does not exist for font large
2009-01-04 18:24:11.097 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 18:24:11.256 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 18:24:11.319 Registering Internal as a media playback plugin.
2009-01-04 18:24:11.535 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 18:24:11.833 Failed to run 'cdrecord --scanbus'
2009-01-04 18:24:11.837 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-04 18:24:11.840 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-04 18:24:11.866 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.4:5060 NAT address 192.168.1.4
SIP: Cannot register; proxy, username or password not set
2009-01-04 18:24:12.047 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 18:24:15.939 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 18:24:15.949 Using protocol version 40
Destroying SipFsm object 
2009-01-04 18:24:33.470 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-04 18:36:58.308 New DB connection, total: 2
2009-01-04 18:36:58.309 Connected to database 'mythconverg' at host: localhost
2009-01-04 18:36:58.310 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 18:36:58.310 Enabled verbose msgs:  important general
2009-01-04 18:36:58.626 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 18:36:58.627 Primary screen 0.
2009-01-04 18:36:58.628 Using screen 0, 1680x1050 at 0,0
2009-01-04 18:36:58.628 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 18:36:58.628 Switching to square mode (Mythbuntu-8.04)
2009-01-04 18:36:58.639 Using the Qt painter
2009-01-04 18:36:58.640 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 18:36:58.641 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 18:36:59.642 Specified base font 'medium' does not exist for font clock
2009-01-04 18:36:59.642 Specified base font 'medium' does not exist for font small
2009-01-04 18:36:59.642 Specified base font 'medium' does not exist for font medium
2009-01-04 18:36:59.642 Specified base font 'medium' does not exist for font large
2009-01-04 18:36:59.643 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 18:36:59.774 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 18:36:59.799 Registering Internal as a media playback plugin.
2009-01-04 18:36:59.924 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 18:36:59.951 Failed to run 'cdrecord --scanbus'
2009-01-04 18:36:59.954 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-04 18:36:59.958 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-04 18:36:59.977 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.4:5060 NAT address 192.168.1.4
SIP: Cannot register; proxy, username or password not set
2009-01-04 18:37:00.041 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 18:37:04.288 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 18:37:04.289 Using protocol version 40
2009-01-04 18:37:43.586 Received a remote 'Clear Cache' request
2009-01-04 18:37:57.645 Received a remote 'Clear Cache' request
2009-01-04 18:38:05.057 Loading from: /usr/share/mythtv/themes/default/appear-ui.xml

Reading package lists... 0%

Reading package lists... 0%

Reading package lists... 9%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

 * Stopping MythTV server: mythbackend 
2009-01-04 18:38:52.058 Event socket closed. No connection to the backend.
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
OK

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

2009-01-04 18:43:05.741 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 18:43:05.742 Using protocol version 40
2009-01-04 18:43:08.487 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
Destroying SipFsm object 
2009-01-04 18:43:19.531 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-04 19:03:29.012 New DB connection, total: 2
2009-01-04 19:03:29.013 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:03:29.014 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 19:03:29.014 Enabled verbose msgs:  important general
2009-01-04 19:03:29.329 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 19:03:29.330 Primary screen 0.
2009-01-04 19:03:29.330 Using screen 0, 1680x1050 at 0,0
2009-01-04 19:03:29.331 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 19:03:29.331 Switching to square mode (Mythbuntu-8.04)
2009-01-04 19:03:29.345 Using the Qt painter
2009-01-04 19:03:29.346 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 19:03:29.346 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 19:03:30.398 Specified base font 'medium' does not exist for font clock
2009-01-04 19:03:30.398 Specified base font 'medium' does not exist for font small
2009-01-04 19:03:30.398 Specified base font 'medium' does not exist for font medium
2009-01-04 19:03:30.398 Specified base font 'medium' does not exist for font large
2009-01-04 19:03:30.399 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 19:03:30.521 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 19:03:30.546 Registering Internal as a media playback plugin.
2009-01-04 19:03:30.667 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 19:03:30.694 Failed to run 'cdrecord --scanbus'
2009-01-04 19:03:30.697 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-04 19:03:30.701 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-04 19:03:30.719 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.4:5060 NAT address 192.168.1.4
SIP: Cannot register; proxy, username or password not set
2009-01-04 19:03:30.783 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 19:04:13.773 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 19:04:13.774 Using protocol version 40
2009-01-04 19:04:13.788 Received a remote 'Clear Cache' request

Reading package lists... 0%

Reading package lists... 0%

Reading package lists... 9%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

 * Stopping MythTV server: mythbackend 
2009-01-04 19:04:39.887 Event socket closed. No connection to the backend.
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
QSocketDevice::writeBlock: Invalid socket
2009-01-04 19:09:13.582 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 19:09:13.583 Using protocol version 40
2009-01-04 19:09:48.129 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

 * Stopping MythTV server: mythbackend 
2009-01-04 19:10:08.973 Event socket closed. No connection to the backend.
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
2009-01-04 19:17:23.531 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 19:17:23.531 Using protocol version 40
2009-01-04 19:17:25.646 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 19:17:28.004 TV: Attempting to change from None to WatchingLiveTV
2009-01-04 19:17:28.005 Using protocol version 40
2009-01-04 19:17:29.223 DPMS Deactivated 
2009-01-04 19:18:09.191 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-01-04 19:18:09.194 TV Error: LiveTV not successfully started
2009-01-04 19:18:09.239 TV: Deleting TV Chain in destructor
2009-01-04 19:18:09.240 DPMS Reactivated.
2009-01-04 19:18:12.615 TV: Attempting to change from None to WatchingLiveTV
2009-01-04 19:18:12.615 Using protocol version 40
2009-01-04 19:18:13.714 DPMS Deactivated 
2009-01-04 19:18:53.700 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-01-04 19:18:53.700 TV Error: LiveTV not successfully started
2009-01-04 19:18:53.800 TV: Deleting TV Chain in destructor
2009-01-04 19:18:53.801 DPMS Reactivated.
2009-01-04 19:18:58.699 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

 * Stopping MythTV server: mythbackend 
2009-01-04 19:19:22.185 Event socket closed. No connection to the backend.
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
2009-01-04 19:26:39.870 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 19:26:39.870 Using protocol version 40
2009-01-04 19:26:39.882 TV: Attempting to change from None to WatchingLiveTV
2009-01-04 19:26:39.882 Using protocol version 40
2009-01-04 19:26:41.085 DPMS Deactivated 
2009-01-04 19:27:20.998 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-01-04 19:27:21.000 TV Error: LiveTV not successfully started
2009-01-04 19:27:21.083 TV: Deleting TV Chain in destructor
2009-01-04 19:27:21.100 DPMS Reactivated.
2009-01-04 19:27:27.589 TV: Attempting to change from None to WatchingLiveTV
2009-01-04 19:27:27.590 Using protocol version 40
2009-01-04 19:27:28.692 DPMS Deactivated 
2009-01-04 19:28:08.682 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-01-04 19:28:08.683 TV Error: LiveTV not successfully started
2009-01-04 19:28:08.718 TV: Deleting TV Chain in destructor
2009-01-04 19:28:08.719 DPMS Reactivated.
2009-01-04 19:28:54.525 Received a remote 'Clear Cache' request

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

 * Stopping MythTV server: mythbackend 
   ...done.
2009-01-04 19:29:26.330 Event socket closed. No connection to the backend.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
2009-01-04 19:32:54.464 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 19:32:54.464 Using protocol version 40
2009-01-04 19:32:54.473 TV: Attempting to change from None to WatchingLiveTV
2009-01-04 19:32:54.474 Using protocol version 40
2009-01-04 19:32:55.677 DPMS Deactivated 
2009-01-04 19:33:35.585 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-01-04 19:33:35.586 TV Error: LiveTV not successfully started
2009-01-04 19:33:35.678 TV: Deleting TV Chain in destructor
2009-01-04 19:33:35.678 DPMS Reactivated.
Destroying SipFsm object 
2009-01-04 19:33:40.257 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-04 19:50:37.981 New DB connection, total: 2
2009-01-04 19:50:37.982 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:50:37.984 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 19:50:37.984 Enabled verbose msgs:  important general
2009-01-04 19:50:38.309 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 19:50:38.310 Primary screen 0.
2009-01-04 19:50:38.310 Using screen 0, 1680x1050 at 0,0
2009-01-04 19:50:38.311 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 19:50:38.311 Switching to square mode (Mythbuntu-8.04)
2009-01-04 19:50:38.324 Using the Qt painter
2009-01-04 19:50:38.325 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 19:50:38.325 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 19:50:39.218 Specified base font 'medium' does not exist for font clock
2009-01-04 19:50:39.218 Specified base font 'medium' does not exist for font small
2009-01-04 19:50:39.218 Specified base font 'medium' does not exist for font medium
2009-01-04 19:50:39.218 Specified base font 'medium' does not exist for font large
2009-01-04 19:50:39.219 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 19:50:39.345 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 19:50:39.370 Registering Internal as a media playback plugin.
2009-01-04 19:50:39.505 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 19:50:39.595 MythMusic adding CD-Writer: 6,0,0 -- DVDRW SHM-165H6S
2009-01-04 19:50:39.595 MythMusic adding CD-Writer: 6,1,0 -- DVD-RAM GSA-H55N
2009-01-04 19:50:39.629 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.4:5060 NAT address 192.168.1.4
SIP: Cannot register; proxy, username or password not set
2009-01-04 19:50:39.694 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 19:50:44.904 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 19:50:44.905 Using protocol version 40
2009-01-04 19:50:44.912 TV: Attempting to change from None to WatchingLiveTV
2009-01-04 19:50:44.913 Using protocol version 40
2009-01-04 19:50:46.116 DPMS Deactivated 
2009-01-04 19:51:26.029 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-01-04 19:51:26.030 TV Error: LiveTV not successfully started
2009-01-04 19:51:26.051 TV: Deleting TV Chain in destructor
2009-01-04 19:51:26.061 DPMS Reactivated.
Destroying SipFsm object 
2009-01-04 19:51:30.161 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-04 19:56:11.687 New DB connection, total: 2
2009-01-04 19:56:11.688 Connected to database 'mythconverg' at host: localhost
2009-01-04 19:56:11.689 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 19:56:11.690 Enabled verbose msgs:  important general
2009-01-04 19:56:12.008 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 19:56:12.010 Primary screen 0.
2009-01-04 19:56:12.010 Using screen 0, 1680x1050 at 0,0
2009-01-04 19:56:12.010 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 19:56:12.011 Switching to square mode (Mythbuntu-8.04)
2009-01-04 19:56:12.023 Using the Qt painter
2009-01-04 19:56:12.023 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 19:56:12.024 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 19:56:12.898 Specified base font 'medium' does not exist for font clock
2009-01-04 19:56:12.898 Specified base font 'medium' does not exist for font small
2009-01-04 19:56:12.898 Specified base font 'medium' does not exist for font medium
2009-01-04 19:56:12.898 Specified base font 'medium' does not exist for font large
2009-01-04 19:56:12.899 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 19:56:13.025 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 19:56:13.050 Registering Internal as a media playback plugin.
2009-01-04 19:56:13.184 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 19:56:13.275 MythMusic adding CD-Writer: 6,0,0 -- DVDRW SHM-165H6S
2009-01-04 19:56:13.275 MythMusic adding CD-Writer: 6,1,0 -- DVD-RAM GSA-H55N
2009-01-04 19:56:13.308 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.4:5060 NAT address 192.168.1.4
SIP: Cannot register; proxy, username or password not set
2009-01-04 19:56:13.372 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 19:56:16.979 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 19:56:16.980 Using protocol version 40
2009-01-04 19:56:16.988 TV: Attempting to change from None to WatchingLiveTV
2009-01-04 19:56:16.989 Using protocol version 40
2009-01-04 19:56:18.193 DPMS Deactivated 
2009-01-04 19:56:58.102 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-01-04 19:56:58.102 TV Error: LiveTV not successfully started
2009-01-04 19:56:58.127 TV: Deleting TV Chain in destructor
2009-01-04 19:56:58.130 DPMS Reactivated.
2009-01-04 19:57:10.957 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/video-ui.xml
2009-01-04 19:57:10.958 Unable to find image file: /usr/share/mythtv/themes/Mythbuntu-8.04/vidgallerybackg.png
2009-01-04 19:57:10.958 UIImageType::LoadImage() - Cannot find image: vidgallerybackg.png
Container: background already exists
2009-01-04 19:57:10.965 Failed to parse a container. Ignoring.
2009-01-04 19:57:11.364 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2009-01-04 19:57:11.364 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2009-01-04 19:57:55.760 Received a remote 'Clear Cache' request
Destroying SipFsm object 
2009-01-04 19:58:07.838 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-04 20:15:20.007 New DB connection, total: 2
2009-01-04 20:15:20.008 Connected to database 'mythconverg' at host: localhost
2009-01-04 20:15:20.009 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 20:15:20.009 Enabled verbose msgs:  important general
2009-01-04 20:15:20.877 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 20:15:20.878 Primary screen 0.
2009-01-04 20:15:20.878 Using screen 0, 1680x1050 at 0,0
2009-01-04 20:15:20.879 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 20:15:20.879 Switching to square mode (Mythbuntu-8.04)
2009-01-04 20:15:20.909 Using the Qt painter
2009-01-04 20:15:20.909 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 20:15:20.950 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 20:15:22.040 Specified base font 'medium' does not exist for font clock
2009-01-04 20:15:22.040 Specified base font 'medium' does not exist for font small
2009-01-04 20:15:22.040 Specified base font 'medium' does not exist for font medium
2009-01-04 20:15:22.040 Specified base font 'medium' does not exist for font large
2009-01-04 20:15:22.041 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 20:15:22.205 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 20:15:22.261 Registering Internal as a media playback plugin.
2009-01-04 20:15:22.453 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 20:15:22.790 MythMusic adding CD-Writer: 1,0,0 -- DVDRW SHM-165H6S
2009-01-04 20:15:22.790 MythMusic adding CD-Writer: 1,1,0 -- DVD-RAM GSA-H55N
2009-01-04 20:15:22.825 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.4:5060 NAT address 192.168.1.4
SIP: Cannot register; proxy, username or password not set
2009-01-04 20:15:23.011 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 20:15:30.136 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 20:15:30.137 Using protocol version 40
2009-01-04 20:15:30.153 TV: Attempting to change from None to WatchingLiveTV
2009-01-04 20:15:30.153 Using protocol version 40
2009-01-04 20:15:31.364 DPMS Deactivated 
2009-01-04 20:16:11.358 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-01-04 20:16:11.358 TV Error: LiveTV not successfully started
2009-01-04 20:16:11.396 TV: Deleting TV Chain in destructor
2009-01-04 20:16:11.397 DPMS Reactivated.
Destroying SipFsm object 
2009-01-04 20:16:34.437 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-04 20:41:57.353 New DB connection, total: 2
2009-01-04 20:41:57.353 Connected to database 'mythconverg' at host: localhost
2009-01-04 20:41:57.355 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 20:41:57.355 Enabled verbose msgs:  important general
2009-01-04 20:41:57.669 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 20:41:57.670 Primary screen 0.
2009-01-04 20:41:57.671 Using screen 0, 1680x1050 at 0,0
2009-01-04 20:41:57.671 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 20:41:57.671 Switching to square mode (Mythbuntu-8.04)
2009-01-04 20:41:57.684 Using the Qt painter
2009-01-04 20:41:57.684 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 20:41:57.685 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 20:41:58.646 Specified base font 'medium' does not exist for font clock
2009-01-04 20:41:58.647 Specified base font 'medium' does not exist for font small
2009-01-04 20:41:58.647 Specified base font 'medium' does not exist for font medium
2009-01-04 20:41:58.647 Specified base font 'medium' does not exist for font large
2009-01-04 20:41:58.647 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 20:41:58.779 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 20:41:58.804 Registering Internal as a media playback plugin.
2009-01-04 20:41:58.932 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 20:41:59.029 MythMusic adding CD-Writer: 1,0,0 -- DVDRW SHM-165H6S
2009-01-04 20:41:59.030 MythMusic adding CD-Writer: 1,1,0 -- DVD-RAM GSA-H55N
2009-01-04 20:41:59.063 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.4:5060 NAT address 192.168.1.4
SIP: Cannot register; proxy, username or password not set
2009-01-04 20:41:59.129 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 20:42:02.803 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 20:42:02.804 Using protocol version 40
2009-01-04 20:42:02.813 TV: Attempting to change from None to WatchingLiveTV
2009-01-04 20:42:02.814 Using protocol version 40
2009-01-04 20:42:04.017 DPMS Deactivated 
2009-01-04 20:42:43.919 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-01-04 20:42:43.919 TV Error: LiveTV not successfully started
2009-01-04 20:42:43.953 TV: Deleting TV Chain in destructor
2009-01-04 20:42:43.954 DPMS Reactivated.
2009-01-04 20:45:12.278 Received a remote 'Clear Cache' request

Reading package lists... 0%

Reading package lists... 0%

Reading package lists... 7%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

 * Stopping MythTV server: mythbackend 
   ...done.
2009-01-04 20:45:42.856 Event socket closed. No connection to the backend.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
2009-01-04 20:50:39.001 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 20:50:39.002 Using protocol version 40
2009-01-04 20:50:39.018 TV: Attempting to change from None to WatchingLiveTV
2009-01-04 20:50:39.019 Using protocol version 40
2009-01-04 20:50:40.222 DPMS Deactivated 
2009-01-04 20:51:20.128 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-01-04 20:51:20.129 TV Error: LiveTV not successfully started
2009-01-04 20:51:20.151 TV: Deleting TV Chain in destructor
2009-01-04 20:51:20.167 DPMS Reactivated.
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

 * Stopping MythTV server: mythbackend 
   ...done.
2009-01-04 20:59:41.778 Event socket closed. No connection to the backend.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
 * Stopping MythTV server: mythbackend 
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
2009-01-04 21:05:39.195 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 21:05:39.196 Using protocol version 40
2009-01-04 21:05:39.209 TV: Attempting to change from None to WatchingLiveTV
2009-01-04 21:05:39.210 Using protocol version 40
2009-01-04 21:05:40.412 DPMS Deactivated 
2009-01-04 21:06:20.318 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-01-04 21:06:20.318 TV Error: LiveTV not successfully started
2009-01-04 21:06:20.363 TV: Deleting TV Chain in destructor
2009-01-04 21:06:20.380 DPMS Reactivated.
Destroying SipFsm object 
2009-01-04 21:06:27.105 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-04 21:21:19.094 New DB connection, total: 2
2009-01-04 21:21:19.094 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:21:19.096 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 21:21:19.096 Enabled verbose msgs:  important general
2009-01-04 21:21:19.415 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:21:19.416 Primary screen 0.
2009-01-04 21:21:19.416 Using screen 0, 1680x1050 at 0,0
2009-01-04 21:21:19.416 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:21:19.417 Switching to square mode (Mythbuntu-8.04)
2009-01-04 21:21:19.428 Using the Qt painter
2009-01-04 21:21:19.428 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 21:21:19.429 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 21:21:20.279 Specified base font 'medium' does not exist for font clock
2009-01-04 21:21:20.279 Specified base font 'medium' does not exist for font small
2009-01-04 21:21:20.279 Specified base font 'medium' does not exist for font medium
2009-01-04 21:21:20.279 Specified base font 'medium' does not exist for font large
2009-01-04 21:21:20.280 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 21:21:20.405 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 21:21:20.430 Registering Internal as a media playback plugin.
2009-01-04 21:21:20.559 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 21:21:21.148 MythMusic adding CD-Writer: 1,0,0 -- DVDRW SHM-165H6S
2009-01-04 21:21:21.148 MythMusic adding CD-Writer: 1,1,0 -- DVD-RAM GSA-H55N
2009-01-04 21:21:21.180 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.4:5060 NAT address 192.168.1.4
SIP: Cannot register; proxy, username or password not set
2009-01-04 21:21:21.245 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:21:39.243 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 21:21:39.244 Using protocol version 40
2009-01-04 21:21:39.252 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: vm: faild to open/read the DVD
2009-01-04 21:21:39.281 Failed to open DVD device at /dev/dvd
2009-01-04 21:21:48.522 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: vm: faild to open/read the DVD
2009-01-04 21:21:48.532 Failed to open DVD device at /dev/dvd
2009-01-04 21:22:06.459 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: vm: faild to open/read the DVD
2009-01-04 21:22:06.469 Failed to open DVD device at /dev/dvd
2009-01-04 21:22:14.348 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/dvd-ui.xml
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Creating config file: /home/mark/.mplayer/config
Terminal type `unknown' is not defined.

Playing vcd://.
CD-ROM Device '/dev/cdrom' not found.
Failed to open vcd://.


Exiting... (End of file)
2009-01-04 21:22:53.175 TV: Attempting to change from None to WatchingLiveTV
2009-01-04 21:22:53.175 Using protocol version 40
2009-01-04 21:22:54.378 DPMS Deactivated 
2009-01-04 21:23:34.279 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-01-04 21:23:34.279 TV Error: LiveTV not successfully started
2009-01-04 21:23:34.304 TV: Deleting TV Chain in destructor
2009-01-04 21:23:34.321 DPMS Reactivated.
Destroying SipFsm object 
2009-01-04 21:23:39.213 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-04 21:25:11.342 New DB connection, total: 2
2009-01-04 21:25:11.342 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:25:11.344 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 21:25:11.344 Enabled verbose msgs:  important general
2009-01-04 21:25:11.658 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:25:11.660 Primary screen 0.
2009-01-04 21:25:11.660 Using screen 0, 1680x1050 at 0,0
2009-01-04 21:25:11.660 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:25:11.661 Switching to square mode (Mythbuntu-8.04)
2009-01-04 21:25:11.672 Using the Qt painter
2009-01-04 21:25:11.673 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 21:25:11.674 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 21:25:12.512 Specified base font 'medium' does not exist for font clock
2009-01-04 21:25:12.512 Specified base font 'medium' does not exist for font small
2009-01-04 21:25:12.512 Specified base font 'medium' does not exist for font medium
2009-01-04 21:25:12.512 Specified base font 'medium' does not exist for font large
2009-01-04 21:25:12.513 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 21:25:12.637 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 21:25:12.662 Registering Internal as a media playback plugin.
2009-01-04 21:25:12.788 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 21:25:14.320 Failed to run 'cdrecord --scanbus'
2009-01-04 21:25:14.352 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.4:5060 NAT address 192.168.1.4
SIP: Cannot register; proxy, username or password not set
2009-01-04 21:25:14.416 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:25:24.600 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 21:25:24.601 Using protocol version 40
2009-01-04 21:25:24.611 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000149
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000004bc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000035a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002cde74
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002cde78
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e916f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e9173
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003027a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003027a4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0033b624
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0033b629
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003487a9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003487ad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0034a9ac
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0034a9b1
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 1
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: DVD Title: BURN_AFTER_READING
libdvdnav: DVD Serial Number: 39513db0
libdvdnav: DVD Title (Alternative): WIDESCREEN_R0
libdvdnav: Unable to find map file '/home/mark/.dvdnav/BURN AFTER READING.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2009-01-04 21:25:25.762 Opened DVD device at /dev/dvd
2009-01-04 21:25:25.763 There are 7 titles on the disk
2009-01-04 21:25:25.763 Title 0 has 0 parts.
2009-01-04 21:25:25.763 Title 1 has 21 parts.
2009-01-04 21:25:25.763 Title 2 has 2 parts.
2009-01-04 21:25:25.763 Title 3 has 2 parts.
2009-01-04 21:25:25.763 Title 4 has 2 parts.
2009-01-04 21:25:25.763 Title 5 has 2 parts.
2009-01-04 21:25:25.763 Title 6 has 2 parts.
2009-01-04 21:25:26.045 AFD: Opened codec 0x963b330, id(MPEG2VIDEO) type(Video)
2009-01-04 21:25:26.045 NVP: Disabling Audio, params(-1,-1,-1)
2009-01-04 21:25:26.074 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-01-04 21:25:26.110 OSD Theme Dimensions W: 640 H: 480
2009-01-04 21:25:26.648 TV: Changing from None to WatchingPreRecorded
2009-01-04 21:25:26.758 Video timing method: USleep with busy wait
2009-01-04 21:25:37.250 AFD: Warning, video codec 0x963b330 id(MPEG2VIDEO) type (Video) already open.
2009-01-04 21:25:37.368 AFD: codec AC3 has 0 channels
2009-01-04 21:25:37.373 AFD: Opened codec 0xa558d470, id(AC3) type(Audio)
2009-01-04 21:25:37.377 Opening audio device 'default'. ch 2(2) sr 48000
2009-01-04 21:25:37.377 Opening ALSA audio device 'default'.
2009-01-04 21:25:37.451 mixer unable to find control Master 1
2009-01-04 21:25:37.452 NVP: Enabling Audio
2009-01-04 21:25:37.633 GetNextFreeFrame() served a busy frame B. Dropping. AUUUUUUUUUUUUUUUUUUUUUUUUUUUuUL
2009-01-04 21:26:46.507 TV: Attempting to change from WatchingPreRecorded to None
2009-01-04 21:26:46.555 TV: Changing from WatchingPreRecorded to None
2009-01-04 21:27:38.494 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: vm: faild to open/read the DVD
2009-01-04 21:27:38.501 Failed to open DVD device at /dev/dvd
2009-01-04 21:27:56.159 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: vm: faild to open/read the DVD
2009-01-04 21:27:56.168 Failed to open DVD device at /dev/dvd
2009-01-04 21:28:00.404 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: vm: faild to open/read the DVD
2009-01-04 21:28:00.415 Failed to open DVD device at /dev/dvd
2009-01-04 21:28:03.157 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/dvd-ui.xml

2009-01-04 21:28:11.178 Using runtime prefix = /usr
2009-01-04 21:28:11.178 Empty LocalHostName.
2009-01-04 21:28:11.178 Using localhost value of Griffindor
2009-01-04 21:28:11.184 New DB connection, total: 1
2009-01-04 21:28:11.188 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:28:11.189 Closing DB connection named 'DBManager0'
2009-01-04 21:28:11.189 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:28:26.185 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: vm: faild to open/read the DVD
2009-01-04 21:28:26.195 Failed to open DVD device at /dev/dvd
Destroying SipFsm object 
2009-01-04 21:29:02.397 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-04 21:35:53.409 New DB connection, total: 2
2009-01-04 21:35:53.410 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:35:53.411 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 21:35:53.412 Enabled verbose msgs:  important general
2009-01-04 21:35:53.730 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:35:53.732 Primary screen 0.
2009-01-04 21:35:53.732 Using screen 0, 1680x1050 at 0,0
2009-01-04 21:35:53.732 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:35:53.733 Switching to square mode (Mythbuntu-8.04)
2009-01-04 21:35:53.745 Using the Qt painter
2009-01-04 21:35:53.745 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 21:35:53.746 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 21:35:54.624 Specified base font 'medium' does not exist for font clock
2009-01-04 21:35:54.624 Specified base font 'medium' does not exist for font small
2009-01-04 21:35:54.625 Specified base font 'medium' does not exist for font medium
2009-01-04 21:35:54.625 Specified base font 'medium' does not exist for font large
2009-01-04 21:35:54.625 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 21:35:54.750 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 21:35:54.775 Registering Internal as a media playback plugin.
2009-01-04 21:35:54.906 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 21:35:54.995 MythMusic adding CD-Writer: 1,0,0 -- DVDRW SHM-165H6S
2009-01-04 21:35:54.995 MythMusic adding CD-Writer: 1,1,0 -- DVD-RAM GSA-H55N
2009-01-04 21:35:55.028 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.4:5060 NAT address 192.168.1.4
SIP: Cannot register; proxy, username or password not set
2009-01-04 21:35:55.094 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:35:58.504 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 21:35:58.505 Using protocol version 40
2009-01-04 21:36:01.383 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSDestroying SipFsm object 
2009-01-04 21:37:05.062 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-04 21:37:34.254 New DB connection, total: 2
2009-01-04 21:37:34.255 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:37:34.256 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 21:37:34.257 Enabled verbose msgs:  important general
2009-01-04 21:37:34.576 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:37:34.577 Primary screen 0.
2009-01-04 21:37:34.577 Using screen 0, 1680x1050 at 0,0
2009-01-04 21:37:34.577 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:37:34.578 Switching to square mode (Mythbuntu-8.04)
2009-01-04 21:37:34.590 Using the Qt painter
2009-01-04 21:37:34.590 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 21:37:34.591 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 21:37:35.447 Specified base font 'medium' does not exist for font clock
2009-01-04 21:37:35.447 Specified base font 'medium' does not exist for font small
2009-01-04 21:37:35.448 Specified base font 'medium' does not exist for font medium
2009-01-04 21:37:35.448 Specified base font 'medium' does not exist for font large
2009-01-04 21:37:35.448 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 21:37:35.573 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 21:37:35.597 Registering Internal as a media playback plugin.
2009-01-04 21:37:35.729 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 21:37:35.817 MythMusic adding CD-Writer: 1,0,0 -- DVDRW SHM-165H6S
2009-01-04 21:37:35.817 MythMusic adding CD-Writer: 1,1,0 -- DVD-RAM GSA-H55N
2009-01-04 21:37:35.849 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.4:5060 NAT address 192.168.1.4
SIP: Cannot register; proxy, username or password not set
2009-01-04 21:37:35.912 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
2009-01-04 21:39:04.497 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 21:39:04.498 Using protocol version 40
2009-01-04 21:39:04.507 TV: Attempting to change from None to WatchingLiveTV
2009-01-04 21:39:04.508 Using protocol version 40
2009-01-04 21:39:45.616 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-01-04 21:39:45.616 TV Error: LiveTV not successfully started
2009-01-04 21:39:45.642 TV: Deleting TV Chain in destructor
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
Destroying SipFsm object 
2009-01-04 21:46:13.908 Deleting UPnP client...
Starting mythfrontend.real..
2009-01-04 21:49:58.058 New DB connection, total: 2
2009-01-04 21:49:58.058 Connected to database 'mythconverg' at host: localhost
2009-01-04 21:49:58.060 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-01-04 21:49:58.060 Enabled verbose msgs:  important general
2009-01-04 21:49:58.379 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:49:58.381 Primary screen 0.
2009-01-04 21:49:58.381 Using screen 0, 1680x1050 at 0,0
2009-01-04 21:49:58.381 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:49:58.382 Switching to square mode (Mythbuntu-8.04)
2009-01-04 21:49:58.394 Using the Qt painter
2009-01-04 21:49:58.394 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mark/.mythtv/joystickmenurc
2009-01-04 21:49:58.395 lirc init success using configuration file: /home/mark/.mythtv/lircrc
2009-01-04 21:49:59.246 Specified base font 'medium' does not exist for font clock
2009-01-04 21:49:59.246 Specified base font 'medium' does not exist for font small
2009-01-04 21:49:59.246 Specified base font 'medium' does not exist for font medium
2009-01-04 21:49:59.246 Specified base font 'medium' does not exist for font large
2009-01-04 21:49:59.247 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-01-04 21:49:59.375 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-04 21:49:59.400 Registering Internal as a media playback plugin.
2009-01-04 21:49:59.528 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-04 21:49:59.615 MythMusic adding CD-Writer: 1,0,0 -- DVDRW SHM-165H6S
2009-01-04 21:49:59.615 MythMusic adding CD-Writer: 1,1,0 -- DVD-RAM GSA-H55N
2009-01-04 21:49:59.647 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.4:5060 NAT address 192.168.1.4
SIP: Cannot register; proxy, username or password not set
2009-01-04 21:49:59.711 No theme dir: /home/mark/.mythtv/themes/Mythbuntu-8.04
2009-01-04 21:51:38.826 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-04 21:51:38.827 Using protocol version 40
2009-01-04 21:51:39.384 Received a remote 'Clear Cache' request

---

### Post by nisbet on 2009-01-04
After going through them myself it looks like it might be a problem with the encoding. in the backend log this seems to be my problem:

2009-01-04 21:39:04.513 TVRec(1): Changing from None to WatchingLiveTV
2009-01-04 21:39:04.520 TVRec(1): HW Tuner: 1->1
2009-01-04 21:39:05.593 NVR(/dev/video0): Unknown video codec. Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles. Assuming RTjpeg for now.
2009-01-04 21:39:05.594 NVR(/dev/video0) Error: Unknown audio codec
2009-01-04 21:39:05.611 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-04 21:39:05.612 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2009-01-04 21:39:45.619 TVRec(1): Changing from WatchingLiveTV to None
2009-01-04 21:39:45.626 Finished recording Unknown: channel 2002
2009-01-04 21:42:41.074 Expiring 0 MBytes for 2002 @ Sun Jan 4 21:39:04 2009 => Unknown


But I still don't know how to fix it...I tried looked at the software encoding profiles and they were using RTjpeg not sure what else to do.

PS if there is a better way to post logs rather than just pasting them please let me know.

Thanks

---

### Post by joho500 on 2009-01-18
I have a similar problem after updating to 8.10. Playback works fine with ```
mplayer /dev/video0
``` But is broken in mplayer too after having started LiveTV in mythtv.

The corresponding part of mythbackend.log:
```
2009-01-18 10:54:08.825 TVRec(3): Changing from None to WatchingLiveTV
2009-01-18 10:54:08.835 TVRec(3): HW Tuner: 3->3
2009-01-18 10:54:08.847 Channel(/dev/video0) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2009-01-18 10:54:10.090 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-18 10:54:15.649 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-18 10:54:16.684 TVRec(3): Changing from WatchingLiveTV to None
2009-01-18 10:54:21.205 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-18 10:54:21.416 Finished recording Vrije Geluiden: channel 1006
2009-01-18 10:54:21.423 scheduler: Finished recording: Vrije Geluiden: channel 1006
```

Anyone a solution?

Cheers,
Joost

---

### Post by joho500 on 2009-01-18
My problem is solved using the suggestion in this post: [http://www.uluga.ubuntuforums.org/showpost.php?p=6096932&postcount=6]("http://www.uluga.ubuntuforums.org/showpost.php?p=6096932&postcount=6")

Joost

---

