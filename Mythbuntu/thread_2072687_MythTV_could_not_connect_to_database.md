---
title: "MythTV could not connect to database"
date: 2012-10-18
forum: Mythbuntu
---

### Post by Crowie on 2012-10-18
Hi all

Since an upgrade to 0.26 ive been having problems with mythtv starting.
Im always presented with the screen "please enter which country your in..." then onto database configuration 1/2 with the message "mythtv could not connect to database" check settings etc
Sometimes the backend has started despite this message but other times it doesnt.  I use mythwelcome.
There is nothing in the logs frontenf, backend or mysql logs that i can find to indicate a problem. Does anyone have any suggestions?

TIA

---

### Post by Crowie on 2012-10-19
Ok ive just started myth from cold boot.  Both mythbacken and mythwelcome are running as per top output.  However im still presented with the screen asking me to select the country in which i reside and then to check database settings.
Here is the output of some logs in case ive missed something, nothing is written to /var/log/mysql/error.log when starting myth:

```

121005 14:48:25 [Note] Event Scheduler: Purging the queue. 0 events
121005 14:48:25  InnoDB: Starting shutdown...
121005 14:48:27  InnoDB: Shutdown completed; log sequence number 0 30384708
121005 14:48:27 [Note] /usr/sbin/mysqld: Shutdown complete

121005 14:48:27 [Note] Plugin 'FEDERATED' is disabled.
121005 14:48:27  InnoDB: Initializing buffer pool, size = 8.0M
121005 14:48:27  InnoDB: Completed initialization of buffer pool
121005 14:48:28  InnoDB: Started; log sequence number 0 30384708
121005 14:48:28 [Note] Event Scheduler: Loaded 0 events
121005 14:48:28 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.63-0ubuntu0.11.10.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
121005 14:50:49 [Note] /usr/sbin/mysqld: Normal shutdown

121005 14:50:49 [Note] Event Scheduler: Purging the queue. 0 events
121005 14:50:51  InnoDB: Starting shutdown...
121005 14:50:53  InnoDB: Shutdown completed; log sequence number 0 30384744
121005 14:50:53 [Note] /usr/sbin/mysqld: Shutdown complete

```

```
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythwelcome version: fixes/0.26 [v0.26.0-16-gbff8eb1] www.mythtv.org
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I Logger logging.cpp:306 (run) Added logging to the console
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Interrupt handler
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Terminated handler
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Segmentation fault handler
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Aborted handler
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Bus error handler
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Floating point exception handler
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Illegal instruction handler
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Real-time signal 0 handler
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/shabba/.mythtv
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of shabba
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I CoreContext mythcontext.cpp:682 (TestDBconnection) Testing network connectivity to '192.168.1.66'
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1280x720 60.000 Hz
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I Logger logging.cpp:487 (launchLogServer) Starting mythlogserver
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/shabba/.mythtv/lircrc' config
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/shabba/.mythtv/joystickmenurc
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP 127.0.0.1:0
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP [::1]:0
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP [fe80::224:8cff:fe7e:e0a2%eth1]:0
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I CoreContext mythmainwindow.cpp:954 (Init) Using Frameless Window
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I CoreContext mythmainwindow.cpp:967 (Init) Using Full Screen Window
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I CoreContext mythmainwindow.cpp:1058 (Init) Using the Qt painter
Oct 19 12:00:17 shabba mythlogserver: mythwelcome[1937]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Oct 19 12:00:22 shabba mythlogserver: mythwelcome[1937]: I Logger logging.cpp:487 (launchLogServer) Starting mythlogserver

```

Nothing in the mythfrontend logs

in the backend logs

