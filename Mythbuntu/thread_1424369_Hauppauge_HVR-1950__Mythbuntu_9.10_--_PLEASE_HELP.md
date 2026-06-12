---
title: "Hauppauge HVR-1950  Mythbuntu 9.10 -- PLEASE HELP"
date: 2010-03-07
forum: Mythbuntu
---

### Post by greenwom on 2010-03-07
Installed Mythbuntu 9.10

HVR was recognized but did not initialize.  Went through the setup best I could.  

I went to the this link to extract firmware: [http://www.isely.net/pipermail/pvrusb2/2008-October/001918.html](http://www.isely.net/pipermail/pvrusb2/2008-October/001918.html) :  

and this

[http://ubuntuforums.org/archive/index.php/t-994566.html](http://ubuntuforums.org/archive/index.php/t-994566.html)


I am stuck.  The card is recognized in myth but I can't scan for channels or watch tv.  (the red led never comes on.)

The remote does not work

I hate large data dumps but I will past my paste bin here (sorry for the bloat but I am stuck...)  I PROMISE I WILL TURN WHATEVER GETS THIS TO WORK INTO A STRONG HOW-TO for the forums.

```
==> /var/log/mythtv/jamu.log <==

! Warning - Creating an instance caused and error for one of: MythTV, MythVideo or MythDB


==> /var/log/mythtv/mtd.log <==
mtd started at Sun Mar 7 19:47:48 2010
mtd is running on a host called tvdesktop
19:47:48: Waiting for connections/jobs
19:47:48: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2010-03-07 19:47:48.037 MythBackend: Starting up as the master server.
2010-03-07 19:47:49.365 New DB connection, total: 2
2010-03-07 19:47:49.903 Connected to database 'mythconverg' at host: localhost
2010-03-07 19:47:50.697 New DB connection, total: 3
2010-03-07 19:47:51.776 Connected to database 'mythconverg' at host: localhost
2010-03-07 19:47:52.388 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2010-03-07 19:47:52.709 DVBChan(6:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(Please add): Unable to find channel in database.
2010-03-07 19:47:52.989 ChannelBase(6) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2010-03-07 19:47:53.515 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2010-03-07 19:47:53.703 DVBChan(7:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(Please add): Unable to find channel in database.
2010-03-07 19:47:53.861 ChannelBase(7) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2010-03-07 19:47:54.680 New DB scheduler connection
2010-03-07 19:47:54.983 Connected to database 'mythconverg' at host: localhost
2010-03-07 19:47:55.722 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-03-07 19:47:55.969 Main::Registering HttpStatus Extension
2010-03-07 19:47:56.233 Enabled verbose msgs:  important general
2010-03-07 19:47:56.504 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-07 19:47:58.288 Reschedule requested for id -1.
2010-03-07 19:47:58.895 Scheduled 0 items in 0.6 = 0.45 match + 0.15 place
2010-03-07 19:47:58.901 Seem to be woken up by USER
2010-03-07 19:48:02.044 MainServer::ANN Monitor
2010-03-07 19:48:02.052 adding: tvdesktop as a client (events: 0)
2010-03-07 19:48:02.053 MainServer::ANN Monitor
2010-03-07 19:48:02.056 adding: tvdesktop as a client (events: 1)
2010-03-07 19:48:20.813 MainServer::ANN Playback
2010-03-07 19:48:20.813 adding: tvdesktop as a client (events: 0)
2010-03-07 19:48:20.830 TVRec(6): Changing from None to Watching WatchingLiveTV
2010-03-07 19:48:20.839 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2010-03-07 19:48:20.839 ChannelBase(6): IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
2010-03-07 19:48:20.840 ChannelBase(6) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2010-03-07 19:48:20.840 TVRec(6): HW Tuner: 6->6
2010-03-07 19:48:20.845 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2010-03-07 19:48:20.845 DVBChan(6:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(Please add): Unable to find channel in database.
2010-03-07 19:48:20.846 TVRec(6) Error: Failed to set channel to Please add. Reverting to kState_None
2010-03-07 19:48:20.846 TVRec(6): Changing from Watching WatchingLiveTV to None
2010-03-07 19:49:15.283 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-07 19:53:02.907 MainServer::ANN Monitor
2010-03-07 19:53:02.909 adding: tvdesktop as a client (events: 0)
2010-03-07 19:53:02.910 MainServer::ANN Monitor
2010-03-07 19:53:02.911 adding: tvdesktop as a client (events: 1)
2010-03-07 19:53:07.296 MainServer::ANN Playback
2010-03-07 19:53:07.297 adding: tvdesktop as a client (events: 0)
2010-03-07 19:53:07.299 TVRec(6): Changing from None to Watching WatchingLiveTV
2010-03-07 19:53:07.302 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2010-03-07 19:53:07.303 ChannelBase(6): IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
2010-03-07 19:53:07.303 ChannelBase(6) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2010-03-07 19:53:07.304 TVRec(6): HW Tuner: 6->6
2010-03-07 19:53:07.308 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2010-03-07 19:53:07.309 DVBChan(6:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(Please add): Unable to find channel in database.
2010-03-07 19:53:07.309 TVRec(6) Error: Failed to set channel to Please add. Reverting to kState_None
2010-03-07 19:53:07.310 TVRec(6): Changing from Watching WatchingLiveTV to None
2010-03-07 20:25:35.644 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-03-07 20:25:35.647 Using runtime prefix = /usr
2010-03-07 20:25:35.648 Using configuration directory = /home/mythtv/.mythtv
2010-03-07 20:25:35.649 Empty LocalHostName.
2010-03-07 20:25:35.649 Using localhost value of tvdesktop
2010-03-07 20:25:35.661 New DB connection, total: 1
2010-03-07 20:25:35.667 Connected to database 'mythconverg' at host: localhost
2010-03-07 20:25:35.667 Closing DB connection named 'DBManager0'
2010-03-07 20:25:35.669 Connected to database 'mythconverg' at host: localhost
2010-03-07 20:25:35.673 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-07 20:25:35.676 MythBackend: Starting up as the master server.
2010-03-07 20:25:35.681 New DB connection, total: 2
2010-03-07 20:25:35.682 Connected to database 'mythconverg' at host: localhost
2010-03-07 20:25:35.723 New DB connection, total: 3
2010-03-07 20:25:35.727 Connected to database 'mythconverg' at host: localhost
2010-03-07 20:25:35.741 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2010-03-07 20:25:35.744 DVBChan(6:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(Please add): Unable to find channel in database.
2010-03-07 20:25:35.745 ChannelBase(6) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2010-03-07 20:25:35.791 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2010-03-07 20:25:35.793 DVBChan(7:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(Please add): Unable to find channel in database.
2010-03-07 20:25:35.794 ChannelBase(7) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2010-03-07 20:25:35.798 New DB scheduler connection
2010-03-07 20:25:35.806 Connected to database 'mythconverg' at host: localhost
2010-03-07 20:25:35.831 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-03-07 20:25:35.835 Main::Registering HttpStatus Extension
2010-03-07 20:25:35.836 Enabled verbose msgs:  important general
2010-03-07 20:25:35.839 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-03-07 20:25:37.841 MainServer::ANN Monitor
2010-03-07 20:25:37.842 adding: tvdesktop as a client (events: 0)
2010-03-07 20:25:37.843 MainServer::ANN Monitor
2010-03-07 20:25:37.844 adding: tvdesktop as a client (events: 1)
2010-03-07 20:25:38.816 Reschedule requested for id -1.
2010-03-07 20:25:38.840 Scheduled 0 items in 0.0 = 0.00 match + 0.02 place
2010-03-07 20:25:38.844 Seem to be woken up by USER
2010-03-07 20:26:55.819 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

==> /var/log/mythtv/mythfrontend.log <==
2010-03-07 19:48:41.511 Gesture: UpRight
2010-03-07 19:48:42.511 Gesture: UpRight
2010-03-07 19:48:43.083 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-03-07 19:48:43.177 Loading menu theme from /usr/share/mythtv/music_settings.xml
2010-03-07 19:48:43.511 Gesture: UpRight
2010-03-07 19:48:44.511 Gesture: UpRight
2010-03-07 19:48:45.511 Gesture: UpRight
2010-03-07 19:48:46.511 Gesture: UpRight
2010-03-07 19:48:47.846 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit
Starting mythfrontend.real..
2010-03-07 19:52:59.792 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-03-07 19:52:59.793 Using runtime prefix = /usr
2010-03-07 19:52:59.793 Using configuration directory = /home/mike1/.mythtv
2010-03-07 19:53:00.647 Empty LocalHostName.
2010-03-07 19:53:00.647 Using localhost value of tvdesktop
2010-03-07 19:53:00.655 New DB connection, total: 1
2010-03-07 19:53:00.658 Connected to database 'mythconverg' at host: localhost
2010-03-07 19:53:00.659 Closing DB connection named 'DBManager0'
2010-03-07 19:53:00.669 ScreenSaverX11Private: Gnome screen saver support enabled
2010-03-07 19:53:00.670 DPMS is active.
2010-03-07 19:53:00.672 Primary screen: 0.
2010-03-07 19:53:00.673 Connected to database 'mythconverg' at host: localhost
2010-03-07 19:53:00.674 Using screen 0, 1440x900 at 0,0
2010-03-07 19:53:00.687 MythUI Image Cache size set to 20971520 bytes
2010-03-07 19:53:00.687 Enabled verbose msgs:  important general
2010-03-07 19:53:00.694 Primary screen: 0.
2010-03-07 19:53:00.694 Using screen 0, 1440x900 at 0,0
2010-03-07 19:53:00.695 Using theme base resolution of 1280x720
2010-03-07 19:53:00.703 LIRC: Successfully initialized '/dev/lircd' using '/home/mike1/.mythtv/lircrc' config
2010-03-07 19:53:00.703 JoystickMenuThread Error: Joystick disabled - Failed to read /home/mike1/.mythtv/joystickmenurc
2010-03-07 19:53:00.889 Using the Qt painter
2010-03-07 19:53:01.044 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2010-03-07 19:53:01.052 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-03-07 19:53:01.065 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-03-07 19:53:01.065 Unable to load window 'backgroundwindow' from base
2010-03-07 19:53:01.071 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-07 19:53:01.307 Desktop video mode: 1440x900 59.9018 Hz
2010-03-07 19:53:01.692 Registering Internal as a media playback plugin.
2010-03-07 19:53:01.719 Registering WebBrowser as a media playback plugin.
2010-03-07 19:53:01.752 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.757 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.760 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.769 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.773 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.775 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.784 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.789 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.795 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.805 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.810 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.815 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.825 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.832 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.834 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.842 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.845 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.851 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-03-07 19:53:01.854 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-03-07 19:53:01.879 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-03-07 19:53:01.922 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-03-07 19:53:01.940 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-03-07 19:53:01.990 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-03-07 19:53:02.051 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-03-07 19:53:02.054 Found mainmenu.xml for theme 'Mythbuntu'
2010-03-07 19:53:02.906 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-03-07 19:53:02.907 Using protocol version 50
2010-03-07 19:53:07.193 New DB connection, total: 2
2010-03-07 19:53:07.194 Connected to database 'mythconverg' at host: localhost
2010-03-07 19:53:07.295 TV: Attempting to change from None to Watching WatchingLiveTV
2010-03-07 19:53:07.295 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-03-07 19:53:07.296 Using protocol version 50
2010-03-07 19:53:07.297 Spawning LiveTV Recorder -- begin
2010-03-07 19:53:07.311 Spawning LiveTV Recorder -- end
2010-03-07 19:53:07.311 GetEntryAt(-1) failed.
2010-03-07 19:53:07.312 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2010-03-07 19:53:07.312 TV Error: HandleStateChange(): LiveTV not successfully started
2010-03-07 19:53:07.312 We have a RingBuffer
2010-03-07 19:53:07.362 TV Error: LiveTV not successfully started
2010-03-07 19:53:07.384 ScreenSaverX11Private: DPMS Deactivated 1
2010-03-07 19:53:07.385 ScreenSaverX11Private: DPMS Reactivated 1
2010-03-07 19:53:16.122 Deleting UPnP client...

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391301] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391307] s5h1411_writereg: writereg error 0x19 0xce 0x2000, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391313] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391319] s5h1411_writereg: writereg error 0x19 0xcf 0x0800, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391325] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391331] s5h1411_writereg: writereg error 0x19 0xd0 0x0800, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391338] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391344] s5h1411_writereg: writereg error 0x19 0xd1 0x0400, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391350] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391356] s5h1411_writereg: writereg error 0x19 0xd2 0x0800, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391362] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391368] s5h1411_writereg: writereg error 0x19 0xd3 0x2000, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391374] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391380] s5h1411_writereg: writereg error 0x19 0xd4 0x3000, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391386] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391392] s5h1411_writereg: writereg error 0x19 0xdb 0x4a9b, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391398] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391405] s5h1411_writereg: writereg error 0x19 0xdc 0x1000, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391412] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391418] s5h1411_writereg: writereg error 0x19 0xde 0x0001, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391424] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391430] s5h1411_writereg: writereg error 0x19 0xdf 0x0000, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391436] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391442] s5h1411_writereg: writereg error 0x19 0xe3 0x0301, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391448] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391454] s5h1411_writereg: writereg error 0x1a 0xf3 0x0000, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391460] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391466] s5h1411_writereg: writereg error 0x1a 0xf3 0x0001, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391472] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391479] s5h1411_writereg: writereg error 0x1a 0x08 0x0600, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391485] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391491] s5h1411_writereg: writereg error 0x1a 0x18 0x4201, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391497] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391503] s5h1411_writereg: writereg error 0x1a 0x1e 0x6476, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391509] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391515] s5h1411_writereg: writereg error 0x1a 0x21 0x0830, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391521] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391528] s5h1411_writereg: writereg error 0x1a 0x0c 0x5679, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391534] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391541] s5h1411_writereg: writereg error 0x1a 0x0d 0x579b, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391547] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391554] s5h1411_writereg: writereg error 0x1a 0x24 0x0102, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391560] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391566] s5h1411_writereg: writereg error 0x1a 0x31 0x7488, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391572] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391578] s5h1411_writereg: writereg error 0x1a 0x32 0x0a08, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391584] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391589] s5h1411_writereg: writereg error 0x1a 0x3d 0x8689, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391595] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391601] s5h1411_writereg: writereg error 0x1a 0x49 0x0048, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391606] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391612] s5h1411_writereg: writereg error 0x1a 0x57 0x2012, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391617] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391623] s5h1411_writereg: writereg error 0x1a 0x5d 0x7676, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391629] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391635] s5h1411_writereg: writereg error 0x1a 0x04 0x0400, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391641] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391647] s5h1411_writereg: writereg error 0x1a 0x58 0x00c0, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391653] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391659] s5h1411_writereg: writereg error 0x1a 0x5b 0x0100, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391665] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391671] s5h1411_readreg: readreg error (ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391675] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391682] s5h1411_writereg: writereg error 0x19 0xbd 0x0000, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391687] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391692] s5h1411_readreg: readreg error (ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391696] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391702] s5h1411_writereg: writereg error 0x19 0x24 0x1000, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391709] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391715] s5h1411_writereg: writereg error 0x19 0x38 0x1be4, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391719] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391725] s5h1411_writereg: writereg error 0x19 0x39 0x3655, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391730] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391736] s5h1411_writereg: writereg error 0x1a 0x2c 0x1be4, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391741] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391746] s5h1411_readreg: readreg error (ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391751] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391757] s5h1411_writereg: writereg error 0x19 0xe0 0x0000, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391763] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391768] s5h1411_readreg: readreg error (ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391772] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391778] s5h1411_writereg: writereg error 0x19 0xbe 0x0000, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391784] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391790] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391794] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391800] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391805] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391811] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391816] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391822] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Mar  7 20:25:35 tvdesktop kernel: [ 2295.391828] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.413086] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.413093] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.413098] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.413103] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.425021] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.425030] tda18271_write_regs: ERROR: i2c_transfer returned: -5
Mar  7 20:25:35 tvdesktop kernel: [ 2295.425037] tda18271_init: error -5 on line 805
Mar  7 20:25:35 tvdesktop kernel: [ 2295.425042] pvrusb2: Attempted to execute control transfer when device not ok
Mar  7 20:25:35 tvdesktop kernel: [ 2295.425050] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)

==> /var/log/Xorg.0.log <==
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: BBY  Model: cd19  Serial#: 184626
(II) intel(0): Year: 2008  Week: 32
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.646 redY: 0.332   greenX: 0.269 greenY: 0.600
(II) intel(0): blueX: 0.142 blueY: 0.072   whiteX: 0.285 whiteY: 0.293
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 88.8 MHz   Image Size:  410 x 256 mm
(II) intel(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1600 h_border: 0
(II) intel(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 106.5 MHz   Image Size:  410 x 256 mm
(II) intel(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) intel(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 61 kHz, PixClock max 110 MHz
(II) intel(0): Monitor name: DX-LCD19-09
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff00085919cd32d10200
(II) intel(0): 	2012010368291a782a8e60a555449924
(II) intel(0): 	12494bafce0001010101010101010101
(II) intel(0): 	010101010101ab22a0a050841a303020
(II) intel(0): 	36009a001100001a9a29a0d051842230
(II) intel(0): 	509836009a001100001c000000fd0038
(II) intel(0): 	4c1f3d0b000a202020202020000000fc
(II) intel(0): 	0044582d4c434431392d30390a2000f2
(II) intel(0): EDID vendor "BBY", prod id 52505
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)

==> /home/mike1/.xsession-errors <==
/etc/gdm/Xsession: Beginning session setup...

2010-03-07 19:47:47.367 Using runtime prefix = /usr
2010-03-07 19:47:47.367 Using configuration directory = /home/mike1/.mythtv
2010-03-07 19:47:47.433 Empty LocalHostName.
2010-03-07 19:47:47.434 Using localhost value of tvdesktop
2010-03-07 19:47:47.455 New DB connection, total: 1
2010-03-07 19:47:47.550 Connected to database 'mythconverg' at host: localhost
2010-03-07 19:47:47.550 Closing DB connection named 'DBManager0'
2010-03-07 19:47:47.551 Connected to database 'mythconverg' at host: localhost
2010-03-07 19:47:47.824 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7

** (gnome-screensaver:1744): WARNING **: Failed to get session presence proxy: Could not get owner of name 'org.gnome.SessionManager': no such name
Failed to run gnome-keyring-daemon: Failed to execute child process "gnome-keyring-daemon" (No such file or directory)
xfdesktop[1877]: starting up
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

(polkit-gnome-authentication-agent-1:2002): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2002): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3
xfce4-settings-helper is already running
2010-03-07 19:47:56.315 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org

(xfce4-terminal:2217): Terminal-WARNING **: Unable to load terminal preferences.

(firefox:2242): GLib-WARNING **: g_set_prgname() called multiple times

** (xfwm4:1869): WARNING **: Cannot get window attributes for window (0x2a0004f)

(firefox:2242): GLib-WARNING **: g_set_prgname() called multiple times
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_2040_7501_7300_00_F050CDB5_if0.
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_2040_7501_7300_00_F050CDB5.
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2010-03-07 19:52:59.769 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mythtv-backend
mythtv-backend stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart mythtv-backend
mythtv-backend start/running, process 2545

==> lsb_release -a <==
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              89G  2.9G   82G   4% /
udev                  1.5G  308K  1.5G   1% /dev
none                  1.5G     0  1.5G   0% /dev/shm
none                  1.5G  336K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sdb1             466G   46G  421G  10% /media/media

==> uname -a <==
Linux tvdesktop 2.6.31-20-generic-pae #57-Ubuntu SMP Mon Feb 8 10:23:59 UTC 2010 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

==> lsusb <==
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 2040:7501 Hauppauge 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 045e:071d Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3016MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.3
          serial: [REMOVED]
          size: 2800MHz
          capacity: 2800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cfe80000-cfefffff ioport:c800(size=8) memory:d0000000-dfffffff(prefetchable) memory:cfe40000-cfe7ffff
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:cfe38000-cfe3bfff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:d000(size=4096)
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:b400(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:b800(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c000(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c400(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:cfe37c00-cfe37fff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:e000(size=4096) memory:cff00000-cfffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32
                resources: irq:20 memory:cffff800-cfffffff ioport:e800(size=128)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=[REMOVED] latency=64 maxlatency=64 mingnt=32 multicast=yes
                resources: irq:21 ioport:e400(size=256) memory:cffff400-cffff4ff
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-cdrom:0
                description: DVD writer
                product: DVD Writer 740b
                vendor: HP
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: ED24
                serial: [REMOVED]
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD reader
                product: DROM6216
                vendor: IDE-DVD
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: HD08
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:b000(size=8) ioport:a800(size=4) ioport:a400(size=8) ioport:a000(size=4) ioport:9800(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage

```

Some help here please

---

### Post by greenwom on 2010-03-12
Shameless Bump,

I've been playing with it and I think there is a hardware issue with this model that one has to contend with.  If the device isn't unplugged at boot up it doesn't reset.  If I unplug and reboot and plug it in it is recognized.  Mythtv still doesn't have the ability to use the card or remote.

When I run Boxee the device lights up (remote doesn't work)

so again, I think a myth config is geeked up  (any help)

---

