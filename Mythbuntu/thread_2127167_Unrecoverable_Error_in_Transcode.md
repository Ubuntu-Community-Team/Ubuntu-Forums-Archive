---
title: "Unrecoverable Error in Transcode"
date: 2013-03-19
forum: Mythbuntu
---

### Post by davekoenig on 2013-03-19
I have installed Mythbuntu 12.04.2 on a older PC with AMD dual core processor, it installs fine, everything seems to setup fine  I have HVR2250 capture card that I manually had to setup drivers, but configured fine. It captures video fine, flags commercials, but gives an Unrecoverable Error when transcoding.  Is there anywhere I can get more information on what exactly the error is?

---

### Post by Elfy on 2013-03-19
*Thread moved to **Mythbuntu**.*

---

### Post by AlecJ on 2013-03-19
It's been fixed (I think) in the repos

[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

---

### Post by davekoenig on 2013-03-22
still does not work, I get following error in mythtranscode.log

Mar 20 23:00:38 MythServer mythtranscode[2856]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythtranscode version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)
Mar 20 23:00:38 MythServer mythtranscode[2856]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Mar 20 23:00:38 MythServer mythtranscode[2856]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Mar 20 23:00:38 MythServer mythtranscode[2856]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Mar 20 23:00:38 MythServer mythtranscode[2856]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Mar 20 23:00:38 MythServer mythtranscode[2856]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Mar 20 23:00:38 MythServer mythtranscode[2856]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Mar 20 23:00:38 MythServer mythtranscode[2856]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Mar 20 23:00:38 MythServer mythtranscode[2856]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Mar 20 23:00:38 MythServer mythtranscode[2856]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Mar 20 23:00:38 MythServer mythtranscode[2856]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
Mar 20 23:00:38 MythServer mythtranscode[2856]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Mar 20 23:00:38 MythServer mythtranscode[2856]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of MythServer
Mar 20 23:00:38 MythServer mythtranscode[2856]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
Mar 20 23:00:38 MythServer mythtranscode[2856]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
Mar 20 23:00:38 MythServer mythtranscode[2856]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Mar 20 23:00:38 MythServer mythtranscode[2856]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Mar 20 23:00:38 MythServer mythtranscode[2856]: N CoreContext main.cpp:540 (main) Transcoding from /var/lib/mythtv/recordings/1052_20130320222100.mpg to /var/lib/mythtv/recordings/1052_20130320222100.mpg.tmp
Mar 20 23:00:39 MythServer mythtranscode[2856]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0xd64180, id(MPEG2VIDEO) type(Video)
Mar 20 23:00:39 MythServer mythtranscode[2856]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec AC3 has 2 channels
Mar 20 23:00:39 MythServer mythtranscode[2856]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0xd64610, id(AC3) type(Audio)
Mar 20 23:00:39 MythServer mythtranscode[2856]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
Mar 20 23:00:39 MythServer mythtranscode[2856]: I ProgramInfoUpdater mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Mar 20 23:00:39 MythServer mythtranscode[2856]: I ProgramInfoUpdater mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Mar 20 23:00:41 MythServer mythtranscode[2856]: N CoreContext transcode.cpp:748 (GetProfile) Transcode: Looking for autodetect profile: Autodetect from 480i
Mar 20 23:00:41 MythServer mythtranscode[2856]: N CoreContext transcode.cpp:773 (GetProfile) Transcode: Using autodetect profile: MPEG2
Mar 20 23:00:41 MythServer mythtranscode[2856]: E CoreContext transcode.cpp:1316 (TranscodeFile) No video information found!
Mar 20 23:00:41 MythServer mythtranscode[2856]: E CoreContext transcode.cpp:1318 (TranscodeFile) Please ensure that recording profiles for the transcoder are set
Mar 20 23:00:41 MythServer mythtranscode[2856]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Mar 20 23:00:41 MythServer mythtranscode[2856]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Mar 20 23:00:41 MythServer mythtranscode[2856]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Mar 20 23:00:41 MythServer mythtranscode[2856]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Mar 20 23:00:41 MythServer mythtranscode[2856]: E CoreContext audio/audiopulsehandler.cpp:260 (Init) Pulse: Context not ready after 1000ms
Mar 20 23:00:41 MythServer mythtranscode[2856]: E CoreContext main.cpp:681 (main) Transcoding /var/lib/mythtv/recordings/1052_20130320222100.mpg failed
Mar 20 23:00:41 MythServer mythtranscode[2856]: N CoreContext main.cpp:775 (WaitToDelete) Transcode: delete old file: waiting while program is in use.
Mar 20 23:00:41 MythServer mythtranscode[2856]: N CoreContext main.cpp:807 (WaitToDelete) Transcode: program is no longer in use.
Mar 20 23:00:41 MythServer mythtranscode[2856]: N CoreContext main.cpp:1039 (CompleteJob) Deleting /var/lib/mythtv/recordings/1052_20130320222100.mpg.tmp
Mar 20 23:00:41 MythServer mythtranscode[2856]: N CoreContext main.cpp:706 (transUnlink) Requesting delete for file 'myth://Default@[::1]:6543/1052_20130320222100.mpg.tmp'.
Mar 20 23:00:41 MythServer mythtranscode[2856]: N CoreContext main.cpp:712 (transUnlink) Deleting file '/var/lib/mythtv/recordings/1052_20130320222100.mpg.tmp'.
Mar 20 23:00:41 MythServer mythtranscode[2856]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: C thread_unknown mythcommandlineparser.cpp:2545 (ConfigureLogging) mythtranscode version: fixes/0.26 [v0.26.0-121-g750a579] [www.mythtv.org](www.mythtv.org)
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: C thread_unknown mythcommandlineparser.cpp:2547 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N thread_unknown mythcommandlineparser.cpp:2549 (ConfigureLogging) Enabled verbose msgs:  general
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N thread_unknown logging.cpp:837 (logStart) Setting Log Level to LOG_INFO
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I Logger logging.cpp:306 (run) Added logging to the console
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I CoreContext mythcorecontext.cpp:231 (Init) Assumed character encoding: en_US.UTF-8
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N CoreContext mythcontext.cpp:493 (LoadDatabaseSettings) Empty LocalHostName.
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I CoreContext mythcontext.cpp:501 (LoadDatabaseSettings) Using localhost value of MythServer
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N CoreContext mythcorecontext.cpp:1283 (InitLocale) Setting QT default locale to EN_US
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I CoreContext mythcorecontext.cpp:1316 (SaveLocaleDefaults) Current locale EN_US
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N CoreContext main.cpp:554 (main) Transcoding from /var/lib/mythtv/recordings/1052_20130320222100.mpg to /var/lib/mythtv/recordings/1052_20130320222100.mpg.tmp
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I Logger logging.cpp:447 (initialTimeout) Added logging to mythlogserver at TCP:35327
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I ProgramInfoUpdater mythcorecontext.cpp:375 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I ProgramInfoUpdater mythcorecontext.cpp:1191 (CheckProtoVersion) Using protocol version 75
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I CoreContext avformatdecoder.cpp:2163 (ScanStreams) AFD: Opened codec 0x139fa20, id(MPEG2VIDEO) type(Video)
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I CoreContext avformatdecoder.cpp:2021 (ScanStreams) AFD: codec AC3 has 2 channels
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I CoreContext avformatdecoder.cpp:2163 (ScanStreams) AFD: Opened codec 0x13a3480, id(AC3) type(Audio)
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N CoreContext transcode.cpp:774 (GetProfile) Transcode: Looking for autodetect profile: Autodetect from 480i
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N CoreContext transcode.cpp:799 (GetProfile) Transcode: Using autodetect profile: MPEG2
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: E CoreContext transcode.cpp:1372 (TranscodeFile) No video information found!
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: E CoreContext transcode.cpp:1374 (TranscodeFile) Please ensure that recording profiles for the transcoder are set
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I SystemSignalManager system-unix.cpp:490 (run) Starting process signal handler
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: E CoreContext audio/audiopulsehandler.cpp:262 (Init) Pulse: Context not ready after 1000ms
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: E CoreContext main.cpp:695 (main) Transcoding /var/lib/mythtv/recordings/1052_20130320222100.mpg failed
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N CoreContext main.cpp:789 (WaitToDelete) Transcode: delete old file: waiting while program is in use.
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N CoreContext main.cpp:821 (WaitToDelete) Transcode: program is no longer in use.
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N CoreContext main.cpp:1053 (CompleteJob) Deleting /var/lib/mythtv/recordings/1052_20130320222100.mpg.tmp
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N CoreContext main.cpp:720 (transUnlink) Requesting delete for file 'myth://Default@[::1]:6543/1052_20130320222100.mpg.tmp'.
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: N CoreContext main.cpp:726 (transUnlink) Deleting file '/var/lib/mythtv/recordings/1052_20130320222100.mpg.tmp'.
Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: I CoreContext mythcontext.cpp:1169 (~MythContext) Waiting for threads to exit.

---

### Post by Akriss on 2013-03-22
Hi,

I am no expert by any means. However, in the log you posted I see: 
> Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: E CoreContext transcode.cpp:1372 (TranscodeFile) No video information found!
 Mar 22 15:16:18 MythServer mythlogserver: mythtranscode[2927]: E CoreContext transcode.cpp:1374 (TranscodeFile) Please ensure that recording profiles for the transcoder are set

I think all you need to do is set up the transcode options on the backend setup page.

This web page [[COLOR="#FF0000"]HERE[/COLOR]]("http://tips.myhdbox.com/2006/05/tip-4-transcode-profiles-for-hdtv.php") should help a bit, or at least point you in the right direction.

Hope it helps.

---