```
Oct 19 00:10:17 shabba mythlogserver: mythbackend[2472]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: shabba as a client (events: 1)
Passed time: 1350614640
Running /usr/bin/setwakeup.sh to set the wakeup time to 1350614640
Passed time: 1350614640
Running /usr/bin/setwakeup.sh to set the wakeup time to 1350614640
rtc_time        : 23:10:37
rtc_date        : 2012-10-18
alrm_time       : 02:44:00
alrm_date       : 2012-10-19
alarm_IRQ       : yes
alrm_pending    : no
update IRQ enabled      : no
periodic IRQ enabled    : no
periodic IRQ frequency  : 1024
max user IRQ frequency  : 64
24hr            : yes
periodic_IRQ    : no
update_IRQ      : no
HPET_emulated   : yes
BCD             : yes
DST_enable      : no
periodic_freq   : 1024
batt_status     : okay
rtc_time        : 23:10:37
rtc_date        : 2012-10-18
alrm_time       : 02:44:00
alrm_date       : 2012-10-19
alarm_IRQ       : yes
alrm_pending    : no
update IRQ enabled      : no
periodic IRQ enabled    : no
periodic IRQ frequency  : 1024
max user IRQ frequency  : 64
24hr            : yes
periodic_IRQ    : no
update_IRQ      : no
HPET_emulated   : yes
BCD             : yes
DST_enable      : no
periodic_freq   : 1024
batt_status     : okay
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythbackend version: fixes/0.26 [
v0.26.0-16-gbff8eb1] www.mythtv.org
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runti
me: 4.8.1
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I Logger logging.cpp:306 (run) Added logging to the console
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Interrupt handler
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Terminated handler
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Segmentation fault handler
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Aborted handler
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Bus error handler
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Floating point exception handler
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Illegal instruction handler
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I thread_unknown signalhandling.cpp:191 (SetHandlerPrivate) Setup Real-time signal 0 handler
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.
mythtv
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_GB.UTF-8
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of shabba
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I Logger logging.cpp:487 (launchLogServer) Starting mythlogserver
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to en_GB
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale en_GB
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mytht
v//locales/en_gb.xml
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1307
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I CoreContext mythtranslation.cpp:65 (load) Loading en_gb translation for module mythfrontend
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: N CoreContext main_helpers.cpp:575 (run_backend) MythBackend: Starting up as the master server.
Oct 19 12:00:21 shabba mythlogserver: mythbackend[2553]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Oct 19 12:00:22 shabba mythlogserver: mythbackend[2553]: I CoreContext programinfo.cpp:2062 (CheckProgramIDAuthorities) Found 10 distinct programid authoriti
es
Oct 19 12:00:22 shabba mythlogserver: mythbackend[2553]: I Scheduler mythdbcon.cpp:436 (getStaticCon) New static DB connectionSchedCon
Oct 19 12:00:22 shabba mythlogserver: mythbackend[2553]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 127.0.0.1:6544
Oct 19 12:00:22 shabba mythlogserver: mythbackend[2553]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 192.168.1.66:6544
Oct 19 12:00:22 shabba mythlogserver: mythbackend[2553]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [::1]:6544
Oct 19 12:00:22 shabba mythlogserver: mythbackend[2553]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [fe80::224:8cff:fe7e:e0a2%eth1]:6544
Oct 19 12:00:23 shabba mythlogserver: mythbackend[2553]: I CoreContext main_helpers.cpp:645 (run_backend) Main::Registering HttpStatus Extension
Oct 19 12:00:23 shabba mythlogserver: mythbackend[2553]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 127.0.0.1:6543
Oct 19 12:00:23 shabba mythlogserver: mythbackend[2553]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 192.168.1.66:6543
Oct 19 12:00:23 shabba mythlogserver: mythbackend[2553]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [::1]:6543
Oct 19 12:00:23 shabba mythlogserver: mythbackend[2553]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [fe80::224:8cff:fe7e:e0a2%eth1]:6543
Oct 19 12:00:23 shabba mythlogserver: mythbackend[2553]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 10.
0 GB w/freq: 15 min
Oct 19 12:00:24 shabba mythlogserver: mythbackend[2553]: I CoreContext bonjourregister.cpp:100 (BonjourCallback) Bonjour: Service registration complete: name
 'Mythbackend on shabba' type '_mythbackend-master._tcp.' domain: 'local.'
Oct 19 12:00:25 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2126 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - SchedulerIn
it
Oct 19 12:00:30 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2239 (HandleReschedule) Scheduled 129 items in 4.4 = 3.78 match + 0.39 che
ck + 0.21 place
Oct 19 12:00:30 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2297 (HandleRunSchedulerStartup) Scheduler: AUTO-Startup assumed
Oct 19 12:00:30 shabba mythlogserver: mythbackend[2553]: I TVRecEvent tv_rec.cpp:1043 (HandleStateChange) TVRec(13): Changing from None to RecordingOnly
Oct 19 12:00:30 shabba mythlogserver: mythbackend[2553]: I TVRecEvent tv_rec.cpp:3562 (TuningCheckForHWChange) TVRec(13): HW Tuner: 13->13
Oct 19 12:00:30 shabba mythlogserver: mythbackend[2553]: N Scheduler autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 12.0
GB w/freq: 14 min
Oct 19 12:00:30 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2646 (HandleRecordingStatusChange) Tuning recording: "Come Dine with Me":
channel 1004 on cardid 13, sourceid 1
Oct 19 12:00:30 shabba mythlogserver: mythbackend[2553]: I TVRecEvent tv_rec.cpp:1557 (HandlePendingRecordings) TVRec(14): ASK_RECORDING 14 0 0 0
Oct 19 12:00:31 shabba mythlogserver: mythbackend[2553]: I CoreContext scheduler.cpp:655 (UpdateRecStatus) Updating status for "Come Dine with Me" on cardid
13 (Tuning => Recording)
Oct 19 12:00:31 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2126 (HandleReschedule) Reschedule requested for PLACE PrepareToRecord
Oct 19 12:00:32 shabba mythlogserver: mythbackend[2553]: I TVRecEvent tv_rec.cpp:4056 (TuningNewRecorder) TVRec(13): rec->GetPathname(): '/var/lib/mythtv/rec
ordings/1004_20121019110000.mpg'
Oct 19 12:00:32 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2239 (HandleReschedule) Scheduled 128 items in 1.5 = 0.00 match + 0.00 che
ck + 1.46 place
Oct 19 12:00:33 shabba mythlogserver: mythbackend[2553]: I HouseKeeping housekeeper.cpp:221 (RunHouseKeeping) Running housekeeping thread
Oct 19 12:00:36 shabba mythlogserver: mythbackend[2553]: I HouseKeeping housekeeper.cpp:814 (UpdateRecordedArtwork) Performing Artwork Refresh: /usr/bin/myth
metadatalookup --refresh-all-artwork  --verbose general --loglevel info --syslog local7
Oct 19 12:00:37 shabba mythlogserver: mythbackend[2553]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Playback
Oct 19 12:00:37 shabba mythlogserver: mythbackend[2553]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: shabba as a client (events: 0)
Oct 19 12:00:37 shabba mythlogserver: mythbackend[2553]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Oct 19 12:00:37 shabba mythlogserver: mythbackend[2553]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: shabba as a client (events: 1)
Oct 19 12:01:43 shabba mythlogserver: mythbackend[2553]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 12.0 GB
w/freq: 14 min
Oct 19 12:01:43 shabba mythlogserver: mythbackend[2553]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 30 MB for 1022 at 2010-11-15T13:48:18Z =>
"Moira C Bags Pick of the Day"
Oct 19 12:01:43 shabba mythlogserver: mythbackend[2553]: E CoreContext programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(1022_20101115134818.mpg): GetPlaybac
kURL: '1022_20101115134818.mpg' should be local, but it can not be found.
Oct 19 12:01:43 shabba mythlogserver: mythbackend[2553]: E CoreContext mainserver.cpp:2622 (DoHandleDeleteRecording) ERROR when trying to delete file: GetPla
ybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/shabba/1022_20101115134818.mpg. File doesn't exist.  Database metadata will not be removed.
Oct 19 12:02:08 shabba mythlogserver: mythbackend[2553]: I HouseKeeping housekeeper.cpp:821 (UpdateRecordedArtwork) Artwork Refresh Complete
Oct 19 12:06:19 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2126 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - EITScanner
Oct 19 12:06:23 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2239 (HandleReschedule) Scheduled 139 items in 4.2 = 3.50 match + 0.44 che
ck + 0.22 place
Oct 19 12:07:14 shabba mythlogserver: mythbackend[2553]: I HouseKeeping housekeeper.cpp:221 (RunHouseKeeping) Running housekeeping thread
Oct 19 12:09:08 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2126 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - EITScanner
Oct 19 12:09:13 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2239 (HandleReschedule) Scheduled 139 items in 4.2 = 3.52 match + 0.44 che
ck + 0.23 place
Oct 19 12:11:55 shabba mythlogserver: mythbackend[2553]: W TFWWrite ThreadedFileWriter.cpp:500 (DiskLoop) TFW(/var/lib/mythtv/recordings/1004_20121019110000.
mpg:77): write(57528) cnt 112 total 6501980 -- took a long time, 12367 ms
Oct 19 12:12:03 shabba mythlogserver: mythbackend[2553]: W TFWWrite ThreadedFileWriter.cpp:500 (DiskLoop) TFW(/var/lib/mythtv/recordings/1004_20121019110000.
mpg:77): write(57716) cnt 116 total 6756908 -- took a long time, 6183 ms
Oct 19 12:12:20 shabba mythlogserver: mythbackend[2553]: I HouseKeeping housekeeper.cpp:221 (RunHouseKeeping) Running housekeeping thread
Oct 19 12:15:43 shabba mythlogserver: mythbackend[2553]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 12.0 GB
w/freq: 14 min
Oct 19 12:16:15 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2126 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - EITScanner
Oct 19 12:16:20 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2239 (HandleReschedule) Scheduled 140 items in 4.2 = 3.54 match + 0.45 che
ck + 0.24 place
Oct 19 12:17:27 shabba mythlogserver: mythbackend[2553]: I HouseKeeping housekeeper.cpp:221 (RunHouseKeeping) Running housekeeping thread
Oct 19 12:19:30 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2126 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - EITScanner
Oct 19 12:19:34 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2239 (HandleReschedule) Scheduled 141 items in 4.2 = 3.54 match + 0.45 che
ck + 0.24 place
Oct 19 12:22:32 shabba mythlogserver: mythbackend[2553]: I HouseKeeping housekeeper.cpp:221 (RunHouseKeeping) Running housekeeping thread
Oct 19 12:22:55 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2126 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - EITScanner
Oct 19 12:22:59 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2239 (HandleReschedule) Scheduled 141 items in 4.3 = 3.57 match + 0.45 che
ck + 0.23 place
Oct 19 12:25:37 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2126 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - EITScanner
Oct 19 12:25:41 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2239 (HandleReschedule) Scheduled 141 items in 4.2 = 3.50 match + 0.44 che
ck + 0.23 place
Oct 19 12:27:36 shabba mythlogserver: mythbackend[2553]: I HouseKeeping housekeeper.cpp:221 (RunHouseKeeping) Running housekeeping thread
Oct 19 12:29:43 shabba mythlogserver: mythbackend[2553]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 12.0 GB
w/freq: 14 min
Oct 19 12:32:01 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2126 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - EITScanner
Oct 19 12:32:05 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2239 (HandleReschedule) Scheduled 141 items in 4.3 = 3.66 match + 0.44 che
ck + 0.23 place
Oct 19 12:32:30 shabba mythlogserver: mythbackend[2553]: I TVRecEvent tv_rec.cpp:1557 (HandlePendingRecordings) TVRec(13): ASK_RECORDING 13 28 0 0
Oct 19 12:32:31 shabba mythlogserver: mythbackend[2553]: I TVRecEvent tv_rec.cpp:1557 (HandlePendingRecordings) TVRec(14): ASK_RECORDING 14 28 0 0
Oct 19 12:32:40 shabba mythlogserver: mythbackend[2553]: I HouseKeeping housekeeper.cpp:221 (RunHouseKeeping) Running housekeeping thread
Oct 19 12:33:00 shabba mythlogserver: mythbackend[2553]: I TVRecEvent tv_rec.cpp:1043 (HandleStateChange) TVRec(14): Changing from None to RecordingOnly
Oct 19 12:33:00 shabba mythlogserver: mythbackend[2553]: I TVRecEvent tv_rec.cpp:3562 (TuningCheckForHWChange) TVRec(14): HW Tuner: 14->14
Oct 19 12:33:00 shabba mythlogserver: mythbackend[2553]: N Scheduler autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 12.0
GB w/freq: 7 min
Oct 19 12:33:00 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2646 (HandleRecordingStatusChange) Tuning recording: "Come Dine with Me":
channel 1004 on cardid 14, sourceid 1
Oct 19 12:33:02 shabba mythlogserver: mythbackend[2553]: I CoreContext scheduler.cpp:655 (UpdateRecStatus) Updating status for "Come Dine with Me" on cardid
14 (Tuning => Recording)
Oct 19 12:33:02 shabba mythlogserver: mythbackend[2553]: I TVRecEvent tv_rec.cpp:4056 (TuningNewRecorder) TVRec(14): rec->GetPathname(): '/var/lib/mythtv/rec
ordings/1004_20121019113300.mpg'
Oct 19 12:34:50 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2126 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - EITScanner
Oct 19 12:34:55 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2239 (HandleReschedule) Scheduled 141 items in 4.3 = 3.67 match + 0.45 che
ck + 0.23 place
Oct 19 12:37:28 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2126 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - EITScanner
Oct 19 12:37:32 shabba mythlogserver: mythbackend[2553]: I Scheduler scheduler.cpp:2239 (HandleReschedule) Scheduled 141 items in 4.4 = 3.73 match + 0.45 che
ck + 0.23 place
Oct 19 12:37:44 shabba mythlogserver: mythbackend[2553]: I HouseKeeping housekeeper.cpp:221 (RunHouseKeeping) Running housekeeping thread
Oct 19 12:38:33 shabba mythlogserver: mythbackend[2553]: I Metadata_5350 jobqueue.cpp:2156 (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for "C
--More--

```

