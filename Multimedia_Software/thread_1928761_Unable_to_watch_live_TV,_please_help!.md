---
title: "Unable to watch live TV, please help!"
date: 2012-02-20
forum: Multimedia Software
---

### Post by drewdin on 2012-02-20
When i try to watch Live TV the screen goes blank shows the word Please... and then comes back to the frontend without seeing any video. 

When i checked the mythbackend.log I have three errors but the most blatent one i can seem to figuire out is Sample Rate: Attempted to add a rate 32000Hz, which is not in the list of allowed rates. 

I have a Hauppage WinTV PVR-150 capture card

below is a link to my logs, any help or suggestions would be greatly appreciated. Thanks in Advance!


[LIST=1]
[*]2012-02-20 14:53:18.147 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] [www.mythtv.org](www.mythtv.org)
[*]2012-02-20 14:53:18.147 Using runtime prefix = /usr
[*]2012-02-20 14:53:18.148 Using configuration directory = /home/dvr/.mythtv
[*]2012-02-20 14:53:18.150 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
[*]2012-02-20 14:53:19.198 Empty LocalHostName.
[*]2012-02-20 14:53:19.199 Using localhost value of MythTVDVR
[*]2012-02-20 14:53:19.315 New DB connection, total: 1
[*]2012-02-20 14:53:19.333 Connected to database 'mythconverg' at host: localhost
[*]2012-02-20 14:53:19.348 Closing DB connection named 'DBManager0'
[*]2012-02-20 14:53:19.349 Connected to database 'mythconverg' at host: localhost
[*]2012-02-20 14:53:19.353 Current locale EN_US
[*]2012-02-20 14:53:19.353 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
[*]2012-02-20 14:53:19.605 ScreenSaverX11Private: XScreenSaver support enabled
[*]2012-02-20 14:53:19.609 DPMS is disabled.
[*]2012-02-20 14:53:19.640 Desktop video mode: 1280x1024 60.020 Hz
[*]2012-02-20 14:53:19.916 Enabled verbose msgs:  important general
[*]2012-02-20 14:53:19.927 Loading en_us translation for module mythfrontend
[*]2012-02-20 14:53:19.992 LIRC: Successfully initialized '/dev/lircd' using '/home/dvr/.mythtv/lircrc' config
[*]2012-02-20 14:53:19.992 JoystickMenuThread: Joystick disabled - Failed to read /home/dvr/.mythtv/joystickmenurc
[*]2012-02-20 14:53:20.164 Using Frameless Window
[*]2012-02-20 14:53:20.165 Using Full Screen Window
[*]2012-02-20 14:53:20.474 Using the Qt painter
[*]2012-02-20 14:53:20.934 New DB connection, total: 2
[*]2012-02-20 14:53:20.937 New DB connection, total: 3
[*]2012-02-20 14:53:20.939 Connected to database 'mythconverg' at host: localhost
[*]2012-02-20 14:53:20.939 Current MythTV Schema Version (DBSchemaVer): 1264
[*]2012-02-20 14:53:20.942 Connected to database 'mythconverg' at host: localhost
[*]2012-02-20 14:53:25.796 ThemeInfo,  Warning: Unable to open themeinfo.xml for  /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
[*]2012-02-20 14:53:25.796 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
[*]2012-02-20 14:53:25.798 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
[*]2012-02-20 14:53:25.798 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
[*]2012-02-20 14:53:26.459 Registering Internal as a media playback plugin.
[*]2012-02-20 14:53:26.527 MediaMonitorUnix::AddDevice() - empty device path.
[*]2012-02-20 14:53:26.527 MediaMonitorUnix::AddDevice() - empty device path.
[*]2012-02-20 14:53:26.528 MediaMonitorUnix::AddDevice() - empty device path.
[*]2012-02-20 14:53:26.529 MonitorRegisterExtensions(0x100, gif,jpg,png)
[*]2012-02-20 14:53:26.530 Loading en_us translation for module mythgallery
[*]2012-02-20 14:53:26.575 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
[*]2012-02-20 14:53:26.679  MonitorRegisterExtensions(0x40,  mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
[*]2012-02-20 14:53:26.695 Loading en_us translation for module mythmusic
[*]2012-02-20 14:53:26.710 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
[*]2012-02-20 14:53:26.758 Loading en_us translation for module mythvideo
[*]2012-02-20 14:53:26.772 Loading en_us translation for module mythweather
[*]2012-02-20 14:53:27.072 Found mainmenu.xml for theme 'Mythbuntu'
[*]2012-02-20 14:53:27.512 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
[*]2012-02-20 14:53:27.514 Using protocol version 63
[*]2012-02-20 14:53:35.535 TV: Attempting to change from None to WatchingLiveTV
[*]2012-02-20 14:53:35.536 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
[*]2012-02-20 14:53:35.537 Using protocol version 63
[*]2012-02-20 14:53:35.594 Spawning LiveTV Recorder -- begin
[*]2012-02-20 14:53:37.289 Spawning LiveTV Recorder -- end
[*]2012-02-20 14:53:37.308 We have a playbackURL(/var/lib/mythtv/livetv/1002_20120220145337.nuv) & cardtype(V4L)
[*]2012-02-20 14:53:37.513 We have a RingBuffer
[*]2012-02-20 14:54:17.514 TV Error: StartRecorder() -- timed out waiting for recorder to start
[*]2012-02-20 14:54:17.514 TV Error: LiveTV not successfully started
[*]2012-02-20 14:54:34.602 Deleting UPnP client...
[*]Error in my_thread_global_end(): 2 threads didn't exit
[/LIST]

Starting mythfrontend.real..
2012-02-20 14:53:18.147 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] [www.mythtv.org](www.mythtv.org)
2012-02-20 14:53:18.147 Using runtime prefix = /usr
2012-02-20 14:53:18.148 Using configuration directory = /home/dvr/.mythtv
2012-02-20 14:53:18.150 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2012-02-20 14:53:19.198 Empty LocalHostName.
2012-02-20 14:53:19.199 Using localhost value of MythTVDVR
2012-02-20 14:53:19.315 New DB connection, total: 1
2012-02-20 14:53:19.333 Connected to database 'mythconverg' at host: localhost
2012-02-20 14:53:19.348 Closing DB connection named 'DBManager0'
2012-02-20 14:53:19.349 Connected to database 'mythconverg' at host: localhost
2012-02-20 14:53:19.353 Current locale EN_US
2012-02-20 14:53:19.353 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2012-02-20 14:53:19.605 ScreenSaverX11Private: XScreenSaver support enabled
2012-02-20 14:53:19.609 DPMS is disabled.
2012-02-20 14:53:19.640 Desktop video mode: 1280x1024 60.020 Hz
2012-02-20 14:53:19.916 Enabled verbose msgs:  important general
2012-02-20 14:53:19.927 Loading en_us translation for module mythfrontend
2012-02-20 14:53:19.992 LIRC: Successfully initialized '/dev/lircd' using '/home/dvr/.mythtv/lircrc' config
2012-02-20 14:53:19.992 JoystickMenuThread: Joystick disabled - Failed to read /home/dvr/.mythtv/joystickmenurc
2012-02-20 14:53:20.164 Using Frameless Window
2012-02-20 14:53:20.165 Using Full Screen Window
2012-02-20 14:53:20.474 Using the Qt painter
2012-02-20 14:53:20.934 New DB connection, total: 2
2012-02-20 14:53:20.937 New DB connection, total: 3
2012-02-20 14:53:20.939 Connected to database 'mythconverg' at host: localhost
2012-02-20 14:53:20.939 Current MythTV Schema Version (DBSchemaVer): 1264
2012-02-20 14:53:20.942 Connected to database 'mythconverg' at host: localhost
2012-02-20 14:53:25.796 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2012-02-20 14:53:25.796 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2012-02-20 14:53:25.798 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2012-02-20 14:53:25.798 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2012-02-20 14:53:26.459 Registering Internal as a media playback plugin.
2012-02-20 14:53:26.527 MediaMonitorUnix::AddDevice() - empty device path.
2012-02-20 14:53:26.527 MediaMonitorUnix::AddDevice() - empty device path.
2012-02-20 14:53:26.528 MediaMonitorUnix::AddDevice() - empty device path.
2012-02-20 14:53:26.529 MonitorRegisterExtensions(0x100, gif,jpg,png)
2012-02-20 14:53:26.530 Loading en_us translation for module mythgallery
2012-02-20 14:53:26.575 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2012-02-20 14:53:26.679 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2012-02-20 14:53:26.695 Loading en_us translation for module mythmusic
2012-02-20 14:53:26.710 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2012-02-20 14:53:26.758 Loading en_us translation for module mythvideo
2012-02-20 14:53:26.772 Loading en_us translation for module mythweather
2012-02-20 14:53:27.072 Found mainmenu.xml for theme 'Mythbuntu'
2012-02-20 14:53:27.512 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2012-02-20 14:53:27.514 Using protocol version 63
2012-02-20 14:53:35.535 TV: Attempting to change from None to WatchingLiveTV
2012-02-20 14:53:35.536 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2012-02-20 14:53:35.537 Using protocol version 63
2012-02-20 14:53:35.594 Spawning LiveTV Recorder -- begin
2012-02-20 14:53:37.289 Spawning LiveTV Recorder -- end
2012-02-20 14:53:37.308 We have a playbackURL(/var/lib/mythtv/livetv/1002_20120220145337.nuv) & cardtype(V4L)
2012-02-20 14:53:37.513 We have a RingBuffer
2012-02-20 14:54:17.514 TV Error: StartRecorder() -- timed out waiting for recorder to start
2012-02-20 14:54:17.514 TV Error: LiveTV not successfully started
2012-02-20 14:54:34.602 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit


Drew

---

### Post by drewdin on 2012-02-21
tough crowd! Did i post in the wrong place or is it that no one is familiar with MythBuntu?

---

### Post by MartyBuntu on 2012-02-21
The PVR-150 is analog-only.
What are you connecting it to?

---

### Post by drewdin on 2012-02-24
i finally got it working with a composite input, for some reason when i was using the tuner i could hear the sound but i could not see the picture. it was just scrabbled fuzz. 

I know need to configure the ir blaster to change the channels on my vernon cable box, any suggestions?

---

