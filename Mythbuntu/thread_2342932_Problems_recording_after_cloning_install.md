---
title: "Problems recording after cloning install"
date: 2016-11-11
forum: Mythbuntu
---

### Post by cain052 on 2016-11-11
I had to clone my Mythbuntu 16.04 installation to another drive since the drive it was on was starting to fail.  Since then, I've had a number of problems getting recordings to work.  For some reason MythTV is having problems connecting to my HDHomeRun tuner.  If I delete and re-add the tuners, sometimes that will solve the problem until the next reboot.  Nothing about the configuration has changed other than being cloned to another drive.  I even did a fresh install, but still run in to these issues.  Here's the errors that I believe are causing the issue, and below I provide the entire log for the time a recording was to take place.

```

Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: E TVRecEvent dtvmultiplex.cpp:379 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0xffffffff80000000
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: E TVRecEvent recorders/dtvchannel.cpp:299 (SetChannelByString) DTVChan[1](103B5110-0): SetChannelByString(13_1): Failed to initialize multiplex options
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: E TVRecEvent tv_rec.cpp:3763 (TuningFrequency) TVRec[1]: Failed to set channel to 13_1. Reverting to kState_None

```

I've tried setting the multiplex option to 1 (it's 2 by default), but I've always had it set to the default an never had problems before.  Originally I had MythTV set up on Arch, but I switched over to Mythbuntu in order to have a more stable environment.

Entire log:

