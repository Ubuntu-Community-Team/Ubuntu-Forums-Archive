---
title: "Need help with livetv and recording. Can't find channel."
date: 2013-04-27
forum: Mythbuntu
---

### Post by whitecruiser on 2013-04-27
I was a mythbuntu user for a couple of years and now I would like to get it working again.  I have an old P4 machine with a pvr-500 card.  Previously I had analog cable and the system took some time understand and get setup correctly but once it as working it was maintenance free.  I started by reinstalling a fresh mythbuntu and now I can't get it to record or watch livetv. This is the second time in the last two months I have reinstalled it,  I was able to get it to record last time.  The problem was getting the MCE remote to change channels on the STB.  I thought it was a setup issue so I started with the fresh install.  

Now with the second install I can't watch livetv or record.  When I start livetv it just jumps back to the menu.  I have checked both the backend and frontend log and can't find a reason it is not working.  It is not able to get the channel.  I am super frustrated and almost ready to get the DVR from the cable company. 

Installed: 2:0.25.2+fixes.20120802.46cab93-0ubuntu1
  Candidate: 2:0.25.3+fixes.20130423.94d67fc-0ubuntu0mythbuntu2
  Version table:
     2:0.25.3+fixes.20130423.94d67fc-0ubuntu0mythbuntu2 0
        500 [http://ppa.launchpad.net/mythbuntu/0.25/ubuntu/](http://ppa.launchpad.net/mythbuntu/0.25/ubuntu/) precise/main i386 Packages
 *** 2:0.25.2+fixes.20120802.46cab93-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse i386 Packages
        100 /var/lib/dpkg/status
     2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse i386 Packages

LOG FROM back end


Apr 27 19:20:32 mythtv-desktop mythbackend[9464]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor Apr 27 19:20:32 mythtv-desktop mythbackend[9464]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythtv-desktop as a client (events: 0) Apr 27 19:20:32 mythtv-desktop mythbackend[9464]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor Apr 27 19:20:32 mythtv-desktop mythbackend[9464]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythtv-desktop as a client (events: 1) Apr 27 19:21:07 mythtv-desktop mythbackend[9464]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback Apr 27 19:21:07 mythtv-desktop mythbackend[9464]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythtv-desktop as a client (events: 0) Apr 27 19:21:07 mythtv-desktop mythbackend[9464]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(1): Changing from None to WatchingLiveTV Apr 27 19:21:07 mythtv-desktop mythbackend[9464]: I TVRecEvent tv_rec.cpp:3495 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1 Apr 27 19:21:07 mythtv-desktop mythbackend[9464]: I TVRecEvent v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(1, NTSC) (v4l v2) input_switch: 0 mode_switch: 0 Apr 27 19:21:07 mythtv-desktop mythbackend[9464]: E TVRecEvent v4lchannel.cpp:450 (GetCurrentChannelNum) V4LChannel(/dev/video0): GetCurrentChannelNum(): Failed to find Channel Apr 27 19:21:07 mythtv-desktop mythbackend[9464]: E TVRecEvent v4lchannel.cpp:467 (Tune) Channel(/dev/video0)::Tune(): Error, failed to find channel. Apr 27 19:21:07 mythtv-desktop mythbackend[9464]: E TVRecEvent tv_rec.cpp:3681 (TuningFrequency) TVRec(1): Failed to set channel to 4. Reverting to kState_None Apr 27 19:21:07 mythtv-desktop mythbackend[9464]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(1): Changing from WatchingLiveTV to None Apr 27 19:24:44 mythtv-desktop mythbackend[9464]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread Apr 27 19:29:49 mythtv-desktop mythbackend[9464]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread Apr 27 19:30:41 mythtv-desktop mythbackend[9464]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min Apr 27 19:34:56 mythtv-desktop mythbackend[9464]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread Apr 27 19:39:59 mythtv-desktop mythbackend[9464]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread Apr 27 19:45:05 mythtv-desktop mythbackend[9464]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread Apr 27 19:46:41 mythtv-desktop mythbackend[9464]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min Apr 27 19:50:12 mythtv-desktop mythbackend[9464]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread Apr 27 19:55:13 mythtv-desktop mythbackend[9464]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread Apr 27 20:00:13 mythtv-desktop mythbackend[9464]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread Apr 27 20:01:41 mythtv-desktop mythbackend[9464]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min Apr 27 20:05:19 mythtv-desktop mythbackend[9464]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread Apr 27 20:10:23 mythtv-desktop mythbackend[9464]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread Apr 27 20:15:25 mythtv-desktop mythbackend[9464]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread Apr 27 20:16:41 mythtv-desktop mythbackend[9464]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
LOG FROM FRONT END


Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow. Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1) Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72 Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: E CoreContext livetvchain.cpp:270 (GetEntryAt) GetEntryAt(-1) failed. Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: E CoreContext livetvchain.cpp:277 (GetEntryAt) It appears that your backend may be misconfigured.  Check your backend logs to determine whether your capture cards, lineups, channels, or storage configuration are reporting errors.  This issue is commonly caused by failing to complete all setup steps properly.  You may wish to review the documentation for mythtv-setup. Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: E CoreContext livetvchain.cpp:294 (EntryToProgram) EntryToProgram(0@Wed Dec 31 16:00:00 1969) failed to get pginfo Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: E CoreContext tv_play.cpp:2200 (HandleStateChange) TV: HandleStateChange(): LiveTV not successfully started Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: E CoreContext tv_play.cpp:2233 (HandleStateChange) TV: LiveTV not successfully started Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled. Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop. Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop. Apr 27 19:21:07 mythtv-desktop mythfrontend[9830]: N CoreContext mythmainwindow.cpp:2591 (PauseIdleTimer) Resuming idle timer Apr 27 19:21:12  mythfrontend[9830]: last message repeated 2 times Apr 27 19:21:12 mythtv-desktop mythfrontend[9830]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on mythtv-desktop' Apr 27 19:21:12 mythtv-desktop mythfrontend[9830]: I CoreContext mythraopdevice.cpp:82 (Cleanup) RAOP Device: Cleaning up. Apr 27 19:21:12 mythtv-desktop mythfrontend[9830]: I CoreContext mythairplayserver.cpp:260 (Cleanup) AirPay: Cleaning up. Apr 27 19:21:12 mythtv-desktop mythfrontend[9830]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client... Apr 27 19:21:14 mythtv-desktop mythfrontend[9830]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.any help would be great