Does anyone have any ideas

TIA

---

### Post by tgm4883 on 2012-10-19
What IP address are you setting in the frontend for your backend? Is the MythTV service enabled in the mythbuntu-control-centre.

---

### Post by Crowie on 2012-10-19
Hi
In the frontend, the hostname is 192.168.1.66 the frontend is on the same machine but I also use another frontend.

It appears to be enabled in the mythbuntu control centre as in primary backend and desktop frontend are enable.  Its also set to Automatically start MythTV Frontend.

Thanks for your help

---

### Post by tgm4883 on 2012-10-19
Can you get into Mythweb? that would verify the backend is up and running properly.

Does the remote frontend work?

---

### Post by Crowie on 2012-10-20
Ive not upgraded the remote frontend yet.

Funnily enough this morning the backend wont start and im caught in a continous loop of confirming country i reside in and verify database settings.  Im going to reboot it and try again.

When the backend is up mythweb works fine. When its not up (according to top) mythweb doesnt work with the following backtrace.

```
   datetime:  2012-10-20 09:57:47 (BST)
    errornum:  256
  error type:  User Error
error string:  !!NoTrans: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) [#2002]

Backtrace
Array
(
    [0] => Array
        (
            [file] => /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
            [line] => 63
            [function] => error
            [class] => Database
            [object] => Database_mysql Object
                (
                    [dbh] => 
                    [error] => Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) [#2002]
                    [err] => Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
                    [errno] => 2002
                    [last_sh] => Database_Query_mysql Object
                        (
                            [dbh] => 
                            [query] => Array
                                (
                                    [0] => SET NAMES utf8;
                                )

                            [last_query] => SET NAMES utf8;
                            [warnings] => Array ( )
                            [num_args_needed] => 0
                            [num_rows] => 
                            [affected_rows] => 
                            [insert_id] => 
                            [db] => Database_mysql Object
 *RECURSION*
                        )

                    [fatal_errors] => 1
                    [query_count] => 0
                    [query_time] => 0
                    [global_name] => 
                    [destruct_handlers] => Array ( )
                )

            [type] => ->
            [args] => Array ( )
        )

    [1] => Array
        (
            [file] => /usr/share/mythtv/mythweb/classes/Database.php
            [line] => 261
            [function] => execute
            [class] => Database_Query_mysql
            [object] => Database_Query_mysql Object
                (
                    [dbh] => 
                    [query] => Array
                        (
                            [0] => SET NAMES utf8;
                        )

                    [last_query] => SET NAMES utf8;
                    [warnings] => Array ( )
                    [num_args_needed] => 0
                    [num_rows] => 
                    [affected_rows] => 
                    [insert_id] => 
                    [db] => Database_mysql Object
                        (
                            [dbh] => 
                            [error] => Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) [#2002]
                            [err] => Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
                            [errno] => 2002
                            [last_sh] => Database_Query_mysql Object
 *RECURSION*
                            [fatal_errors] => 1
                            [query_count] => 0
                            [query_time] => 0
                            [global_name] => 
                            [destruct_handlers] => Array ( )
                        )

                )

            [type] => ->
            [args] => Array
                (
                    [0] => Array ( )
                )

        )

    [2] => Array
        (
            [file] => /usr/share/mythtv/mythweb/classes/Database.php
            [line] => 124
            [function] => query
            [class] => Database
            [object] => Database_mysql Object
                (
                    [dbh] => 
                    [error] => Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) [#2002]
                    [err] => Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
                    [errno] => 2002
                    [last_sh] => Database_Query_mysql Object
                        (
                            [dbh] => 
                            [query] => Array
                                (
                                    [0] => SET NAMES utf8;
                                )

                            [last_query] => SET NAMES utf8;
                            [warnings] => Array ( )
                            [num_args_needed] => 0
                            [num_rows] => 
                            [affected_rows] => 
                            [insert_id] => 
                            [db] => Database_mysql Object
 *RECURSION*
                        )

                    [fatal_errors] => 1
                    [query_count] => 0
                    [query_time] => 0
                    [global_name] => 
                    [destruct_handlers] => Array ( )
                )

            [type] => ->
            [args] => Array
                (
                    [0] => SET NAMES utf8;
                )

        )

    [3] => Array
        (
            [file] => /usr/share/mythtv/mythweb/includes/database.php
            [line] => 49
            [function] => connect
            [class] => Database
            [type] => ::
            [args] => Array
                (
                    [0] => mythconverg
                    [1] => mythtv
                    [2] => FEL5FIZr
                    [3] => localhost
                    [4] => 
                    [5] => mysql
                )

        )

    [4] => Array
        (
            [file] => /usr/share/mythtv/mythweb/includes/init.php
            [line] => 40
            [args] => Array
                (
                    [0] => /usr/share/mythtv/mythweb/includes/database.php
                )

            [function] => require_once
        )

    [5] => Array
        (
            [file] => /usr/share/mythtv/mythweb/mythweb.php
            [line] => 20
            [args] => Array
                (
                    [0] => /usr/share/mythtv/mythweb/includes/init.php
                )

            [function] => require_once
        )

)
!!
    filename:  /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
  error line:  64

==========================================================================

Backtrace: 

    file:  /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
    line:  64
   class:  
function:  trigger_error
    type:  
    args:  Array
(
    [0] => Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) [#2002]

Backtrace
Array
(
    [0] => Array
        (
            [file] => /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
            [line] => 63
            [function] => error
            [class] => Database
            [object] => Database_mysql Object
                (
                    [dbh] => 
                    [error] => Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) [#2002]
                    [err] => Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
                    [errno] => 2002
                    [last_sh] => Database_Query_mysql Object
                        (
                            [dbh] => 
                            [query] => Array
                                (
                                    [0] => SET NAMES utf8;
                                )

                            [last_query] => SET NAMES utf8;
                            [warnings] => Array ( )
                            [num_args_needed] => 0
                            [num_rows] => 
                            [affected_rows] => 
                            [insert_id] => 
                            [db] => Database_mysql Object
 *RECURSION*
                        )

                    [fatal_errors] => 1
                    [query_count] => 0
                    [query_time] => 0
                    [global_name] => 
                    [destruct_handlers] => Array ( )
                )

            [type] => ->
            [args] => Array ( )
        )

    [1] => Array
        (
            [file] => /usr/share/mythtv/mythweb/classes/Database.php
            [line] => 261
            [function] => execute
            [class] => Database_Query_mysql
            [object] => Database_Query_mysql Object
                (
                    [dbh] => 
                    [query] => Array
                        (
                            [0] => SET NAMES utf8;
                        )

                    [last_query] => SET NAMES utf8;
                    [warnings] => Array ( )
                    [num_args_needed] => 0
                    [num_rows] => 
                    [affected_rows] => 
                    [insert_id] => 
                    [db] => Database_mysql Object
                        (
                            [dbh] => 
                            [error] => Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) [#2002]
                            [err] => Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
                            [errno] => 2002
                            [last_sh] => Database_Query_mysql Object
 *RECURSION*
                            [fatal_errors] => 1
                            [query_count] => 0
                            [query_time] => 0
                            [global_name] => 
                            [destruct_handlers] => Array ( )
                        )

                )

            [type] => ->
            [args] => Array
                (
                    [0] => Array ( )
                )

        )

    [2] => Array
        (
            [file] => /usr/share/mythtv/mythweb/classes/Database.php
            [line] => 124
            [function] => query
            [class] => Database
            [object] => Database_mysql Object
                (
                    [dbh] => 
                    [error] => Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) [#2002]
                    [err] => Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
                    [errno] => 2002
                    [last_sh] => Database_Query_mysql Object
                        (
                            [dbh] => 
                            [query] => Array
                                (
                                    [0] => SET NAMES utf8;
                                )

                            [last_query] => SET NAMES utf8;
                            [warnings] => Array ( )
                            [num_args_needed] => 0
                            [num_rows] => 
                            [affected_rows] => 
                            [insert_id] => 
                            [db] => Database_mysql Object
 *RECURSION*
                        )

                    [fatal_errors] => 1
                    [query_count] => 0
                    [query_time] => 0
                    [global_name] => 
                    [destruct_handlers] => Array ( )
                )

            [type] => ->
            [args] => Array
                (
                    [0] => SET NAMES utf8;
                )

        )

    [3] => Array
        (
            [file] => /usr/share/mythtv/mythweb/includes/database.php
            [line] => 49
            [function] => connect
            [class] => Database
            [type] => ::
            [args] => Array
                (
                    [0] => mythconverg
                    [1] => mythtv
                    [2] => FEL5FIZr
                    [3] => localhost
                    [4] => 
                    [5] => mysql
                )

        )

    [4] => Array
        (
            [file] => /usr/share/mythtv/mythweb/includes/init.php
            [line] => 40
            [args] => Array
                (
                    [0] => /usr/share/mythtv/mythweb/includes/database.php
                )

            [function] => require_once
        )

    [5] => Array
        (
            [file] => /usr/share/mythtv/mythweb/mythweb.php
            [line] => 20
            [args] => Array
                (
                    [0] => /usr/share/mythtv/mythweb/includes/init.php
                )

            [function] => require_once
        )

)

    [1] => 256
)

    file:  /usr/share/mythtv/mythweb/classes/Database.php
    line:  261
   class:  Database_Query_mysql
function:  execute
    type:  ->
    args:  Array
(
    [0] => Array ( )
)

    file:  /usr/share/mythtv/mythweb/classes/Database.php
    line:  124
   class:  Database
function:  query
    type:  ->
    args:  Array
(
    [0] => SET NAMES utf8;
)

    file:  /usr/share/mythtv/mythweb/includes/database.php
    line:  49
   class:  Database
function:  connect
    type:  ::
    args:  Array
(
    [0] => mythconverg
    [1] => mythtv
    [2] => FEL5FIZr
    [3] => localhost
    [4] => 
    [5] => mysql
)

    file:  /usr/share/mythtv/mythweb/includes/init.php
    line:  40
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/includes/database.php
)

    file:  /usr/share/mythtv/mythweb/mythweb.php
    line:  20
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/includes/init.php
)


==========================================================================

$_SESSION: Array
(
    [language] => English
)

==========================================================================

$_SERVER: Array
(
    [REDIRECT_STATUS] => 200
    [db_server] => localhost
    [db_name] => mythconverg
    [db_login] => mythtv
    [db_password] => FEL5FIZr
    [HTTP_HOST] => shabba
    [HTTP_CONNECTION] => keep-alive
    [HTTP_USER_AGENT] => Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.4 (KHTML, like Gecko) Chrome/22.0.1229.94 Safari/537.4
    [HTTP_ACCEPT] => text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
    [HTTP_ACCEPT_ENCODING] => gzip,deflate,sdch
    [HTTP_ACCEPT_LANGUAGE] => en-US,en;q=0.8
    [HTTP_ACCEPT_CHARSET] => ISO-8859-1,utf-8;q=0.7,*;q=0.3
    [HTTP_COOKIE] => mythweb_id=do7dc4dq3thh7ithj8pp6bmo70
    [PATH] => /usr/local/bin:/usr/bin:/bin
    [SERVER_SIGNATURE] => <address>Apache/2.2.22 (Ubuntu) Server at shabba Port 80</address>

    [SERVER_SOFTWARE] => Apache/2.2.22 (Ubuntu)
    [SERVER_NAME] => shabba
    [SERVER_ADDR] => 192.168.1.66
    [SERVER_PORT] => 80
    [REMOTE_ADDR] => 192.168.1.65
    [DOCUMENT_ROOT] => /var/www
    [SERVER_ADMIN] => webmaster@localhost
    [SCRIPT_FILENAME] => /var/www/mythweb/mythweb.php
    [REMOTE_PORT] => 49479
    [REDIRECT_URL] => /mythweb/
    [GATEWAY_INTERFACE] => CGI/1.1
    [SERVER_PROTOCOL] => HTTP/1.1
    [REQUEST_METHOD] => GET
    [QUERY_STRING] => 
    [REQUEST_URI] => /mythweb/
    [SCRIPT_NAME] => /mythweb/mythweb.php
    [PHP_SELF] => /mythweb/mythweb.php
    [REQUEST_TIME] => 1350723467
    [STATUS] => 200
    [URL] => /mythweb/
)

==========================================================================

$constant_list["user"]: Array
(
    [ERROR] => 512
    [E_ASSERT_ERROR] => 4096
    [FATAL] => 256
    [PHP_MIN_VERSION] => 5.3
    [WARNING] => 1024
)



```

