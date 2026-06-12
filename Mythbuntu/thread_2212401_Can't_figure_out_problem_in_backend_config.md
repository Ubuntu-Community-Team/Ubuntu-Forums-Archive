---
title: "Can't figure out problem in backend config"
date: 2014-03-21
forum: Mythbuntu
---

### Post by Johnathon_Galtman on 2014-03-21
I suspect I've missed something simple, but I can't figure it out :confused:. I'm using a [COLOR=#000000]WinTV-PVR-USB2[/COLOR] capture device (the composite input) with my MythTV .27 Mythbuntu system but when I select live tv I just get a quick flash of "Please Wait" and then back to the FE menu.

I am using the VDPAU video profile mode, but have tried others with the same results.

I can successfully use vlc to open the /dev/video0 capture device (pvr) and watch my composite video source no problem, so I presume the pvrusb2 driver and required firmware are OK.

The BE log shows an error in trying to tune a channel, but my starting channel is fine and I have left the channel changing script input field empty (could that be the issue? The help text for that field says "If specified...", so it doesn't seem to be required). I'm hoping to use my old Actisys IR200L IR blaster to tune my DTV converter box but that's another trial for another day. I shouldn't **need** it now to see video in mythTV.

I started off my installing the mythbuntu 12.04 / .25 ISO, but that didn't work either. However that trial at least played video, even tho it didn't sync very well and was basically unwatchable. I couldn't use vlc to view video as I can now. My second attempt using the same ISO file worked better in that I can at least see stable video with vlc.

My capture device is set to an mpeg 2 (pvr x50 | pvr 500) analog capture device. The BE setup correctly displays the WinTV PVR USB2 string in the probed field. Well, that's all of the pertinent info I can think of, aside from log output which appears below. If anyone has experience with this capture device under MythTV I'd sure appreciate some help. I managed to upgrade from .25 to .27 (not trivial but I got it done in one evening).

Here's some BE log data:
```

Mar 21 00:12:29 Asus-Quad-Core mythbackend: mythbackend[15527]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Mar 21 00:27:29 Asus-Quad-Core mythbackend: mythbackend[15527]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Mar 21 00:36:31 Asus-Quad-Core mythbackend: mythbackend[15527]: C CoreContext signalhandling.cpp:305 (handleSignal) Received Terminated: Code 0, PID 1, UID 0, Value 0x00000000
Mar 21 00:36:31 Asus-Quad-Core mythbackend: mythbackend[15527]: N CoreContext main_helpers.cpp:706 (run_backend) MythBackend exiting
Mar 21 00:36:31 Asus-Quad-Core mythbackend: mythbackend[15527]: I CoreContext bonjourregister.cpp:28 (~BonjourRegister) Bonjour: De-registering service '_mythbackend._tcp.' on 'Mythbackend on Asus-Quad-Core'
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-187-g30d86b1] www.mythtv.org
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I Logger logging.cpp:315 (run) Added logging to the console
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of Asus-Quad-Core
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to EN_US
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale EN_US
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: N CoreContext main_helpers.cpp:582 (run_backend) MythBackend: Starting up as the master server.
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext recorders/v4lchannel.cpp:558 (SetInputAndFormat) V4LChannel[1](/dev/video0): SetInputAndFormat(1, NTSC) (v4l v2) input_switch: 1 mode_switch: 0
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext recorders/v4lchannel.cpp:558 (SetInputAndFormat) V4LChannel[1](/dev/video0): SetInputAndFormat(1, NTSC) (v4l v2) input_switch: 0 mode_switch: 0
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: E CoreContext recorders/v4lchannel.cpp:375 (GetCurrentChannelNum) V4LChannel[1](/dev/video0): GetCurrentChannelNum(3.1): Failed to find Channel
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: E CoreContext recorders/v4lchannel.cpp:392 (Tune) Channel(/dev/video0)::Tune(3.1): Error, failed to find channel.
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext programinfo.cpp:2136 (CheckProgramIDAuthorities) Found 1 distinct programid authorities
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I Scheduler mythdbcon.cpp:436 (getStaticCon) New static DB connectionSchedCon
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'LogClean'.
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'DBCleanup'.
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'ThemeUpdateNotifications'.
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'RecordedArtworkUpdate'.
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'MythFillDB'.
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'JobQueueRecover'.
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask 'HardwareProfiler'.
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext housekeeper.cpp:648 (Start) Queueing HouseKeeperTask 'ThemeUpdateNotifications'.
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext housekeeper.cpp:655 (Start) Starting HouseKeeper.
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6544
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.10.2.20:6544
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6544
Mar 21 00:49:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::f66d:4ff:fe08:bd59%eth0]:6544
Mar 21 00:49:37 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext main_helpers.cpp:668 (run_backend) Main::Registering HttpStatus Extension
Mar 21 00:49:37 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6543
Mar 21 00:49:37 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP 10.10.2.20:6543
Mar 21 00:49:37 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6543
Mar 21 00:49:37 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext serverpool.cpp:399 (listen) Listening on TCP [fe80::f66d:4ff:fe08:bd59%eth0]:6543
Mar 21 00:49:37 Asus-Quad-Core mythbackend: mythbackend[19250]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Mar 21 00:49:38 Asus-Quad-Core mythbackend: mythbackend[19250]: I CoreContext bonjourregister.cpp:114 (BonjourCallback) Bonjour: Service registration complete: name 'Mythbackend on Asus-Quad-Core' type '_mythbackend._tcp.' domain: 'local.'
Mar 21 00:49:39 Asus-Quad-Core mythbackend: mythbackend[19250]: I Scheduler scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - SchedulerInit
Mar 21 00:49:39 Asus-Quad-Core mythbackend: mythbackend[19250]: I Scheduler scheduler.cpp:2211 (HandleReschedule) Scheduled 0 items in 0.0 = 0.01 match + 0.00 check + 0.01 place
Mar 21 00:49:39 Asus-Quad-Core mythbackend: mythbackend[19250]: I Scheduler scheduler.cpp:2278 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
Mar 21 00:50:36 Asus-Quad-Core mythbackend: mythbackend[19250]: I HouseKeeping housekeeper.cpp:133 (Run) Running HouseKeeperTask 'ThemeUpdateNotifications'.
Mar 21 00:50:37 Asus-Quad-Core mythbackend: mythbackend[19250]: I HouseKeeping housekeeper.cpp:151 (Run) HouseKeeperTask 'ThemeUpdateNotifications' Finished Successfully.
Mar 21 00:50:55 Asus-Quad-Core mythbackend: mythbackend[19250]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Mar 21 01:05:55 Asus-Quad-Core mythbackend: mythbackend[19250]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Mar 21 01:20:55 Asus-Quad-Core mythbackend: mythbackend[19250]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Mar 21 01:24:17 Asus-Quad-Core mythbackend: mythbackend[19250]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 21 01:24:17 Asus-Quad-Core mythbackend: mythbackend[19250]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: Asus-Quad-Core as a client (events: 0)
Mar 21 01:24:17 Asus-Quad-Core mythbackend: mythbackend[19250]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
Mar 21 01:24:17 Asus-Quad-Core mythbackend: mythbackend[19250]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: Asus-Quad-Core as a client (events: 1)
Mar 21 01:24:22 Asus-Quad-Core mythbackend: mythbackend[19250]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Playback
Mar 21 01:24:22 Asus-Quad-Core mythbackend: mythbackend[19250]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: Asus-Quad-Core as a client (events: 0)
Mar 21 01:24:22 Asus-Quad-Core mythbackend: mythbackend[19250]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange) TVRec[1]: Changing from None to WatchingLiveTV
Mar 21 01:24:22 Asus-Quad-Core mythbackend: mythbackend[19250]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[1]: HW Tuner: 1->1
Mar 21 01:24:22 Asus-Quad-Core mythbackend: mythbackend[19250]: I TVRecEvent recorders/v4lchannel.cpp:558 (SetInputAndFormat) V4LChannel[1](/dev/video0): SetInputAndFormat(1, NTSC) (v4l v2) input_switch: 0 mode_switch: 0
Mar 21 01:24:22 Asus-Quad-Core mythbackend: mythbackend[19250]: E TVRecEvent recorders/v4lchannel.cpp:375 (GetCurrentChannelNum) V4LChannel[1](/dev/video0): GetCurrentChannelNum(3.1): Failed to find Channel
Mar 21 01:24:22 Asus-Quad-Core mythbackend: mythbackend[19250]: E TVRecEvent recorders/v4lchannel.cpp:392 (Tune) Channel(/dev/video0)::Tune(3.1): Error, failed to find channel.
Mar 21 01:24:22 Asus-Quad-Core mythbackend: mythbackend[19250]: E TVRecEvent tv_rec.cpp:3792 (TuningFrequency) TVRec[1]: Failed to set channel to 3.1. Reverting to kState_None
Mar 21 01:24:22 Asus-Quad-Core mythbackend: mythbackend[19250]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange) TVRec[1]: Changing from WatchingLiveTV to None
Mar 21 01:24:23 Asus-Quad-Core mythbackend: mythbackend[19250]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Playback
Mar 21 01:24:23 Asus-Quad-Core mythbackend: mythbackend[19250]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding: Asus-Quad-Core as a client (events: 0)
Mar 21 01:24:23 Asus-Quad-Core mythbackend: mythbackend[19250]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange) TVRec[1]: Changing from None to WatchingLiveTV
Mar 21 01:24:23 Asus-Quad-Core mythbackend: mythbackend[19250]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[1]: HW Tuner: 1->1
Mar 21 01:24:23 Asus-Quad-Core mythbackend: mythbackend[19250]: I TVRecEvent recorders/v4lchannel.cpp:558 (SetInputAndFormat) V4LChannel[1](/dev/video0): SetInputAndFormat(1, NTSC) (v4l v2) input_switch: 0 mode_switch: 0
Mar 21 01:24:23 Asus-Quad-Core mythbackend: mythbackend[19250]: E TVRecEvent recorders/v4lchannel.cpp:375 (GetCurrentChannelNum) V4LChannel[1](/dev/video0): GetCurrentChannelNum(3.1): Failed to find Channel
Mar 21 01:24:23 Asus-Quad-Core mythbackend: mythbackend[19250]: E TVRecEvent recorders/v4lchannel.cpp:392 (Tune) Channel(/dev/video0)::Tune(3.1): Error, failed to find channel.
Mar 21 01:24:23 Asus-Quad-Core mythbackend: mythbackend[19250]: E TVRecEvent tv_rec.cpp:3792 (TuningFrequency) TVRec[1]: Failed to set channel to 3.1. Reverting to kState_None
Mar 21 01:24:23 Asus-Quad-Core mythbackend: mythbackend[19250]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange) TVRec[1]: Changing from WatchingLiveTV to None
Mar 21 01:35:55 Asus-Quad-Core mythbackend: mythbackend[19250]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Mar 21 01:50:55 Asus-Quad-Core mythbackend: mythbackend[19250]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Mar 21 02:05:55 Asus-Quad-Core mythbackend: mythbackend[19250]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

```

---

### Post by blm-ubunet on 2014-03-21
Have you read through this ?
[http://www.mythtv.org/wiki/Hauppauge_PVR-500](http://www.mythtv.org/wiki/Hauppauge_PVR-500)
(IVTV mpeg2video PS files)
I believe you can create a dummy channel change script or just use:
```
/bin/true
```

Could be some clues (channel changing) in:
[http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR)
Altho this is a H264 encoder that outputs mpegts stream over LAN.

---

### Post by Johnathon_Galtman on 2014-03-22
Just can't get enough of my beans hey blm-ubunet):P I read in a post online (for an old version of mythtv) that running the  BE setup program as root solved the poster's problem. Although I didn't  think that was likely going to do anything in my case I gave it a try.  The result of doing that is I can now select watch tv and see video.  However, it is just as it was in my previous installation, serious  tearing or loss of sync periodically and too much so to be unusable.

So I quit the FE and tried vlc, hoping it would still be OK. Whatever  running the BE setup as root did screwed up the pvrusb2 driver or  firmware or something else used by vlc b/c it also has the same tearing  problem that mythtv does. Bummer, back to square 1. Well, maybe square 2  since now I'm running .27.

Haven't looked at the logs yet to see if anything has changed in them I can spot but I will. 

I hope I don't have to start from scratch again. It would be a real time  consuming pain in the ass, to redo all the updates and the upgrade to  .27.

It's quite discouraging to have to deal with these issues. Is the  current version 0.27 or is it 2.27? I thought I read somewhere the  version is actually 2.27 despite everyone always referring to it as .27.  However, as slick and refined as mythtv looks, if the problems I'm  experiencing are indicative of the lack of robustness of the code (and I  suspect they are), then I can see why the version is only 0.27. 

I will look into the firmware and driver being altered somehow. Whatever  the problem is has changed something in common with vlc & mythtv. I  don't suspect the channel changing has anything to do with why I just  saw the brief flash of please wait now, since I still don't have  anything in the setup field to change the channel. 

I may need to read up on the firmware extraction and why it is ever  necessary to do that. If the date on the FW files is not recent then  they weren't corrupted, same with the pvrusb2 driver.

Also, I can see in the logs above references to v4l, although I have  chosen VDPAU not v4l in the setup. Not clear on why that is.

---

### Post by blm-ubunet on 2014-03-22
Don't assume or presume anything...

In a terminal:
```
dmesg | egrep -i '(ivtv|tveeprom|tuner)'
```

Grubby hacks like running stuff as sudo to "make it work" are often symptoms of users & groups permissions problems.
MythTV BE runs as user "mythtv" regardless of any user the FE could be running as...
Stock mythbuntu runs FE as user "mythtv"

From fading memory... 
The user "mythtv" (backend) user needs to be a member of audio & video (& mythtv) groups.
Are your FE user & "mythtv" user members of the mythtv group?
Or am I remembering this wrong..

---

### Post by Johnathon_Galtman on 2014-03-22
I suspended the system last night when I was done and I just now resumed it to check the firmware files, and they look OK with a date in 2011.

I tried vlc again and I got the green 4:3 screen, then did the "echo "composite" > /sys/class/pvrusb2/sn-8632731/ctl_input/cur_val" to select the composite input. Much to my surprise VLC displays the video clear as a bell without tearing or any other problems. So not only are the firmware files OK so is the pvrusb2 driver.

I started the mythTV FE and the video tearing problem is still present. Switched between auto, qt and openGL paint engines and all exhibited the problem.

Exiting the myth FE I then tried VLC and now it has the tearing also. Something the the myth initialization is changing the (driver?) configuration. I'm going to try suspending / resuming and see if it revers to no tearing upon resume. I haven't touched the backend.

----- UPDATE -----

After the system comes out of suspension VLC once again displays the video perfectly, despite the suspension lasting only around 5 seconds. I had to reissue the sysfs "composite" echo as the input mode reverted to the tv tuner.

I may try to switch the video from composite to tv and back again while the mythTV FE is running and see what that does.

----- UPDATE 2 -----

Switching input modes doesn't resolve the problem in vlc or mthtv. I have tried suspending the OS several times and that takes care of it. Not sure how to pin this problem down or what to try next.

---

### Post by blm-ubunet on 2014-03-22
What desktop are you running on mythbuntu ?
The stock Xfce ? or have you logged into a session using unity or gnome3 or something?

What happens if you try to run
```
ccsm
```
If this runs then tick "legacy full screen" & "un-redirect full screen"

---

### Post by Johnathon_Galtman on 2014-03-22
Here's the dmesg output you suggested blu-ubunet:
```

[   15.964171] pvrusb2: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
[   16.121394] tuner 0-0061: Tuner -1 found with type(s) Radio TV.
[   16.121408] pvrusb2: Attached sub-driver tuner
[   16.576173] tuner 0-0043: Tuner 74 found with type(s) Radio TV.
[   16.576192] pvrusb2: Attached sub-driver tuner
[   17.546170] tveeprom 0-00a2: Hauppauge model 24012, rev D3A3, serial# 8632731
[   17.546176] tveeprom 0-00a2: tuner model is TCL MFNM05-4 (idx 103, type 43)
[   17.546178] tveeprom 0-00a2: TV standards NTSC(M) (eeprom 0x08)
[   17.546181] tveeprom 0-00a2: audio processor is CX25843 (idx 37)
[   17.546182] tveeprom 0-00a2: decoder processor is CX25843 (idx 30)
[   17.546184] tveeprom 0-00a2: has radio, has IR receiver, has no IR transmitter
[   17.908088] tuner-simple 0-0061: creating new instance
[   17.908093] tuner-simple 0-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[  575.555134] tuner-simple 0-0061: destroying instance
[  579.798289] tuner 0-0061: Tuner -1 found with type(s) Radio TV.
[  579.798303] pvrusb2: Attached sub-driver tuner
[  579.808314] tuner 0-0043: Tuner 74 found with type(s) Radio TV.
[  579.808326] pvrusb2: Attached sub-driver tuner
[  580.732245] tveeprom 0-00a2: Hauppauge model 24012, rev D3A3, serial# 8632731
[  580.732250] tveeprom 0-00a2: tuner model is TCL MFNM05-4 (idx 103, type 43)
[  580.732255] tveeprom 0-00a2: TV standards NTSC(M) (eeprom 0x08)
[  580.732258] tveeprom 0-00a2: audio processor is CX25843 (idx 37)
[  580.732262] tveeprom 0-00a2: decoder processor is CX25843 (idx 30)
[  580.732265] tveeprom 0-00a2: has radio, has IR receiver, has no IR transmitter
[  581.016113] tuner-simple 0-0061: creating new instance
[  581.016120] tuner-simple 0-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[ 2741.633874] tuner-simple 0-0061: destroying instance
[ 2770.511370] tuner 0-0061: Tuner -1 found with type(s) Radio TV.
[ 2770.511384] pvrusb2: Attached sub-driver tuner
[ 2770.522255] tuner 0-0043: Tuner 74 found with type(s) Radio TV.
[ 2770.522276] pvrusb2: Attached sub-driver tuner
[ 2771.443943] tveeprom 0-00a2: Hauppauge model 24012, rev D3A3, serial# 8632731
[ 2771.443948] tveeprom 0-00a2: tuner model is TCL MFNM05-4 (idx 103, type 43)
[ 2771.443953] tveeprom 0-00a2: TV standards NTSC(M) (eeprom 0x08)
[ 2771.443956] tveeprom 0-00a2: audio processor is CX25843 (idx 37)
[ 2771.443960] tveeprom 0-00a2: decoder processor is CX25843 (idx 30)
[ 2771.443963] tveeprom 0-00a2: has radio, has IR receiver, has no IR transmitter
[ 2771.730432] tuner-simple 0-0061: creating new instance
[ 2771.730440] tuner-simple 0-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[ 4137.761485] tuner-simple 0-0061: destroying instance
[ 4145.065773] tuner 0-0061: Tuner -1 found with type(s) Radio TV.
[ 4145.065793] pvrusb2: Attached sub-driver tuner
[ 4145.076884] tuner 0-0043: Tuner 74 found with type(s) Radio TV.
[ 4145.076904] pvrusb2: Attached sub-driver tuner
[ 4145.996320] tveeprom 0-00a2: Hauppauge model 24012, rev D3A3, serial# 8632731
[ 4145.996326] tveeprom 0-00a2: tuner model is TCL MFNM05-4 (idx 103, type 43)
[ 4145.996330] tveeprom 0-00a2: TV standards NTSC(M) (eeprom 0x08)
[ 4145.996334] tveeprom 0-00a2: audio processor is CX25843 (idx 37)
[ 4145.996337] tveeprom 0-00a2: decoder processor is CX25843 (idx 30)
[ 4145.996341] tveeprom 0-00a2: has radio, has IR receiver, has no IR transmitter
[ 4146.281726] tuner-simple 0-0061: creating new instance
[ 4146.281736] tuner-simple 0-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))

```

I'm running the xfce WM.
The program 'ccsm' is currently not installed.

---

### Post by Johnathon_Galtman on 2014-03-22
> **blm-ubunet said:**
> Don't assume or presume anything....
Excellent policy, I definitely try not to but...

> **blm-ubunet said:**
> Grubby hacks like running stuff as sudo to "make it work" are often symptoms of users & groups permissions problems.
MythTV BE runs as user "mythtv" regardless of any user the FE could be running as...
Stock mythbuntu runs FE as user "mythtv"

From fading memory... 
The user "mythtv" (backend) user needs to be a member of audio & video (& mythtv) groups.
Are your FE user & "mythtv" user members of the mythtv group?
Or am I remembering this wrong..

I agree, but isn't the point of using an ISO like mythbuntu supposed to be that configuration issues like that are already cooked into the soup?

My erroneous **assumption** was that running the BE setup as root caused a change in configuration that resulted the the tearing problem, but as you can see from my posts tonight that isn't the case. It's looking more like some sort of initialization problem similar to the lack of sound on first channel change you posted the link for earlier.

---

### Post by blm-ubunet on 2014-03-22
Yes, a distribution like mythbuntu should have all issues sorted..but people do like to expt..

Like you said your video tearing sounds more like a capture/encoder configuration problem.
Video tearing caused by composite effect managers/video drivers tend to be evident on the whole desktop experience (everywhere).

Tuner/encoder support comes form LinuxTV.org & associated projects IVTV. MythTV just uses the published APIs.
I think most of the mythtv devs have moved on to DVB & ATSC & HD-PVR & cablecard solns.

---

### Post by Johnathon_Galtman on 2014-03-23
I'm going to try recompiling the kernel with the debug interface for the pvrusb2 driver turned on. When I looked for the kernel source for the binaries of the mythbuntu .27 release (3.8.0.29 according to uname -r) the closest I could find was 3.8.0.37 so I'm trying to use that but am having trouble.

Getting all the prerequisite packages required to build the kernel is a pain. I tried using [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel) but it's not sufficient; I had to get ncurses-dev[el] for example. And when I run 
[COLOR=#333333]```
fakeroot debian/rules binary-headers binary-generic
```
[/COLOR][COLOR=#333333]
it fails saying I need to run mrproper. But if I do it wipes the debian folder!
[/COLOR]```

**...**
#
# configuration written to .config
#
  SYSHDR  arch/x86/syscalls/../include/generated/uapi/asm/unistd_32.h
  SYSHDR  arch/x86/syscalls/../include/generated/uapi/asm/unistd_64.h
  SYSHDR  arch/x86/syscalls/../include/generated/uapi/asm/unistd_x32.h
  SYSTBL  arch/x86/syscalls/../include/generated/asm/syscalls_32.h
  SYSHDR  arch/x86/syscalls/../include/generated/asm/unistd_32_ia32.h
  SYSHDR  arch/x86/syscalls/../include/generated/asm/unistd_64_x32.h
  SYSTBL  arch/x86/syscalls/../include/generated/asm/syscalls_64.h
  HOSTCC  arch/x86/tools/relocs
  Using /usr/linux-lts-raring-3.8.0 as source for kernel
  /usr/linux-lts-raring-3.8.0 is not clean, please run 'make mrproper'
  in the '/usr/linux-lts-raring-3.8.0' directory.
make[4]: *** [prepare3] Error 1
make[3]: *** [sub-make] Error 2
make[2]: *** [prepare] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/usr/linux-lts-raring-3.8.0'
make: *** [/usr/linux-lts-raring-3.8.0/debian/stamps/stamp-prepare-tree-generic] Error 2

```[COLOR=#333333]
[/COLOR]> [COLOR=#000000]I think most of the mythtv devs have moved on to DVB & ATSC & HD-PVR & cablecard solns.[/COLOR][COLOR=#333333]
That's very likely, so if I'm going to get this working it's up to me to figure it out, hopefully with help I find here like yours. [/COLOR]

---

### Post by blm-ubunet on 2014-03-23
I draw a line at building complete kernels..

You can (easily) build just v4l-dvb modules.
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

No sure if you can enable debug on just some kernel modules.

Have you looked into the "pvr-usb2" module options (modinfo pvrusb2)?
Specifically "debug".

The module source code will reveal exactly what the mask values are/do.

---

### Post by Johnathon_Galtman on 2014-03-23
I got the kernel rebuilt with the debug option turned on for Isely's pvrusb2 driver and have been playing around with it.

I've generated a lot of files, comparing VLC & mythTV under various operational scenarios.

Bottom line is I can get the video to stop it's jumping / jittering in mythTV live TV mode by issuing a "decoder reset" command while the stream is active, but doing so causes the video to be cropped on the right. That also happens in VLC. Whatever MythTV does upon starting "Watch TV" re initializes the Hauppauge and the jumping / jitter problem returns.

The other reset commands don't seem to help, and can screw up communications badly so as to require a reboot, Here is the list of resets provided: " [COLOR=#000000][FONT=monospace]reset cpu, [/FONT][/COLOR][COLOR=#000000][FONT=monospace]reset bus, [/FONT][/COLOR][COLOR=#000000][FONT=monospace]reset soft, [/FONT][/COLOR][COLOR=#000000][FONT=monospace]reset deep, [/FONT][/COLOR][COLOR=#000000][FONT=monospace]reset firmware, [/FONT][/COLOR][COLOR=#000000][FONT=monospace]reset decoder, [/FONT][/COLOR][COLOR=#000000][FONT=monospace]reset worker".

Here is the driver debug output after the jitter was "fixed" by the "decoder reset" command:

[/FONT][/COLOR]```
cat debuginfo 
Driver hardware description: WinTV PVR USB2 Model 24xxx
Driver state info:
driver: <ok> <init> <connected> <mode=analog>
pipeline: <idle> <configok>
worker: <decode:quiescent> <encode:virgin> <encode:waitok> <usb:stop> <pathway:ok>
state: ready
Hardware supported inputs: television, composite, s-video, radio
Bytes streamed=0 URBs: queued=0 idle=0 ready=0 processed=0 failed=0
ir scheme: id=1 24xxx (29xxx emulation)
Associated v4l2-subdev drivers and I2C clients:
  cx25840: cx25840 @ 44
  tuner: tuner @ 61
  wm8775: wm8775 @ 1b
  tuner: tuner @ 43

```[COLOR=#000000][FONT=monospace]

And here it is after a fresh reboot after exiting the mythTV FE (and never using the FE, just esc to exit):

[/FONT][/COLOR]```
Driver hardware description: WinTV PVR USB2 Model 24xxxDriver state info:
driver: <ok> <init> <connected> <mode=analog>
pipeline: <idle> <configok>
worker: <decode:quiescent> <encode:virgin> <encode:waitok> <usb:stop> <pathway:ok>
state: ready
Hardware supported inputs: television, composite, s-video, radio
Bytes streamed=0 URBs: queued=0 idle=0 ready=0 processed=0 failed=0
ir scheme: id=1 24xxx (29xxx emulation)
Associated v4l2-subdev drivers and I2C clients:
  cx25840: cx25840 @ 44
  tuner: tuner @ 61
  wm8775: wm8775 @ 1b
  tuner: tuner @ 43

```[COLOR=#000000][FONT=monospace]

And this one while mythTV is in live TV mode and the video is problematic: 
[/FONT][/COLOR]
```

Driver hardware description: WinTV PVR USB2 Model 24xxx
Driver state info:
driver: <ok> <init> <connected> <mode=analog>
pipeline: <idle> <configok>
worker: <decode:quiescent> <encode:stop> <encode:waitok> <usb:stop> <pathway:ok>
state: ready
Hardware supported inputs: television, composite, s-video, radio
Bytes streamed=279772160 URBs: queued=0 idle=0 ready=0 processed=17105 failed=0
ir scheme: id=1 24xxx (29xxx emulation)
Associated v4l2-subdev drivers and I2C clients:
  cx25840: cx25840 @ 44
  tuner: tuner @ 61
  wm8775: wm8775 @ 1b
  tuner: tuner @ 43

```[COLOR=#000000][FONT=monospace]

As you can see there isn't much difference.

Here is a link to a very short video I captured exhibiting the problem: [http://www.ozarkcoclassifieds.com/tearing2.mpeg](http://www.ozarkcoclassifieds.com/tearing2.mpeg).

It also shows the cropping that occurs after doing a "decoder reset". The reason it shows the tearing problem after doing a decoder reset is I started the live tv in mythTV afterwards.



[/FONT][/COLOR]

---

### Post by blm-ubunet on 2014-03-24
That video is not tearing exactly..
That problem looks to be video capture not finding or locking horizontal or vertical sync.

Possibly your STB is producing reduced vertical blanking interval video timing.
Or some video timing that is more targeted at modern TVs (not slow CRT).

This changes with myth LiveTV:
<encode:virgin>  ---> <encode:stop>

Can you use S-Video connection?

---

### Post by Johnathon_Galtman on 2014-03-24
There's no sVideo out on STB. Even if there were it wouldn't fit into how I would like everything connected. I haven't seen a receiver yet that handles analog video and sVideo on the same bus; might as well be talking about how analog audio and digital audio are handled, same functional difference. Occasionally I watch VHS, or want to digitize something from an old camcoder, and they're all analog of course.
 
I'm not actually certain of your logic about the sync being weak, since VLC works perfect when it initializes the WinTV first. I could always connect a different video source to the WinTV instead of the STB to check that. I do understand why you mention sVideo, as that is superior to an analog connection with it's separate sync. As for the diff between tearing and loss of sync, I thought they're the same thing. Tearing is loss of h sync, rolling is loss of v sync. It may not be either one technically, if there's an issue with the digital transfer.

I do concur that the video looks like a loss of sync, but I don't presume it's a weak analog signal since VLC is just fine with it. The STB is a Dish DTV converter box, the most sensitive one I could get back in '09. Also, the decoder reset eliminates the problem no matter what the history of use is. I would consider employing that as a hack-fix if it didn't also crop the video.

And that makes me wonder if there's anything in the WinTV init that sets an odd resolution or timing value.

---

### Post by blm-ubunet on 2014-03-25
The video tearing you read about here (now) is almost always frame rendering timing related issues. All related to GPU driver composite effects & incorrect video mode reporting etc..nothing to do with analogue video capture.

I did not say the sync was weak just that the capture PLL or similar does not find lock on that input signal.
Could be input signal or presets like TV standard or timing settings/ voltage thresholds etc.

S-Video was just another idea to debug the sync-tearing & get superior signals (especially sync). 

What's with the analogy with digital & analogue audio; there is none.
It is easy to convert s-video to composite & simple sync separator circuits  for converting composite to s-video (with no improvement to PQ).
I am surprised you can't find an old HT amp/receiver that can convert between them..

IMO it was fairly conclusive from previous posts that mythtv induced the problem & a driver initialization parameter is most likely the difference between working & not..

I would think it highly unlikely that corruption of digital transfer (over USB) would then correctly & consistently resync part way down the video frame.

---

### Post by Johnathon_Galtman on 2014-03-25
> [COLOR=#000000]That problem looks to be video capture not finding or locking horizontal or vertical sync.[/COLOR]

That can be comprehended in two ways:
1) [COLOR=#000000]That problem looks to be: (video capture not finding or locking horizontal or vertical sync).
2) [/COLOR][COLOR=#000000]That problem looks to be video capture, (as opposed to) not finding or locking horizontal or vertical sync.

I ran with the first interpretation, apparently just the opposite of what you intended.

> [/COLOR][COLOR=#000000]The video tearing you read about [/COLOR][COLOR=#000000]... nothing to do with analogue video capture.[/COLOR][COLOR=#000000]
> [/COLOR][COLOR=#000000]IMO it was fairly conclusive from previous posts ... _driver initialization parameter_ is most likely the difference between working & not..[/COLOR]
[COLOR=#000000]

I'm confused by these statements, they seem to be contradictory in that analog video capture is dictated by initialization parameters.

> [/COLOR][COLOR=#000000]What's with the analogy with digital & analogue audio; there is none.[/COLOR][COLOR=#000000][/COLOR]

[COLOR=#000000]Oh there is, you just didn't get it.[/COLOR]

[COLOR=#000000]I have a 2001 vintage Sony STR-DE935 Digital Audio / Video Control Center, Digital cinema sound processing 32 bit as labeled on it's face.[/COLOR]
[COLOR=#000000]It is not unique in the way it handles analog video and s-video, they are treated as completely separate [/COLOR]***types***[COLOR=#000000] of signals. I have seen this in many other components by many other manufacturers as well. [/COLOR]

[COLOR=#000000]If I use the s-video output ofthe Sony to drive my monitor it will only display video sources that come in through an s-video jack. Not every source has both s-video and analog inputs. I believe the DVD has both. I distinctly remember arguments with several friends that didn't believe this. Showing them the manual was not enough (it was indeed worded rather ambiguously), but when they saw it with their own eyes in my living room they changed their tune. [/COLOR]

[COLOR=#000000]I also tried to find a DVD / VHS combo component that would provide both DVD and VHS outputs through the s-video connector and could find NONE.[/COLOR]

[COLOR=#000000]I don't disagree with you about how easy it is to create a composite signal from an s-video connection, though you will loose the benefit of the isolation of sync & video, obviously. Doing the conversion the other way around is not as trivial however, and I believe that is what would be required for VHS.[/COLOR]

[COLOR=#000000]Don't ask me why Sony & all the other manuf. I have come across (I have no experience with the ultra high end, Nakimichi, Harmon Kardon, or professional / studio gear) don't convert s-video and analog into a common internal bus and switch that but they don't. That's my experience. If your's is different that's kewl. I'd be curious to know what components you've encountered treat analog and s-video inputs the same (different than my Sony STR-DE935). [/COLOR]

[COLOR=#000000]The analogy holds, in that both digital and analog audio are both audio. A component could convert all analog audio inputs to digital and then treat all audio sources internally the same, and even have a D/A converter to produce analog audio out. But that isn't how any consumer gear I've seen is designed.[/COLOR]

[COLOR=#000000]I do agree that the difference between composite & s-video is far less significant than the difference between digital and analog audio. But I never said it was a perfect analogy.[/COLOR]
[COLOR=#000000]---[/COLOR]
[COLOR=#000000]Back to the WinTV issue. I'm not sure we're on the same page concerning what the problem is. You seem to say tearing and sync are not the same thing, and, that the issue is GPU output related not source input related. Is that right?[/COLOR]
 
[COLOR=#000000]I admit I have a rather limited understanding of how mythTV processes input sources and renders them to the output, and how the resolution and frame refresh rates of input and output relate to each other. That is what I understand a "compositor" does, it digitally combines the mythTV UI elements with the input source elements and the result of that is rendered by the GPU.[/COLOR]

[COLOR=#000000]I am not clear what "compositor" is involved in my mythTV configuration. The "paint engine" as it is labeled in the FE is set to auto, and the other choices for that are opendGL and Qt. I am not running Unity so no compiz.
[/COLOR]
The more I watch the live TV mode in myth the more I'm confused, b/c it mostly is locked with no tearing or problems now. If I changed the input source to something else and it NEVER exhibited the problem I would conclude it's a sync or signal issue. I'm noticing when there's text in the video tearing occurs and when it's just a natural scene and no sharp edges it's almost perfect with a rare flicker or line cutting across the picture. I can trigger the problem just by hitting "menu" on the STB for example, and it takes a while for it to return to stability after I dismiss it.

Although as you said there is an obvious difference between VLC and mythTV initialization, it may be possible to compensate for it with a different / buffered / stronger analog signal. 

[COLOR=#000000]Also, I might try using the F-connector input and see if that changes the problem. [/COLOR]

---

### Post by Johnathon_Galtman on 2014-03-25
I just found what _**might**_ be the culprit.

Under the BE setup, Recording Profiles --> MPEG2 Encoder (PVR-x50 etc) --> default | live TV | Composite | S-Video are width and height settings.

I discovered that for all of the these sources the width AND height were both set to 480. Now if that was the cause of the problem why would the picture EVER be good?

Unfortunately I'm now getting an error in the FE when I start live TV that says: "Error starting jump program file buffer", and I have to use kill -9 to kill the FE as it locks up.

Don't know what was up with that, a reboot resolved the error. 

Not surprisingly the erroneous width values under Recording Profiles had no affect on the problem, and neither did using the F-connector tuned to channel 3.

---

