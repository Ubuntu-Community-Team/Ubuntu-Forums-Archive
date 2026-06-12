---
title: "&quot;recordings not found&quot;"
date: 2013-09-26
forum: Mythbuntu
---

### Post by itlarson2 on 2013-09-26
I have been getting the "recording not found" dialog for some of my recordings when I go to play them.  If I reboot they will start recording normaly and I can start recordings on all three tuners.  here are some log excerpts:

Sep 25 20:57:40 itlmyth mythbackend[3734]: I TVRecEvent tv_rec.cpp:1536 (HandlePendingRecordings) TVRec(9): ASK_RECORDING 9 18 0 0
Sep 25 20:58:00 itlmyth mythbackend[3734]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(9): Changing from None to RecordingOnly
Sep 25 20:58:00 itlmyth mythbackend[3734]: I TVRecEvent tv_rec.cpp:3495 (TuningCheckForHWChange) TVRec(9): HW Tuner: 9->9
Sep 25 20:58:00 itlmyth mythbackend[3734]: E ProcessRequest programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(1021_20130925205800.mpg): GetPlaybackURL: '1021_20130925205800.mpg' should be local, but it can not be found.
Sep 25 20:58:01  mythbackend[3734]: last message repeated 2 times
Sep 25 20:58:01 itlmyth mythbackend[3734]: E TVRecEvent dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(9:/dev/dvb/adapter1/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)
Sep 25 20:58:01 itlmyth mythbackend[3734]: W TVRecEvent dvbsignalmonitor.cpp:85 (DVBSignalMonitor) DVBSM(/dev/dvb/adapter1/frontend0): Cannot measure Signal Strength#012#011#011#011eno: Invalid argument (22)
Sep 25 20:58:01 itlmyth mythbackend[3734]: E TVRecEvent dvbchannel.cpp:1051 (GetSNR) DVBChan(9:/dev/dvb/adapter1/frontend0): Getting Frontend signal/noise ratio failed.#012#011#011#011eno: Invalid argument (22)
Sep 25 20:58:01 itlmyth mythbackend[3734]: W TVRecEvent dvbsignalmonitor.cpp:87 (DVBSignalMonitor) DVBSM(/dev/dvb/adapter1/frontend0): Cannot measure S/N#012#011#011#011eno: Invalid argument (22)
Sep 25 20:58:01 itlmyth mythbackend[3734]: N Scheduler autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
Sep 25 20:58:01 itlmyth mythbackend[3734]: I Scheduler scheduler.cpp:2514 (HandleRecordingStatusChange) Tuning recording: "Skeletons of the Sahara": channel 1021 on cardid 9, sourceid 1
Sep 25 20:58:01 itlmyth mythbackend[3734]: I CoreContext scheduler.cpp:637 (UpdateRecStatus) Updating status for "Skeletons of the Sahara" on cardid 9 (Tuning => Recording)
Sep 25 20:58:02 itlmyth mythbackend[3734]: I TVRecEvent tv_rec.cpp:3989 (TuningNewRecorder) TVRec(9): rec->GetPathname(): '/home/.store/1021_20130925205800.mpg'
Sep 25 20:58:05 itlmyth mythbackend[3734]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Sep 25 20:58:05 itlmyth mythbackend[3734]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: itlmyth as a client (events: 0)
Sep 25 20:58:05 itlmyth mythbackend[3734]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor




Sep 25 21:00:00 itlmyth mythbackend[3734]: I Scheduler scheduler.cpp:2514 (HandleRecordingStatusChange) Started recording: Nashville:"I Fall to Pieces": channel 1051 on cardid 8, sourceid 1
Sep 25 21:00:01 itlmyth mythbackend[3734]: E ProcessRequest programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(1111_20130904205400.mpg): GetPlaybackURL: '1111_20130904205400.mpg' should be local, but it can not be found.
Sep 25 21:00:01 itlmyth mythbackend[3734]: E ProcessRequest programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(1051_20130517204400.mpg): GetPlaybackURL: '1051_20130517204400.mpg' should be local, but it can not be found.
Sep 25 21:00:01 itlmyth mythbackend[3734]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Sep 25 21:00:01 itlmyth mythbackend[3734]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: itlmyth as a client (events: 0)
Sep 25 21:00:01 itlmyth mythbackend[3734]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Sep 25 21:00:01 itlmyth mythbackend[3734]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: itlmyth as a client (events: 1)
Sep 25 21:01:02 itlmyth mythbackend[2561]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythbackend version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)

---

### Post by Kirboosy on 2013-09-26
Welcome to the forums!

Have you recently updated your MythTV box? I was searching around to see if someone had a solution and it looks like when they upgraded MythTV they had a simliar issue.

[Cause of recordings not found]("http://www.gossamer-threads.com/lists/mythtv/users/415263")

Hope that helps!
~Caboose

---

### Post by itlarson2 on 2013-09-26
Thanks for the reply.  I hadn't updated for a month or two before this started happening.  Since then I've tried rescanning one of the tuners, a mysql database repair command- which found nothing wrong, and activating .26 fixes and then updating.

---

### Post by itlarson2 on 2013-09-26
I rescanned each tuner, and although they recorded the first three programs fine, only one of the next three recorded.  After a reboot, all three were working.    I am wondering if this could be something wrong with my two tuner Divco card.  It seems strange that it would fail, but then be fine after a reboot.    For this reason it seems like hardware shouldn't be the issue.  I found the following in the backend log though:

Sep 26 20:13:02 itlmyth mythbackend[7884]: E SignalMonitor dvbchannel.cpp:1022 (GetSignalStrength) DVBChan(10:/dev/dvb/adapter2/frontend0): Getting Frontend signal strength failed.#012#011#011#011eno: Invalid argument (22)

and this:

Sep 26 20:01:00 itlmyth mythbackend[7884]: E CoreContext  mainserver.cpp:871 (customEvent) MainServer: PREVIEW_SUCCESS but no  receivers.

I know /dev/dvb/adapter2/frontend0 is on the divco card.  Both these are from right after the recording failed.

---

### Post by Kirboosy on 2013-09-27
I definitely think it could be a bad driver, bad hardware support. Does DVico made a official Linux driver?

I  found this wiki on DVico cards in Ubuntu but its really old. I don't know if its relevant at all

[DVICO Dual Digital 4]("https://help.ubuntu.com/community/DViCO_Dual_Digital_4")

Hope that helps!
~Caboose

---

### Post by itlarson2 on 2013-09-27
Actualy the tuner is a Dvico Fusion hdtv7.  I've been using it for about two years without problems.  If I can't fix this soon, i'll do a reinstall on saturday.

---

### Post by itlarson2 on 2013-09-28
I don&#8217;t want to curse it, but it seems to be working right after a complete reinstall.  I've had all tuners recording non-stop for a couple hours, and so far all the recordings are good.

---

### Post by Kirboosy on 2013-09-30
Hopefully so. 

Sorry I couldn't save you the hassle but I'm glad that it was just a simple re-install to fix. 


~Caboose

---

### Post by itlarson2 on 2013-10-05
This turned out to be bad hardware.  The reinstall seemed to fix the problem for one day, but the next day I started getting bad recordings again. Replacing my dual tuner pcie Dvico card with the Hauppauge single tuner card I used before i got the Dvico has fixed the problem.  Apparently being baked by the video card for two years did the Dvico in.  Interestingly the Pchdtv-5500 tuner installed on the opposite side is still going strong, despite being twice as old.

---

