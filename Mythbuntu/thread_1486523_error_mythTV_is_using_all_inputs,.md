---
title: "error: mythTV is using all inputs,"
date: 2010-05-17
forum: Mythbuntu
---

### Post by thor999 on 2010-05-17
Upon attempting to watch live tv, I am greeted w/ the message "error: mythTV is using all inputs, but there are no active recordings? This is Mythbuntu 10.04 64-bit, running a pchdtv 5500 tuner card, any input would be appreciated!Here are my logs: 
  thor999@thor999-desktop:~$ mythbackend
2010-05-17 22:17:19.528 mythbackend version: branches/release-0-23-fixes [24678] [www.mythtv.org](www.mythtv.org)
2010-05-17 22:17:19.528 Using runtime prefix = /usr
2010-05-17 22:17:19.528 Using configuration directory = /home/thor999/.mythtv
2010-05-17 22:17:19.529 Empty LocalHostName.
2010-05-17 22:17:19.529 Using localhost value of thor999-desktop
2010-05-17 22:17:19.534 New DB connection, total: 1
2010-05-17 22:17:19.537 Connected to database 'mythconverg' at host: localhost
2010-05-17 22:17:19.537 Closing DB connection named 'DBManager0'
2010-05-17 22:17:19.538 Connected to database 'mythconverg' at host: localhost
2010-05-17 22:17:19.540 Current MythTV Schema Version (DBSchemaVer): 1254
2010-05-17 22:17:19.541 MythBackend: Starting up as the master server.
2010-05-17 22:17:19.542 mythbackend: MythBackend started as master server
2010-05-17 22:17:19.543 New DB connection, total: 2
2010-05-17 22:17:19.544 Connected to database 'mythconverg' at host: localhost
2010-05-17 22:17:19.546 Channel(/dev/video0)::Open(): Can't open video device, error "No such file or directory"
2010-05-17 22:17:19.547 mythbackend: Problem with capture cards: Card 1failed init
2010-05-17 22:17:19.548 DVBChan(2:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: No such file or directory (2)
2010-05-17 22:17:19.548 DVBChan(2:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2010-05-17 22:17:19.548 mythbackend: Problem with capture cards: Card 2failed init
2010-05-17 22:17:19.549 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: No such file or directory (2)
2010-05-17 22:17:19.549 DVBChan(3:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2010-05-17 22:17:19.550 mythbackend: Problem with capture cards: Card 3failed init
2010-05-17 22:17:19.550 MythBackend, Error: No valid capture cards are defined in the database.
            Perhaps you should re-read the installation instructions?
2010-05-17 22:17:19.550 mythbackend: No capture cards are defined: Please run the setup program.
2010-05-17 22:17:19.552 New DB connection, total: 3
2010-05-17 22:17:19.552 Connected to database 'mythconverg' at host: localhost
2010-05-17 22:17:19.554 MediaServer::HttpServer Create Error
2010-05-17 22:17:19.555 Enabled verbose msgs:  important general
2010-05-17 22:17:19.556 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-05-17 22:17:19.557 Failed to bind port 6543. Exiting.
2010-05-17 22:17:19.557 Backend exiting, MainServer initialization error.
Error in my_thread_global_end(): 1 threads didn't exit
thor999@thor999-desktop:~$ mythfrontend
2010-05-17 22:17:49.679 mythfrontend version: branches/release-0-23-fixes [24678] [www.mythtv.org](www.mythtv.org)
2010-05-17 22:17:49.679 Using runtime prefix = /usr
2010-05-17 22:17:49.679 Using configuration directory = /home/thor999/.mythtv
2010-05-17 22:17:50.371 Empty LocalHostName.
2010-05-17 22:17:50.371 Using localhost value of thor999-desktop
2010-05-17 22:17:50.377 New DB connection, total: 1
2010-05-17 22:17:50.379 Connected to database 'mythconverg' at host: localhost
2010-05-17 22:17:50.380 Closing DB connection named 'DBManager0'
2010-05-17 22:17:50.400 ScreenSaverX11Private: XScreenSaver support enabled
2010-05-17 22:17:50.401 DPMS is disabled.
2010-05-17 22:17:50.402 Primary screen: 0.
2010-05-17 22:17:50.403 Connected to database 'mythconverg' at host: localhost
2010-05-17 22:17:50.404 Using screen 0, 1600x900 at 0,0
2010-05-17 22:17:50.415 Desktop video mode: 1600x900 60.0024 Hz
2010-05-17 22:17:50.426 MythUI Image Cache size set to 20971520 bytes
2010-05-17 22:17:50.440 Enabled verbose msgs:  important general
2010-05-17 22:17:50.451 Primary screen: 0.
2010-05-17 22:17:50.451 Using screen 0, 1600x900 at 0,0
2010-05-17 22:17:50.452 Using theme base resolution of 1280x720
2010-05-17 22:17:50.456 LIRC: Successfully initialized '/dev/lircd' using '/home/thor999/.mythtv/lircrc' config
2010-05-17 22:17:50.456 JoystickMenuThread Error: Joystick disabled - Failed to read /home/thor999/.mythtv/joystickmenurc
2010-05-17 22:17:50.480 Using Frameless Window
2010-05-17 22:17:50.480 Using Full Screen Window
2010-05-17 22:17:50.682 Using the Qt painter
2010-05-17 22:17:50.758 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-05-17 22:17:50.765 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-05-17 22:17:50.772 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-05-17 22:17:50.773 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-05-17 22:17:50.779 Current MythTV Schema Version (DBSchemaVer): 1254
2010-05-17 22:17:51.058 Registering Internal as a media playback plugin.
2010-05-17 22:17:51.074 Cannot load language en_us for module mytharchive
2010-05-17 22:17:51.092 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.092 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.093 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.094 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.094 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.094 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.095 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.096 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.096 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.097 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.097 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.097 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.098 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.098 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.098 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:17:51.099 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-05-17 22:17:51.099 Cannot load language en_us for module mythgallery
2010-05-17 22:17:51.101 Cannot load language en_us for module mythmovies
2010-05-17 22:17:51.117 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-05-17 22:17:51.141 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-05-17 22:17:51.148 Cannot load language en_us for module mythmusic
2010-05-17 22:17:51.153 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-05-17 22:17:51.167 Cannot load language en_us for module mythvideo
2010-05-17 22:17:51.172 Cannot load language en_us for module mythweather
2010-05-17 22:17:51.175 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-05-17 22:17:51.216 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-05-17 22:17:51.218 Found mainmenu.xml for theme 'Mythbuntu'
2010-05-17 22:17:51.712 MythContext: Connecting to backend server: 192.168.1.7:6543 (try 1 of 1)
2010-05-17 22:17:51.713 Using protocol version 56
2010-05-17 22:17:55.963 Deleting UPnP client...
thor999@thor999-desktop:~$ mythfrontend
2010-05-17 22:22:22.798 mythfrontend version: branches/release-0-23-fixes [24678] [www.mythtv.org](www.mythtv.org)
2010-05-17 22:22:22.798 Using runtime prefix = /usr
2010-05-17 22:22:22.798 Using configuration directory = /home/thor999/.mythtv
2010-05-17 22:22:23.489 Empty LocalHostName.
2010-05-17 22:22:23.489 Using localhost value of thor999-desktop
2010-05-17 22:22:23.495 New DB connection, total: 1
2010-05-17 22:22:23.498 Connected to database 'mythconverg' at host: localhost
2010-05-17 22:22:23.498 Closing DB connection named 'DBManager0'
2010-05-17 22:22:23.513 ScreenSaverX11Private: XScreenSaver support enabled
2010-05-17 22:22:23.514 DPMS is disabled.
2010-05-17 22:22:23.520 Primary screen: 0.
2010-05-17 22:22:23.521 Connected to database 'mythconverg' at host: localhost
2010-05-17 22:22:23.522 Using screen 0, 1600x900 at 0,0
2010-05-17 22:22:23.531 Desktop video mode: 1600x900 60.0024 Hz
2010-05-17 22:22:23.542 MythUI Image Cache size set to 20971520 bytes
2010-05-17 22:22:23.557 Enabled verbose msgs:  important general
2010-05-17 22:22:23.560 Primary screen: 0.
2010-05-17 22:22:23.561 Using screen 0, 1600x900 at 0,0
2010-05-17 22:22:23.561 Using theme base resolution of 1280x720
2010-05-17 22:22:23.565 LIRC: Successfully initialized '/dev/lircd' using '/home/thor999/.mythtv/lircrc' config
2010-05-17 22:22:23.565 JoystickMenuThread Error: Joystick disabled - Failed to read /home/thor999/.mythtv/joystickmenurc
2010-05-17 22:22:23.592 Using Frameless Window
2010-05-17 22:22:23.592 Using Full Screen Window
2010-05-17 22:22:23.800 Using the Qt painter
2010-05-17 22:22:23.877 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-05-17 22:22:23.884 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-05-17 22:22:23.892 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-05-17 22:22:23.892 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-05-17 22:22:23.899 Current MythTV Schema Version (DBSchemaVer): 1254
2010-05-17 22:22:24.186 Registering Internal as a media playback plugin.
2010-05-17 22:22:24.200 Cannot load language en_us for module mytharchive
2010-05-17 22:22:24.218 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.218 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.218 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.219 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.219 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.220 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.221 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.221 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.221 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.222 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.222 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.222 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.223 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.223 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.223 MediaMonitorUnix::AddDevice() - empty device path.
2010-05-17 22:22:24.224 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-05-17 22:22:24.224 Cannot load language en_us for module mythgallery
2010-05-17 22:22:24.226 Cannot load language en_us for module mythmovies
2010-05-17 22:22:24.242 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-05-17 22:22:24.265 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-05-17 22:22:24.268 Cannot load language en_us for module mythmusic
2010-05-17 22:22:24.274 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-05-17 22:22:24.291 Cannot load language en_us for module mythvideo
2010-05-17 22:22:24.297 Cannot load language en_us for module mythweather
2010-05-17 22:22:24.299 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-05-17 22:22:24.343 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-05-17 22:22:24.345 Found mainmenu.xml for theme 'Mythbuntu'
2010-05-17 22:22:24.825 MythContext: Connecting to backend server: 192.168.1.7:6543 (try 1 of 1)
2010-05-17 22:22:24.826 Using protocol version 56
TIA and FWIW somewhat of a newb here.

---

### Post by thor999 on 2010-05-18
Oh BTW this problem is intermittent, I am sometimes able to watch livetv, but while changing channels, I often get a strange error: the last channel shifts to the bottom of the screen, and "freezes", the new channel takes up the top left 50% of the screen, and the top right is a pattern of ugly green lines.

---

### Post by trevs.bronco on 2010-05-18
I came across the solution, or is it a work around, to yo firs issue which is to restart the backend. it appears there are a few people having ths issue. th second issue I haven't come accros yet, but tha is probably because I haven't watched much TV as I have the same show displayed twice on my screen, one above the other.

Trev

---

### Post by thor999 on 2010-05-19
I think we're solved, will do some more testing tonight on both i386 and amd64 builds to make sure. Check this thread, post # 3 did it for me.   [http://ubuntuforums.org/showthread.php?t=1481488](http://ubuntuforums.org/showthread.php?t=1481488)

---