TIA

---

### Post by Crowie on 2012-10-20
ok backend is starting up now after a reboot but I still get this window asking me to verify database settings.
Mythweb is working fine and the backend is up.  
As soon as I confirm database settings, the frontend starts.

Im clutching at straws but could it be anything to do with the order they start?

---

### Post by Crowie on 2012-10-30
Still getting presented with a window to configure the database.
The backend starts, mysqld starts.
Mythweb doesnt work even after confirming database configuration.

```
Array
(
    [0] => Array
        (
            [file] => /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
            [line] => 63
            [function] => error
            [class] => Database
            [object] => Database_mysql Object
                (
                    [dbh] => 
                    [error] => Can't connect to MySQL server on '127.0.0.1' (111) [#2003]
                    [err] => Can't connect to MySQL server on '127.0.0.1' (111)
                    [errno] => 2003
                    [last_sh] => Database_Query_mysql Object
                        (
                            [dbh] => 
                            [query] => Array
                                (
                                    [0] => SET NAMES utf8;
                                )

                            [last_query] => SET NAMES utf8;
                            [warnings] => Array ( )
                            [num_args_needed] => 0
                            [num_rows] => 
                            [affected_rows] => 
                            [insert_id] => 
                            [db] => Database_mysql Object
 *RECURSION*
                        )

                    [fatal_errors] => 1
                    [query_count] => 0
                    [query_time] => 0
                    [global_name] => 
                    [destruct_handlers] => Array ( )
                )

            [type] => ->
            [args] => Array ( )
        )

    [1] => Array
        (
            [file] => /usr/share/mythtv/mythweb/classes/Database.php
            [line] => 261
            [function] => execute
            [class] => Database_Query_mysql
            [object] => Database_Query_mysql Object
                (
                    [dbh] => 
                    [query] => Array
                        (
                            [0] => SET NAMES utf8;
                        )

                    [last_query] => SET NAMES utf8;
                    [warnings] => Array ( )
                    [num_args_needed] => 0
                    [num_rows] => 
                    [affected_rows] => 
                    [insert_id] => 
                    [db] => Database_mysql Object
                        (
                            [dbh] => 
                            [error] => Can't connect to MySQL server on '127.0.0.1' (111) [#2003]
                            [err] => Can't connect to MySQL server on '127.0.0.1' (111)
                            [errno] => 2003
                            [last_sh] => Database_Query_mysql Object
 *RECURSION*
                            [fatal_errors] => 1
                            [query_count] => 0
                            [query_time] => 0
                            [global_name] => 
                            [destruct_handlers] => Array ( )
                        )

                )

            [type] => ->
            [args] => Array
                (
                    [0] => Array ( )
                )

        )

    [2] => Array
        (
            [file] => /usr/share/mythtv/mythweb/classes/Database.php
            [line] => 124
            [function] => query
            [class] => Database
            [object] => Database_mysql Object
                (
                    [dbh] => 
                    [error] => Can't connect to MySQL server on '127.0.0.1' (111) [#2003]
                    [err] => Can't connect to MySQL server on '127.0.0.1' (111)
                    [errno] => 2003
                    [last_sh] => Database_Query_mysql Object
                        (
                            [dbh] => 
                            [query] => Array
                                (
                                    [0] => SET NAMES utf8;
                                )

                            [last_query] => SET NAMES utf8;
                            [warnings] => Array ( )
                            [num_args_needed] => 0
                            [num_rows] => 
                            [affected_rows] => 
                            [insert_id] => 
                            [db] => Database_mysql Object
 *RECURSION*
                        )

                    [fatal_errors] => 1
                    [query_count] => 0
                    [query_time] => 0
                    [global_name] => 
                    [destruct_handlers] => Array ( )
                )

            [type] => ->
            [args] => Array
                (
                    [0] => SET NAMES utf8;
                )

        )

    [3] => Array
        (
            [file] => /usr/share/mythtv/mythweb/includes/database.php
            [line] => 49
            [function] => connect
            [class] => Database
            [type] => ::
            [args] => Array
                (
                    [0] => mythconverg
                    [1] => mythtv
                    [2] => FEL5FIZr
                    [3] => 127.0.0.1
                    [4] => 
                    [5] => mysql
                )

        )

    [4] => Array
        (
            [file] => /usr/share/mythtv/mythweb/includes/init.php
            [line] => 40
            [args] => Array
                (
                    [0] => /usr/share/mythtv/mythweb/includes/database.php
                )

            [function] => require_once
        )

    [5] => Array
        (
            [file] => /usr/share/mythtv/mythweb/mythweb.php
            [line] => 20
            [args] => Array
                (
                    [0] => /usr/share/mythtv/mythweb/includes/init.php
                )

            [function] => require_once
        )

)
!!
    filename:  /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
  error line:  64

==========================================================================

Backtrace: 

    file:  /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
    line:  64
   class:  
function:  trigger_error
    type:  
    args:  Array
(
    [0] => Can't connect to MySQL server on '127.0.0.1' (111) [#2003]

Backtrace
Array
(
    [0] => Array
        (
            [file] => /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
            [line] => 63
            [function] => error
            [class] => Database
            [object] => Database_mysql Object
                (
                    [dbh] => 
                    [error] => Can't connect to MySQL server on '127.0.0.1' (111) [#2003]
                    [err] => Can't connect to MySQL server on '127.0.0.1' (111)
                    [errno] => 2003
                    [last_sh] => Database_Query_mysql Object
                        (
                            [dbh] => 
                            [query] => Array
                                (
                                    [0] => SET NAMES utf8;
                                )

                            [last_query] => SET NAMES utf8;
                            [warnings] => Array ( )
                            [num_args_needed] => 0
                            [num_rows] => 
                            [affected_rows] => 
                            [insert_id] => 
                            [db] => Database_mysql Object
 *RECURSION*
                        )

                    [fatal_errors] => 1
                    [query_count] => 0
                    [query_time] => 0
                    [global_name] => 
                    [destruct_handlers] => Array ( )
                )

            [type] => ->
            [args] => Array ( )
        )

    [1] => Array
        (
            [file] => /usr/share/mythtv/mythweb/classes/Database.php
            [line] => 261
            [function] => execute
            [class] => Database_Query_mysql
            [object] => Database_Query_mysql Object
                (
                    [dbh] => 
                    [query] => Array
                        (
                            [0] => SET NAMES utf8;
                        )

                    [last_query] => SET NAMES utf8;
                    [warnings] => Array ( )
                    [num_args_needed] => 0
                    [num_rows] => 
                    [affected_rows] => 
                    [insert_id] => 
                    [db] => Database_mysql Object
                        (
                            [dbh] => 
                            [error] => Can't connect to MySQL server on '127.0.0.1' (111) [#2003]
                            [err] => Can't connect to MySQL server on '127.0.0.1' (111)
                            [errno] => 2003
                            [last_sh] => Database_Query_mysql Object
 *RECURSION*
                            [fatal_errors] => 1
                            [query_count] => 0
                            [query_time] => 0
                            [global_name] => 
                            [destruct_handlers] => Array ( )
                        )

                )

            [type] => ->
            [args] => Array
                (
                    [0] => Array ( )
                )

        )

    [2] => Array
        (
            [file] => /usr/share/mythtv/mythweb/classes/Database.php
            [line] => 124
            [function] => query
            [class] => Database
            [object] => Database_mysql Object
                (
                    [dbh] => 
                    [error] => Can't connect to MySQL server on '127.0.0.1' (111) [#2003]
                    [err] => Can't connect to MySQL server on '127.0.0.1' (111)
                    [errno] => 2003
                    [last_sh] => Database_Query_mysql Object
                        (
                            [dbh] => 
                            [query] => Array
                                (
                                    [0] => SET NAMES utf8;
                                )

                            [last_query] => SET NAMES utf8;
                            [warnings] => Array ( )
                            [num_args_needed] => 0
                            [num_rows] => 
                            [affected_rows] => 
                            [insert_id] => 
                            [db] => Database_mysql Object
 *RECURSION*
                        )

                    [fatal_errors] => 1
                    [query_count] => 0
                    [query_time] => 0
                    [global_name] => 
                    [destruct_handlers] => Array ( )
                )

            [type] => ->
            [args] => Array
                (
                    [0] => SET NAMES utf8;
                )

        )

    [3] => Array
        (
            [file] => /usr/share/mythtv/mythweb/includes/database.php
            [line] => 49
            [function] => connect
            [class] => Database
            [type] => ::
            [args] => Array
                (
                    [0] => mythconverg
                    [1] => mythtv
                    [2] => FEL5FIZr
                    [3] => 127.0.0.1
                    [4] => 
                    [5] => mysql
                )

        )

    [4] => Array
        (
            [file] => /usr/share/mythtv/mythweb/includes/init.php
            [line] => 40
            [args] => Array
                (
                    [0] => /usr/share/mythtv/mythweb/includes/database.php
                )

            [function] => require_once
        )

    [5] => Array
        (
            [file] => /usr/share/mythtv/mythweb/mythweb.php
            [line] => 20
            [args] => Array
                (
                    [0] => /usr/share/mythtv/mythweb/includes/init.php
                )

            [function] => require_once
        )

)

    [1] => 256
)

    file:  /usr/share/mythtv/mythweb/classes/Database.php
    line:  261
   class:  Database_Query_mysql
function:  execute
    type:  ->
    args:  Array
(
    [0] => Array ( )
)

    file:  /usr/share/mythtv/mythweb/classes/Database.php
    line:  124
   class:  Database
function:  query
    type:  ->
    args:  Array
(
    [0] => SET NAMES utf8;
)

    file:  /usr/share/mythtv/mythweb/includes/database.php
    line:  49
   class:  Database
function:  connect
    type:  ::
    args:  Array
(
    [0] => mythconverg
    [1] => mythtv
    [2] => FEL5FIZr
    [3] => 127.0.0.1
    [4] => 
    [5] => mysql
)

    file:  /usr/share/mythtv/mythweb/includes/init.php
    line:  40
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/includes/database.php
)

    file:  /usr/share/mythtv/mythweb/mythweb.php
    line:  20
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/includes/init.php
)


==========================================================================

$_SESSION: Array
(
    [language] => English
)

==========================================================================

$_SERVER: Array
(
    [REDIRECT_STATUS] => 200
    [db_server] => 127.0.0.1
    [db_name] => mythconverg
    [db_login] => mythtv
    [db_password] => FEL5FIZr
    [HTTP_HOST] => shabba
    [HTTP_CONNECTION] => keep-alive
    [HTTP_USER_AGENT] => Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.4 (KHTML, like Gecko) Chrome/22.0.1229.94 Safari/537.4
    [HTTP_ACCEPT] => text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
    [HTTP_ACCEPT_ENCODING] => gzip,deflate,sdch
    [HTTP_ACCEPT_LANGUAGE] => en-US,en;q=0.8
    [HTTP_ACCEPT_CHARSET] => ISO-8859-1,utf-8;q=0.7,*;q=0.3
    [PATH] => /usr/local/bin:/usr/bin:/bin
    [SERVER_SIGNATURE] => <address>Apache/2.2.22 (Ubuntu) Server at shabba Port 80</address>

    [SERVER_SOFTWARE] => Apache/2.2.22 (Ubuntu)
    [SERVER_NAME] => shabba
    [SERVER_ADDR] => 192.168.1.66
    [SERVER_PORT] => 80
    [REMOTE_ADDR] => 192.168.1.65
    [DOCUMENT_ROOT] => /var/www
    [SERVER_ADMIN] => webmaster@localhost
    [SCRIPT_FILENAME] => /var/www/mythweb/mythweb.php
    [REMOTE_PORT] => 52289
    [REDIRECT_URL] => /mythweb/
    [GATEWAY_INTERFACE] => CGI/1.1
    [SERVER_PROTOCOL] => HTTP/1.1
    [REQUEST_METHOD] => GET
    [QUERY_STRING] => 
    [REQUEST_URI] => /mythweb/
    [SCRIPT_NAME] => /mythweb/mythweb.php
    [PHP_SELF] => /mythweb/mythweb.php
    [REQUEST_TIME] => 1351604068
    [STATUS] => 200
    [URL] => /mythweb/
)

==========================================================================

$constant_list["user"]: Array
(
    [ERROR] => 512
    [E_ASSERT_ERROR] => 4096
    [FATAL] => 256
    [PHP_MIN_VERSION] => 5.3
    [WARNING] => 1024
)



```

