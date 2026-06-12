---
title: "Storage Groups, External RAID"
date: 2012-06-10
forum: Mythbuntu
---

### Post by jlp_engineer on 2012-06-10
I am attempting to attach an external RAID enclosure to my Mythbuntu 12.04 master backend.  When I modify the paths in the storage groups, everything works fine until I change the path for the default group.  When I do this, LiveTV no longer works even though there is a LiveTV storage group defined. The frontend will freeze as soon as you select Watch TV. A few minutes later the FE complains that the connection to the backend has been lost, and then when you click OK, another message that all tuners are busy. Change the default back to /var/lib/mythtv/recordings then everything returns to normal. I have checked permissions, corrected one error. But the problem still happens.

Suggestions?

---

### Post by nickrout on 2012-06-10
logs?

---

### Post by anonymousdog on 2012-06-10
particularly backend logs

---

### Post by jlp_engineer on 2012-06-12
Backend Log:



```
Jun 12 00:30:04 MYTHMBE mythbackend[1856]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythbackend version: fixes/0.25 [v0.25.1] [www.mythtv.org](www.mythtv.org)
Jun 12 00:30:04 MYTHMBE mythbackend[1856]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jun 12 00:30:04 MYTHMBE mythbackend[1856]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Jun 12 00:30:04 MYTHMBE mythbackend[1856]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Jun 12 00:30:04 MYTHMBE mythbackend[1856]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Jun 12 00:30:04 MYTHMBE mythbackend[1856]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Jun 12 00:30:04 MYTHMBE mythbackend[1856]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Jun 12 00:30:04 MYTHMBE mythbackend[1856]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Jun 12 00:30:04 MYTHMBE mythbackend[1856]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Jun 12 00:30:04 MYTHMBE mythbackend[1856]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 12 00:30:04 MYTHMBE mythbackend[1856]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
Jun 12 00:30:04 MYTHMBE mythbackend[1856]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Jun 12 00:30:04 MYTHMBE mythbackend[1856]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of MYTHMBE
Jun 12 00:30:05 MYTHMBE mythbackend[1856]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
Jun 12 00:30:05 MYTHMBE mythbackend[1856]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
Jun 12 00:30:05 MYTHMBE mythbackend[1856]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 12 00:30:06 MYTHMBE mythbackend[1856]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Jun 12 00:30:06 MYTHMBE mythbackend[1856]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Jun 12 00:30:06 MYTHMBE mythbackend[1856]: N CoreContext main_helpers.cpp:556 (run_backend) MythBackend: Starting up as the master server.
Jun 12 00:30:11 MYTHMBE mythbackend[1856]: I CoreContext programinfo.cpp:2052 (CheckProgramIDAuthorities) Found 1 distinct programid authorities
Jun 12 00:30:11 MYTHMBE mythbackend[1856]: I Scheduler mythdbcon.cpp:422 (getStaticCon) New static DB connectionSchedCon
Jun 12 00:30:11 MYTHMBE mythbackend[1856]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 127.0.0.1:6544
Jun 12 00:30:11 MYTHMBE mythbackend[1856]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 192.168.1.100:6544
Jun 12 00:30:11 MYTHMBE mythbackend[1856]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP [::1]:6544
Jun 12 00:30:12 MYTHMBE mythbackend[1856]: I CoreContext main_helpers.cpp:626 (run_backend) Main::Registering HttpStatus Extension
Jun 12 00:30:12 MYTHMBE mythbackend[1856]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 127.0.0.1:6543
Jun 12 00:30:12 MYTHMBE mythbackend[1856]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 192.168.1.100:6543
Jun 12 00:30:12 MYTHMBE mythbackend[1856]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP [::1]:6543
Jun 12 00:30:12 MYTHMBE mythbackend[1856]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Jun 12 00:30:13 MYTHMBE mythbackend[1856]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythbackend on MYTHMBE' type '_mythbackend-master._tcp.' domain: 'local.'
Jun 12 00:30:14 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id -1.
Jun 12 00:30:14 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 0 items in 0.1 = 0.03 match + 0.03 place
Jun 12 00:30:14 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2135 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
Jun 12 00:30:21 MYTHMBE mythbackend[1856]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun 12 00:30:25 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun 12 00:30:25 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MYTHMBE as a client (events: 0)
Jun 12 00:30:25 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun 12 00:30:25 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MYTHMBE as a client (events: 1)
Jun 12 00:30:25 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Jun 12 00:30:25 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythmbe as a client (events: 0)
Jun 12 00:30:25 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun 12 00:30:25 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythmbe as a remote file transfer
Jun 12 00:30:52 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun 12 00:30:52 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: tzcheck as a client (events: 0)
Jun 12 00:30:54 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1410 (HandleAnnounce) adding: MYTHSBE as a slave backend server
Jun 12 00:30:54 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Jun 12 00:30:54 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
Jun 12 00:31:02 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun 12 00:31:02 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MYTHSBE as a client (events: 0)
Jun 12 00:31:02 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun 12 00:31:02 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MYTHSBE as a client (events: 1)
Jun 12 00:31:17 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Jun 12 00:31:17 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythsbe as a client (events: 0)
Jun 12 00:31:17 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jun 12 00:31:17 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythsbe as a remote file transfer
Jun 12 00:31:27 MYTHMBE mythbackend[1856]: E FreeSpaceUpdater mythsocket.cpp:534 (readStringList) MythSocket(990c388:64): readStringList: Error, timed out after 30000 ms.
Jun 12 00:31:27 MYTHMBE mythbackend[1856]: E FreeSpaceUpdater mainserver.cpp:5700 (connectionClosed) Slave backend: MYTHSBE no longer connected
Jun 12 00:31:27 MYTHMBE mythbackend[1856]: E FreeSpaceUpdater playbacksock.cpp:132 (SendReceiveStringList) PlaybackSock::SendReceiveStringList(): No response.
Jun 12 00:31:27 MYTHMBE mythbackend[1856]: E Update mythsocket.cpp:311 (writeStringList) MythSocket(990c388:-1): writeStringList: Error, called with unconnected socket.
Jun 12 00:31:27 MYTHMBE mythbackend[1856]: E Update mythsocket.cpp:520 (readStringList) MythSocket(990c388:-1): readStringList: Error, called with unconnected socket.
Jun 12 00:31:27 MYTHMBE mythbackend[1856]: E Update playbacksock.cpp:132 (SendReceiveStringList) PlaybackSock::SendReceiveStringList(): No response.
Jun 12 00:31:27 MYTHMBE mythbackend[1856]: N Update autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Jun 12 00:31:27 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Jun 12 00:31:27 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
Jun 12 00:31:28 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1410 (HandleAnnounce) adding: MYTHSBE as a slave backend server
Jun 12 00:31:28 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Jun 12 00:31:28 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
Jun 12 00:31:59 MYTHMBE mythbackend[1856]: E Expire mythsocket.cpp:534 (readStringList) MythSocket(99186d8:64): readStringList: Error, timed out after 30000 ms.
Jun 12 00:31:59 MYTHMBE mythbackend[1856]: E Expire mainserver.cpp:5700 (connectionClosed) Slave backend: MYTHSBE no longer connected
Jun 12 00:31:59 MYTHMBE mythbackend[1856]: E Expire playbacksock.cpp:132 (SendReceiveStringList) PlaybackSock::SendReceiveStringList(): No response.
Jun 12 00:31:59 MYTHMBE mythbackend[1856]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Jun 12 00:31:59 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Jun 12 00:31:59 MYTHMBE mythbackend[1856]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x98e5cf8)
Jun 12 00:31:59 MYTHMBE mythbackend[1856]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x98e5cf8)
Jun 12 00:31:59 MYTHMBE mythbackend[1856]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(98e5cf8:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 21 bytes with 1 errors#012#011#011#011starts with: 13      ACCEPT[]:[]72
Jun 12 00:31:59 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.02 place
Jun 12 00:32:00 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1410 (HandleAnnounce) adding: MYTHSBE as a slave backend server
Jun 12 00:32:00 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Jun 12 00:32:00 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: E Update mythsocket.cpp:534 (readStringList) MythSocket(989f0a8:65): readStringList: Error, timed out after 30000 ms.
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: E Update mainserver.cpp:5700 (connectionClosed) Slave backend: MYTHSBE no longer connected
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: E Update playbacksock.cpp:132 (SendReceiveStringList) PlaybackSock::SendReceiveStringList(): No response.
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: N Update autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x98e5a28)
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x98e5a28)
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(98e5a28:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 21 bytes with 1 errors#012#011#011#011starts with: 13      ACCEPT[]:[]72
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x98e6020)
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x98e6020)
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x98e5ad0)
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x98e5ad0)
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(98e5ad0:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 21 bytes with 1 errors#012#011#011#011starts with: 13      ACCEPT[]:[]72
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(98e6020:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 21 bytes with 1 errors#012#011#011#011starts with: 13      ACCEPT[]:[]72
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MYTHFE1 as a client (events: 0)
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MYTHFE1 as a client (events: 1)
Jun 12 00:32:34 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
Jun 12 00:32:35 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1410 (HandleAnnounce) adding: MYTHSBE as a slave backend server
Jun 12 00:32:35 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Jun 12 00:32:35 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
Jun 12 00:33:09 MYTHMBE mythbackend[1856]: E Update mythsocket.cpp:534 (readStringList) MythSocket(990cb80:65): readStringList: Error, timed out after 30000 ms.
Jun 12 00:33:09 MYTHMBE mythbackend[1856]: E Update mainserver.cpp:5700 (connectionClosed) Slave backend: MYTHSBE no longer connected
Jun 12 00:33:09 MYTHMBE mythbackend[1856]: E Update playbacksock.cpp:132 (SendReceiveStringList) PlaybackSock::SendReceiveStringList(): No response.
Jun 12 00:33:09 MYTHMBE mythbackend[1856]: N Update autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Jun 12 00:33:09 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Jun 12 00:33:09 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
Jun 12 00:33:10 MYTHMBE mythbackend[1856]: I ProcessRequest mainserver.cpp:1410 (HandleAnnounce) adding: MYTHSBE as a slave backend server
Jun 12 00:33:10 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Jun 12 00:33:10 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
Jun 12 00:33:44 MYTHMBE mythbackend[1856]: E Update mythsocket.cpp:534 (readStringList) MythSocket(99091d8:64): readStringList: Error, timed out after 30000 ms.
Jun 12 00:33:44 MYTHMBE mythbackend[1856]: E Update mainserver.cpp:5700 (connectionClosed) Slave backend: MYTHSBE no longer connected
Jun 12 00:33:44 MYTHMBE mythbackend[1856]: E Update playbacksock.cpp:132 (SendReceiveStringList) PlaybackSock::SendReceiveStringList(): No response.
Jun 12 00:33:44 MYTHMBE mythbackend[1856]: N Update autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Jun 12 00:33:44 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
Jun 12 00:33:44 MYTHMBE mythbackend[1856]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
```

