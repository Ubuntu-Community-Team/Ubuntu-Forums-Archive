---
title: "How come MeTV can scan channels and work while MythTV cant scan?"
date: 2014-03-29
forum: Mythbuntu
---

### Post by sdowney717 on 2014-03-29
In the backend under channel config I see a channel scan. But the button click does not nothing at all.

This is NAmerica ATSC

---

### Post by blm-ubunet on 2014-03-29
What tuner type did you select (for this card)?
"DVB-T/S/C, ATSC or ISDB-T tuner card"

The analogue part does not work (AFAIK).

Sure the BE is not running during scan in myth-setup?
sudo service mythtv-backend status

Don't use "sudo" unless really necessary..**don't use** sudo to start mythtv-setup.
Don't use sudo with "hg svn git make".

mythtv BE logs from startup or start mythtv-setup with extra logging to a file..
The default loglevel stdout (into terminal) might be enough but will overflow the buffer.

---

### Post by sdowney717 on 2014-03-29
Oh my, so 
how do you run from the commandline again?
And how to record a log?

Yes it is not running, when I run mythtv backend, it asks me to stop and I say yes.
I managed to find a tuner section, it shows a lot of tuners, I select an ATSC DVBT type tuner, seems like generic not specific listing for what I have.
It does not say its an avermedia genie card.
I go to next and scan channels cant be clicked, ot skips right over.

In the myth frontend, some place it shows the status, and says tuners have a problem in yellow.

I have never been able to figure out how to make myth tv work for years. Seriously.

Is it a mystery?

If I could run in a window, I could show screen shots, how to run mythtv backend windowed?

---

### Post by sdowney717 on 2014-03-29
ok, used a camera to take pictures of screen.

Channel scan is disabled, cant select it.

Also The tuner is Avertv Combo PCIE(M780), which does not show in the list. Myth says Divico Fusion etc...

---

### Post by sdowney717 on 2014-03-29
I picked up var log backendlog for myth for mar29

