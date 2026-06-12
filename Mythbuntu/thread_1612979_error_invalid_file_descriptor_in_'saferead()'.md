---
title: "error: invalid file descriptor in 'saferead()'"
date: 2010-11-03
forum: Mythbuntu
---

### Post by tunzo on 2010-11-03
Hi everyone.  I am having an issue trying to watch live tv in a fresh mythbuntu setup.  I am pretty sure that I have all of the backend configuration set up properly.  the backend and frontend are running on the same machine.  though i am new to the mythtv scene, i did have myth running on this machine before for a week or so, but i ended up having to reinstall.

now, when i go to watch live tv, i get "please wait" for (apparently) 16 seconds, and then a pop-up window telling me that it couldnt find the database.  when i look at the mythfrontend.log, i see this:


> Starting mythfrontend.real..
2010-11-03 22:03:06.339 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-11-03 22:03:06.339 Using runtime prefix = /usr
2010-11-03 22:03:06.339 Using configuration directory = /home/tunzo/.mythtv
2010-11-03 22:03:07.067 Empty LocalHostName.
2010-11-03 22:03:07.067 Using localhost value of ninja
2010-11-03 22:03:07.086 New DB connection, total: 1
2010-11-03 22:03:07.098 Connected to database 'mythconverg' at host: 127.0.0.1
2010-11-03 22:03:07.099 Closing DB connection named 'DBManager0'
2010-11-03 22:03:07.130 ScreenSaverX11Private: XScreenSaver support enabled
2010-11-03 22:03:07.132 DPMS is active.
2010-11-03 22:03:07.134 Primary screen: 0.
2010-11-03 22:03:07.135 Connected to database 'mythconverg' at host: 127.0.0.1
2010-11-03 22:03:07.149 Using screen 0, 1024x768 at 0,0
2010-11-03 22:03:07.210 Desktop video mode: 1024x768 60.006 Hz
2010-11-03 22:03:07.262 MythUI Image Cache size set to 20971520 bytes
2010-11-03 22:03:07.318 Enabled verbose msgs:  important general
2010-11-03 22:03:07.334 Primary screen: 0.
2010-11-03 22:03:07.335 Using screen 0, 1024x768 at 0,0
2010-11-03 22:03:07.336 Using theme base resolution of 1280x720
2010-11-03 22:03:07.352 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-11-03 22:03:07.352 JoystickMenuThread Error: Joystick disabled - Failed to read /home/tunzo/.mythtv/joystickmenurc
2010-11-03 22:03:07.453 Using Frameless Window
2010-11-03 22:03:07.453 Using Full Screen Window
2010-11-03 22:03:07.783 Using the Qt painter
2010-11-03 22:03:07.991 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-11-03 22:03:08.011 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-11-03 22:03:08.025 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-11-03 22:03:08.025 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-11-03 22:03:08.043 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-03 22:03:11.706 Registering Internal as a media playback plugin.
2010-11-03 22:03:11.752 Cannot load language en_us for module mytharchive
2010-11-03 22:03:11.799 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-03 22:03:11.799 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-03 22:03:11.800 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-03 22:03:11.800 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-11-03 22:03:11.801 Cannot load language en_us for module mythgallery
2010-11-03 22:03:11.806 Cannot load language en_us for module mythmovies
2010-11-03 22:03:11.830 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-11-03 22:03:11.901 MonitorRegisterExtensions(0x40,  mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-11-03 22:03:11.911 Cannot load language en_us for module mythmusic
2010-11-03 22:03:11.923 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-11-03 22:03:11.972 Cannot load language en_us for module mythvideo
2010-11-03 22:03:11.983 Cannot load language en_us for module mythweather
2010-11-03 22:03:11.987 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-11-03 22:03:12.106 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-11-03 22:03:12.113 Found mainmenu.xml for theme 'Mythbuntu'
2010-11-03 22:03:13.049 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-03 22:03:13.052 Using protocol version 56
2010-11-03 22:03:44.292 TV: Attempting to change from None to WatchingLiveTV
2010-11-03 22:03:44.293 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-03 22:03:44.294 Using protocol version 56
2010-11-03 22:03:44.313 Spawning LiveTV Recorder -- begin
2010-11-03 22:03:45.330 Spawning LiveTV Recorder -- end
2010-11-03 22:03:45.337 ProgramInfo(): Updated pathname '':'' -> '1242_20101103220345.mpg'
2010-11-03 22:03:45.350 We have a playbackURL(/mnt/storage1/myth/livetv/1242_20101103220345.mpg) & cardtype(HDPVR)
2010-11-03 22:03:51.850  RingBuf(/mnt/storage1/myth/livetv/1242_20101103220345.mpg): Invalid file  (fd -1) when opening  '/mnt/storage1/myth/livetv/1242_20101103220345.mpg'.
2010-11-03 22:03:51.851 We have a RingBuffer
2010-11-03 22:03:52.000  RingBuf(/mnt/storage1/myth/livetv/1242_20101103220345.mpg) Error:  Invalid file descriptor in 'safe_read()'

that error on the last line is repeated about 330,000 times in a row in the mythfrontend.log file (each time i try this the file grows by about 40 MB).  additionally, that .mpg does get created in my livetv directory, but it has 0 size.  following the 300,000 lines of the same error, i get this:
> 
2010-11-03 22:04:08.009 RingBuf(/mnt/storage1/myth/livetv/1242_20101103220345.mpg) Error: Waited 16 seconds for data, aborting.
2010-11-03 22:04:08.009 RingBuf(/mnt/storage1/myth/livetv/1242_20101103220345.mpg) Warning: Peek() requested 2048 bytes, but only returning 0
2010-11-03 22:04:08.009 NVP::OpenFile(): Error, couldn't read file: /mnt/storage1/myth/livetv/1242_20101103220345.mpg
2010-11-03 22:04:08.009 TV Error: LiveTV not successfully started
2010-11-03 22:04:08.021 ScreenSaverX11Private: DPMS Deactivated 1
2010-11-03 22:04:08.009 RingBuf(/mnt/storage1/myth/livetv/1242_20101103220345.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-11-03 22:04:08.023 ScreenSaverX11Private: DPMS Reactivated 1
2010-11-03 22:04:10.842 MythSocket(93df580:26): readStringList: Connection died (select).
2010-11-03 22:04:10.842 Connection to backend server lost
2010-11-03 22:04:10.843 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-03 22:04:10.843 Connection to master server timed out.
            Either the server is down or the master server settings
            in mythtv-settings does not contain the proper IP address

2010-11-03 22:04:10.843 Reconnection to backend server failed
2010-11-03 22:04:10.843 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-03 22:04:10.844 Connection to master server timed out.
            Either the server is down or the master server settings
            in mythtv-settings does not contain the proper IP address

2010-11-03 22:04:10.849 Event socket closed. No connection to the backend.
2010-11-03 22:04:11.401 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-03 22:04:11.402 Connection to master server timed out.
            Either the server is down or the master server settings
            in mythtv-settings does not contain the proper IP address

2010-11-03 22:04:15.131 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-03 22:04:15.135 Using protocol version 56
2010-11-03 22:04:16.591 Deleting UPnP client...

i am really lost as to what could be going on here.  if anyone has any ideas i would be very grateful.

thanks!
tunzo

---

### Post by tunzo on 2010-11-10
it turns out that this issue was caused by the fact that i had the sound input on the hdpvr set to spdif but my optical cable was not actually plugged into it.  apparently when myth tells the hdpvr to record and to look for sound on spdif, it crashes the hdpvr.  

tunzo

---