---

### Post by whitecruiser on 2013-04-29
Hello all,

I am not sure why there aren't any replies to this thread.  Not sure if I didn't ask a question correctly?  
Here is the problem I am having restated.  

When i start livetv it jumps back to the menu.  The frontend in the log states the backend might be configured incorrectly. 
The backend can't get the channel I am setting.  
I have a PVR-500 card and a cable set top box (STB).  The STB is set to up channel four instead of three for what ever reason.  
I was told I have to make sure that mythtv knows to use channel four.  I will have to use a IR blaster to change channel but I am not even at that point yet.  
Because of that I have to add the channels one at a time.  I add two channels to start, channel 4 and another one. 
I understand that it needs to be configured to get channel four to get the analog signal from the STB but after that I am not sure what it wants.  
I don't know if it needs seperate channel lineups, one for the channel 4 and another for all the other channels.  

THings i know
Tuner gets a signal from the STB.  mplayer /dev/video0 works.
previously recorded shows play.

Suggestions?

---

### Post by PhilWig on 2013-04-29
I don't have your setup so cannot really help much, but others might see similarities with their setup if you give more information.  eg:

Which cable provider?
How do you connect your mythtv box to the cable box?
Do you get reliable direct tv reception? 
How did you set it up - did you find some guide somewhere?
Can you post a backend log of a time for a short recording (say 1 minute manual one)?
Can you post it so end of line characters are not lost and its more readable?

Phil

---

### Post by whitecruiser on 2013-04-29
Phil,
Thanks for the response. 
xfinity is the cable provider.  
coax in the connection to the cable box and the cable tv reception is good through the set top box.  
I also stated that mplayer work which it did yesteday but today it won't start.
I have setup it up several times and don't really use a guide.  They seem to give limited details sometimes.
I can't get it to record, I tried but it said it failed.  

I don't know what I did to remove the end of line characters.  I posted the full logs below.  

[http://pastebin.com/HdARrmDY](http://pastebin.com/HdARrmDY)  frontend log
[http://pastebin.com/uxRB1etH](http://pastebin.com/uxRB1etH)   setup log
[http://pastebin.com/TrH3VYvD](http://pastebin.com/TrH3VYvD)  backend log

Thanks for you help

---

### Post by PhilWig on 2013-05-13
See your backend log entry:
> Apr 24 15:10:14 mythtv-desktop mythbackend[3426]: E CoreContext mythdbcon.cpp:214 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on '127.0.0.1' (111)

Frontend log has similar entries.  This might be because the database server is not running, or because you are not connecting to it properly.  

klc5555 has discussed this in this thread:
[http://ubuntuforums.org/showthread.php?t=2106554](http://ubuntuforums.org/showthread.php?t=2106554)

Don’t be alarmed if your mysql log is unhelpful – mine is empty.

Phil

---