Anyone any ideas?

---

### Post by Crowie on 2012-11-13
BUMP

This is becoming a PITA each time.  I can no longer access mythweb with the above errors.

Anyone offer some help?

TIA

---

### Post by Crowie on 2012-11-13
Somewhat closer.

If I edit my /etc/apache2/sites-available/mythweb.conf

from
```
 setenv db_server        "127.0.0.1"
            setenv db_name          "mythconverg"
            setenv db_login         "mythtv"
            setenv db_password      "FEL5FIZr"

```

to the ip address

```
setenv db_server        "192.168.1.66"
            setenv db_name          "mythconverg"
            setenv db_login         "mythtv"
            setenv db_password      "FEL5FIZr"

```

I can access mythweb fine.  So it looks like I have probles connecting to mysql on 127.0.0.1 for some reason.

Im not sure where next to look....

---

### Post by Crowie on 2012-11-24
Bump

Anyone?

---

### Post by Addanc on 2012-11-24
What I have found is that if my router is **not** powered so that the default DHCP network configuration cannot take place, then Ubuntu doesn't appear to allow even the loop-back address (127.0.0.1, used when back and front end are installed on a single machine) to operate; giving the appearance that the front-end cannot communicate with the back-end.

The solution I employed for this problem was to assign an IP address statically, so that the network stack always comes up.

