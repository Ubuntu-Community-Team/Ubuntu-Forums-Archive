---
title: "unable to play AVI (DV format) in mythvideo"
date: 2011-05-21
forum: Mythbuntu
---

### Post by domv on 2011-05-21
hello

I am trying to read AVI file in mythvideo but when I select the file, mythvideo exits and restart (16:47:38.665 in the log).

This file is from a DV camcorder and was not compressed (DV format) nor copyprotected. I set access rights to 777 for this file
No problem with VLC or dragonplayer

I am running myth 0.24 with KUBUNTU 11.04
I do not have TV tuner and remote  to date as I am testing video, music, pictures, DvD functionalities (this explains errors in the log)

I can play DVD with mythvideo as i have installed libdvcss2 (don't think that helps)

Any idea about what is missing in my setup ?

here the frontend log
```
Starting mythfrontend.real..
2011-05-21 16:47:32.161 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org]("http://www.mythtv.org")
2011-05-21 16:47:32.161 Using runtime prefix = /usr
2011-05-21 16:47:32.161 Using configuration directory = /home/domi/.mythtv
2011-05-21 16:47:32.162 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-05-21 16:47:32.740 Empty LocalHostName.
2011-05-21 16:47:32.741 Using localhost value of salon
2011-05-21 16:47:32.746 New DB connection, total: 1
2011-05-21 16:47:32.748 Connected to database 'mythconverg' at host: localhost
2011-05-21 16:47:32.753 Closing DB connection named 'DBManager0'
2011-05-21 16:47:32.754 Connected to database 'mythconverg' at host: localhost
2011-05-21 16:47:32.754 Current locale fr_FR
2011-05-21 16:47:32.755 Reading locale defaults from /usr/share/mythtv//locales/fr_fr.xml
2011-05-21 16:47:32.962 DPMS is disabled.
2011-05-21 16:47:32.979 Desktop video mode: 1280x1024 60.020 Hz
2011-05-21 16:47:33.149 Enabled verbose msgs:  important general
2011-05-21 16:47:33.151 Loading fr translation for module mythfrontend
2011-05-21 16:47:33.158 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: Aucun fichier ou dossier de ce type (2)
2011-05-21 16:47:33.158 JoystickMenuThread: Joystick disabled - Failed to read /home/domi/.mythtv/joystickmenurc
2011-05-21 16:47:33.187 Using Frameless Window
2011-05-21 16:47:33.188 Using Full Screen Window
2011-05-21 16:47:33.272 Using the Qt painter
2011-05-21 16:47:33.303 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 6
            Name: 'basesmall'    Type: 'fontdef'
2011-05-21 16:47:33.306 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 12
            Name: 'basesmaller'    Type: 'fontdef'
2011-05-21 16:47:33.306 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 16
            Name: 'basesmallbold'    Type: 'fontdef'
2011-05-21 16:47:33.306 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 20
            Name: 'basesmallboldblue'    Type: 'fontdef'
2011-05-21 16:47:33.306 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 24
            Name: 'basesmallboldgrey'    Type: 'fontdef'
2011-05-21 16:47:33.306 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 28
            Name: 'basesmallboldgreyhighlight'    Type: 'fontdef'
2011-05-21 16:47:33.307 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 32
            Name: 'small'    Type: 'fontdef'
2011-05-21 16:47:33.309 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 38
            Name: 'basemedium'    Type: 'fontdef'
2011-05-21 16:47:33.312 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 42
            Name: 'baselarge'    Type: 'fontdef'
2011-05-21 16:47:33.315 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 50
            Name: 'baselargenormal'    Type: 'fontdef'
2011-05-21 16:47:33.318 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 54
            Name: 'baseextralarge'    Type: 'fontdef'
2011-05-21 16:47:33.318 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 63
            Name: 'basesmallwhite'    Type: 'fontdef'
2011-05-21 16:47:33.318 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 67
            Name: 'basesmalllightgrey'    Type: 'fontdef'
2011-05-21 16:47:33.318 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 71
            Name: 'basesmallgrey'    Type: 'fontdef'
2011-05-21 16:47:33.318 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 75
            Name: 'basesmallpurple'    Type: 'fontdef'
2011-05-21 16:47:33.318 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 79
            Name: 'basesmallblack'    Type: 'fontdef'
2011-05-21 16:47:33.318 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 83
            Name: 'basesmallyellow'    Type: 'fontdef'
2011-05-21 16:47:33.318 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 87
            Name: 'basesmallgreen'    Type: 'fontdef'
2011-05-21 16:47:33.318 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 91
            Name: 'basesmallblue'    Type: 'fontdef'
2011-05-21 16:47:33.318 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 95
            Name: 'basesmallred'    Type: 'fontdef'
2011-05-21 16:47:33.319 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 99
            Name: 'basemediumwhite'    Type: 'fontdef'
2011-05-21 16:47:33.319 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 103
            Name: 'basemediumlightgrey'    Type: 'fontdef'
2011-05-21 16:47:33.319 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 107
            Name: 'basemediumgrey'    Type: 'fontdef'
2011-05-21 16:47:33.319 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 111
            Name: 'basemediumgreen'    Type: 'fontdef'
2011-05-21 16:47:33.319 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 115
            Name: 'basemediumred'    Type: 'fontdef'
2011-05-21 16:47:33.319 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 119
            Name: 'basemediumyellow'    Type: 'fontdef'
2011-05-21 16:47:33.403 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'small'    Type: 'fontdef'
2011-05-21 16:47:33.407 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1013
            Name: 'medium'    Type: 'fontdef'
2011-05-21 16:47:33.413 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1019
            Name: 'large'    Type: 'fontdef'
2011-05-21 16:47:33.419 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1025
            Name: 'clock'    Type: 'fontdef'
2011-05-21 16:47:33.425 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/default/base.xml @ 11
            Name: 'basetiny'    Type: 'fontdef'
2011-05-21 16:47:33.425 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/default/base.xml @ 36
            Name: 'basetinyred'    Type: 'fontdef'
2011-05-21 16:47:33.428 New DB connection, total: 2
2011-05-21 16:47:33.429 Connected to database 'mythconverg' at host: localhost
2011-05-21 16:47:33.429 Current MythTV Schema Version (DBSchemaVer): 1264
2011-05-21 16:47:33.491 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-05-21 16:47:33.491 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-05-21 16:47:33.492 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-05-21 16:47:33.492 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-05-21 16:47:33.631 Registering Internal as a media playback plugin.
2011-05-21 16:47:33.645 Loading fr translation for module mytharchive
2011-05-21 16:47:33.648 Registering WebBrowser as a media playback plugin.
2011-05-21 16:47:33.648 Loading fr translation for module mythbrowser
2011-05-21 16:47:33.665 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-21 16:47:33.665 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-21 16:47:33.666 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-21 16:47:33.666 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-05-21 16:47:33.666 Loading fr translation for module mythgallery
2011-05-21 16:47:33.672 Loading fr translation for module mythgame
2011-05-21 16:47:33.683 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-05-21 16:47:33.703 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-05-21 16:47:33.706 Loading fr translation for module mythmusic
2011-05-21 16:47:33.709 Loading fr translation for module mythnetvision
2011-05-21 16:47:33.712 Loading fr translation for module mythnews
2011-05-21 16:47:33.716 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-05-21 16:47:33.727 Loading fr translation for module mythvideo
2011-05-21 16:47:33.731 Loading fr translation for module mythweather
2011-05-21 16:47:33.739 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 7
            Name: 'menufont'    Type: 'fontdef'
2011-05-21 16:47:33.743 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 16
            Name: 'clock'    Type: 'fontdef'
2011-05-21 16:47:34.014 Found mainmenu.xml for theme 'MythCenter'
2011-05-21 16:47:34.053 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-05-21 16:47:34.053 Using protocol version 63
2011-05-21 16:47:37.536 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@salon/video/)
2011-05-21 16:47:38.456 TV: Attempting to change from None to WatchingVideo
2011-05-21 16:47:38.587 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-05-21 16:47:38.587 AFD: Opened codec 0x7f0330311f20, id(DVVIDEO) type(Video)
2011-05-21 16:47:38.587 AFD: codec PCM_S16LE has 2 channels
2011-05-21 16:47:38.587 AFD: Opened codec 0x7f0330e586c0, id(PCM_S16LE) type(Audio)
2011-05-21 16:47:38.587 AFD: codec PCM_S16LE has 2 channels
2011-05-21 16:47:38.587 AFD: Opened codec 0x7f0330e58b20, id(PCM_S16LE) type(Audio)
2011-05-21 16:47:38.611 AO: Opening audio device 'default' ch 2(2) sr 32000 sf signed 16 bit reenc 0
2011-05-21 16:47:38.612 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2011-05-21 16:47:38.627 ALSA, Error: no playback control PCM found on mixer device default
2011-05-21 16:47:38.627 ALSA, Error: Unable to open audio mixer. Volume control disabled
2011-05-21 16:47:38.627 AudioPlayer: Enabling Audio
2011-05-21 16:47:38.641 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-05-21 16:47:38.665 OSD: Base theme size: 800x600
2011-05-21 16:47:38.665 OSD: Scaling factors: 0.9x0.96
Restarting mythfrontend.real...
2011-05-21 16:47:39.025 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org]("http://www.mythtv.org")
2011-05-21 16:47:39.025 Using runtime prefix = /usr
2011-05-21 16:47:39.025 Using configuration directory = /home/domi/.mythtv
2011-05-21 16:47:39.025 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-05-21 16:47:39.604 Empty LocalHostName.
2011-05-21 16:47:39.604 Using localhost value of salon
2011-05-21 16:47:39.609 New DB connection, total: 1
2011-05-21 16:47:39.611 Connected to database 'mythconverg' at host: localhost
2011-05-21 16:47:39.617 Closing DB connection named 'DBManager0'
2011-05-21 16:47:39.618 Connected to database 'mythconverg' at host: localhost
2011-05-21 16:47:39.618 Current locale fr_FR
2011-05-21 16:47:39.619 Reading locale defaults from /usr/share/mythtv//locales/fr_fr.xml
2011-05-21 16:47:39.834 DPMS is disabled.
2011-05-21 16:47:39.854 Desktop video mode: 1280x1024 60.020 Hz
2011-05-21 16:47:40.023 Enabled verbose msgs:  important general
2011-05-21 16:47:40.024 Loading fr translation for module mythfrontend
2011-05-21 16:47:40.029 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: Aucun fichier ou dossier de ce type (2)
2011-05-21 16:47:40.029 JoystickMenuThread: Joystick disabled - Failed to read /home/domi/.mythtv/joystickmenurc
2011-05-21 16:47:40.058 Using Frameless Window
2011-05-21 16:47:40.059 Using Full Screen Window
2011-05-21 16:47:40.129 Using the Qt painter
2011-05-21 16:47:40.160 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 6
            Name: 'basesmall'    Type: 'fontdef'
2011-05-21 16:47:40.164 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 12
            Name: 'basesmaller'    Type: 'fontdef'
2011-05-21 16:47:40.164 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 16
            Name: 'basesmallbold'    Type: 'fontdef'
2011-05-21 16:47:40.164 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 20
            Name: 'basesmallboldblue'    Type: 'fontdef'
2011-05-21 16:47:40.164 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 24
            Name: 'basesmallboldgrey'    Type: 'fontdef'
2011-05-21 16:47:40.164 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 28
            Name: 'basesmallboldgreyhighlight'    Type: 'fontdef'
2011-05-21 16:47:40.165 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 32
            Name: 'small'    Type: 'fontdef'
2011-05-21 16:47:40.168 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 38
            Name: 'basemedium'    Type: 'fontdef'
2011-05-21 16:47:40.171 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 42
            Name: 'baselarge'    Type: 'fontdef'
2011-05-21 16:47:40.174 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 50
            Name: 'baselargenormal'    Type: 'fontdef'
2011-05-21 16:47:40.176 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 54
            Name: 'baseextralarge'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 63
            Name: 'basesmallwhite'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 67
            Name: 'basesmalllightgrey'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 71
            Name: 'basesmallgrey'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 75
            Name: 'basesmallpurple'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 79
            Name: 'basesmallblack'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 83
            Name: 'basesmallyellow'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 87
            Name: 'basesmallgreen'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 91
            Name: 'basesmallblue'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 95
            Name: 'basesmallred'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 99
            Name: 'basemediumwhite'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 103
            Name: 'basemediumlightgrey'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 107
            Name: 'basemediumgrey'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 111
            Name: 'basemediumgreen'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 115
            Name: 'basemediumred'    Type: 'fontdef'
2011-05-21 16:47:40.177 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 119
            Name: 'basemediumyellow'    Type: 'fontdef'
2011-05-21 16:47:40.266 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'small'    Type: 'fontdef'
2011-05-21 16:47:40.270 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1013
            Name: 'medium'    Type: 'fontdef'
2011-05-21 16:47:40.275 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1019
            Name: 'large'    Type: 'fontdef'
2011-05-21 16:47:40.279 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1025
            Name: 'clock'    Type: 'fontdef'
2011-05-21 16:47:40.285 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/default/base.xml @ 11
            Name: 'basetiny'    Type: 'fontdef'
2011-05-21 16:47:40.285 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/default/base.xml @ 36
            Name: 'basetinyred'    Type: 'fontdef'
2011-05-21 16:47:40.288 New DB connection, total: 2
2011-05-21 16:47:40.288 New DB connection, total: 3
2011-05-21 16:47:40.288 Connected to database 'mythconverg' at host: localhost
2011-05-21 16:47:40.288 Connected to database 'mythconverg' at host: localhost
2011-05-21 16:47:40.288 New DB connection, total: 4
2011-05-21 16:47:40.288 Connected to database 'mythconverg' at host: localhost
2011-05-21 16:47:40.288 Current MythTV Schema Version (DBSchemaVer): 1264
2011-05-21 16:47:40.356 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-05-21 16:47:40.356 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-05-21 16:47:40.357 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-05-21 16:47:40.357 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-05-21 16:47:40.512 Registering Internal as a media playback plugin.
2011-05-21 16:47:40.526 Loading fr translation for module mytharchive
2011-05-21 16:47:40.530 Registering WebBrowser as a media playback plugin.
2011-05-21 16:47:40.530 Loading fr translation for module mythbrowser
2011-05-21 16:47:40.548 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-21 16:47:40.548 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-21 16:47:40.549 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-21 16:47:40.549 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-05-21 16:47:40.549 Loading fr translation for module mythgallery
2011-05-21 16:47:40.555 Loading fr translation for module mythgame
2011-05-21 16:47:40.567 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-05-21 16:47:40.593 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-05-21 16:47:40.596 Loading fr translation for module mythmusic
2011-05-21 16:47:40.598 Loading fr translation for module mythnetvision
2011-05-21 16:47:40.602 Loading fr translation for module mythnews
2011-05-21 16:47:40.606 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-05-21 16:47:40.618 Loading fr translation for module mythvideo
2011-05-21 16:47:40.622 Loading fr translation for module mythweather
2011-05-21 16:47:40.630 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 7
            Name: 'menufont'    Type: 'fontdef'
2011-05-21 16:47:40.633 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 16
            Name: 'clock'    Type: 'fontdef'
2011-05-21 16:47:40.935 Found mainmenu.xml for theme 'MythCenter'
2011-05-21 16:47:40.980 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-05-21 16:47:40.981 Using protocol version 63
2011-05-21 16:47:47.601 Deleting UPnP client...
Error in my_thread_global_end(): 3 threads didn't exit

```here jamu log about the AVI file:
! Warning: Skipping "corse'20070723 14 08 45" as there is no TMDB or IMDB number for this movie.
Use interactive option (-I) or (-R) to select the TMDB or IMDB number.


Thanks for any help

---

### Post by domv on 2011-05-22
Previous message was with mytvideo set to Internal player.
I tried also with mplayer but I had same result, but mytfront end did not crash with mplayer. Nothing happened


```

Starting mythfrontend.real..
2011-05-22 22:06:11.808 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] www.mythtv.org
2011-05-22 22:06:11.808 Using runtime prefix = /usr
2011-05-22 22:06:11.808 Using configuration directory = /home/domi/.mythtv
2011-05-22 22:06:11.809 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-05-22 22:06:12.388 Empty LocalHostName.
2011-05-22 22:06:12.388 Using localhost value of salon
2011-05-22 22:06:12.393 New DB connection, total: 1
2011-05-22 22:06:12.396 Connected to database 'mythconverg' at host: localhost
2011-05-22 22:06:12.401 Closing DB connection named 'DBManager0'
2011-05-22 22:06:12.402 Connected to database 'mythconverg' at host: localhost
2011-05-22 22:06:12.403 Current locale fr_FR
2011-05-22 22:06:12.403 Reading locale defaults from /usr/share/mythtv//locales/fr_fr.xml
2011-05-22 22:06:12.615 DPMS is active.
2011-05-22 22:06:12.636 Desktop video mode: 1280x1024 60.020 Hz
2011-05-22 22:06:12.802 Enabled verbose msgs:  important general
2011-05-22 22:06:12.806 Loading fr translation for module mythfrontend
2011-05-22 22:06:12.814 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: Aucun fichier ou dossier de ce type (2)
2011-05-22 22:06:12.815 JoystickMenuThread: Joystick disabled - Failed to read /home/domi/.mythtv/joystickmenurc
2011-05-22 22:06:12.850 Using Frameless Window
2011-05-22 22:06:12.850 Using Full Screen Window
2011-05-22 22:06:12.927 Using the Qt painter
2011-05-22 22:06:12.954 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 6
            Name: 'basesmall'    Type: 'fontdef'
2011-05-22 22:06:12.957 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 12
            Name: 'basesmaller'    Type: 'fontdef'
2011-05-22 22:06:12.957 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 16
            Name: 'basesmallbold'    Type: 'fontdef'
2011-05-22 22:06:12.957 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 20
            Name: 'basesmallboldblue'    Type: 'fontdef'
2011-05-22 22:06:12.957 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 24
            Name: 'basesmallboldgrey'    Type: 'fontdef'
2011-05-22 22:06:12.957 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 28
            Name: 'basesmallboldgreyhighlight'    Type: 'fontdef'
2011-05-22 22:06:12.957 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 32
            Name: 'small'    Type: 'fontdef'
2011-05-22 22:06:12.960 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 38
            Name: 'basemedium'    Type: 'fontdef'
2011-05-22 22:06:12.963 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 42
            Name: 'baselarge'    Type: 'fontdef'
2011-05-22 22:06:12.966 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 50
            Name: 'baselargenormal'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 54
            Name: 'baseextralarge'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 63
            Name: 'basesmallwhite'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 67
            Name: 'basesmalllightgrey'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 71
            Name: 'basesmallgrey'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 75
            Name: 'basesmallpurple'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 79
            Name: 'basesmallblack'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 83
            Name: 'basesmallyellow'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 87
            Name: 'basesmallgreen'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 91
            Name: 'basesmallblue'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 95
            Name: 'basesmallred'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 99
            Name: 'basemediumwhite'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 103
            Name: 'basemediumlightgrey'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 107
            Name: 'basemediumgrey'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 111
            Name: 'basemediumgreen'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 115
            Name: 'basemediumred'    Type: 'fontdef'
2011-05-22 22:06:12.969 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 119
            Name: 'basemediumyellow'    Type: 'fontdef'
2011-05-22 22:06:13.136 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'small'    Type: 'fontdef'
2011-05-22 22:06:13.141 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1013
            Name: 'medium'    Type: 'fontdef'
2011-05-22 22:06:13.145 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1019
            Name: 'large'    Type: 'fontdef'
2011-05-22 22:06:13.149 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1025
            Name: 'clock'    Type: 'fontdef'
2011-05-22 22:06:13.155 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/default/base.xml @ 11
            Name: 'basetiny'    Type: 'fontdef'
2011-05-22 22:06:13.155 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/default/base.xml @ 36
            Name: 'basetinyred'    Type: 'fontdef'
2011-05-22 22:06:13.157 New DB connection, total: 2
2011-05-22 22:06:13.158 New DB connection, total: 3
2011-05-22 22:06:13.158 Current MythTV Schema Version (DBSchemaVer): 1264
2011-05-22 22:06:13.158 Connected to database 'mythconverg' at host: localhost
2011-05-22 22:06:13.159 Connected to database 'mythconverg' at host: localhost
2011-05-22 22:06:13.296 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-05-22 22:06:13.296 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-05-22 22:06:13.299 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-05-22 22:06:13.299 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-05-22 22:06:13.481 Registering Internal as a media playback plugin.
2011-05-22 22:06:13.504 Loading fr translation for module mytharchive
2011-05-22 22:06:13.509 Registering WebBrowser as a media playback plugin.
2011-05-22 22:06:13.510 Loading fr translation for module mythbrowser
2011-05-22 22:06:13.536 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-22 22:06:13.536 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-22 22:06:13.536 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-22 22:06:13.537 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-05-22 22:06:13.537 Loading fr translation for module mythgallery
2011-05-22 22:06:13.550 Loading fr translation for module mythgame
2011-05-22 22:06:13.582 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-05-22 22:06:13.612 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-05-22 22:06:13.617 Loading fr translation for module mythmusic
2011-05-22 22:06:13.621 Loading fr translation for module mythnetvision
2011-05-22 22:06:13.626 Loading fr translation for module mythnews
2011-05-22 22:06:13.636 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-05-22 22:06:13.655 Loading fr translation for module mythvideo
2011-05-22 22:06:13.664 Loading fr translation for module mythweather
2011-05-22 22:06:13.672 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 7
            Name: 'menufont'    Type: 'fontdef'
2011-05-22 22:06:13.677 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 16
            Name: 'clock'    Type: 'fontdef'
2011-05-22 22:06:14.041 Found mainmenu.xml for theme 'MythCenter'
2011-05-22 22:06:14.094 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-05-22 22:06:14.094 Using protocol version 63
2011-05-22 22:06:30.930 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 7
            Name: 'menufont'    Type: 'fontdef'
2011-05-22 22:06:30.930 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 16
            Name: 'clock'    Type: 'fontdef'
2011-05-22 22:07:14.281 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@salon/video/)
2011-05-22 22:07:17.501 Locking input devices
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing myth://Videos@127.0.0.1:6543/corse'20070723 14.08.45.avi.
No stream found to handle url myth://Videos@127.0.0.1:6543/corse'20070723 14.08.45.avi


Exiting... (End of file)
2011-05-22 22:07:17.674 Unlocking input devices
2011-05-22 22:07:23.412 Locking input devices
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing myth://Videos@127.0.0.1:6543/corse'20070723 14.08.45.avi.
No stream found to handle url myth://Videos@127.0.0.1:6543/corse'20070723 14.08.45.avi


Exiting... (End of file)
2011-05-22 22:07:23.479 Unlocking input devices
2011-05-22 22:07:30.688 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit


```any idea ?

---