```
Mar 29 16:48:25 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Mar 29 16:48:25 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Mar 29 16:48:25 scott-P5QC mythbackend: mythbackend[1976]: N CoreContext main_helpers.cpp:582 (run_backend) MythBackend: Starting up as the master server.
Mar 29 16:48:25 scott-P5QC mythbackend: mythbackend[1976]: W CoreContext main_helpers.cpp:214 (setupTVs) MythBackend: No valid capture cards are defined in the database.
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: E CoreContext scheduler.cpp:180 (VerifyCards) Scheduler: **No capture cards are defined in the database.#012#011#011#011Perhaps you should re-read the installation instructions?**
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext programinfo.cpp:2136 (CheckProgramIDAuthorities) Found 0 distinct programid authorities
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I Scheduler mythdbcon.cpp:436 (getStaticCon) New static DB connectionSchedCon
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'LogClean'.
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'DBCleanup'.
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'ThemeUpdateNotifications'.
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'RecordedArtworkUpdate'.
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'MythFillDB'.
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'JobQueueRecover'.
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'HardwareProfiler'.
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext housekeeper.cpp:655 (Start) Starting HouseKeeper.
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6544
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6544
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::222:15ff:fe54:faa6%eth1]:6544
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: N CoreContext mediaserver.cpp:168 (Init) MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext main_helpers.cpp:668 (run_backend) Main::Registering HttpStatus Extension
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6543
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6543
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::222:15ff:fe54:faa6%eth1]:6543
Mar 29 16:48:26 scott-P5QC mythbackend: mythbackend[1976]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E CoreContext storagegroup.cpp:763 (CheckAllStorageGroupDirs) SG(Videos): Group 'Videos' wants to use directory '/mnt/', but this directory is not writeable.
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E CoreContext storagegroup.cpp:763 (CheckAllStorageGroupDirs) SG(Streaming): Group 'Streaming' wants to use directory '/mnt/', but this directory is not writeable.
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext housekeeper.cpp:674 (Run) Queueing HouseKeeperTask 'LogClean'.
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I HouseKeeping housekeeper.cpp:133 (Run) Running HouseKeeperTask 'LogClean'.
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I HouseKeeping housekeeper.cpp:151 (Run) HouseKeeperTask 'LogClean' Finished Successfully.
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 0)
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 1)
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Playback
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 0)
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 0)
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 1)
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Playback
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-p5qc as a client (events: 0)
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1538 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1540 (HandleAnnounce) adding: scott-p5qc as a remote file transfer
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 0)
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 1)
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 0)
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 1)
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 4
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Playback
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-p5qc as a client (events: 0)
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1538 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1540 (HandleAnnounce) adding: scott-p5qc as a remote file transfer
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:850 (ProcessRequestWork) Reloading backend settings
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
Mar 29 16:48:27 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 2
Mar 29 16:48:29 scott-P5QC mythbackend: mythbackend[1976]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - SchedulerInit
Mar 29 16:48:29 scott-P5QC mythbackend: mythbackend[1976]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 0 items in 0.0 = 0.03 match + 0.00 check + 0.01 place
Mar 29 16:48:29 scott-P5QC mythbackend: mythbackend[1976]: I Scheduler scheduler.cpp:2278 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
Mar 29 16:49:45 scott-P5QC mythbackend: mythbackend[1976]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Mar 29 18:37:12 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 18:37:12 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 0)
Mar 29 18:37:12 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 18:37:12 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 1)
Mar 29 18:37:12 scott-P5QC mythbackend: mythbackend[1976]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 5
Mar 29 18:37:12 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
Mar 29 18:37:12 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
Mar 29 18:38:26 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Playback
Mar 29 18:38:26 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 0)
Mar 29 18:38:40 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 18:38:40 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 0)
Mar 29 18:38:40 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 18:38:40 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 1)
Mar 29 18:38:52 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:850 (ProcessRequestWork) Reloading backend settings
Mar 29 18:38:56 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Playback
Mar 29 18:38:56 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-p5qc as a client (events: 0)
Mar 29 18:38:56 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1538 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Mar 29 18:38:56 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1540 (HandleAnnounce) adding: scott-p5qc as a remote file transfer
Mar 29 18:39:24 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
Mar 29 18:39:24 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 1
Mar 29 18:39:24 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
Mar 29 18:39:24 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_SLEEPSTATUS) Unknown encoder: 2
Mar 29 18:39:41 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:850 (ProcessRequestWork) Reloading backend settings
Mar 29 18:39:50 scott-P5QC mythbackend: mythbackend[1976]: I Scheduler mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 6
Mar 29 18:39:50 scott-P5QC mythbackend: mythbackend[1976]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for PLACE TVMenuCallback
Mar 29 18:39:50 scott-P5QC mythbackend: mythbackend[1976]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.00 check + 0.01 place
Mar 29 18:39:53 scott-P5QC mythbackend: mythbackend[1976]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for PLACE SaveChannelPriority
Mar 29 18:39:53 scott-P5QC mythbackend: mythbackend[1976]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 0 items in 0.0 = 0.00 match + 0.00 check + 0.01 place
Mar 29 18:40:31 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 18:40:31 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 0)
Mar 29 18:40:31 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 18:40:31 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 1)
Mar 29 18:40:31 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
Mar 29 18:40:31 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
Mar 29 18:49:45 scott-P5QC mythbackend: mythbackend[1976]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Mar 29 19:04:45 scott-P5QC mythbackend: mythbackend[1976]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Mar 29 19:16:38 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 19:16:38 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 0)
Mar 29 19:16:38 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 29 19:16:38 scott-P5QC mythbackend: mythbackend[1976]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: scott-P5QC as a client (events: 1)
Mar 29 19:16:38 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1
Mar 29 19:16:38 scott-P5QC mythbackend: mythbackend[1976]: E ProcessRequest mainserver.cpp:4251 (HandleRemoteEncoder) MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
Mar 29 19:19:45 scott-P5QC mythbackend: mythbackend[1976]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

---

### Post by sdowney717 on 2014-03-29
run from terminal shows this
```
scott@scott-P5QC:~$  mythbackend
2014-03-29 19:38:17.142576 C  mythbackend version: fixes/0.27 [v0.27-187-g30d86b1] www.mythtv.org
2014-03-29 19:38:17.142593 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2014-03-29 19:38:17.142596 N  Enabled verbose msgs:  general
2014-03-29 19:38:17.142604 N  Setting Log Level to LOG_INFO
2014-03-29 19:38:17.153114 I  Added logging to the console
2014-03-29 19:38:17.153584 I  Setup Interrupt handler
2014-03-29 19:38:17.153593 I  Setup Terminated handler
2014-03-29 19:38:17.153601 I  Setup Segmentation fault handler
2014-03-29 19:38:17.153608 I  Setup Aborted handler
2014-03-29 19:38:17.153615 I  Setup Bus error handler
2014-03-29 19:38:17.153623 I  Setup Floating point exception handler
2014-03-29 19:38:17.153631 I  Setup Illegal instruction handler
2014-03-29 19:38:17.153641 I  Setup Real-time signal 0 handler
2014-03-29 19:38:17.153670 N  Using runtime prefix = /usr
2014-03-29 19:38:17.153680 N  Using configuration directory = /home/scott/.mythtv
2014-03-29 19:38:17.153731 I  Assumed character encoding: en_US.UTF-8
2014-03-29 19:38:17.154010 N  Empty LocalHostName.
2014-03-29 19:38:17.154018 I  Using localhost value of scott-P5QC
2014-03-29 19:38:17.172085 N  Setting QT default locale to EN_US
2014-03-29 19:38:17.172143 I  Current locale EN_US
2014-03-29 19:38:17.172189 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2014-03-29 19:38:17.175881 I  Current MythTV Schema Version (DBSchemaVer): 1317
2014-03-29 19:38:17.176177 I  Loading en_us translation for module mythfrontend
2014-03-29 19:38:17.176451 N  MythBackend: Starting up as the master server.
2014-03-29 19:38:17.178207 E  TVRec[1]: Problem finding starting channel, setting to default of '3'.
2014-03-29 19:38:17.198440 E  InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
2014-03-29 19:38:17.198468 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2014-03-29 19:38:17.198522 E  Problem with capture cardsCard 1failed init
2014-03-29 19:38:17.199155 E  TVRec[2]: Problem finding starting channel, setting to default of '3'.
2014-03-29 19:38:17.199231 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.249322 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.254394 I  New Client:  (#1)
2014-03-29 19:38:17.299478 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.349573 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.399730 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.449829 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.499974 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.550068 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.600213 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.650334 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.700484 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.750577 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.800722 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.850816 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.900963 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:17.951056 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:18.001218 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:18.051311 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:18.101472 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:18.151619 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-03-29 19:38:18.151634 E  DVBChan[2](/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2014-03-29 19:38:18.151645 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2014-03-29 19:38:18.151686 E  Problem with capture cardsCard 2failed init
2014-03-29 19:38:18.151700 W  MythBackend: No valid capture cards are defined in the database.
2014-03-29 19:38:18.152189 E  Scheduler: No channel sources defined in the database
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2014-03-29
```
scott@scott-P5QC:~$ ls -lh /dev/dvb/adapter0/** 
crw-rw----+ 1 root video 212, 1 Mar 29 16:47 /dev/dvb/adapter0/demux0
crw-rw----+ 1 root video 212, 2 Mar 29 16:47 /dev/dvb/adapter0/dvr0
crw-rw----+ 1 root video 212, 0 Mar 29 16:47 /dev/dvb/adapter0/frontend0
crw-rw----+ 1 root video 212, 3 Mar 29 16:47 /dev/dvb/adapter0/net0

scott@scott-P5QC:~$ cat /etc/group | grep video* 
scott@scott-P5QC:~$ 
```

From web page [http://www.gossamer-threads.com/lists/mythtv/users/524578](http://www.gossamer-threads.com/lists/mythtv/users/524578)

mentions something about video group, his shows mythtv, mine shows nothing

I dont have a clue.

---

### Post by sdowney717 on 2014-03-29
I ran a manual scan of ATSC 
[http://www.linuxquestions.org/questions/linux-hardware-18/dvbscan-not-working-with-pinnacle-tv-pci-card-failed-to-open-frontend-4175443792/](http://www.linuxquestions.org/questions/linux-hardware-18/dvbscan-not-working-with-pinnacle-tv-pci-card-failed-to-open-frontend-4175443792/)
here is output
It definitely finds  the channels
here is the list
```
dumping lists (26 services)
Trinity Broadcasting Network:177028615:8VSB:49:52:3
Trinity Broadcasting Network:177028615:8VSB:65:68:4
Trinity Broadcasting Network:177028615:8VSB:81:84:5
Trinity Broadcasting Network:177028615:8VSB:97:100:6
Trinity Broadcasting Network:177028615:8VSB:113:116:7
WSKY-HD:189028615:8VSB:49:52:3
WVEC-HD:213028615:8VSB:49:52:1
LWN:213028615:8VSB:65:68:2
Me TV:213028615:8VSB:81:84:3
WHRO High Definition:485028615:8VSB:49:52:3
WORLD:485028615:8VSB:65:68:4
KIDS:485028615:8VSB:97:100:6
WVBT:563028615:8VSB:49:52:3
WAVY:575028615:8VSB:49:52:3
Bounce:575028615:8VSB:65:68:4
WTVZ-MY:587028615:8VSB:49:52:3
WTVZ-TC:587028615:8VSB:81:84:5
WTKR-DT:629028615:8VSB:49:52:3
WPXV ION:665028615:8VSB:49:52:3
WPXV qubo:665028615:8VSB:65:68:4
IONLife:665028615:8VSB:81:84:5
Shop:665028615:8VSB:97:100:6
WPXV QVC:665028615:8VSB:113:116:7
HSN:665028615:8VSB:129:132:8
WGNT-DT:689028615:8VSB:49:52:1
Antenna:689028615:8VSB:65:68:2
Done.

```

```

scott@scott-P5QC:~$ scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB
scanning /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 57028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 79028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 79028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 85028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 85028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 177028615:8VSB
service is running. Channel number: 21:1. Name: 'Trinity Broadcasting Network'
service is running. Channel number: 21:2. Name: 'Trinity Broadcasting Network'
service is running. Channel number: 21:3. Name: 'Trinity Broadcasting Network'
service is running. Channel number: 21:4. Name: 'Trinity Broadcasting Network'
service is running. Channel number: 21:5. Name: 'Trinity Broadcasting Network'
>>> tune to: 183028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 183028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 189028615:8VSB
service is running. Channel number: 4:1. Name: 'WSKY-HD'
>>> tune to: 195028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 201028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 207028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 207028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 213028615:8VSB
service is running. Channel number: 13:1. Name: 'WVEC-HD'
service is running. Channel number: 13:2. Name: 'LWN'
service is running. Channel number: 13:3. Name: 'Me TV'
>>> tune to: 473028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 479028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 479028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 485028615:8VSB
service is running. Channel number: 15:1. Name: 'WHRO High Definition'
service is running. Channel number: 15:2. Name: 'WORLD'
service is running. Channel number: 15:3. Name: 'KIDS'
>>> tune to: 491028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 497028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 497028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 503028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 503028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 509028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 515028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 515028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 521028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 527028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 527028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 533028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 533028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 539028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 545028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 551028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 551028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 557028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 557028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 563028615:8VSB
service is running. Channel number: 43:1. Name: 'WVBT'
>>> tune to: 569028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 569028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 575028615:8VSB
service is running. Channel number: 10:1. Name: 'WAVY'
service is running. Channel number: 10:2. Name: 'Bounce'
>>> tune to: 581028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 581028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 587028615:8VSB
service is running. Channel number: 33:1. Name: 'WTVZ-MY'
service is running. Channel number: 33:3. Name: 'WTVZ-TC'
>>> tune to: 593028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 593028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 599028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 599028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 605028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 605028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 611028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 611028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 617028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 617028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 623028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 623028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 629028615:8VSB
service is running. Channel number: 3:1. Name: 'WTKR-DT'
>>> tune to: 635028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 635028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 641028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 647028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 653028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 653028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 659028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 665028615:8VSB
service is running. Channel number: 49:1. Name: 'WPXV ION'
service is running. Channel number: 49:2. Name: 'WPXV qubo'
WARNING: compressed strings are not supported yet
service is running. Channel number: 49:3. Name: 'IONLife'
WARNING: compressed strings are not supported yet
service is running. Channel number: 49:4. Name: 'Shop'
service is running. Channel number: 49:5. Name: 'WPXV QVC'
service is running. Channel number: 49:6. Name: 'HSN'
>>> tune to: 671028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 671028615:8VSB (tuning failed)
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 677028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 677028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 683028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 683028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 689028615:8VSB
service is running. Channel number: 27:1. Name: 'WGNT-DT'
service is running. Channel number: 27:2. Name: 'Antenna'
>>> tune to: 695028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 695028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 701028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 701028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 707028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 707028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 713028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 713028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 719028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 719028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 725028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 725028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 731028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 731028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 737028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 737028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 743028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 743028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 749028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 749028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 755028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 755028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 761028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 761028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 767028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 767028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 773028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 773028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 779028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 779028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 785028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 785028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 791028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 791028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 797028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 797028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 803028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 803028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (26 services)
Trinity Broadcasting Network:177028615:8VSB:49:52:3
Trinity Broadcasting Network:177028615:8VSB:65:68:4
Trinity Broadcasting Network:177028615:8VSB:81:84:5
Trinity Broadcasting Network:177028615:8VSB:97:100:6
Trinity Broadcasting Network:177028615:8VSB:113:116:7
WSKY-HD:189028615:8VSB:49:52:3
WVEC-HD:213028615:8VSB:49:52:1
LWN:213028615:8VSB:65:68:2
Me TV:213028615:8VSB:81:84:3
WHRO High Definition:485028615:8VSB:49:52:3
WORLD:485028615:8VSB:65:68:4
KIDS:485028615:8VSB:97:100:6
WVBT:563028615:8VSB:49:52:3
WAVY:575028615:8VSB:49:52:3
Bounce:575028615:8VSB:65:68:4
WTVZ-MY:587028615:8VSB:49:52:3
WTVZ-TC:587028615:8VSB:81:84:5
WTKR-DT:629028615:8VSB:49:52:3
WPXV ION:665028615:8VSB:49:52:3
WPXV qubo:665028615:8VSB:65:68:4
IONLife:665028615:8VSB:81:84:5
Shop:665028615:8VSB:97:100:6
WPXV QVC:665028615:8VSB:113:116:7
HSN:665028615:8VSB:129:132:8
WGNT-DT:689028615:8VSB:49:52:1
Antenna:689028615:8VSB:65:68:2
Done.
scott@scott-P5QC:~$ 

```

---

### Post by blm-ubunet on 2014-03-29
Check the tuner card has loaded firmware
```
dmesg | egrep -i '(firmware|atsc|dvb)'
```

Have you worked thru' each screen one by one from start to finish??
The error message indicates you have not connected a "video source" to the capture card.

Is your tuner card a dual tuner ?
If it is then create a 2nd tuner entry & connect both to the same video source.

The user "mythtv" (BE user) needs to be a member of video group.

```
sudo -u mythtv groups
```

ASTC/DVB tuner support is via v4l-dvb v4l2 API...mythtv does not have individual drivers for h/w.

I always run
```
sudo service mythtv-backend stop 
```
before running mythtv-setup

Screen shots work via <prt scrn> key (horror/shock)..don't expect that to extend to video overlays tho.. 

Can make mythtv apps windowed &/or smaller with --geometry XXXxYYY+xxx+yyy --windowed

---

### Post by sdowney717 on 2014-03-30
```
scott@scott-P5QC:~$ dmesg | egrep -i '(firmware|atsc|dvb)'
[    9.629153] ngene: Found Aver M780 ATSC/QAM-B
[    9.794045] ngene: Loading firmware file ngene_15.fw.
[   10.193175] DVB: registering new adapter (nGene)
[   10.193180] ngene 0000:04:00.0: DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[   11.146009] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[23969.320144] Modules linked in: nls_iso8859_1 usb_storage btrfs raid6_pq xor ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c bnep rfcomm bluetooth binfmt_misc nvidia(POF) nls_utf8 cifs fscache ivtv_alsa cs53l32a mt2131 saa7115 lgdt330x snd_hda_codec_realtek ivtv snd_hda_intel tveeprom cx2341x v4l2_common snd_hda_codec videodev snd_hwdep i2c_algo_bit snd_pcm snd_page_alloc snd_seq_midi ngene snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer cxd2099(C) serio_raw snd dvb_core coretemp soundcore lpc_ich asus_atk0110 mac_hid lp parport pata_acpi pata_marvell hid_generic usbhid hid firewire_ohci firewire_core crc_itu_t floppy atl1e ahci libahci
scott@scott-P5QC:~$ 


```

---

### Post by sdowney717 on 2014-03-30
```
scott@scott-P5QC:~$ sudo -u mythtv groups
[sudo] password for scott: 
mythtv dialout cdrom audio video
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2014-03-30
> **blm-ubunet said:**
> Check the tuner card has loaded firmware
```
dmesg | egrep -i '(firmware|atsc|dvb)'
```

Have you worked thru' each screen one by one from start to finish??
The error message indicates you have not connected a "video source" to the capture card.

Is your tuner card a dual tuner ?
If it is then create a 2nd tuner entry & connect both to the same video source.

The user "mythtv" (BE user) needs to be a member of video group.

```
sudo -u mythtv groups
```

ASTC/DVB tuner support is via v4l-dvb v4l2 API...mythtv does not have individual drivers for h/w.

I always run
```
sudo service mythtv-backend stop 
```
before running mythtv-setup

Screen shots work via <prt scrn> key (horror/shock)..don't expect that to extend to video overlays tho.. 

Can make mythtv apps windowed &/or smaller with --geometry XXXxYYY+xxx+yyy --windowed

The card only has one ATSC tuner. The other tuner is NTSC
MythTV shows 2 tuners in the status menu.

In the past, Mythtv has been confused about my PCI video'OH' Adaptec capture card thinking it is a tuner card. But all it does is capture stereo and svideo or composite like from VHS, DVD for recording onto a computer.

---

### Post by blm-ubunet on 2014-03-30
So did you create the entry for the analogue tuner (along with digital ATSC) ?

It is possible (v common with Haupaugue hybrid models) that the analogue & digital parts can not be used together.
You have to make them part of the same *input group* to prevent them from being used at same time.
Not sure if it is better or not to just delete analogue entry.

So.. did you connect the video source to the digital tuner ??
(as it states in error log)

---

### Post by sdowney717 on 2014-03-30
> **blm-ubunet said:**
> So did you create the entry for the analogue tuner (along with digital ATSC) ?

It is possible (v common with Haupaugue hybrid models) that the analogue & digital parts can not be used together.
You have to make them part of the same *input group* to prevent them from being used at same time.
Not sure if it is better or not to just delete analogue entry.

So.. did you connect the video source to the digital tuner ??
(as it states in error log)

Actually dont know, did I create an entry?
Did I connect the video source to the digital tuner?
Dont know, where and how to do that?

I really dont know. IMO, logically a person selects the ATSC tuner, then goto channel edit  and select scan. I did nothing else.
Did I miss something in setting up a tuner?

---

### Post by blm-ubunet on 2014-03-30
Logically someone who does not know what they are doing would do lots of reading & then follow instructions on the mythtv wiki.
[http://www.mythtv.org/wiki/MythTV-HOWTO_-_0.27](http://www.mythtv.org/wiki/MythTV-HOWTO_-_0.27)

It is not perfect but it is there..

---

### Post by sdowney717 on 2014-03-30
> **blm-ubunet said:**
> Logically someone who does not know what they are doing would do lots of reading & then follow instructions on the mythtv wiki.
[http://www.mythtv.org/wiki/MythTV-HOWTO_-_0.27](http://www.mythtv.org/wiki/MythTV-HOWTO_-_0.27)

It is not perfect but it is there..

Yup, thanks. 
It would be nice to run windowed and look at the wiki. It is disconcerting to have to close out mythbackend to read instructions.

Do you know how to run mythbackend windowed?

---

### Post by sdowney717 on 2014-03-31
I managed to get myth to scan channels
Running mythfilldatabase is being a problem I think.
I noticed  a schedules direct default. I set to EIT so should get the data from the transmitters.

But it remains stuck on downloading datadirect feed

Is this ok? How long will it take?

---

### Post by sdowney717 on 2014-03-31
Ok, I can now watch TV in MythTV.

It works ok, but I dont really like the skip behind design. I would have rather seen a timeline bar and be able to select like in WMC.
Sometimes the subchannels dont show th numbers, just a 49... vs 49.1 then 49.2 when changing channels using the arrow keys.

I started myth frontend before the datagrabber was don, and that finally terminated.
And I have EPG data showing in mythTV

To run windowed, but I only found info for the frontend, not backend use like this format

mythfrontend -w --geometry 1024x768

example, this is channel 13.3, but only shows 1....

---

### Post by sdowney717 on 2014-03-31
sometimes channel number appears as it should, sometimes it does not.

Notice this IS the same channel 13.3 with the same description. Picture taken minute apart.

---

### Post by sdowney717 on 2014-03-31
That was bizarre, I started mythtv and all channels were slomotion with no sound.
Then I closed and the program hung and eventually I had to force quit.
Then restarted and it was ok again.

---