---

### Post by nickrout on 2012-11-24
> **Addanc said:**
> What I have found is that if my router is **not** powered so that the default DHCP network configuration cannot take place, then Ubuntu doesn't appear to allow even the loop-back address (127.0.0.1, used when back and front end are installed on a single machine) to operate; giving the appearance that the front-end cannot communicate with the back-end.

The solution I employed for this problem was to assign an IP address statically, so that the network stack always comes up.

Well of course if your network is not up mysql and the backend will not work.

---

### Post by jksj on 2012-11-26
I think most users do not have this problem as they are using a wired ethernet connection, in which case it is trivial to apply a static network address which is there at boot. For those of us using a wireless connection how do you make it static?

---

### Post by klc5555 on 2012-11-26
> **jksj said:**
> I think most users do not have this problem as they are using a wired ethernet connection, in which case it is trivial to apply a static network address which is there at boot. For those of us using a wireless connection how do you make it static?

There are at least three ways. The normal and probably best way is to enter your wireless router's setup routine. In this, there will be a setting whereby you can reserve a specific and defined IP address always to be leased to a specific device/MAC address when that device connects. The device (in this case your master backend) is still on DHCP, but always gets leased the same address at bootup. As far as Mythtv is concerned, this is good enough.

The second and more old-fashioned method, generally more difficult on contemporary multi-device home networks, is to enter the wireless router's setup routine and disable the router's DHCP server. This puts the responsibility on the network administrator (you) to go into and configure Network Manager (or the equivalents on non-Ubuntu non-Gnome) for Static IP on each device: manually assign a valid non-conflicting IP address to each device on this network, enter the correct netmask value and enter the IP address of the gateway to the outside world.

