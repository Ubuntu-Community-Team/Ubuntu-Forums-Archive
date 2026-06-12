---
title: "Problem watching LiveTV with ATI TV Wonder USB"
date: 2010-03-21
forum: Multimedia Software
---

### Post by d_mcqueen on 2010-03-21
I am using the ATI TV Wonder 600 USB>  I have installed it and can get it to work using channels.conf after a scan with VLC, but I get an error watching LiveTV.  My logs are as follows:

```
2010-03-21 16:00:34.188 MainServer::ANN Monitor
2010-03-21 16:00:34.254 adding: mythpvr as a client (events: 1)
2010-03-21 16:00:34.312 Reschedule requested for id -1.
2010-03-21 16:00:34.576 Scheduled 0 items in 0.3 = 0.08 match + 0.18 place
2010-03-21 16:05:05.280 MainServer::ANN Monitor
2010-03-21 16:05:05.353 adding: mythpvr as a client (events: 0)
2010-03-21 16:05:05.410 MainServer::ANN Monitor
2010-03-21 16:05:05.464 adding: mythpvr as a client (events: 1)
2010-03-21 16:05:27.350 MainServer::ANN Playback
2010-03-21 16:05:27.412 adding: mythpvr as a client (events: 0)
2010-03-21 16:05:27.460 TVRec(1): Changing from None to Watching WatchingLiveTV
2010-03-21 16:05:27.521 TVRec(1): HW Tuner: 1->1
2010-03-21 16:05:27.599 DTVMux, Error: Could not find tuning parameters for mplex 32767
2010-03-21 16:05:27.647 DVBChan(1:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(48): Failed to initialize multiplex options
2010-03-21 16:05:27.691 TVRec(1) Error: Failed to set channel to 48. Reverting to kState_None
2010-03-21 16:05:27.736 TVRec(1): Changing from Watching WatchingLiveTV to None
2010-03-21 16:05:37.457 MainServer::ANN Playback
2010-03-21 16:05:37.537 adding: mythpvr as a client (events: 0)
2010-03-21 16:05:37.585 TVRec(1): Changing from None to Watching WatchingLiveTV
2010-03-21 16:05:37.657 TVRec(1): HW Tuner: 1->1
2010-03-21 16:05:37.704 DTVMux, Error: Could not find tuning parameters for mplex 32767
2010-03-21 16:05:37.749 DVBChan(1:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(48): Failed to initialize multiplex options
2010-03-21 16:05:37.816 TVRec(1) Error: Failed to set channel to 48. Reverting to kState_None
2010-03-21 16:05:37.861 TVRec(1): Changing from Watching WatchingLiveTV to None
2010-03-21 16:15:26.209 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-21 16:17:02.131 MainServer::ANN Monitor
2010-03-21 16:17:02.201 adding: mythpvr as a client (events: 0)
2010-03-21 16:30:26.363 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-21 16:40:19.088 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-03-21 16:40:19.212 Using runtime prefix = /usr
2010-03-21 16:40:19.345 Using configuration directory = /home/mythtv/.mythtv
2010-03-21 16:40:19.582 Empty LocalHostName.
2010-03-21 16:40:19.712 Using localhost value of mythpvr
2010-03-21 16:40:20.383 New DB connection, total: 1
2010-03-21 16:40:20.593 Connected to database 'mythconverg' at host: localhost
2010-03-21 16:40:20.671 Closing DB connection named 'DBManager0'
2010-03-21 16:40:20.807 Connected to database 'mythconverg' at host: localhost
2010-03-21 16:40:21.123 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-21 16:40:21.248 MythBackend: Starting up as the master server.
2010-03-21 16:40:21.367 New DB connection, total: 2
2010-03-21 16:40:21.507 Connected to database 'mythconverg' at host: localhost
2010-03-21 16:40:21.801 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2010-03-21 16:40:21.862 DVBChan(1:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2010-03-21 16:40:22.011 DVBChan(2:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2010-03-21 16:40:22.174 DVBChan(2:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2010-03-21 16:40:22.322 Channel(/dev/video0)::Open(): Can't open video device, error "No such file or directory"
2010-03-21 16:40:22.419 MythBackend, Error: No valid capture cards are defined in the database.
			Perhaps you should re-read the installation instructions?
2010-03-21 16:40:22.755 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-03-21 16:40:23.564 Main::Registering HttpStatus Extension
2010-03-21 16:40:23.731 Enabled verbose msgs:  important general
2010-03-21 16:40:23.987 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-21 16:40:36.380 MainServer::ANN Monitor
2010-03-21 16:40:36.419 adding: mythpvr as a client (events: 0)
2010-03-21 16:40:36.465 MainServer::ANN Monitor
2010-03-21 16:40:36.520 adding: mythpvr as a client (events: 1)
2010-03-21 16:41:42.587 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-21 16:56:42.731 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-21 17:03:46.670 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-03-21 17:03:46.783 Using runtime prefix = /usr
2010-03-21 17:03:46.894 Using configuration directory = /home/mythtv/.mythtv
2010-03-21 17:03:47.142 Empty LocalHostName.
2010-03-21 17:03:47.362 Using localhost value of mythpvr
2010-03-21 17:03:47.864 New DB connection, total: 1
2010-03-21 17:03:48.042 Connected to database 'mythconverg' at host: localhost
2010-03-21 17:03:48.109 Closing DB connection named 'DBManager0'
2010-03-21 17:03:48.199 Connected to database 'mythconverg' at host: localhost
2010-03-21 17:03:48.505 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-21 17:03:48.645 MythBackend: Starting up as the master server.
2010-03-21 17:03:48.872 New DB connection, total: 2
2010-03-21 17:03:48.989 Connected to database 'mythconverg' at host: localhost
2010-03-21 17:03:49.543 New DB connection, total: 3
2010-03-21 17:03:49.723 Connected to database 'mythconverg' at host: localhost
2010-03-21 17:03:49.880 DTVMux, Error: Could not find tuning parameters for mplex 32767
2010-03-21 17:03:49.967 DVBChan(1:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(48): Failed to initialize multiplex options
2010-03-21 17:03:50.068 DTVMux, Error: Could not find tuning parameters for mplex 32767
2010-03-21 17:03:50.114 DVBChan(2:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(48): Failed to initialize multiplex options
2010-03-21 17:03:52.902 New DB scheduler connection
2010-03-21 17:03:53.038 Connected to database 'mythconverg' at host: localhost
2010-03-21 17:03:53.360 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-03-21 17:03:53.505 Main::Registering HttpStatus Extension
2010-03-21 17:03:53.616 Enabled verbose msgs:  important general
2010-03-21 17:03:54.024 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-21 17:03:56.215 Reschedule requested for id -1.
2010-03-21 17:03:57.075 Scheduled 0 items in 0.9 = 0.34 match + 0.52 place
2010-03-21 17:03:57.166 Seem to be woken up by USER
2010-03-21 17:04:03.795 MainServer::ANN Monitor
2010-03-21 17:04:03.838 adding: mythpvr as a client (events: 0)
2010-03-21 17:04:03.895 MainServer::ANN Monitor
2010-03-21 17:04:03.949 adding: mythpvr as a client (events: 1)
2010-03-21 17:04:38.378 MainServer::ANN Playback
2010-03-21 17:04:38.425 adding: mythpvr as a client (events: 0)
2010-03-21 17:04:38.501 TVRec(1): Changing from None to Watching WatchingLiveTV
2010-03-21 17:04:38.557 TVRec(1): HW Tuner: 1->1
2010-03-21 17:04:38.625 DTVMux, Error: Could not find tuning parameters for mplex 32767
2010-03-21 17:04:38.681 DVBChan(1:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(48): Failed to initialize multiplex options
2010-03-21 17:04:38.737 TVRec(1) Error: Failed to set channel to 48. Reverting to kState_None
2010-03-21 17:04:38.793 TVRec(1): Changing from Watching WatchingLiveTV to None
```

---

