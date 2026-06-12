---
title: "mythbuntu hangs after ten minutes"
date: 2011-07-31
forum: Mythbuntu
---

### Post by blkbx on 2011-07-31
Hi
well the titles says it all really. Here is also a snippet from the myth log

2011-07-31 20:10:25.566 New DB connection, total: 1
2011-07-31 20:10:25.680 Connected to database 'mythconverg' at host: 192.168.2.6
2011-07-31 20:10:25.969 New DB connection, total: 2
2011-07-31 20:10:26.031 New DB connection, total: 3
2011-07-31 20:10:27.598 Reschedule requested for id -1.
2011-07-31 20:10:27.636 New DB connection, total: 4
2011-07-31 20:10:31.222 Connected to database 'mythconverg' at host: 192.168.2.6
2011-07-31 20:10:31.316 New DB connection, total: 5
2011-07-31 20:10:34.595 New DB connection, total: 6
2011-07-31 20:10:34.633 New DB connection, total: 7
2011-07-31 20:10:36.461 Connected to database 'mythconverg' at host: 192.168.2.6
2011-07-31 20:10:41.699 Connected to database 'mythconverg' at host: 192.168.2.6
2011-07-31 20:10:41.828 Scheduled 2 items in 14.2 = 0.04 match + 14.19 place
2011-07-31 20:10:41.870 Seem to be woken up by USER
2011-07-31 20:10:42.112 Connected to database 'mythconverg' at host: 192.168.2.6
2011-07-31 20:10:42.436 Connected to database 'mythconverg' at host: 192.168.2.6
2011-07-31 20:10:42.890 Connected to database 'mythconverg' at host: 192.168.2.6
2011-07-31 20:10:44.596 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-07-31 20:10:44.686 Expiring 4687 MB for 1002 at 2011-07-30T01:30:01 => Infomercial
2011-07-31 20:10:44.714 Expiring 29 MB for 1010 at 2011-07-30T17:57:58 => "Prime News - First At 5.30"
2011-07-31 20:10:44.747 Expiring 332 MB for 1001 at 2011-07-30T18:00:00 => "ONE News At 6"
2011-07-31 20:10:44.781 Expiring 3982 MB for 1003 at 2011-07-30T18:04:23 => "3 News"
2011-07-31 20:10:44.826 Expiring 2588 MB for 1003 at 2011-07-30T19:00:00 => .
2011-07-31 20:12:27.508 Reschedule requested for id -1.
2011-07-31 20:12:27.641 Scheduled 2 items in 0.1 = 0.06 match + 0.07 place
2011-07-31 20:14:00.842 MainServer::ANN Monitor
2011-07-31 20:14:00.885 adding: myth-frontend as a client (events: 0)
2011-07-31 20:14:00.919 MainServer::ANN Monitor
2011-07-31 20:14:00.952 adding: myth-frontend as a client (events: 1)
2011-07-31 20:14:04.888 MainServer::ANN Playback
2011-07-31 20:14:04.963 adding: myth-frontend as a client (events: 0)
2011-07-31 20:14:06.385 TVRec(9): Changing from None to WatchingLiveTV
2011-07-31 20:14:06.482 TVRec(9): HW Tuner: 9->9
2011-07-31 20:14:06.571 LoadFromScheduler(): Error, called from backend.
2011-07-31 20:14:06.577 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-07-31 20:14:07.382 Finished recording 60 Minutes: channel 1003
2011-07-31 20:14:07.428 LoadFromScheduler(): Error, called from backend.
2011-07-31 20:14:07.436 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-07-31 20:14:07.474 Finished recording 60 Minutes: channel 1003
2011-07-31 20:14:07.568 MainServer::ANN Playback
2011-07-31 20:14:07.654 adding: myth-frontend as a client (events: 0)
2011-07-31 20:14:07.733 MainServer::HandleAnnounce FileTransfer
2011-07-31 20:14:07.788 adding: myth-frontend as a remote file transfer
2011-07-31 20:14:09.898 RecBase(9:/dev/dvb/adapter0/frontend0): GetKeyframePositions(1,9223372036854775807,#1) out of 2
2011-07-31 20:14:10.028 RecBase(9:/dev/dvb/adapter0/frontend0): GetKeyframePositions(1,9223372036854775807,#1) out of 2
2011-07-31 20:16:44.896 Expiring 0 MB for 1003 at 2011-07-31T20:14:06 => "60 Minutes"
2011-07-31 20:17:04.043 MainServer::ANN Monitor
2011-07-31 20:17:04.095 adding: backend as a client (events: 2)
2007-01-01 13:25:13.714 mythbackend version: fixes/0.24 [v0.24.1-58-g760c8db] [www.mythtv.org](www.mythtv.org)
2007-01-01 13:25:14.033 Using runtime prefix = /usr
2007-01-01 13:25:14.179 Using configuration directory = /home/mythtv/.mythtv
2007-01-01 13:25:14.258 Using localhost value of backend
2007-01-01 13:25:14.325 Testing network connectivity to '192.168.2.6'
2007-01-01 13:25:14.643 New DB connection, total: 1
2007-01-01 13:25:14.966 Connected to database 'mythconverg' at host: 192.168.2.6
2007-01-01 13:25:15.288 Closing DB connection named 'DBManager0'
2007-01-01 13:25:15.599 Connected to database 'mythconverg' at host: 192.168.2.6
2007-01-01 13:25:16.001 Current locale en_NZ
2007-01-01 13:25:16.207 No locale defaults file for en_NZ, skipping
2007-01-01 13:25:16.258 Current MythTV Schema Version (DBSchemaVer): 1264
2007-01-01 13:25:16.360 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2007-01-01 13:25:16.495 Enabling Upnpmedia rebuild thread.
2007-01-01 13:25:17.728 MythBackend: Starting up as the master server.
2007-01-01 13:25:17.767 New DB connection, total: 2
2007-01-01 13:25:18.153 Connected to database 'mythconverg' at host: 192.168.2.6
2007-01-01 13:25:18.438 New DB connection, total: 3
2007-01-01 13:25:18.708 Connected to database 'mythconverg' at host: 192.168.2.6
2007-01-01 13:25:19.742 TVRec(12) Error: Problem finding starting channel, setting to default of '3'.
2007-01-01 13:25:19.916 ChannelBase(12) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2007-01-01 13:25:19.944 TVRec(13) Error: Problem finding starting channel, setting to default of '3'.
2007-01-01 13:25:19.976 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:20.060 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:20.137 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:20.215 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:20.293 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:20.371 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:20.449 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:20.527 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:20.605 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:20.683 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:20.761 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:20.838 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:20.916 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:20.994 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:21.072 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:21.150 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:21.228 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:21.306 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:21.384 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:21.462 DVBChan(13:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:21.490 DVBChan(13:/dev/dvb/adapter1/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2007-01-01 13:25:21.524 TVRec(14) Error: Problem finding starting channel, setting to default of '3'.
2007-01-01 13:25:21.556 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:21.640 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:21.718 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:21.796 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:21.874 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:21.952 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:22.030 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:22.107 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:22.185 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:22.263 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:22.341 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:22.419 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:22.497 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:22.575 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:22.653 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:22.731 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:22.808 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:22.886 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:22.964 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:23.042 DVBChan(14:/dev/dvb/adapter1/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2007-01-01 13:25:23.070 DVBChan(14:/dev/dvb/adapter1/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2007-01-01 13:25:23.104 New DB scheduler connection
2007-01-01 13:25:23.522 Connected to database 'mythconverg' at host: 192.168.2.6
2007-01-01 13:25:23.549 Scheduler, Warning: Listings source 'card 01' is defined, but is not attached to a card input.
2007-01-01 13:25:23.583 Main::Registering HttpStatus Extension
2007-01-01 13:25:23.626 Enabled verbose msgs:  important general
2007-01-01 13:25:23.675 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2007-01-01 13:25:26.556 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2007-01-01 13:25:26.627 Reschedule requested for id -1.
2007-01-01 13:25:26.645 UPnpMedia: BuildMediaMap Done. Found 135 objects
2007-01-01 13:25:26.796 Scheduled 3 items in 0.2 = 0.09 match + 0.07 place
2007-01-01 13:25:26.832 Seem to be woken up by USER
2011-07-31 20:25:46.542 New DB connection, total: 1
2011-07-31 20:25:46.709 Connected to database 'mythconverg' at host: 192.168.2.6
2011-07-31 20:25:47.056 New DB connection, total: 2
2011-07-31 20:25:47.145 New DB connection, total: 3
2011-07-31 20:25:47.166 Connected to database 'mythconverg' at host: 192.168.2.6
2011-07-31 20:25:47.211 New DB connection, total: 4
2011-07-31 20:25:47.278 New DB connection, total: 5
2011-07-31 20:25:47.289 Connected to database 'mythconverg' at host: 192.168.2.6
2011-07-31 20:25:47.406 New DB connection, total: 6
2011-07-31 20:25:47.464 Connected to database 'mythconverg' at host: 192.168.2.6
2011-07-31 20:25:47.599 Connected to database 'mythconverg' at host: 192.168.2.6
2011-07-31 20:25:47.650 Connected to database 'mythconverg' at host: 192.168.2.6
2011-07-31 20:25:47.693 TVRec(9): Changing from None to RecordingOnly
2011-07-31 20:25:47.735 TVRec(9): HW Tuner: 9->9
2011-07-31 20:25:47.800 TVRec(9): Changing from RecordingOnly to None
2011-07-31 20:25:47.865 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-07-31 20:25:47.914 Started recording: "friday (Manual Record)":"Fri Jan 12 21:25:00 2007": channel 1002 on cardid 9, sourceid 1
2011-07-31 20:25:47.928 TVRec(10): ASK_RECORDING 10 0 0 0
2011-07-31 20:25:47.932 TVRec(11): ASK_RECORDING 11 0 0 0
2011-07-31 20:25:48.085 recording already exists...
2011-07-31 20:25:48.119 TVRec(9): Changing from None to RecordingOnly
2011-07-31 20:25:48.150 TVRec(9): HW Tuner: 9->9
2011-07-31 20:25:48.192 TVRec(9): Changing from RecordingOnly to None
2011-07-31 20:25:48.257 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-07-31 20:25:48.295 Started recording: "friday (Manual Record)":"Fri Jan 19 21:25:00 2007": channel 1002 on cardid 9, sourceid 1
2011-07-31 20:25:48.329 Updating status for "friday (Manual Record)":"Fri Jan 12 21:25:00 2007" on cardid 9 (Tuning => Recorder Failed)
2011-07-31 20:25:48.364 Updating status for "friday (Manual Record)":"Fri Jan 19 21:25:00 2007" on cardid 9 (Tuning => Recorder Failed)
2011-07-31 20:25:49.004 TVRec(10): ASK_RECORDING 10 0 0 0
2011-07-31 20:25:49.050 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 1002 --starttime 20110731202600  > /dev/null'
2011-07-31 20:25:49.082 TVRec(11): ASK_RECORDING 11 0 0 0
2011-07-31 20:25:49.329 Reschedule requested for id 0.
2011-07-31 20:25:49.350 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 1002 --starttime 20110731202601  > /dev/null'
2011-07-31 20:25:49.374 Reschedule requested for id 0.
2011-07-31 20:25:49.463 Reschedule requested for id 0.
2011-07-31 20:25:49.509 Reschedule requested for id 0.
2011-07-31 20:25:49.605 Scheduled 0 items in 0.3 = 0.22 match + 0.05 place
2011-07-31 20:26:43.775 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

Really have no idea where the "2007 ..." has come from.

---