Frontend logs from the remote frontend that initiated the LiveTV request:

```
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25.1] www.mythtv.org
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/jpreston/.mythtv
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of MYTHFE1
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I CoreContext mythcontext.cpp:608 (TestDBconnection) Testing network connectivity to '192.168.1.100'
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to en_US
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale en_US
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1440x900 59.887 Hz
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 127.0.0.1:6547
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 192.168.1.9:6547
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP [::1]:6547
Jun 12 00:31:48 MYTHFE1 mythfrontend[1524]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP [fe80::201:2eff:fe2b:fb17%eth0]:6547
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: E CoreContext mythraopconnection.cpp:1276 (LoadKey) RAOP Conn: Failed to read key from: /home/jpreston/.mythtv/RAOPKey.rsa
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/jpreston/.mythtv/lircrc' config
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/jpreston/.mythtv/joystickmenurc
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: I CoreContext serverpool.cpp:424 (bind) Binding to UDP 127.0.0.1:6948
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: I CoreContext serverpool.cpp:424 (bind) Binding to UDP 192.168.1.9:6948
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: I CoreContext serverpool.cpp:424 (bind) Binding to UDP [::1]:6948
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: I CoreContext serverpool.cpp:424 (bind) Binding to UDP [fe80::201:2eff:fe2b:fb17%eth0]:6948
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: I CoreContext serverpool.cpp:424 (bind) Binding to UDP 192.168.1.255:6948
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: I CoreContext mythmainwindow.cpp:948 (Init) Using Frameless Window
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: I CoreContext mythmainwindow.cpp:961 (Init) Using Full Screen Window
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: I CoreContext mythmainwindow.cpp:1013 (Init) Trying the OpenGL painter
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: W CoreContext util-nvctrl.cpp:62 (CheckNVOpenGLSyncToVBlank) NVCtrl: OpenGL Sync to VBlank is disabled.
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: W CoreContext util-nvctrl.cpp:63 (CheckNVOpenGLSyncToVBlank) NVCtrl: For best results enable this in NVidia settings or try running:
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: W CoreContext util-nvctrl.cpp:64 (CheckNVOpenGLSyncToVBlank) NVCtrl: nvidia-settings -a "SyncToVBlank=1"
Jun 12 00:31:49 MYTHFE1 mythfrontend[1524]: W CoreContext util-nvctrl.cpp:76 (CheckNVOpenGLSyncToVBlank) NVCtrl: Alternatively try setting the '__GL_SYNC_TO_VBLANK' environment variable.
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: I CoreContext mythrender_opengl1.cpp:77 (InitFeatures) OpenGL1: Fragment program support available
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: I CoreContext mythrender_opengl.cpp:932 (InitFeatures) OpenGL: OpenGL vendor  : NVIDIA Corporation
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: I CoreContext mythrender_opengl.cpp:934 (InitFeatures) OpenGL: OpenGL renderer: ION/integrated/SSE2
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: I CoreContext mythrender_opengl.cpp:936 (InitFeatures) OpenGL: OpenGL version : 3.3.0 NVIDIA 295.40
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: I CoreContext mythrender_opengl.cpp:938 (InitFeatures) OpenGL: Max texture size: 8192 x 8192
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: I CoreContext mythrender_opengl.cpp:940 (InitFeatures) OpenGL: Max texture units: 4
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: I CoreContext mythrender_opengl.cpp:942 (InitFeatures) OpenGL: Direct rendering: Yes
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: I CoreContext mythrender_opengl.cpp:949 (InitFeatures) OpenGL: PixelBufferObject support available
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: I CoreContext mythrender_opengl.cpp:127 (Init) OpenGL: Initialised MythRenderOpenGL
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Jun 12 00:31:50 MYTHFE1 mythfrontend[1524]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Jun 12 00:31:51 MYTHFE1 mythfrontend[1524]: N CoreContext mythmainwindow.cpp:1862 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Jun 12 00:31:51 MYTHFE1 mythfrontend[1524]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
Jun 12 00:31:51 MYTHFE1 mythfrontend[1524]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
Jun 12 00:31:51 MYTHFE1 mythfrontend[1524]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
Jun 12 00:31:51 MYTHFE1 mythfrontend[1524]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Mythbuntu'
Jun 12 00:31:51 MYTHFE1 mythfrontend[1524]: I Reconnect mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
Jun 12 00:31:51 MYTHFE1 mythfrontend[1524]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on MYTHFE1' type '_mythfrontend._tcp.' domain: 'local.'
Jun 12 00:31:58 MYTHFE1 mythfrontend[1524]: E Reconnect mythsocket.cpp:534 (readStringList) MythSocket(7fe1c80149d0:62): readStringList: Error, timed out after 7000 ms.
Jun 12 00:31:58 MYTHFE1 mythfrontend[1524]: C Reconnect mythcorecontext.cpp:1154 (CheckProtoVersion) Protocol version check failure.#012#011#011#011The response to MYTH_PROTO_VERSION was empty.#012#011#011#011This happens when the backend is too busy to respond,#012#011#011#011or has deadlocked in due to bugs or hardware failure.
Jun 12 00:32:03 MYTHFE1 mythfrontend[1524]: I Reconnect mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
Jun 12 00:32:10 MYTHFE1 mythfrontend[1524]: E Reconnect mythsocket.cpp:534 (readStringList) MythSocket(7fe1c80149d0:52): readStringList: Error, timed out after 7000 ms.
Jun 12 00:32:10 MYTHFE1 mythfrontend[1524]: C Reconnect mythcorecontext.cpp:1154 (CheckProtoVersion) Protocol version check failure.#012#011#011#011The response to MYTH_PROTO_VERSION was empty.#012#011#011#011This happens when the backend is too busy to respond,#012#011#011#011or has deadlocked in due to bugs or hardware failure.
Jun 12 00:32:10 MYTHFE1 mythfrontend[1524]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
Jun 12 00:32:17 MYTHFE1 mythfrontend[1524]: E CoreContext mythsocket.cpp:534 (readStringList) MythSocket(1a22f40:52): readStringList: Error, timed out after 7000 ms.
Jun 12 00:32:17 MYTHFE1 mythfrontend[1524]: C CoreContext mythcorecontext.cpp:1154 (CheckProtoVersion) Protocol version check failure.#012#011#011#011The response to MYTH_PROTO_VERSION was empty.#012#011#011#011This happens when the backend is too busy to respond,#012#011#011#011or has deadlocked in due to bugs or hardware failure.
Jun 12 00:32:17 MYTHFE1 mythfrontend[1524]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
Jun 12 00:32:24 MYTHFE1 mythfrontend[1524]: E CoreContext mythsocket.cpp:534 (readStringList) MythSocket(19af420:52): readStringList: Error, timed out after 7000 ms.
Jun 12 00:32:24 MYTHFE1 mythfrontend[1524]: C CoreContext mythcorecontext.cpp:1154 (CheckProtoVersion) Protocol version check failure.#012#011#011#011The response to MYTH_PROTO_VERSION was empty.#012#011#011#011This happens when the backend is too busy to respond,#012#011#011#011or has deadlocked in due to bugs or hardware failure.
Jun 12 00:32:29 MYTHFE1 mythfrontend[1524]: I Reconnect mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
Jun 12 00:32:34 MYTHFE1 mythfrontend[1524]: I Reconnect mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Jun 12 00:32:41 MYTHFE1 mythfrontend[1524]: N CoreContext mythmainwindow.cpp:2591 (PauseIdleTimer) Resuming idle timer
Jun 12 00:32:41 MYTHFE1 mythfrontend[1524]: N CoreContext mythmainwindow.cpp:2591 (PauseIdleTimer) Resuming idle timer
Jun 12 00:32:41 MYTHFE1 mythfrontend[1524]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on MYTHFE1'
Jun 12 00:32:41 MYTHFE1 mythfrontend[1524]: I CoreContext mythraopdevice.cpp:82 (Cleanup) RAOP Device: Cleaning up.
Jun 12 00:32:41 MYTHFE1 mythfrontend[1524]: I CoreContext mythairplayserver.cpp:260 (Cleanup) AirPay: Cleaning up.
Jun 12 00:32:41 MYTHFE1 mythfrontend[1524]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
Jun 12 00:32:43 MYTHFE1 mythfrontend[1524]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
Jun 12 00:32:43 MYTHFE1 mythfrontend[1524]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
Jun 12 00:32:43 MYTHFE1 mythfrontend[1524]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.
```