```

Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I TVRecEvent tv_rec.cpp:1073 (HandleStateChange) TVRec[1]: Changing from None to RecordingOnly
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I TVRecEvent mythdbcon.cpp:422 (PurgeIdleConnections) New DB connection, total: 8
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I TVRecEvent tv_rec.cpp:3563 (TuningCheckForHWChange) TVRec[1]: HW Tuner: 1->1
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I TVRecEvent tv_rec.cpp:3685 (TuningFrequency) TVRec[1]: TuningFrequency
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: E TVRecEvent dtvmultiplex.cpp:379 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0xffffffff80000000
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: E TVRecEvent recorders/dtvchannel.cpp:299 (SetChannelByString) DTVChan[1](103B5110-0): SetChannelByString(13_1): Failed to initialize multiplex options
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: E TVRecEvent tv_rec.cpp:3763 (TuningFrequency) TVRec[1]: Failed to set channel to 13_1. Reverting to kState_None
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I TVRecEvent tv_rec.cpp:1073 (HandleStateChange) TVRec[1]: Changing from RecordingOnly to None
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I CoreContext scheduler.cpp:725 (UpdateRecStatus) Updating status for "Grey's Anatomy":"The Room Where It Happens" on cardid 1 (Will Record => Recorder Failed)
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I Scheduler scheduler.cpp:2819 (HandleRecordingStatusChange) Tuning recording: "Grey's Anatomy":"The Room Where It Happens": channel 1131 on cardid 1, sourceid 1
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I Scheduler scheduler.cpp:2267 (HandleReschedule) Reschedule requested for CHECK -9 2 0 UpdateRecStatus2 | Grey's Anatomy | The Room Where It Happens | A critical surgery brings back pivotal memories for Meredit
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: E Scheduler recordinginfo.cpp:1025 (InsertProgram) RecordingInfo::InsertProgram(ProgramInfo(1131_20161111000000.ts): channame(CJOH) startts(Fri Nov 11 00:00:00 2016 GMT) endts(Fri Nov 11 01:00:00 2016 GMT)
                                                       recstartts(Fri Nov 11 00:00:00 2016 GMT) recendts(Fri Nov 11 01:00:00 2016 GMT)
                                                       title(Grey's Anatomy)): recording already exists...
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I TVRecEvent tv_rec.cpp:1073 (HandleStateChange) TVRec[1]: Changing from None to RecordingOnly
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I TVRecEvent tv_rec.cpp:3563 (TuningCheckForHWChange) TVRec[1]: HW Tuner: 1->1
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I TVRecEvent tv_rec.cpp:3685 (TuningFrequency) TVRec[1]: TuningFrequency
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: E TVRecEvent dtvmultiplex.cpp:379 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0xffffffff80000000
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: E TVRecEvent recorders/dtvchannel.cpp:299 (SetChannelByString) DTVChan[1](103B5110-0): SetChannelByString(13_1): Failed to initialize multiplex options
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: E TVRecEvent tv_rec.cpp:3763 (TuningFrequency) TVRec[1]: Failed to set channel to 13_1. Reverting to kState_None
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I TVRecEvent tv_rec.cpp:1073 (HandleStateChange) TVRec[1]: Changing from RecordingOnly to None
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I CoreContext scheduler.cpp:725 (UpdateRecStatus) Updating status for "Grey's Anatomy":"The Room Where It Happens" on cardid 1 (Tuning => Recorder Failed)
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: E Scheduler scheduler.cpp:787 (ChangeRecordingEnd) Failed to change end time on card 1 to 2016-11-11T01:00:00Z
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I Scheduler scheduler.cpp:2371 (HandleReschedule) Reschedule interrupted, will retry
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I Scheduler scheduler.cpp:2267 (HandleReschedule) Reschedule requested for CHECK -9 2 0 UpdateRecStatus2 | Grey's Anatomy | The Room Where It Happens | A critical surgery brings back pivotal memories for Meredit
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I Scheduler scheduler.cpp:2267 (HandleReschedule) Reschedule requested for PLACE Interrupted
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: I Scheduler scheduler.cpp:2380 (HandleReschedule) Scheduled 4 items in 0.0 = 0.00 match + 0.00 check + 0.00 place
Nov 10 19:00:00 server mythbackend[1039]: mythbackend[1039]: C CoreContext programinfo.cpp:351 (ProgramInfo) ProgramInfo(): Failed to find recorded entry for 0.
Nov 10 19:00:05 server mythbackend[1039]: mythbackend[1039]: N Update autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 0.0 GB w/freq: 15 min
Nov 10 19:00:05 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Monitor
Nov 10 19:00:05 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: server(1684af0) as a client (events: 0)
Nov 10 19:00:05 server mythbackend[1039]: mythbackend[1039]: E ProcessRequest programinfo.cpp:2594 (GetPlaybackURL) ProgramInfo(1131_20161111000001.ts): GetPlaybackURL: '1131_20161111000001.ts' should be local, but it can not be found.
Nov 10 19:00:05 server mythbackend[1039]: mythbackend[1039]: E ProcessRequest programinfo.cpp:2594 (GetPlaybackURL) ProgramInfo(1131_20161111000000.ts): GetPlaybackURL: '1131_20161111000000.ts' should be local, but it can not be found.
Nov 10 19:00:05 server mythbackend[1039]: mythbackend[1039]: I MythSocketThread(60) mainserver.cpp:7629 (connectionClosed) Monitor sock(1684af0) 'server' disconnected
Nov 10 19:01:28 server mythbackend[1039]: mythbackend[1039]: E JobQueue programinfo.cpp:2594 (GetPlaybackURL) ProgramInfo(1131_20161111000000.ts): GetPlaybackURL: '1131_20161111000000.ts' should be local, but it can not be found.
Nov 10 19:01:28 server mythbackend[1039]: mythbackend[1039]: E JobQueue programinfo.cpp:2594 (GetPlaybackURL) ProgramInfo(1131_20161111000000.ts): GetPlaybackURL: '1131_20161111000000.ts' should be local, but it can not be found.
Nov 10 19:01:28 server mythbackend[1039]: mythbackend[1039]: I Metadata_45 jobqueue.cpp:2157 (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for "Grey's Anatomy":"The Room Where It Happens" recorded from channel 1131 at 2016-11-11T00:00:00Z
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythmetadatalookup version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I Logger logging.cpp:313 (run) Added logging to the console
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_CA.UTF-8
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of server
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_CA
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_CA
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I CoreContext mythtranslation.cpp:73 (load) Loading en_ca translation for module mythfrontend
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I CoreContext main.cpp:112 (main) Testing grabbers and metadata sites for functionality...
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I SystemSignalManager mythsystemunix.cpp:509 (run) Starting process signal handler
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I SystemManager mythsystemunix.cpp:276 (run) Starting process manager
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I SystemIOHandlerR mythsystemunix.cpp:92 (run) Starting IO manager (read)
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I SystemIOHandlerW mythsystemunix.cpp:92 (run) Starting IO manager (write)
Nov 10 19:01:28 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Nov 10 19:01:29 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I CoreContext main.cpp:119 (main) All grabbers tested and working.  Continuing...
Nov 10 19:01:29 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I CoreContext mythcorecontext.cpp:436 (ConnectCommandSocket) MythCoreContext::ConnectCommandSocket(): Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Nov 10 19:01:29 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I CoreContext mythcorecontext.cpp:1578 (CheckProtoVersion) MythCoreContext::CheckProtoVersion(): Using protocol version 88 XmasGift
Nov 10 19:01:29 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Monitor
Nov 10 19:01:29 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: server(1684af0) as a client (events: 0)
Nov 10 19:01:29 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Monitor
Nov 10 19:01:29 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: server(16af410) as a client (events: 1)
Nov 10 19:01:29 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I MetadataDownload metadatagrabber.cpp:453 (RunGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -a CA -N Grey's Anatomy The Room Where It Happens
Nov 10 19:01:36 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I MetadataDownload metadatacommon.cpp:1202 (ParseMetadataItem) Result Found, Season 13 Episode 8
Nov 10 19:01:37 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I MetadataDownload metadatagrabber.cpp:453 (RunGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -a CA -N 73762 The Room Where It Happens
Nov 10 19:01:37 server mythbackend[1039]: mythbackend[1039]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 0.0 GB w/freq: 15 min
Nov 10 19:01:37 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I MetadataDownload metadatacommon.cpp:1202 (ParseMetadataItem) Result Found, Season 13 Episode 8
Nov 10 19:01:37 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I MetadataDownload metadatadownload.cpp:176 (run) Returning Metadata Results: Grey's Anatomy 13 8
Nov 10 19:01:38 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I MetadataImageDownload metadataimagedownload.cpp:243 (run) Metadata Image Download: http://www.thetvdb.com/banners/seasons/73762-13-2.jpg -> myth://Coverart@server/Grey's Anatomy Season 13_coverar
Nov 10 19:01:39 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: E MetadataImageDownload remotefile.cpp:250 (openSocket) RemoteFile::openSocket(file data socket): Failed to open socket, error was filetransfer_directory_not_found
Nov 10 19:01:39 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: E MetadataImageDownload metadataimagedownload.cpp:270 (run) Image Download: Failed to open remote file (myth://Coverart@server/Grey's Anatomy Season 13_coverart.jpg) for write.  Does Storage Group 
Nov 10 19:01:39 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Playback
Nov 10 19:01:39 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: server(1686e70) as a client (events: 0)
Nov 10 19:01:39 server mythbackend[1039]: mythbackend[1039]: E ProcessRequest mainserver.cpp:1867 (HandleAnnounce) MainServer: Unable to determine directory to write to in FileTransfer write command
Nov 10 19:01:39 server mythbackend[1039]: mythbackend[1039]: I MythSocketThread(68) mainserver.cpp:7669 (connectionClosed) Control sock(16da5a0) disconnected
Nov 10 19:01:39 server mythbackend[1039]: mythbackend[1039]: I MythSocketThread(66) mainserver.cpp:7629 (connectionClosed) Playback sock(1686e70) 'server' disconnected
Nov 10 19:01:40 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: N CoreContext main.cpp:167 (main) MythMetadataLookup run complete.
Nov 10 19:01:40 server mythmetadatalookup[5025]: mythmetadatalookup[5025]: I CoreContext mythcontext.cpp:1195 (~MythContext) Waiting for threads to exit.
Nov 10 19:01:41 server mythbackend[1039]: mythbackend[1039]: I MythSocketThread(60) mainserver.cpp:7629 (connectionClosed) Monitor sock(1684af0) 'server' disconnected
Nov 10 19:01:41 server mythbackend[1039]: mythbackend[1039]: I MythSocketThread(64) mainserver.cpp:7629 (connectionClosed) Monitor sock(16af410) 'server' disconnected
Nov 10 19:02:33 server mythbackend[1039]: mythbackend[1039]: E JobQueue programinfo.cpp:2594 (GetPlaybackURL) ProgramInfo(1131_20161111000001.ts): GetPlaybackURL: '1131_20161111000001.ts' should be local, but it can not be found.
Nov 10 19:02:33 server mythbackend[1039]: mythbackend[1039]: E JobQueue programinfo.cpp:2594 (GetPlaybackURL) ProgramInfo(1131_20161111000001.ts): GetPlaybackURL: '1131_20161111000001.ts' should be local, but it can not be found.
Nov 10 19:02:33 server mythbackend[1039]: mythbackend[1039]: I Metadata_46 jobqueue.cpp:2157 (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for "Grey's Anatomy":"The Room Where It Happens" recorded from channel 1131 at 2016-11-11T00:00:01Z
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythmetadatalookup version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I Logger logging.cpp:313 (run) Added logging to the console
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_CA.UTF-8
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of server
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_CA
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_CA
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I CoreContext mythtranslation.cpp:73 (load) Loading en_ca translation for module mythfrontend
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I CoreContext main.cpp:112 (main) Testing grabbers and metadata sites for functionality...
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I SystemManager mythsystemunix.cpp:276 (run) Starting process manager
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I SystemSignalManager mythsystemunix.cpp:509 (run) Starting process signal handler
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I SystemIOHandlerR mythsystemunix.cpp:92 (run) Starting IO manager (read)
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I SystemIOHandlerW mythsystemunix.cpp:92 (run) Starting IO manager (write)
Nov 10 19:02:33 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Nov 10 19:02:34 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I CoreContext main.cpp:119 (main) All grabbers tested and working.  Continuing...
Nov 10 19:02:34 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I CoreContext mythcorecontext.cpp:436 (ConnectCommandSocket) MythCoreContext::ConnectCommandSocket(): Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Nov 10 19:02:34 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I CoreContext mythcorecontext.cpp:1578 (CheckProtoVersion) MythCoreContext::CheckProtoVersion(): Using protocol version 88 XmasGift
Nov 10 19:02:34 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Monitor
Nov 10 19:02:34 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: server(16866e0) as a client (events: 0)
Nov 10 19:02:34 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Monitor
Nov 10 19:02:34 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: server(1684af0) as a client (events: 1)
Nov 10 19:02:34 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I MetadataDownload metadatagrabber.cpp:453 (RunGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -a CA -N Grey's Anatomy The Room Where It Happens
Nov 10 19:02:35 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I MetadataDownload metadatacommon.cpp:1202 (ParseMetadataItem) Result Found, Season 13 Episode 8
Nov 10 19:02:35 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I MetadataDownload metadatagrabber.cpp:453 (RunGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -a CA -N 73762 The Room Where It Happens
Nov 10 19:02:35 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I MetadataDownload metadatacommon.cpp:1202 (ParseMetadataItem) Result Found, Season 13 Episode 8
Nov 10 19:02:35 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I MetadataDownload metadatadownload.cpp:176 (run) Returning Metadata Results: Grey's Anatomy 13 8
Nov 10 19:02:36 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I MetadataImageDownload metadataimagedownload.cpp:243 (run) Metadata Image Download: http://www.thetvdb.com/banners/seasons/73762-13-2.jpg -> myth://Coverart@server/Grey's Anatomy Season 13_coverar
Nov 10 19:02:37 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: E MetadataImageDownload remotefile.cpp:250 (openSocket) RemoteFile::openSocket(file data socket): Failed to open socket, error was filetransfer_directory_not_found
Nov 10 19:02:37 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: E MetadataImageDownload metadataimagedownload.cpp:270 (run) Image Download: Failed to open remote file (myth://Coverart@server/Grey's Anatomy Season 13_coverart.jpg) for write.  Does Storage Group 
Nov 10 19:02:37 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Playback
Nov 10 19:02:37 server mythbackend[1039]: mythbackend[1039]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: server(1684b90) as a client (events: 0)
Nov 10 19:02:37 server mythbackend[1039]: mythbackend[1039]: E ProcessRequest mainserver.cpp:1867 (HandleAnnounce) MainServer: Unable to determine directory to write to in FileTransfer write command
Nov 10 19:02:37 server mythbackend[1039]: mythbackend[1039]: I MythSocketThread(68) mainserver.cpp:7669 (connectionClosed) Control sock(16f5a00) disconnected
Nov 10 19:02:37 server mythbackend[1039]: mythbackend[1039]: I MythSocketThread(66) mainserver.cpp:7629 (connectionClosed) Playback sock(1684b90) 'server' disconnected
Nov 10 19:02:38 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: N CoreContext main.cpp:167 (main) MythMetadataLookup run complete.
Nov 10 19:02:38 server mythmetadatalookup[5094]: mythmetadatalookup[5094]: I CoreContext mythcontext.cpp:1195 (~MythContext) Waiting for threads to exit.
Nov 10 19:02:39 server mythbackend[1039]: mythbackend[1039]: I MythSocketThread(60) mainserver.cpp:7629 (connectionClosed) Monitor sock(16866e0) 'server' disconnected
Nov 10 19:02:39 server mythbackend[1039]: mythbackend[1039]: I MythSocketThread(64) mainserver.cpp:7629 (connectionClosed) Monitor sock(1684af0) 'server' disconnected

```

---

### Post by cain052 on 2017-01-11
I'm still having this issue, and was hoping to get a response.  If you need me to provide more information please let me know.  The only way I can resolve it is to remove all my hdhr sources, add them back in then stop apache2, mythtv-backend and mysql, then restart them in the reverse order.  It is a real pain to have to do this on every reboot.  I'd really appreciate some help with the issue.

---

### Post by uteck on 2017-01-26
Not sure how to fix the problem, but looks like you found a work around.  You could put your commands into cron so things get restarted properly when the system boots.

sudo crontab -e
@reboot enter command here
@reboot another command

or create a scrpt and put the path to it instead of listing the commands separately.

---