The third way --incorrect, and a bit block-headed, but sometimes functional for those who are either unable or unwilling to enter the setup routine on their wireless router-- is simply to choose an address from the range that the wireless router is configured to lease, but beyond the group that the router is likely to lease to the number of the devices on the subnet, and then set up Static IP on that one device alone (i.e. the myth master backend) to arrogate that chosen IP address to itself, even though there's no DHCP lease for that address. 

For example, if the class C wireless network were on 192.168.1.0, and there were 5 other devices and also your Mythtv master backend, on this network, then 192.168.1.1 would likely be your gateway address, and DHCP would generally lease the addresses 192.168.1.2-7 to the 6 total devices on your network. If the myth backend machine has static IP set to, say, 192.168.1.15, this is an address that would be unlikely to be assigned by DHCP to one of your other devices, and therefore an IP address conflict between your backend and another device is unlikely. Of course, in this example, if 8 of your closest friends come over for the evening, each toting his own wifi tablet, then you're busted with a guaranteed IP conflict. So in all this is the least satisfactory method.

On my own network, I use static IP on all my ethernet boxes including my 3 myth backend-only machines, and two frontend-only machines. I have a separate subnet set up for normal wireless with DHCP, and from this subnet two frontend-only laptops and two frontend-only tablets connect.

---

### Post by jksj on 2012-11-26
High thanks for the pointers on setting up a static address. I already use the first one you mention ie locking the address which the wireless router allocates using DHCP. However if the router fails to allocate the address for some reason (fault with network provider modem) myth will not start. This is disconcerting as your main tv now has a dependence on your internet provider. 
I use a combined front/backend and on every startup the frontend (mythwelcome) shows a fail to connect status for about 30 seconds, then if the wireless network has started ok it connects and all is well. This is with the network address in Myth set to localhost!
I understand the time delay is due to network manager, which only runs on user login taking time to allocate the address.
My original question was how to make localhost valid early in the boot process before myth starts up when there is no hardwired ethernet connection.

---

### Post by klc5555 on 2012-11-26
> **jksj said:**
> High thanks for the pointers on setting up a static address. I already use the first one you mention ie locking the address which the wireless router allocates using DHCP. However if the router fails to allocate the address for some reason (fault with network provider modem) myth will not start. This is disconcerting as your main tv now has a dependence on your internet provider. 
I use a combined front/backend and on every startup the frontend (mythwelcome) shows a fail to connect status for about 30 seconds, then if the wireless network has started ok it connects and all is well. This is with the network address in Myth set to localhost!
I understand the time delay is due to network manager, which only runs on user login taking time to allocate the address.
My original question was how to make localhost valid early in the boot process before myth starts up when there is no hardwired ethernet connection.

There are many potential ways to address these issues.

1) Reserve the appropriate DHCP address in the router for your backend, but set up static IP for _that very same address_ on your backend machine anyway. No IP conflict, because the address is reserved for you, but you don't have to wait for your gimpy DHCP server in the router to dish out the address.

2) Go to pure static IP on this subnet. No DHCP delays here, either.

3) Put a "sleep 30" or similar delay at the start of the mythfrontend script to delay the frontend startup to after the network fully initializes. This has become a traditional workaround for mythfrontend startup timing issues.

4) Network manager was added to Mythbuntu in 8.04, and has generally been slower than molasses, contributing timing problems to mythfrontend startup. Primarily (in my opinion) from misplacing what ought to happen early in init or upstart process well before Xinit to the graphical shell instead. Good for laptops, bad for everybody else. But Network Manager is not the only solution --wicd is possible and does its real work before X starts up. Also some of the more intrepid 8.04 users just ripped out Network Manager and composed upstart scripts to connect to their networks prior to X starting, using a command set more or less in accordance with what can now be found in places like sections 1.3 and 1.3.1 of a networking guide for 12.04 found here: [http://ubuntuguide.org/wiki/Ubuntu_Precise_Network_Management#Set_a_static_IP_address](http://ubuntuguide.org/wiki/Ubuntu_Precise_Network_Management#Set_a_static_IP_address) 

One of these solutions or workarounds would be expected to work for you. There are likely to be several others.

---

### Post by dibuntux on 2012-11-26
Hi, just upgraded from 10.04 lts amd64 to 12.04 lts amd64. Everything OK on the main pc (frontend & backend), but cannot connect to database on remote frontend.
I get the set country screen, then I'm presented with the database set option, and everything is as it shoud be: IP, ID, PWD, port... it does not work anymore. On Myth control the MySQL test is succesful; I can use MythWeb, connect to shares & control the PC with VNC...Tried uninstalling Myth (0.25) and reinstall, the same.
Tried from a LiveCD 12.04 from a notebook: test ok but the frontend does not start.
Any ideas? TIA

---

### Post by klc5555 on 2012-11-26
Is the mysqld service on the master backend still set to accept remote connections after the upgrade?  

Have you run "mythfrontend" from a terminal on one of the remote frontends to see what the output is on the screen when mythfrontend fails to connect? Have you taken a look at what the mythbackend log and the mythfrontend log indicate after one of the failed connect attempts? May give you a bit more data to debug your issue with.

---

### Post by boy007 on 2012-12-02
I have:
- 12.4 LTS 64bit server, mythweb and 3 mythfrontends
- mythfrontend did not start
- mythweb was ok
- mysql worked
- ping was ok

Solution:

a) I checked out "Check server availability" from setting
and the its started.


b) time to time I have had problem's if difrent time between
sever and clients, booting, crash, poweroff,... then ntp time must be updated:
> ntpdate ntp.ubuntu.com

c) Several time's lost country / time zone after software upgrades 
and had to corect it:
  	 	 	 	 	 	   > dpkg-reconfigure tzdata

---

### Post by 0nelove on 2012-12-03
> **klc5555 said:**
> There are many potential ways to address these issues.

1) Reserve the appropriate DHCP address in the router for your backend, but set up static IP for _that very same address_ on your backend machine anyway. No IP conflict, because the address is reserved for you, but you don't have to wait for your gimpy DHCP server in the router to dish out the address.