And just in case, here are the logs from the slave backend that has the tuner in it that was called for (same thing happens if I call for a tuner in the master, however):

```
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythbackend version: fixes/0.25 [v0.25.1] www.mythtv.org
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of MYTHSBE
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: I CoreContext mythcontext.cpp:608 (TestDBconnection) Testing network connectivity to '192.168.1.100'
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Jun 12 00:30:50 MYTHSBE mythbackend[1388]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to en_US
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale en_US
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext main_helpers.cpp:483 (connect_to_master) Backend is running in America/Chicago time zone.
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: N CoreContext main_helpers.cpp:560 (run_backend) MythBackend: Running as a slave backend.
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(7, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(7, NTSC) (v4l v2) input_switch: 0 mode_switch: 0
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video1): SetInputAndFormat(8, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video1): SetInputAndFormat(8, NTSC) (v4l v2) input_switch: 0 mode_switch: 0
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video2): SetInputAndFormat(9, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video2): SetInputAndFormat(9, NTSC) (v4l v2) input_switch: 0 mode_switch: 0
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 127.0.0.1:6544
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 192.168.1.110:6544
Jun 12 00:30:51 MYTHSBE mythbackend[1388]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP [::1]:6544
Jun 12 00:30:52 MYTHSBE mythbackend[1388]: I CoreContext main_helpers.cpp:626 (run_backend) Main::Registering HttpStatus Extension
Jun 12 00:30:52 MYTHSBE mythbackend[1388]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 127.0.0.1:6543
Jun 12 00:30:52 MYTHSBE mythbackend[1388]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 192.168.1.110:6543
Jun 12 00:30:52 MYTHSBE mythbackend[1388]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP [::1]:6543
Jun 12 00:30:54 MYTHSBE mythbackend[1388]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythbackend on MYTHSBE' type '_mythbackend-slave._tcp.' domain: 'local.'
Jun 12 00:30:54 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:30:54 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:30:58 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(887b7f0:30): writeStringList: Error, invalid string list.
Jun 12 00:31:03 MYTHSBE mythbackend[1388]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun 12 00:31:29 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:31:29 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:31:30 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(88daee8:30): writeStringList: Error, invalid string list.
Jun 12 00:32:00 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:32:00 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:32:05 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8873ae8:30): writeStringList: Error, invalid string list.
Jun 12 00:32:35 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:32:35 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:32:39 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8869d78:30): writeStringList: Error, invalid string list.
Jun 12 00:33:11 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:33:11 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:33:15 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(886b200:30): writeStringList: Error, invalid string list.
Jun 12 00:33:45 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:33:45 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:33:49 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8871540:30): writeStringList: Error, invalid string list.
Jun 12 00:34:20 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:34:20 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:34:24 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8869d78:30): writeStringList: Error, invalid string list.
Jun 12 00:34:55 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:34:55 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:34:59 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8876320:30): writeStringList: Error, invalid string list.
Jun 12 00:35:30 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:35:30 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:35:34 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8871448:30): writeStringList: Error, invalid string list.
Jun 12 00:36:03 MYTHSBE mythbackend[1388]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun 12 00:36:05 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:36:05 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:36:09 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8869d78:30): writeStringList: Error, invalid string list.
Jun 12 00:36:40 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:36:40 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:36:44 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(887aa90:30): writeStringList: Error, invalid string list.
Jun 12 00:37:15 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:37:15 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:37:19 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8871488:30): writeStringList: Error, invalid string list.
Jun 12 00:37:50 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:37:50 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:37:54 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8873ae8:30): writeStringList: Error, invalid string list.
Jun 12 00:38:25 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:38:25 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:38:29 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8876268:30): writeStringList: Error, invalid string list.
Jun 12 00:39:00 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:39:00 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:39:04 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(887ab30:30): writeStringList: Error, invalid string list.
Jun 12 00:39:35 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:39:35 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:39:39 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(88707a0:30): writeStringList: Error, invalid string list.
Jun 12 00:40:10 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:40:10 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:40:14 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8876268:30): writeStringList: Error, invalid string list.
Jun 12 00:40:45 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:40:45 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:40:49 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8878268:30): writeStringList: Error, invalid string list.
Jun 12 00:41:10 MYTHSBE mythbackend[1388]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun 12 00:41:20 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:41:20 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:41:24 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8886e20:30): writeStringList: Error, invalid string list.
Jun 12 00:41:55 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:41:55 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:41:59 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8878268:30): writeStringList: Error, invalid string list.
Jun 12 00:42:30 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:42:30 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:42:34 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(886c4d0:30): writeStringList: Error, invalid string list.
Jun 12 00:43:05 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:43:05 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:43:09 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8866bc0:30): writeStringList: Error, invalid string list.
Jun 12 00:43:40 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:43:40 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:43:44 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8878268:30): writeStringList: Error, invalid string list.
Jun 12 00:44:15 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:44:15 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:44:19 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(886c4d0:30): writeStringList: Error, invalid string list.
Jun 12 00:44:50 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:44:50 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:44:54 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8882e70:30): writeStringList: Error, invalid string list.
Jun 12 00:45:25 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:45:25 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:45:29 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(886c510:30): writeStringList: Error, invalid string list.
Jun 12 00:46:00 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:46:00 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:46:04 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(888a8f0:30): writeStringList: Error, invalid string list.
Jun 12 00:46:17 MYTHSBE mythbackend[1388]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun 12 00:46:35 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:46:35 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:46:39 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8886e20:30): writeStringList: Error, invalid string list.
Jun 12 00:47:10 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:47:10 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:47:14 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(887e050:30): writeStringList: Error, invalid string list.
Jun 12 00:47:45 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:47:45 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:47:49 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(888a8f0:30): writeStringList: Error, invalid string list.
Jun 12 00:48:20 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:48:20 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:48:24 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8886e20:30): writeStringList: Error, invalid string list.
Jun 12 00:48:55 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:48:55 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:48:59 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(888a8f0:30): writeStringList: Error, invalid string list.
Jun 12 00:49:30 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:49:30 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:49:34 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(886c568:30): writeStringList: Error, invalid string list.
Jun 12 00:50:05 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:50:05 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:50:09 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8886e20:30): writeStringList: Error, invalid string list.
Jun 12 00:50:40 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:50:40 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:50:44 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8882e58:30): writeStringList: Error, invalid string list.
Jun 12 00:51:15 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:51:15 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:51:19 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8877c18:30): writeStringList: Error, invalid string list.
Jun 12 00:51:22 MYTHSBE mythbackend[1388]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun 12 00:51:50 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:51:50 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:51:54 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(888a980:30): writeStringList: Error, invalid string list.
Jun 12 00:52:25 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:52:25 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:52:29 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8882e38:30): writeStringList: Error, invalid string list.
Jun 12 00:53:00 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.100:6543
Jun 12 00:53:00 MYTHSBE mythbackend[1388]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
Jun 12 00:53:04 MYTHSBE mythbackend[1388]: E ProcessRequest mythsocket.cpp:304 (writeStringList) MythSocket(8865ed8:30): writeStringList: Error, invalid string list.
```

Please let me know if any directory listings with permissions displayed would be of any assistance and I will post those as well.

Thank you.

---

### Post by nickrout on 2012-06-12
What path do you have set as the storage group?

Are there any SG's set on the SBE?

I hate the new log format of mythtv, it is impossible to read on a page like this, I suggest you put it on pastebin and post the link.

---

### Post by nickrout on 2012-06-12
The backend appears to have crashed.

> Jun 12 00:31:58 MYTHFE1 mythfrontend[1524]: C Reconnect mythcorecontext.cpp:1154 (CheckProtoVersion) Protocol version check failure.#012#011#011#011The response to MYTH_PROTO_VERSION was empty.#012#011#011#011This happens when the backend is too busy to respond,#012#011#011#011or has deadlocked in due to bugs or hardware failure.
Jun 12 00:32:03 MYTHFE1 mythfrontend[1524]: I Reconnect mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
Jun 12 00:32:10 MYTHFE1 mythfrontend[1524]: E Reconnect mythsocket.cpp:534 (readStringList) MythSocket(7fe1c80149d0:52): readStringList: Error, timed out after 7000 ms.
Jun 12 00:32:10 MYTHFE1 mythfrontend[1524]: C Reconnect mythcorecontext.cpp:1154 (CheckProtoVersion) Protocol version check failure.#012#011#011#011The response to MYTH_PROTO_VERSION was empty.#012#011#011#011This happens when the backend is too busy to respond,#012#011#011#011or has deadlocked in due to bugs or hardware failure.