Appreciated - this solution was useful, as was this thread in general.

---

### Post by dibuntux on 2012-12-06
> **klc5555 said:**
> Is the mysqld service on the master backend still set to accept remote connections after the upgrade?  

Have you run "mythfrontend" from a terminal on one of the remote frontends to see what the output is on the screen when mythfrontend fails to connect? Have you taken a look at what the mythbackend log and the mythfrontend log indicate after one of the failed connect attempts? May give you a bit more data to debug your issue with.

My Backend is on a static IP, time zone is ok & NTP is Ok.
I started Mythfrontend from the remote, and this is the error I get:

QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'ttbunt.local' (using password: YES)

mythtv is the right user I always used and all PWD are correct. Pin is 0000 and tested OK. ttbunt is the remote machine I'm using.

Any ideas?

---

### Post by klc5555 on 2012-12-06
> **dibuntux said:**
> My Backend is on a static IP, time zone is ok & NTP is Ok.
I started Mythfrontend from the remote, and this is the error I get:

QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'ttbunt.local' (using password: YES)

mythtv is the right user I always used and all PWD are correct. Pin is 0000 and tested OK. ttbunt is the remote machine I'm using.

Any ideas?


Is the mysqld service on the master backend still set to accept remote connections after the upgrade? Check in its MCC.

If the above is not the issue, then is the password that your mythfrontend is using after the upgrade really the current correct one? Can you use it to log into mysql directly from a prompt on the backend machine? i.e.:```
mysql -u mythtv -p
```

If you can log into mysql using the mysql password, and have exited, check whether the config.xml file in the /.mythtv directory under /home/mythtv (and the one under /home/[your main user]) on the remote frontend machine is set up with the correct dbhost address, username, and mysql password.  

On the backend, check whether the my.cnf file (usually under /etc/mysql/ ) has the line "skip-networking" remarked out ("#"), and that there is a line ```
bind-address =
``` that has your master backend's IP address. Also the init or upstart script under /etc/init.d used to start the mysql daemon can be checked for a line similar to:```
SKIP=" --skip-networking"
``` which, if it exists in the file, will need to be remarked out (#) . Either of these "skip" lines being active would render your backend mysqld local-host only. If a change is introduced in either of these files, mysqld will need to be restarted for it to take effect.

These are some of the things that can be checked.

---

### Post by dibuntux on 2012-12-07
OK the pwd is incorrect: mysql -u mythtv -p
I can enter with the pwd which is displayed on the backend in Setup/General, which is a new one.

On the remote, if I try to input this pwd in place of the old one I had previous the upgrade, the procedure come back at same mask, with displayed the old pwd: I cannot change the pwd!

So now what?

---

### Post by nickrout on 2012-12-07
Change the password in the see file. mysql.txt and/or config.xml

---

### Post by klc5555 on 2012-12-07
Note also that on your remote frontend you'll have at least 2 of these config.xml files, and possibly as many as four or more (under /home/mythtv/.mythtv ; /home/[your user]/.mythtv ; /root/.mythtv ; maybe under /user/share/mythtv/somewhere-or-other ; also possibly under /etc/mythtv ; and finally under /home/any-other-users-on-the-machine/.mythtv ) These will all need to be found, checked and (where necessary) corrected.  There may be multiple mysql.txt's with roughly the same distribution as above, or none (the file is now deprecated). But, wherever it may exist, it will need to be checked for correctness.

---

### Post by 4partee on 2012-12-08
This happens even though you check the box or answer the question about "Are you going to access the backend from a remote frontend?" during installation.

What actually happens is remote FEs cannot connect and you get the cannot connect to database message.

It is a MythBuntu install bug that has been around for years.

In addition to the bind 127.0.0.1 problem in my.cnf, the installer sets the backend to use 127.0.0.1 in error as well. What happens is that if you have a just installed a FE/BE, the FE only works on that system, but not on any remote system. 

The installer should use the current IP# as was assigned during install because you already said you are going to use remote FEs.  The other problem is that IP# is a DHCP and you really want a static, manual IP#.  Also the installer should fix my.cnf to allow remote FEs.

For now:
1. # the bind line in my.cnf, restart mysql
2. set up a static IP on BE
3. put the IP into the BE
4. put the IP and password in remote FEs

That is what I do. I am sure I have something wrong, so feel free to correct.

HTH;
John

---

### Post by notchicken on 2012-12-08
I've just upgraded from 0.25 to 0.26 and had the same problem.  i.e. not being able to get the frontend to connected to the backend, mythweb was working fine all the passwords, IP addresses etc etc etc all good just couldn't connect to the backend.

The solution was ridiculously simple:

1. On the backend machine, open the system menu and open "Mythbuntu Control Centre"
2. Click the MySQL tab and at the top of the page change the "Master Backend Role" from "Disable" to "Enable" then hit Apply.

:popcorn:

---

### Post by dibuntux on 2012-12-09
> **klc5555 said:**
> Note also that on your remote frontend you'll have at least 2 of these config.xml files, and possibly as many as four or more (under /home/mythtv/.mythtv ; /home/[your user]/.mythtv ; /root/.mythtv ; maybe under /user/share/mythtv/somewhere-or-other ; also possibly under /etc/mythtv ; and finally under /home/any-other-users-on-the-machine/.mythtv ) These will all need to be found, checked and (where necessary) corrected.  There may be multiple mysql.txt's with roughly the same distribution as above, or none (the file is now deprecated). But, wherever it may exist, it will need to be checked for correctness.

To re-check backend net capabilities I downloaded MythTv Android Frontend on my Zopo mobile: it worked ok, so no problem on the backend.

So I checked files is /home/[your user]/.mythtv :
config.xml had user permission and in there the new pwd was set
mysql.txt had root permission and pwd was the OLD one! Changed the pwd to the new one (as root) and it now works as before.

Not exactly user friendly... even for a long time myth user...

Thank you for helping me, and hopefully many others, in solving this!

Merry Xmas to all!

---

### Post by 4partee on 2012-12-09
There should be only one!

```
 locate mysql.txt
/etc/mythtv/mysql.txt
/home/gelmjw/.mythtv/mysql.txt
/home/mythtv/.mythtv/mysql.txt
/usr/share/mythtv/mysql.txt.dist
root@pvr:/home/gelmjw# ls -lha /home/gelmjw/.mythtv/mysql.txt
lrwxrwxrwx 1 gelmjw gelmjw 21 Dec  7 14:28 /home/gelmjw/.mythtv/mysql.txt -> /etc/mythtv/mysql.txt
root@pvr:/home/gelmjw# ls -lha /home/mythtv/.mythtv/mysql.txt
lrwxrwxrwx 1 root root 21 Dec  7 14:20 /home/mythtv/.mythtv/mysql.txt -> /etc/mythtv/mysql.txt
root@pvr:/home/gelmjw# 

```

Links to the one.

HTH;
John

---

### Post by desmane on 2013-01-05
> **notchicken said:**
> I've just upgraded from 0.25 to 0.26 and had the same problem.  i.e. not being able to get the frontend to connected to the backend, mythweb was working fine all the passwords, IP addresses etc etc etc all good just couldn't connect to the backend.

The solution was ridiculously simple:

1. On the backend machine, open the system menu and open "Mythbuntu Control Centre"
2. Click the MySQL tab and at the top of the page change the "Master Backend Role" from "Disable" to "Enable" then hit Apply.

:popcorn:

that was working, thanks dude!! Supercool ):P

---