---

### Post by jlp_engineer on 2012-06-12
> **nickrout said:**
> What path do you have set as the storage group?

Are there any SG's set on the SBE?

I hate the new log format of mythtv, it is impossible to read on a page like this, I suggest you put it on pastebin and post the link.

There are no SG's on the SBE.  

Here are the links on Pastebin for the logs:

Backend log: [http://pastebin.com/Dfw0xExc](http://pastebin.com/Dfw0xExc)

Slave Backend log: [http://pastebin.com/v2wqraf0](http://pastebin.com/v2wqraf0)

Frontend Log: [http://pastebin.com/PNCuTXKZ](http://pastebin.com/PNCuTXKZ)

---

### Post by jlp_engineer on 2012-06-12
> **nickrout said:**
> The backend appears to have crashed.

OK, I am guessing that the RAID storage unit, which is connected via eSATA, is somehow causing the issue, even though copying using Thunar, Gnome Commander, or even via Terminal, works just fine.  The storage system is mounted at /mnt/mythstor.  Then I created the same folder structure that exists under /var/lib for mythtv, so /mnt/mythstor/mythtv, and then all the folders necessary for SG's.

I will keep trying, and post any progress here.  Things I will try next are:

1 - Using a second internal hard disk

2 - Use a different external RAID box, instead of the one I am using now, with different hard disks.

Later...

---

### Post by jlp_engineer on 2012-06-16
OK....

I have done everything I know of to figure this thing out.  I tried a different brand/model of RAID unit - same problem.  I tried an internal hard disk, using a separate interface from the RAID system - same problem.  I tried them both again, this time with the file systems formatted as ext4, and not XFS - same problem.  

I can move all the storage groups from the root file system to secondary internal or external storage.  I can load up the videos storage group path with videos on the external RAID device or the internal 2nd hard disk, and I can play videos all day long from any one of my frontends, either local to the backends or stand-alone remotes, and they work fine.  BUT, as soon as I move the default storage group off of the root file system, no liveTV.  The frontend locks up, and then moments later (about 30 seconds or less sometimes) I get the message that the backend server has gone away, and then that all the tuners are busy.  What the heck does the default group have to do with LiveTV anyway.  Isn't there already a group for that? :-k  

I was able to get video for several seconds on the FE that sits on the MBE, but then once I tried to change to a tuner on the slave - BANG!  It hung, never to return.  :-\"

I am about at my wits end on this, and numerous google searches have come up empty.  I am about ready to admit defeat and just put a really large drive with the main root file system, keep the default group where it is happy, and then put all my videos on the external RAID unit.  ](*,)

I know someone else has to be running their default group on a secondary hard disk - what is your secret ???  :confused:

---

### Post by nickrout on 2012-06-16
How  is this RAID device mounted - I guess either cifs or nfs. 

Go into command line and change to mythtv user. Try to create a file in the directory you have set as the default SG:```
sudo su - mythtv
touch /mnt/mountpoint/defaultsgpath/test
```

This will confirm whether the mythtv user has write permissions on that directory.

A point of difference between videos and recordings of course is that mythtv doesn't have to write to the videos SG whereas recordings does have to write to the default SG.

---

### Post by jlp_engineer on 2012-06-17
> **nickrout said:**
> How  is this RAID device mounted - I guess either cifs or nfs

It is a directly attached type of storage unit (eSATA).  It is one of the units our company sells.

[http://www.sabioproducts.com/images/sabio/pdfs/DM4UsersManual_V1.1.pdf](http://www.sabioproducts.com/images/sabio/pdfs/DM4UsersManual_V1.1.pdf)

> Go into command line and change to mythtv user. Try to create a file in the directory you have set as the default SG:```
sudo su - mythtv
touch /mnt/mountpoint/defaultsgpath/test
```

This will confirm whether the mythtv user has write permissions on that directory.

A point of difference between videos and recordings of course is that mythtv doesn't have to write to the videos SG whereas recordings does have to write to the default SG.

OK, did that, and the test file was created without an issue.  There does seem to be a file that is rather strange sitting in the directory.  Perhaps you can tell me what it is.

```

mythtv@MYTHMBE:~$ touch /mnt/hdd/mythtv/recordings/test
mythtv@MYTHMBE:~$ ls -l /mnt/hdd/mythtv/recordings
total 1080
-rw-r--r-- 1 root   mythtv 1105009 Jun  4 12:14 mythconverg-1299-20120604121413.sql.gz
-rw-r--r-- 1 mythtv mythtv       0 Jun 16 23:10 test
mythtv@MYTHMBE:~$ 

```

Here is a directory listing of the folders showing the recordings folder:
```


mythtv@MYTHMBE:~$ ls -l /mnt/hdd/mythtv
total 52
drwxrwsrwx 2 mythtv mythtv 4096 Jun 15 10:50 banners
drwxrwsrwx 2 mythtv mythtv 4096 Apr 23 08:34 bare-client
drwxrwsrwx 2 mythtv mythtv 4096 Jun 15 10:50 coverart
drwxrwsrwx 2 mythtv mythtv 4096 Jun 15 10:50 db_backups
drwxrwsrwx 2 mythtv mythtv 4096 Jun 15 10:50 fanart
drwxrwsrwx 2 mythtv mythtv 4096 Jun 16 23:09 livetv
drwxrwsrwx 2 mythtv mythtv 4096 Apr 10 04:30 music
drwxrwxrwx 2 mythtv mythtv 4096 Apr 10 04:30 pictures
drwxrwsrwx 2 mythtv mythtv 4096 Jun 16 23:10 recordings
drwxrwsrwx 2 mythtv mythtv 4096 Jun 15 10:50 screenshots
drwxrwsrwx 2 mythtv mythtv 4096 May 30 07:39 streaming
drwxrwsrwx 2 mythtv mythtv 4096 Jun 15 10:50 trailers
drwxrwsrwx 2 mythtv mythtv 4096 Jun 16 23:09 videos
mythtv@MYTHMBE:~$ 

```

I changed the access and permissions manually, so that anyone or anything can write to the recordings folder.  Is there a way to put the Backend into a debug mode so it will show exactly what it is doing and what is failing when I initiate a LiveTV session from a remote frontend?

Do you have any more ideas?  Anyone?

---

### Post by nickrout on 2012-06-17
The mysterious file is a backup file, probably created by /etc/cron.weekly/mythtv-database

It will go to the default SG unless you define a DB_Backup SG, same as live tv will if there is no livetv SG set up.

can you touch a file in the livetc directory?

Have you read this thoroughly? [http://www.mythtv.org/wiki/Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups)

It confuses me re slave backends. Seems to me if /mnt/hdd/mythtv/recordings is your ONLY directory defined in the default SG on the MBE then that directory must also be defined on the SBE.

You could take down the SBE for a while to eliminate problems arising from it.

Sorry, I wish I could help more. 

Other thing is the BE seeming to die, it may be a hardware problem? perhpas associated with your SATA card? Perhaps try the NAS plugged into USB or firewire. USB may not be what you want to use given the way better throughput of eSATA, but it elminates a driver crash.

---

### Post by Lester_Burnham on 2012-06-17
Hi,

I haven't read the whole thread, but I take it it relates to master and slave backends.
Back in the mythtv 0.20/0.21 days, I used to cheat and just mount my large storage area to /var/lib/mythtv/recordings with mythtv permissions to get around some of the problems. Seeing it is the default path, it should "just work".

I think I also used nfs on the slave backend to mount recordings to /var/lib/mythtv/recordings from the master. Too long ago now.
You might be able to mount the whole mythtv folder to your large storage, to get around live TV issues.

Surely it can be done other ways too though.

Lester

---

### Post by jlp_engineer on 2012-06-18
> **nickrout said:**
> Have you read this thoroughly? [http://www.mythtv.org/wiki/Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups)

It confuses me re slave backends. Seems to me if /mnt/hdd/mythtv/recordings is your ONLY directory defined in the default SG on the MBE then that directory must also be defined on the SBE.

Well, that is interesting that you should say that.  I have read the SG Wiki, many, MANY times, hoping for some inspiration to help ferret out this issue.  I noticed that there is some information about Slave BE's, but only that you need not create any SG's on the slaves, and not really describing how things work, so no real help, at least not to the situation I have.  I also noticed you said that if you have the default SG "defined" on the master, then that directory must also be defined on the SBE.  

OK, so I took a look at the Slave BE settings, and there are no SG's "defined" there.  However, the same directories exist on the local drive on the Slave BE.  So the thought occurred to me :idea: what if the folders exist on the slave because they **_have_** to be there.  So I took a look in them, and low and behold, there were recording files in the \var\lib\mythtv\recordings directory on the slave.  OK, but aren't the recordings supposed to be on the Master BE???  But then I remembered something I read on the wiki that the recordings are made on the local BE where the tuner is, or something to that affect.  

OK, so then I thought, well, I wonder if the directory structure has to be the same on the master and all slaves in order for everything to work.  Weird, but OK, I am willing to go along if that is the case.  So, I created directories on the slave that have the same identical path as the directories on the master BE.  Now, keeping in mind that the Master has a second HDD mounted at /mnt/hdd, with the directories, /mnt/hdd/mythtv/recordings and /mnt/hdd/mythtv/livetv, and so on, I created the following directories on the SBE:

/mnt/hdd/mythtv/recordings
/mnt/hdd/mythtv/livetv
and so on....

I then fired everything back up, including the FE's on my Slave and Master BE's.  I can see video from my digital tuners in the Master, but when I try to switch to the analog tuners that sit on the slave, nothing but a blank screen, and after a minute, back to the menu, but no error messages on the screen.  The FE on the slave is a different story....  I can see video from my analog tuners (no audio because there is no audio card, but that is not the issue), and I can also see video from the digital tuners on the Master BE.  

Ah HA!!!  That seems like progress!

OK, so I then took a look in the folders I created on the Slave, and I did not expect to see any files in them, BUT THERE WERE!  A brand new recording file was created in the /mnt/hdd/mythtv/recordings directory on the Slave.  And when I switched inputs to one of the digital tuners on the Master, that gave me live TV video, but the recording file for it showed up on the Master BE under /mnt/hdd/mythtv/livetv.

Based on this new information, do you care to take a stab at what is going on and how to fix it?  Is this a bug with regard to SG's and slave BE's???

---

### Post by nickrout on 2012-06-19
I believe that SBE's save their files in their own filesystem. IF your ONLY default SG directory on the MBE is /mnt/hdd/mythtv/recordings AND there is no override on the SBE AND that directory does not exist on the SBE then recordings on the SBE will, I think, fail.

You could save SBE recordings on your NAS by mounting it on the SBE at the same mount point, using cifs or nfs. That would create network traffic, but you may prefer everything there.

---

### Post by jlp_engineer on 2012-06-19
OK, some more information...

I have got all Frontends, local to the Backends (master and slave), and remote working.  And what, you ask, made it start working? :rolleyes:  I disabled the Master Backend Override setting on the Master BE.  Don't know why that setting was enabled, but as soon as I unchecked it, everything started working like it should have been.  However, the directory structure on the slave still needs to be identical to the master backend, as far as I can tell.  

For example, if I mount a second hard disk on the master at /mnt/hdd, and then create a folder called "mythtv", and then all the necessary sub-folders, then I will have something like this when I am done:

/mnt/hdd/mythtv/banners
/mnt/hdd/mythtv/bare-client
/mnt/hdd/mythtv/coverart
/mnt/hdd/mythtv/db_backup
/mnt/hdd/mythtv/fanart
/mnt/hdd/mythtv/livetv
/mnt/hdd/mythtv/music
/mnt/hdd/mythtv/pictures
/mnt/hdd/mythtv/recordings
/mnt/hdd/mythtv/screenshots
/mnt/hdd/mythtv/trailers
/mnt/hdd/mythtv/videos

Then it seems I have to, at least in regards to LiveTV video, create the same directory structures on the slave backend.  Odd, but something I can certainly live with.  I am pretty sure at this point, that the only folder I would need on the slave would be the /mnt/hdd/mythtv/recordings folder, but I could be wrong.  I will experiment and see.  

I am going to try backing out the other changes I have made (adding the RAID storage unit back in, reformatting it to XFS, etc.) to get back to where I was, and begin stress testing the system again.  I will report my findings in a few days.  8-[

While I am testing, I would really appreciate some feedback.  Did I find a bug here with regard to the SG paths on the slave, or is it supposed to be that way?  Also, would having the Master Backend Override enabled cause video from the slave tuners to go missing, thereby causing the FE's to lockup???

Thanks

---

### Post by jlp_engineer on 2012-06-25
OK...

I continue to make discoveries on my way.  I believe the following to be true with regard to slave backends and adding storage:

1 - If you add storage to the master, and you change the paths for LiveTV and recordings in storage groups, you must create the same paths on the slave.  

2 - If you add storage capacity on the Master BE to store recordings, you must also add storage to the slave for the same purpose.  I believe you can add the paths to the added storage or 2nd disk, keeping the original settings, but if you only have one path in the master that points to the storage device or 2nd hard disk, you must duplicate the same thing on the slave or the tuners on the slave will not produce video on your remote frontends.  

3 - If you are going to try to centralize storage for your MythTV installation, and you don't want to use NFS or CIFS, and you have a Master / Slave installation, you are out of luck.  Since the recordings for each tuner are recorded locally, you are stuck putting those files on each backend, whether it is the slave or master.

Let me know if I am off on any of these.

---

### Post by tgm4883 on 2012-06-25
> **jlp_engineer said:**
> OK...

I continue to make discoveries on my way.  I believe the following to be true with regard to slave backends and adding storage:

1 - If you add storage to the master, and you change the paths for LiveTV and recordings in storage groups, you must create the same paths on the slave.  

2 - If you add storage capacity on the Master BE to store recordings, you must also add storage to the slave for the same purpose.  I believe you can add the paths to the added storage or 2nd disk, keeping the original settings, but if you only have one path in the master that points to the storage device or 2nd hard disk, you must duplicate the same thing on the slave or the tuners on the slave will not produce video on your remote frontends.  

3 - If you are going to try to centralize storage for your MythTV installation, and you don't want to use NFS or CIFS, and you have a Master / Slave installation, you are out of luck.  Since the recordings for each tuner are recorded locally, you are stuck putting those files on each backend, whether it is the slave or master.

Let me know if I am off on any of these.

#1 and #2 aren't necessarily true. IIRC, if you have storage groups specified on the SBE, then the SBE will use those directories. If you have no storage groups specified on the SBE, then it will use whatever storage groups are specified on the MBE. So #1 and #2 should only be true if you have no SGs defined on the SBE. 

#3 is true, although in your situation you could share the storage from the MBE via NFS or CIFS and mount it on the SBE. It is true though that the storage must be locally mounted to the machine.

---

### Post by jlp_engineer on 2012-07-02
Another little nugget of information, that might be known to only a few of us diehard MythTV addicts.  It seems that frontends on the network will pull in (from a scan for changes) videos and list them from the .....\mythtv\videos directories on BOTH the master and slave backends, but it will ONLY play them off of the master backend.  I find that particularly confusing because the scans lists videos from both physical locations!

Should I open a ticket?  Is this a bug, or is it operating "as designed", or "as implemented so far"?

I feel like I should start writing a book, but then I am far from an authority on MythTV or Ubuntu.

):P

---

### Post by tgm4883 on 2012-07-02
> **jlp_engineer said:**
> Another little nugget of information, that might be known to only a few of us diehard MythTV addicts.  It seems that frontends on the network will pull in (from a scan for changes) videos and list them from the .....\mythtv\videos directories on BOTH the master and slave backends, but it will ONLY play them off of the master backend.  I find that particularly confusing because the scans lists videos from both physical locations!

Should I open a ticket?  Is this a bug, or is it operating "as designed", or "as implemented so far"?

I feel like I should start writing a book, but then I am far from an authority on MythTV or Ubuntu.

):P

For that particular issue, probably wouldn't open a bug as local media sections are going away. I'd bet they are gone by 0.26.

Unless you are saying that network frontend won't play media located in a slave backend's storage group. If that is the case, then yes open a bug

---

### Post by jlp_engineer on 2012-07-02
> **tgm4883 said:**
> For that particular issue, probably wouldn't open a bug as local media sections are going away. I'd bet they are gone by 0.26.


What do you mean by "local media sections"?  I have a lot of DVD ISO's and I hope that MythTV will continue to be able to play them.  I really enjoy having one place I can go to use LiveTV, recorded TV, and DVD's, and right now MythTV makes that possible.  I know that the music piece was not integrated into the storage group effort, but that sounded like it was unavoidable.

> 
Unless you are saying that network frontend won't play media located in a slave backend's storage group. If that is the case, then yes open a bug

Well, the directories on the backends are:

Master
/mnt/hdd/mythtv/videos

Slave
/mnt/hdd/mythtv/videos

One storage group for Videos defined on the Master, but none are defined on the Slave. I placed ISO files on the Master and some on the Slave, and ALL the videos are found by a scan from all my FE's (even the ones on each of the backends), but only the ISO's located on the Master will play.  The ones on the slave backend will not play.  SWhen I pull one of them up, hit play, nothing happens, but no error message, and no lockup.  Is that the way it was designed or is it just an artifact of the current implementation?

I very much appreciate you taking the time to reply to my posting.

---

### Post by tgm4883 on 2012-07-02
> **jlp_engineer said:**
> What do you mean by "local media sections"?  I have a lot of DVD ISO's and I hope that MythTV will continue to be able to play them.  I really enjoy having one place I can go to use LiveTV, recorded TV, and DVD's, and right now MythTV makes that possible.  I know that the music piece was not integrated into the storage group effort, but that sounded like it was unavoidable.


By local media sections, I mean that storage groups are the future and the ability to set a local frontend path for storage on the frontend will go away. IIRC, you can play ISO's via storage groups so that shouldn't be an issue.

> **jlp_engineer said:**
> 
Well, the directories on the backends are:

Master
/mnt/hdd/mythtv/videos

Slave
/mnt/hdd/mythtv/videos

One storage group for Videos defined on the Master, but none are defined on the Slave. I placed ISO files on the Master and some on the Slave, and ALL the videos are found by a scan from all my FE's (even the ones on each of the backends), but only the ISO's located on the Master will play.  The ones on the slave backend will not play.  SWhen I pull one of them up, hit play, nothing happens, but no error message, and no lockup.  Is that the way it was designed or is it just an artifact of the current implementation?

I very much appreciate you taking the time to reply to my posting.

I'm unsure if that is the way it is suppose to work, I would think that it should playback fine. You will need to post the backend logs from both the slave backend and the master backend and the frontend log from when you tried to access that media.

---

