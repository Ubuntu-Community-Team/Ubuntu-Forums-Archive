---
title: "Issue with adding videos"
date: 2010-12-19
forum: Mythbuntu
---

### Post by steeleweb on 2010-12-19
I have set my box up as a standalone server.

I am trying to add video in the avi format however I have been unable to.

I have copied my avi files to the /var/lib/mythtv/video location but still unable to see videos.

Suggestions please.

---

### Post by thatguruguy on 2010-12-19
Once in mythvideo (click on "Media Library", then "Watch Videos"), simply click the "M" key to pull up a menu, and then select "Scan for Changes".

---

### Post by steeleweb on 2010-12-19
Thanks,  that helped however unable to play. Not sure of the issue on that.  These are avi files.  I will try another one to see if it reacts the same way.

---

### Post by steeleweb on 2010-12-19
Still no luck on playing the avi files is there something that I could check on for this issue.

---

### Post by newlinux on 2010-12-19
what error do you get? you may need to look in your frontend logs. do other files in mythvideo play?

---

### Post by steeleweb on 2010-12-19
There is no error, when I click to play it is just waiting then it comes back to the selection again for me to hit play.


Sorry if I have to ask how do you check the frontend logs and is there anything I should be looking for.

---

### Post by thatguruguy on 2010-12-19
Do the videos play in vlc?

Your log should be located at /var/log/mythtv/mythfrontend.log

---

### Post by steeleweb on 2010-12-19
Yes I can play them in vlc.


Here is the log:

Starting mythfrontend.real..
2010-12-04 12:50:12.689 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-04 12:50:12.690 Using runtime prefix = /usr
2010-12-04 12:50:12.690 Using configuration directory = /home/steeleweb/.mythtv
2010-12-04 12:50:13.281 Empty LocalHostName.
2010-12-04 12:50:13.281 Using localhost value of steeleweb
2010-12-04 12:50:13.293 New DB connection, total: 1
2010-12-04 12:50:13.301 Connected to database 'mythconverg' at host: localhost
2010-12-04 12:50:13.302 Closing DB connection named 'DBManager0'
2010-12-04 12:50:13.473 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-04 12:50:13.474 DPMS is disabled.
2010-12-04 12:50:13.646 Primary screen: 0.
2010-12-04 12:50:13.647 Connected to database 'mythconverg' at host: localhost
2010-12-04 12:50:13.649 Using screen 0, 1280x960 at 0,0
2010-12-04 12:50:13.756 Desktop video mode: 1280x960 60.0024 Hz
2010-12-04 12:50:13.772 MythUI Image Cache size set to 20971520 bytes
2010-12-04 12:50:14.111 Enabled verbose msgs:  important general
2010-12-04 12:50:14.316 Primary screen: 0.
2010-12-04 12:50:14.317 Using screen 0, 1280x960 at 0,0
2010-12-04 12:50:14.439 Using theme base resolution of 1280x720
2010-12-04 12:50:14.474 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-04 12:50:14.474 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-04 12:50:14.563 Using Frameless Window
2010-12-04 12:50:14.563 Using Full Screen Window
2010-12-04 12:50:16.204 Using the Qt painter
2010-12-04 12:50:16.966 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-12-04 12:50:17.045 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-12-04 12:50:17.158 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-04 12:50:17.158 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-12-04 12:50:17.164 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-04 12:50:17.288 New DB connection, total: 2
2010-12-04 12:50:17.299 Connected to database 'mythconverg' at host: localhost
2010-12-04 12:50:19.310 Writing settings file /home/steeleweb/.mythtv/mysql.txt
2010-12-04 12:50:19.311 Closing DB connection named 'DBManager1'
2010-12-04 12:50:19.311 Closing DB connection named 'DBManager0'
2010-12-04 12:50:19.312 Connected to database 'mythconverg' at host: localhost
2010-12-04 12:50:19.313 Connected to database 'mythconverg' at host: localhost
2010-12-04 12:50:19.619 Registering Internal as a media playback plugin.
2010-12-04 12:50:19.775 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-04 12:50:19.779 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-04 12:50:19.780 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-04 12:50:19.780 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-04 12:50:19.780 Cannot load language en_us for module mythgallery
2010-12-04 12:50:19.807 Cannot load language en_us for module mythmovies
2010-12-04 12:50:20.251 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-04 12:50:20.356 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-04 12:50:20.363 Cannot load language en_us for module mythmusic
2010-12-04 12:50:20.455 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-04 12:50:20.502 Cannot load language en_us for module mythvideo
2010-12-04 12:50:20.519 Cannot load language en_us for module mythweather
2010-12-04 12:50:20.522 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-12-04 12:50:20.632 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-04 12:50:20.634 Found mainmenu.xml for theme 'Mythbuntu'
2010-12-04 12:50:31.159 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-04 12:50:31.161 Using protocol version 23056
2010-12-04 12:50:44.209 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-12-04 12:50:46.616 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-12-04 12:50:55.960 Received a remote 'Clear Cache' request
2010-12-04 12:50:56.018 Primary screen: 0.
2010-12-04 12:50:56.018 Using screen 0, 1280x960 at 0,0
2010-12-04 12:50:56.020 Using theme base resolution of 800x600
2010-12-04 12:50:56.046 Using Frameless Window
2010-12-04 12:50:56.046 Using Full Screen Window
2010-12-04 12:50:56.278 Using the Qt painter
2010-12-04 12:50:56.289 Removing stale cache dir: /home/steeleweb/.mythtv/themecache/Mythbuntu.1280.960
2010-12-04 12:50:56.331 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-04 12:50:56.334 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-04 12:50:56.334 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-04 12:50:56.335 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-04 12:50:56.335 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-04 12:50:56.335 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-04 12:50:56.335 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-04 12:50:56.338 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-04 12:50:56.342 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-04 12:50:56.345 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-04 12:50:56.349 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-04 12:50:56.349 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-04 12:50:56.349 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-04 12:50:56.349 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-04 12:50:56.349 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-04 12:50:56.349 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-04 12:50:56.350 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-04 12:50:56.350 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-04 12:50:56.350 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-04 12:50:56.350 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-04 12:50:56.350 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-04 12:50:56.350 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-04 12:50:56.350 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-04 12:50:56.350 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-04 12:50:56.350 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-04 12:50:56.350 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-04 12:50:56.399 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-04 12:50:56.409 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-04 12:50:56.422 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-04 12:50:56.431 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-04 12:50:56.432 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-04 12:50:56.446 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-04 12:50:57.982 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-04 12:50:57.999 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-04 12:50:58.003 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-04 12:50:58.070 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-04 12:50:58.071 Found mainmenu.xml for theme 'MythCenter'
2010-12-04 12:51:16.175 Deleting UPnP client...
Starting mythfrontend.real..
2010-12-04 13:00:43.031 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-04 13:00:43.031 Using runtime prefix = /usr
2010-12-04 13:00:43.031 Using configuration directory = /home/steeleweb/.mythtv
2010-12-04 13:00:43.957 Empty LocalHostName.
2010-12-04 13:00:43.957 Using localhost value of steeleweb
2010-12-04 13:00:43.962 New DB connection, total: 1
2010-12-04 13:00:43.966 Connected to database 'mythconverg' at host: localhost
2010-12-04 13:00:43.967 Closing DB connection named 'DBManager0'
2010-12-04 13:00:43.979 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-04 13:00:43.980 DPMS is disabled.
2010-12-04 13:00:43.982 Primary screen: 0.
2010-12-04 13:00:43.983 Connected to database 'mythconverg' at host: localhost
2010-12-04 13:00:43.984 Using screen 0, 1280x960 at 0,0
2010-12-04 13:00:43.996 Desktop video mode: 1280x960 60.0024 Hz
2010-12-04 13:00:44.012 MythUI Image Cache size set to 20971520 bytes
2010-12-04 13:00:44.028 Enabled verbose msgs:  important general
2010-12-04 13:00:44.034 Primary screen: 0.
2010-12-04 13:00:44.036 Using screen 0, 1280x960 at 0,0
2010-12-04 13:00:44.037 Using theme base resolution of 800x600
2010-12-04 13:00:44.041 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-04 13:00:44.041 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-04 13:00:44.070 Using Frameless Window
2010-12-04 13:00:44.070 Using Full Screen Window
2010-12-04 13:00:44.297 Using the Qt painter
2010-12-04 13:00:44.336 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-04 13:00:44.339 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-04 13:00:44.340 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-04 13:00:44.340 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-04 13:00:44.340 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-04 13:00:44.340 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-04 13:00:44.340 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-04 13:00:44.348 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-04 13:00:44.356 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-04 13:00:44.363 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-04 13:00:44.371 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-04 13:00:44.371 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-04 13:00:44.372 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-04 13:00:44.372 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-04 13:00:44.372 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-04 13:00:44.372 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-04 13:00:44.372 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-04 13:00:44.372 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-04 13:00:44.372 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-04 13:00:44.372 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-04 13:00:44.372 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-04 13:00:44.372 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-04 13:00:44.373 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-04 13:00:44.373 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-04 13:00:44.373 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-04 13:00:44.373 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-04 13:00:44.501 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-04 13:00:44.520 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-04 13:00:44.525 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-04 13:00:44.536 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-04 13:00:44.538 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-04 13:00:44.552 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-04 13:00:44.564 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-04 13:00:44.567 New DB connection, total: 2
2010-12-04 13:00:44.572 Connected to database 'mythconverg' at host: localhost
2010-12-04 13:00:45.118 Registering Internal as a media playback plugin.
2010-12-04 13:00:45.145 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-04 13:00:45.145 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-04 13:00:45.145 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-04 13:00:45.146 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-04 13:00:45.146 Cannot load language en_us for module mythgallery
2010-12-04 13:00:45.149 Cannot load language en_us for module mythmovies
2010-12-04 13:00:45.163 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-04 13:00:45.203 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-04 13:00:45.210 Cannot load language en_us for module mythmusic
2010-12-04 13:00:45.217 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-04 13:00:45.244 Cannot load language en_us for module mythvideo
2010-12-04 13:00:45.251 Cannot load language en_us for module mythweather
2010-12-04 13:00:45.253 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-04 13:00:45.261 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-04 13:00:45.264 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-04 13:00:45.359 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-04 13:00:45.365 Found mainmenu.xml for theme 'MythCenter'
2010-12-04 13:00:45.921 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-04 13:00:45.928 Using protocol version 23056
2010-12-04 13:00:49.495 TV: Attempting to change from None to WatchingLiveTV
2010-12-04 13:00:49.495 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-04 13:00:49.499 Using protocol version 23056
2010-12-04 13:00:49.587 Spawning LiveTV Recorder -- begin
2010-12-04 13:00:49.903 Spawning LiveTV Recorder -- end
2010-12-04 13:00:49.904 GetEntryAt(-1) failed.
2010-12-04 13:00:49.924 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2010-12-04 13:00:49.924 TV Error: HandleStateChange(): LiveTV not successfully started
2010-12-04 13:00:49.926 We have a RingBuffer
2010-12-04 13:00:49.988 TV Error: LiveTV not successfully started
2010-12-04 13:01:00.188 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-12-04 13:01:02.143 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-12-04 13:01:08.512 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//media_settings.xml
2010-12-04 13:01:38.636 Received a remote 'Clear Cache' request
2010-12-04 13:01:47.947 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-04 13:27:58.154 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-04 13:27:58.155 Using runtime prefix = /usr
2010-12-04 13:27:58.155 Using configuration directory = /home/steeleweb/.mythtv
2010-12-04 13:27:58.765 Empty LocalHostName.
2010-12-04 13:27:58.766 Using localhost value of steeleweb
2010-12-04 13:27:58.771 New DB connection, total: 1
2010-12-04 13:27:58.778 Connected to database 'mythconverg' at host: localhost
2010-12-04 13:27:58.778 Closing DB connection named 'DBManager0'
2010-12-04 13:27:58.857 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-04 13:27:58.858 DPMS is disabled.
2010-12-04 13:27:58.930 Primary screen: 0.
2010-12-04 13:27:58.930 Connected to database 'mythconverg' at host: localhost
2010-12-04 13:27:58.932 Using screen 0, 1280x960 at 0,0
2010-12-04 13:27:59.048 Desktop video mode: 1280x960 60.0024 Hz
2010-12-04 13:27:59.202 MythUI Image Cache size set to 20971520 bytes
2010-12-04 13:27:59.250 Enabled verbose msgs:  important general
2010-12-04 13:27:59.282 Primary screen: 0.
2010-12-04 13:27:59.282 Using screen 0, 1280x960 at 0,0
2010-12-04 13:27:59.324 Using theme base resolution of 800x600
2010-12-04 13:27:59.329 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-04 13:27:59.329 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-04 13:27:59.410 Using Frameless Window
2010-12-04 13:27:59.410 Using Full Screen Window
2010-12-04 13:27:59.904 Using the Qt painter
2010-12-04 13:27:59.993 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-04 13:27:59.997 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-04 13:27:59.997 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-04 13:27:59.997 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-04 13:27:59.997 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-04 13:27:59.997 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-04 13:27:59.997 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-04 13:28:00.009 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-04 13:28:00.014 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-04 13:28:00.018 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-04 13:28:00.022 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-04 13:28:00.022 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-04 13:28:00.023 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-04 13:28:00.023 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-04 13:28:00.023 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-04 13:28:00.023 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-04 13:28:00.023 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-04 13:28:00.023 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-04 13:28:00.023 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-04 13:28:00.023 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-04 13:28:00.023 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-04 13:28:00.024 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-04 13:28:00.024 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-04 13:28:00.024 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-04 13:28:00.024 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-04 13:28:00.024 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-04 13:28:00.186 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-04 13:28:00.195 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-04 13:28:00.200 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-04 13:28:00.206 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-04 13:28:00.209 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-04 13:28:00.279 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-04 13:28:00.289 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-04 13:28:01.468 Registering Internal as a media playback plugin.
2010-12-04 13:28:01.550 Cannot load language en_us for module mytharchive
2010-12-04 13:28:01.561 Cannot load language en_us for module mythbrowser
2010-12-04 13:28:01.564 Registering WebBrowser as a media playback plugin.
2010-12-04 13:28:01.565 Cannot load language en_us for module mythbrowser
2010-12-04 13:28:01.609 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-04 13:28:01.609 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-04 13:28:01.610 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-04 13:28:01.610 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-04 13:28:01.611 Cannot load language en_us for module mythgallery
2010-12-04 13:28:01.638 Cannot load language en_us for module mythgame
2010-12-04 13:28:01.651 Cannot load language en_us for module mythmovies
2010-12-04 13:28:02.053 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-04 13:28:02.096 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-04 13:28:02.102 Cannot load language en_us for module mythmusic
2010-12-04 13:28:02.150 Cannot load language en_us for module mythnetvision
2010-12-04 13:28:02.170 Cannot load language en_us for module mythnews
2010-12-04 13:28:02.251 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-04 13:28:02.280 Cannot load language en_us for module mythvideo
2010-12-04 13:28:02.290 Cannot load language en_us for module mythweather
2010-12-04 13:28:02.293 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-04 13:28:02.314 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-04 13:28:02.318 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-04 13:28:02.431 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-04 13:28:02.433 Found mainmenu.xml for theme 'MythCenter'
2010-12-04 13:28:03.180 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-04 13:28:03.187 Using protocol version 23056
2010-12-04 13:28:07.130 TV: Attempting to change from None to WatchingLiveTV
2010-12-04 13:28:07.130 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-04 13:28:07.136 Using protocol version 23056
2010-12-04 13:28:07.232 Spawning LiveTV Recorder -- begin
2010-12-04 13:28:07.660 Spawning LiveTV Recorder -- end
2010-12-04 13:28:07.661 GetEntryAt(-1) failed.
2010-12-04 13:28:07.677 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2010-12-04 13:28:07.677 TV Error: HandleStateChange(): LiveTV not successfully started
2010-12-04 13:28:07.679 We have a RingBuffer
2010-12-04 13:28:07.735 TV Error: LiveTV not successfully started
2010-12-04 13:28:16.867 Deleting UPnP client...
Starting mythfrontend.real..
2010-12-18 15:45:04.024 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-18 15:45:04.025 Using runtime prefix = /usr
2010-12-18 15:45:04.025 Using configuration directory = /home/steeleweb/.mythtv
2010-12-18 15:45:04.034 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-18 15:45:04.034 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-18 15:45:04.035 Empty LocalHostName.
2010-12-18 15:45:04.035 Using localhost value of steeleweb
2010-12-18 15:45:04.054 New DB connection, total: 1
2010-12-18 15:45:04.066 Connected to database 'mythconverg' at host: localhost
2010-12-18 15:45:04.066 Closing DB connection named 'DBManager0'
2010-12-18 15:45:04.127 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-18 15:45:04.128 DPMS is disabled.
2010-12-18 15:45:04.130 Primary screen: 0.
2010-12-18 15:45:04.130 Connected to database 'mythconverg' at host: localhost
2010-12-18 15:45:04.132 Using screen 0, 1280x960 at 0,0
2010-12-18 15:45:04.150 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-18 15:45:04.188 Desktop video mode: 1280x960 60.0024 Hz
2010-12-18 15:45:04.237 MythUI Image Cache size set to 20971520 bytes
2010-12-18 15:45:04.315 Enabled verbose msgs:  important general
2010-12-18 15:45:04.325 Primary screen: 0.
2010-12-18 15:45:04.326 Using screen 0, 1280x960 at 0,0
2010-12-18 15:45:04.327 Using theme base resolution of 800x600
2010-12-18 15:45:04.349 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-18 15:45:04.350 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-18 15:45:04.521 Using Frameless Window
2010-12-18 15:45:04.521 Using Full Screen Window
2010-12-18 15:45:05.417 Using the Qt painter
2010-12-18 15:45:05.460 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-18 15:45:05.464 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-18 15:45:05.464 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-18 15:45:05.464 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-18 15:45:05.464 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-18 15:45:05.464 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-18 15:45:05.465 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-18 15:45:05.484 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-18 15:45:05.488 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-18 15:45:05.492 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-18 15:45:05.513 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-18 15:45:05.513 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-18 15:45:05.513 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-18 15:45:05.513 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-18 15:45:05.513 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-18 15:45:05.513 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-18 15:45:05.514 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-18 15:45:05.514 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-18 15:45:05.514 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-18 15:45:05.514 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-18 15:45:05.514 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-18 15:45:05.514 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-18 15:45:05.514 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-18 15:45:05.514 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-18 15:45:05.514 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-18 15:45:05.514 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-18 15:45:05.636 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-18 15:45:05.651 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-18 15:45:05.665 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-18 15:45:05.670 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-18 15:45:05.675 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-18 15:45:05.691 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-18 15:45:05.697 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-18 15:45:05.703 New DB connection, total: 2
2010-12-18 15:45:05.703 Connected to database 'mythconverg' at host: localhost
2010-12-18 15:45:06.380 Registering Internal as a media playback plugin.
2010-12-18 15:45:06.407 Cannot load language en_us for module mytharchive
2010-12-18 15:45:06.409 Cannot load language en_us for module mythbrowser
2010-12-18 15:45:06.413 Registering WebBrowser as a media playback plugin.
2010-12-18 15:45:06.413 Cannot load language en_us for module mythbrowser
2010-12-18 15:45:06.443 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-18 15:45:06.443 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-18 15:45:06.443 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-18 15:45:06.444 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-18 15:45:06.444 Cannot load language en_us for module mythgallery
2010-12-18 15:45:06.451 Cannot load language en_us for module mythgame
2010-12-18 15:45:06.454 Cannot load language en_us for module mythmovies
2010-12-18 15:45:06.468 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-18 15:45:06.517 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-18 15:45:06.524 Cannot load language en_us for module mythmusic
2010-12-18 15:45:06.531 Cannot load language en_us for module mythnetvision
2010-12-18 15:45:06.537 Cannot load language en_us for module mythnews
2010-12-18 15:45:06.544 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-18 15:45:06.574 Cannot load language en_us for module mythvideo
2010-12-18 15:45:06.582 Cannot load language en_us for module mythweather
2010-12-18 15:45:06.584 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-18 15:45:06.592 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-18 15:45:06.595 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-18 15:45:06.696 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-18 15:45:06.698 Found mainmenu.xml for theme 'MythCenter'
2010-12-18 15:45:07.276 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-18 15:45:07.278 Using protocol version 23056
2010-12-18 15:45:22.153 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-18 15:45:28.464 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-18 15:45:40.363 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/recordings-ui.xml
2010-12-18 15:45:40.478 PlaybackBox Error: SortedList is Empty
2010-12-18 15:45:40.806 PlaybackBox Error: SortedList is Empty
2010-12-18 15:45:50.448 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-12-18 15:45:52.957 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-12-18 15:46:00.849 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//media_settings.xml
2010-12-18 15:46:03.424 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-18 15:46:03.428 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-18 15:46:03.428 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-18 15:46:03.488 Loading menu theme from /usr/share/mythtv/video_settings.xml
2010-12-18 15:46:07.189 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-18 15:46:14.897 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-18 15:46:18.520 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-18 15:46:42.911 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-18 15:46:44.972 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-18 15:46:46.498 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/recordings-ui.xml
2010-12-18 15:46:46.578 PlaybackBox Error: SortedList is Empty
2010-12-18 15:46:46.680 PlaybackBox Error: SortedList is Empty
2010-12-18 15:46:53.571 Deleting UPnP client...
2010-12-18 15:46:53.572 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-18 23:50:08.214 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-18 23:50:08.214 Using runtime prefix = /usr
2010-12-18 23:50:08.215 Using configuration directory = /home/steeleweb/.mythtv
2010-12-18 23:50:08.216 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-18 23:50:08.217 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-18 23:50:08.217 Empty LocalHostName.
2010-12-18 23:50:08.218 Using localhost value of steeleweb
2010-12-18 23:50:08.224 New DB connection, total: 1
2010-12-18 23:50:08.227 Connected to database 'mythconverg' at host: localhost
2010-12-18 23:50:08.227 Closing DB connection named 'DBManager0'
2010-12-18 23:50:08.242 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-18 23:50:08.243 DPMS is disabled.
2010-12-18 23:50:08.244 Primary screen: 0.
2010-12-18 23:50:08.245 Connected to database 'mythconverg' at host: localhost
2010-12-18 23:50:08.247 Using screen 0, 1280x960 at 0,0
2010-12-18 23:50:08.258 Desktop video mode: 1280x960 60.0024 Hz
2010-12-18 23:50:08.273 MythUI Image Cache size set to 20971520 bytes
2010-12-18 23:50:08.288 Enabled verbose msgs:  important general
2010-12-18 23:50:08.294 Primary screen: 0.
2010-12-18 23:50:08.295 Using screen 0, 1280x960 at 0,0
2010-12-18 23:50:08.296 Using theme base resolution of 800x600
2010-12-18 23:50:08.300 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-18 23:50:08.300 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-18 23:50:08.323 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-18 23:50:08.330 Using Frameless Window
2010-12-18 23:50:08.330 Using Full Screen Window
2010-12-18 23:50:08.567 Using the Qt painter
2010-12-18 23:50:08.600 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-18 23:50:08.608 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-18 23:50:08.608 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-18 23:50:08.608 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-18 23:50:08.609 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-18 23:50:08.609 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-18 23:50:08.609 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-18 23:50:08.617 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-18 23:50:08.620 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-18 23:50:08.632 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-18 23:50:08.640 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-18 23:50:08.640 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-18 23:50:08.640 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-18 23:50:08.640 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-18 23:50:08.640 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-18 23:50:08.641 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-18 23:50:08.641 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-18 23:50:08.641 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-18 23:50:08.641 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-18 23:50:08.641 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-18 23:50:08.641 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-18 23:50:08.641 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-18 23:50:08.641 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-18 23:50:08.641 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-18 23:50:08.641 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-18 23:50:08.642 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-18 23:50:08.770 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-18 23:50:08.789 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-18 23:50:08.799 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-18 23:50:08.807 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-18 23:50:08.815 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-18 23:50:08.822 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-18 23:50:08.835 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-18 23:50:08.842 New DB connection, total: 2
2010-12-18 23:50:08.842 Connected to database 'mythconverg' at host: localhost
2010-12-18 23:50:09.401 Registering Internal as a media playback plugin.
2010-12-18 23:50:09.426 Cannot load language en_us for module mytharchive
2010-12-18 23:50:09.428 Cannot load language en_us for module mythbrowser
2010-12-18 23:50:09.432 Registering WebBrowser as a media playback plugin.
2010-12-18 23:50:09.432 Cannot load language en_us for module mythbrowser
2010-12-18 23:50:09.458 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-18 23:50:09.458 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-18 23:50:09.459 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-18 23:50:09.459 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-18 23:50:09.460 Cannot load language en_us for module mythgallery
2010-12-18 23:50:09.466 Cannot load language en_us for module mythgame
2010-12-18 23:50:09.469 Cannot load language en_us for module mythmovies
2010-12-18 23:50:09.483 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-18 23:50:09.525 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-18 23:50:09.532 Cannot load language en_us for module mythmusic
2010-12-18 23:50:09.539 Cannot load language en_us for module mythnetvision
2010-12-18 23:50:09.544 Cannot load language en_us for module mythnews
2010-12-18 23:50:09.551 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-18 23:50:09.579 Cannot load language en_us for module mythvideo
2010-12-18 23:50:09.586 Cannot load language en_us for module mythweather
2010-12-18 23:50:09.589 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-18 23:50:09.597 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-18 23:50:09.601 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-18 23:50:09.697 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-18 23:50:09.699 Found mainmenu.xml for theme 'MythCenter'
2010-12-18 23:50:10.265 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-18 23:50:10.266 Using protocol version 23056
2010-12-18 23:50:14.710 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-18 23:50:17.149 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-18 23:50:25.436 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-12-18 23:50:27.457 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-12-18 23:50:34.506 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//media_settings.xml
2010-12-18 23:50:36.071 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-18 23:50:36.074 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-18 23:50:36.075 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-18 23:50:36.110 Loading menu theme from /usr/share/mythtv/video_settings.xml
2010-12-18 23:51:03.135 Deleting UPnP client...
2010-12-18 23:51:03.136 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-18 23:55:50.686 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-18 23:55:50.686 Using runtime prefix = /usr
2010-12-18 23:55:50.686 Using configuration directory = /home/steeleweb/.mythtv
2010-12-18 23:55:50.707 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-18 23:55:50.708 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-18 23:55:50.712 Empty LocalHostName.
2010-12-18 23:55:50.712 Using localhost value of steeleweb
2010-12-18 23:55:50.779 New DB connection, total: 1
2010-12-18 23:55:50.809 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-18 23:55:50.924 Connected to database 'mythconverg' at host: localhost
2010-12-18 23:55:50.925 Closing DB connection named 'DBManager0'
2010-12-18 23:55:50.953 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-18 23:55:50.965 DPMS is disabled.
2010-12-18 23:55:50.967 Primary screen: 0.
2010-12-18 23:55:50.968 Connected to database 'mythconverg' at host: localhost
2010-12-18 23:55:51.013 Using screen 0, 1280x960 at 0,0
2010-12-18 23:55:51.058 Desktop video mode: 1280x960 60.0024 Hz
2010-12-18 23:55:51.072 MythUI Image Cache size set to 20971520 bytes
2010-12-18 23:55:51.146 Enabled verbose msgs:  important general
2010-12-18 23:55:51.208 Primary screen: 0.
2010-12-18 23:55:51.209 Using screen 0, 1280x960 at 0,0
2010-12-18 23:55:51.217 Using theme base resolution of 800x600
2010-12-18 23:55:51.222 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-18 23:55:51.222 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-18 23:55:51.251 Using Frameless Window
2010-12-18 23:55:51.252 Using Full Screen Window
2010-12-18 23:55:51.637 Using the Qt painter
2010-12-18 23:55:51.679 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-18 23:55:51.691 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-18 23:55:51.691 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-18 23:55:51.691 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-18 23:55:51.691 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-18 23:55:51.692 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-18 23:55:51.692 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-18 23:55:51.703 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-18 23:55:51.707 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-18 23:55:51.711 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-18 23:55:51.714 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-18 23:55:51.714 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-18 23:55:51.714 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-18 23:55:51.715 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-18 23:55:51.715 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-18 23:55:51.732 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-18 23:55:51.732 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-18 23:55:51.732 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-18 23:55:51.732 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-18 23:55:51.732 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-18 23:55:51.732 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-18 23:55:51.732 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-18 23:55:51.733 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-18 23:55:51.733 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-18 23:55:51.733 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-18 23:55:51.733 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-18 23:55:51.852 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-18 23:55:51.862 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-18 23:55:51.872 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-18 23:55:51.885 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-18 23:55:51.891 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-18 23:55:51.913 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-18 23:55:51.973 New DB connection, total: 2
2010-12-18 23:55:51.975 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-18 23:55:51.975 Connected to database 'mythconverg' at host: localhost
2010-12-18 23:55:52.748 Registering Internal as a media playback plugin.
2010-12-18 23:55:52.816 Cannot load language en_us for module mytharchive
2010-12-18 23:55:52.828 Cannot load language en_us for module mythbrowser
2010-12-18 23:55:52.832 Registering WebBrowser as a media playback plugin.
2010-12-18 23:55:52.832 Cannot load language en_us for module mythbrowser
2010-12-18 23:55:52.902 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-18 23:55:52.902 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-18 23:55:52.902 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-18 23:55:52.903 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-18 23:55:52.903 Cannot load language en_us for module mythgallery
2010-12-18 23:55:52.938 Cannot load language en_us for module mythgame
2010-12-18 23:55:52.952 Cannot load language en_us for module mythmovies
2010-12-18 23:55:53.247 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-18 23:55:53.287 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-18 23:55:53.294 Cannot load language en_us for module mythmusic
2010-12-18 23:55:53.322 Cannot load language en_us for module mythnetvision
2010-12-18 23:55:53.337 Cannot load language en_us for module mythnews
2010-12-18 23:55:53.386 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-18 23:55:53.413 Cannot load language en_us for module mythvideo
2010-12-18 23:55:53.422 Cannot load language en_us for module mythweather
2010-12-18 23:55:53.424 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-18 23:55:53.447 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-18 23:55:53.450 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-18 23:55:53.551 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-18 23:55:53.553 Found mainmenu.xml for theme 'MythCenter'
2010-12-18 23:55:54.191 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-18 23:55:54.192 Using protocol version 23056
2010-12-18 23:55:59.270 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-18 23:56:00.857 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-18 23:56:07.514 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/recordings-ui.xml
2010-12-18 23:56:07.682 PlaybackBox Error: SortedList is Empty
2010-12-18 23:56:07.759 PlaybackBox Error: SortedList is Empty
2010-12-18 23:56:17.309 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-18 23:56:20.702 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-12-18 23:56:22.768 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-12-18 23:56:25.711 Received a remote 'Clear Cache' request
2010-12-18 23:56:28.057 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//media_settings.xml
2010-12-18 23:56:29.351 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-18 23:56:29.355 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-18 23:56:29.355 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-18 23:56:29.401 Loading menu theme from /usr/share/mythtv/video_settings.xml
2010-12-18 23:56:40.855 Deleting UPnP client...
2010-12-18 23:56:40.856 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-18 23:58:03.554 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-18 23:58:03.554 Using runtime prefix = /usr
2010-12-18 23:58:03.554 Using configuration directory = /home/steeleweb/.mythtv
2010-12-18 23:58:03.582 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-18 23:58:03.582 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-18 23:58:03.585 Empty LocalHostName.
2010-12-18 23:58:03.586 Using localhost value of steeleweb
2010-12-18 23:58:03.653 New DB connection, total: 1
2010-12-18 23:58:03.678 Connected to database 'mythconverg' at host: localhost
2010-12-18 23:58:03.679 Closing DB connection named 'DBManager0'
2010-12-18 23:58:03.683 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-18 23:58:03.710 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-18 23:58:03.711 DPMS is disabled.
2010-12-18 23:58:03.713 Primary screen: 0.
2010-12-18 23:58:03.713 Connected to database 'mythconverg' at host: localhost
2010-12-18 23:58:03.715 Using screen 0, 1280x960 at 0,0
2010-12-18 23:58:03.761 Desktop video mode: 1280x960 60.0024 Hz
2010-12-18 23:58:03.775 MythUI Image Cache size set to 20971520 bytes
2010-12-18 23:58:03.829 Enabled verbose msgs:  important general
2010-12-18 23:58:03.865 Primary screen: 0.
2010-12-18 23:58:03.866 Using screen 0, 1280x960 at 0,0
2010-12-18 23:58:03.867 Using theme base resolution of 800x600
2010-12-18 23:58:03.884 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-18 23:58:03.884 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-18 23:58:03.913 Using Frameless Window
2010-12-18 23:58:03.913 Using Full Screen Window
2010-12-18 23:58:04.259 Using the Qt painter
2010-12-18 23:58:04.302 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-18 23:58:04.310 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-18 23:58:04.310 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-18 23:58:04.310 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-18 23:58:04.310 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-18 23:58:04.310 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-18 23:58:04.311 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-18 23:58:04.318 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-18 23:58:04.335 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-18 23:58:04.348 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-18 23:58:04.360 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-18 23:58:04.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-18 23:58:04.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-18 23:58:04.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-18 23:58:04.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-18 23:58:04.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-18 23:58:04.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-18 23:58:04.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-18 23:58:04.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-18 23:58:04.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-18 23:58:04.361 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-18 23:58:04.362 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-18 23:58:04.362 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-18 23:58:04.362 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-18 23:58:04.362 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-18 23:58:04.362 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-18 23:58:04.475 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-18 23:58:04.488 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-18 23:58:04.497 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-18 23:58:04.510 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-18 23:58:04.511 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-18 23:58:04.537 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-18 23:58:04.550 New DB connection, total: 2
2010-12-18 23:58:04.553 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-18 23:58:04.553 Connected to database 'mythconverg' at host: localhost
2010-12-18 23:58:05.229 Registering Internal as a media playback plugin.
2010-12-18 23:58:05.308 Cannot load language en_us for module mytharchive
2010-12-18 23:58:05.334 Cannot load language en_us for module mythbrowser
2010-12-18 23:58:05.337 Registering WebBrowser as a media playback plugin.
2010-12-18 23:58:05.338 Cannot load language en_us for module mythbrowser
2010-12-18 23:58:05.422 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-18 23:58:05.422 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-18 23:58:05.422 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-18 23:58:05.423 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-18 23:58:05.423 Cannot load language en_us for module mythgallery
2010-12-18 23:58:05.455 Cannot load language en_us for module mythgame
2010-12-18 23:58:05.501 Cannot load language en_us for module mythmovies
2010-12-18 23:58:05.745 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-18 23:58:05.784 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-18 23:58:05.790 Cannot load language en_us for module mythmusic
2010-12-18 23:58:05.855 Cannot load language en_us for module mythnetvision
2010-12-18 23:58:05.875 Cannot load language en_us for module mythnews
2010-12-18 23:58:05.933 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-18 23:58:05.959 Cannot load language en_us for module mythvideo
2010-12-18 23:58:05.968 Cannot load language en_us for module mythweather
2010-12-18 23:58:05.971 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-18 23:58:05.978 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-18 23:58:05.982 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-18 23:58:06.084 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-18 23:58:06.089 Found mainmenu.xml for theme 'MythCenter'
2010-12-18 23:58:06.729 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-18 23:58:06.730 Using protocol version 23056
2010-12-18 23:58:08.329 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-18 23:58:09.908 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-18 23:58:14.465 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/recordings-ui.xml
2010-12-18 23:58:14.624 PlaybackBox Error: SortedList is Empty
2010-12-18 23:58:14.705 PlaybackBox Error: SortedList is Empty
2010-12-18 23:58:22.689 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//manage_recordings.xml
2010-12-18 23:58:25.809 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//info_menu.xml
2010-12-18 23:58:31.844 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//optical_menu.xml
2010-12-18 23:58:43.639 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-18 23:58:43.642 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-18 23:58:43.643 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-18 23:58:43.703 Loading menu theme from /usr/share/mythtv/archivemenu.xml
2010-12-18 23:58:46.557 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/mythnative-ui.xml
2010-12-18 23:58:46.557 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default/mythnative-ui.xml
2010-12-18 23:59:47.924 Loading menu theme from /usr/share/mythtv/archiveutils.xml
2010-12-18 23:59:53.490 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-12-18 23:59:54.789 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-12-19 00:00:13.875 Received a remote 'Clear Cache' request
2010-12-19 00:00:16.788 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//media_settings.xml
2010-12-19 00:00:18.235 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-19 00:00:18.239 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-19 00:00:18.239 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-19 00:00:18.290 Loading menu theme from /usr/share/mythtv/video_settings.xml
2010-12-19 00:00:21.942 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 00:00:32.483 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 00:00:32.490 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default/video-ui.xml
2010-12-19 00:00:40.821 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 00:00:40.828 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default/video-ui.xml
2010-12-19 00:01:21.371 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default/keyboard/en_us_ui.xml'
2010-12-19 00:01:54.742 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-19 00:01:56.306 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 00:02:04.031 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/recordings-ui.xml
2010-12-19 00:02:04.053 PlaybackBox Error: SortedList is Empty
2010-12-19 00:02:04.154 PlaybackBox Error: SortedList is Empty
2010-12-19 00:02:17.480 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//manage_recordings.xml
2010-12-19 00:02:21.166 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//info_menu.xml
2010-12-19 00:02:24.852 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/status-ui.xml
2010-12-19 00:02:24.852 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default/status-ui.xml
2010-12-19 00:02:35.923 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-12-19 00:02:38.824 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-12-19 00:02:43.668 Received a remote 'Clear Cache' request
2010-12-19 00:02:46.110 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//media_settings.xml
2010-12-19 00:02:49.099 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-19 00:02:49.104 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-19 00:02:49.104 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-19 00:02:49.139 Loading menu theme from /usr/share/mythtv/video_settings.xml
2010-12-19 00:04:30.333 XMLParse: LoadTheme using '/usr/share/mythtv/themes/default/keyboard/en_us_ui.xml'
2010-12-19 00:04:57.609 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-19 00:04:59.097 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/recordings-ui.xml
2010-12-19 00:04:59.119 PlaybackBox Error: SortedList is Empty
2010-12-19 00:04:59.220 PlaybackBox Error: SortedList is Empty
2010-12-19 00:05:01.043 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 00:05:10.512 Could not find widget to detach
2010-12-19 00:05:10.513 Could not find widget to detach
2010-12-19 00:05:10.514 Deleting UPnP client...
2010-12-19 00:05:10.519 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 00:09:13.696 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 00:09:13.696 Using runtime prefix = /usr
2010-12-19 00:09:13.696 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 00:09:13.698 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-19 00:09:13.698 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-19 00:09:13.699 Empty LocalHostName.
2010-12-19 00:09:13.699 Using localhost value of steeleweb
2010-12-19 00:09:13.705 New DB connection, total: 1
2010-12-19 00:09:13.708 Connected to database 'mythconverg' at host: localhost
2010-12-19 00:09:13.709 Closing DB connection named 'DBManager0'
2010-12-19 00:09:13.725 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 00:09:13.726 DPMS is disabled.
2010-12-19 00:09:13.728 Primary screen: 0.
2010-12-19 00:09:13.728 Connected to database 'mythconverg' at host: localhost
2010-12-19 00:09:13.730 Using screen 0, 1280x960 at 0,0
2010-12-19 00:09:13.742 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 00:09:13.756 MythUI Image Cache size set to 20971520 bytes
2010-12-19 00:09:13.773 Enabled verbose msgs:  important general
2010-12-19 00:09:13.779 Primary screen: 0.
2010-12-19 00:09:13.780 Using screen 0, 1280x960 at 0,0
2010-12-19 00:09:13.781 Using theme base resolution of 800x600
2010-12-19 00:09:13.785 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 00:09:13.785 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 00:09:13.803 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-19 00:09:13.815 Using Frameless Window
2010-12-19 00:09:13.815 Using Full Screen Window
2010-12-19 00:09:14.044 Using the Qt painter
2010-12-19 00:09:14.077 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-19 00:09:14.081 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-19 00:09:14.081 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-19 00:09:14.081 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-19 00:09:14.081 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-19 00:09:14.082 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-19 00:09:14.082 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-19 00:09:14.093 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-19 00:09:14.101 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-19 00:09:14.113 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-19 00:09:14.117 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-19 00:09:14.117 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-19 00:09:14.117 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-19 00:09:14.117 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-19 00:09:14.117 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-19 00:09:14.117 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-19 00:09:14.117 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-19 00:09:14.117 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-19 00:09:14.118 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-19 00:09:14.118 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-19 00:09:14.118 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-19 00:09:14.118 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-19 00:09:14.118 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-19 00:09:14.118 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-19 00:09:14.118 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-19 00:09:14.118 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-19 00:09:14.261 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-19 00:09:14.274 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-19 00:09:14.282 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-19 00:09:14.299 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-19 00:09:14.301 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-19 00:09:14.308 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 00:09:14.321 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 00:09:14.325 New DB connection, total: 2
2010-12-19 00:09:14.329 Connected to database 'mythconverg' at host: localhost
2010-12-19 00:09:14.882 Registering Internal as a media playback plugin.
2010-12-19 00:09:14.907 Cannot load language en_us for module mytharchive
2010-12-19 00:09:14.909 Cannot load language en_us for module mythbrowser
2010-12-19 00:09:14.913 Registering WebBrowser as a media playback plugin.
2010-12-19 00:09:14.913 Cannot load language en_us for module mythbrowser
2010-12-19 00:09:14.938 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 00:09:14.939 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 00:09:14.939 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 00:09:14.939 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 00:09:14.940 Cannot load language en_us for module mythgallery
2010-12-19 00:09:14.946 Cannot load language en_us for module mythgame
2010-12-19 00:09:14.948 Cannot load language en_us for module mythmovies
2010-12-19 00:09:14.963 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 00:09:15.004 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 00:09:15.013 Cannot load language en_us for module mythmusic
2010-12-19 00:09:15.020 Cannot load language en_us for module mythnetvision
2010-12-19 00:09:15.024 Cannot load language en_us for module mythnews
2010-12-19 00:09:15.032 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 00:09:15.059 Cannot load language en_us for module mythvideo
2010-12-19 00:09:15.066 Cannot load language en_us for module mythweather
2010-12-19 00:09:15.068 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-19 00:09:15.075 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-19 00:09:15.079 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-19 00:09:15.180 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-19 00:09:15.183 Found mainmenu.xml for theme 'MythCenter'
2010-12-19 00:09:15.748 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 00:09:15.749 Using protocol version 23056
2010-12-19 00:09:19.584 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-19 00:09:21.277 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 00:09:29.699 Deleting UPnP client...
2010-12-19 00:09:29.700 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 08:59:58.993 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 08:59:58.994 Using runtime prefix = /usr
2010-12-19 08:59:58.994 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 08:59:58.995 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-19 08:59:58.996 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-19 08:59:58.997 Empty LocalHostName.
2010-12-19 08:59:58.997 Using localhost value of steeleweb
2010-12-19 08:59:59.024 New DB connection, total: 1
2010-12-19 08:59:59.027 Connected to database 'mythconverg' at host: localhost
2010-12-19 08:59:59.028 Closing DB connection named 'DBManager0'
2010-12-19 08:59:59.052 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 08:59:59.054 DPMS is disabled.
2010-12-19 08:59:59.055 Primary screen: 0.
2010-12-19 08:59:59.056 Connected to database 'mythconverg' at host: localhost
2010-12-19 08:59:59.057 Using screen 0, 1280x960 at 0,0
2010-12-19 08:59:59.070 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 08:59:59.087 MythUI Image Cache size set to 20971520 bytes
2010-12-19 08:59:59.099 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-19 08:59:59.136 Enabled verbose msgs:  important general
2010-12-19 08:59:59.144 Primary screen: 0.
2010-12-19 08:59:59.145 Using screen 0, 1280x960 at 0,0
2010-12-19 08:59:59.145 Using theme base resolution of 800x600
2010-12-19 08:59:59.151 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 08:59:59.151 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 08:59:59.182 Using Frameless Window
2010-12-19 08:59:59.182 Using Full Screen Window
2010-12-19 08:59:59.524 Using the Qt painter
2010-12-19 08:59:59.553 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-19 08:59:59.562 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-19 08:59:59.562 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-19 08:59:59.563 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-19 08:59:59.563 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-19 08:59:59.567 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-19 08:59:59.567 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-19 08:59:59.575 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-19 08:59:59.579 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-19 08:59:59.591 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-19 08:59:59.594 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-19 08:59:59.594 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-19 08:59:59.594 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-19 08:59:59.594 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-19 08:59:59.595 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-19 08:59:59.595 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-19 08:59:59.599 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-19 08:59:59.600 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-19 08:59:59.600 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-19 08:59:59.600 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-19 08:59:59.600 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-19 08:59:59.600 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-19 08:59:59.600 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-19 08:59:59.600 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-19 08:59:59.600 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-19 08:59:59.600 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-19 08:59:59.734 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-19 08:59:59.749 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-19 08:59:59.763 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-19 08:59:59.768 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-19 08:59:59.770 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-19 08:59:59.788 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 08:59:59.793 New DB connection, total: 2
2010-12-19 08:59:59.794 Connected to database 'mythconverg' at host: localhost
2010-12-19 08:59:59.797 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 09:00:00.434 Registering Internal as a media playback plugin.
2010-12-19 09:00:00.499 Cannot load language en_us for module mytharchive
2010-12-19 09:00:00.510 Cannot load language en_us for module mythbrowser
2010-12-19 09:00:00.513 Registering WebBrowser as a media playback plugin.
2010-12-19 09:00:00.514 Cannot load language en_us for module mythbrowser
2010-12-19 09:00:00.584 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 09:00:00.584 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 09:00:00.584 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 09:00:00.585 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 09:00:00.585 Cannot load language en_us for module mythgallery
2010-12-19 09:00:00.620 Cannot load language en_us for module mythgame
2010-12-19 09:00:00.634 Cannot load language en_us for module mythmovies
2010-12-19 09:00:00.920 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 09:00:00.960 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 09:00:00.966 Cannot load language en_us for module mythmusic
2010-12-19 09:00:01.003 Cannot load language en_us for module mythnetvision
2010-12-19 09:00:01.019 Cannot load language en_us for module mythnews
2010-12-19 09:00:01.067 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 09:00:01.095 Cannot load language en_us for module mythvideo
2010-12-19 09:00:01.105 Cannot load language en_us for module mythweather
2010-12-19 09:00:01.108 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-19 09:00:01.116 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-19 09:00:01.120 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-19 09:00:01.229 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-19 09:00:01.232 Found mainmenu.xml for theme 'MythCenter'
2010-12-19 09:00:01.786 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 09:00:01.787 Using protocol version 23056
2010-12-19 09:00:06.068 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-19 09:00:07.126 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/recordings-ui.xml
2010-12-19 09:00:07.276 PlaybackBox Error: SortedList is Empty
2010-12-19 09:00:07.390 PlaybackBox Error: SortedList is Empty
2010-12-19 09:00:10.296 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 09:00:19.244 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 09:00:34.598 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-12-19 09:00:36.481 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-12-19 09:00:38.803 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//media_settings.xml
2010-12-19 09:00:50.137 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-19 09:00:50.142 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-19 09:00:50.142 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-19 09:00:50.202 Loading menu theme from /usr/share/mythtv/video_settings.xml
2010-12-19 09:00:52.679 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 09:01:12.143 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 09:01:52.582 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/keyboard/keyboard.xml
2010-12-19 09:01:52.582 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default/keyboard/keyboard.xml
2010-12-19 09:01:52.602 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/default/keyboard/keyboard.xml @ 7
            Name: 'key'    Type: 'font'
2010-12-19 09:01:52.702 Loading definitions from: /usr/share/mythtv/themes/default/keyboard/en_us.xml
2010-12-19 09:02:20.245 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-19 09:02:21.609 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 09:02:29.427 Deleting UPnP client...
2010-12-19 09:02:29.428 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 15:30:59.244 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 15:30:59.245 Using runtime prefix = /usr
2010-12-19 15:30:59.245 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 15:30:59.953 Empty LocalHostName.
2010-12-19 15:30:59.953 Using localhost value of steeleweb
2010-12-19 15:30:59.964 New DB connection, total: 1
2010-12-19 15:30:59.967 Connected to database 'mythconverg' at host: localhost
2010-12-19 15:30:59.968 Closing DB connection named 'DBManager0'
2010-12-19 15:31:00.161 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 15:31:00.162 DPMS is disabled.
2010-12-19 15:31:00.164 Primary screen: 0.
2010-12-19 15:31:00.168 Connected to database 'mythconverg' at host: localhost
2010-12-19 15:31:00.169 Using screen 0, 1280x960 at 0,0
2010-12-19 15:31:00.185 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 15:31:00.201 MythUI Image Cache size set to 20971520 bytes
2010-12-19 15:31:00.218 Enabled verbose msgs:  important general
2010-12-19 15:31:00.225 Primary screen: 0.
2010-12-19 15:31:00.225 Using screen 0, 1280x960 at 0,0
2010-12-19 15:31:00.226 Using theme base resolution of 800x600
2010-12-19 15:31:00.232 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 15:31:00.233 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 15:31:00.328 Using Frameless Window
2010-12-19 15:31:00.328 Using Full Screen Window
2010-12-19 15:31:00.565 Using the Qt painter
2010-12-19 15:31:00.623 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-19 15:31:00.626 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-19 15:31:00.627 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-19 15:31:00.637 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-19 15:31:00.637 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-19 15:31:00.637 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-19 15:31:00.637 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-19 15:31:00.641 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-19 15:31:00.661 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-19 15:31:00.669 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-19 15:31:00.673 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-19 15:31:00.673 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-19 15:31:00.673 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-19 15:31:00.673 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-19 15:31:00.673 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-19 15:31:00.673 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-19 15:31:00.673 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-19 15:31:00.673 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-19 15:31:00.673 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-19 15:31:00.674 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-19 15:31:00.674 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-19 15:31:00.674 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-19 15:31:00.674 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-19 15:31:00.674 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-19 15:31:00.674 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-19 15:31:00.674 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-19 15:31:00.783 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-19 15:31:00.794 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-19 15:31:00.810 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-19 15:31:00.819 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-19 15:31:00.821 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-19 15:31:00.835 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 15:31:00.841 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 15:31:00.845 New DB connection, total: 2
2010-12-19 15:31:00.849 Connected to database 'mythconverg' at host: localhost
2010-12-19 15:31:01.530 Registering Internal as a media playback plugin.
2010-12-19 15:31:01.558 Cannot load language en_us for module mytharchive
2010-12-19 15:31:01.560 Cannot load language en_us for module mythbrowser
2010-12-19 15:31:01.564 Registering WebBrowser as a media playback plugin.
2010-12-19 15:31:01.565 Cannot load language en_us for module mythbrowser
2010-12-19 15:31:01.595 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 15:31:01.596 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 15:31:01.596 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 15:31:01.597 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 15:31:01.597 Cannot load language en_us for module mythgallery
2010-12-19 15:31:01.604 Cannot load language en_us for module mythgame
2010-12-19 15:31:01.607 Cannot load language en_us for module mythmovies
2010-12-19 15:31:01.625 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 15:31:01.672 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 15:31:01.679 Cannot load language en_us for module mythmusic
2010-12-19 15:31:01.686 Cannot load language en_us for module mythnetvision
2010-12-19 15:31:01.692 Cannot load language en_us for module mythnews
2010-12-19 15:31:01.700 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 15:31:01.731 Cannot load language en_us for module mythvideo
2010-12-19 15:31:01.739 Cannot load language en_us for module mythweather
2010-12-19 15:31:01.741 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-19 15:31:01.749 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-19 15:31:01.753 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-19 15:31:01.853 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-19 15:31:01.860 Found mainmenu.xml for theme 'MythCenter'
2010-12-19 15:31:02.434 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 15:31:02.442 Using protocol version 23056
2010-12-19 15:31:06.924 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-19 15:31:08.229 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 15:31:14.615 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 15:42:53.663 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 15:42:53.664 Using runtime prefix = /usr
2010-12-19 15:42:53.664 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 15:42:54.264 Empty LocalHostName.
2010-12-19 15:42:54.265 Using localhost value of steeleweb
2010-12-19 15:42:54.276 New DB connection, total: 1
2010-12-19 15:42:54.279 Connected to database 'mythconverg' at host: localhost
2010-12-19 15:42:54.280 Closing DB connection named 'DBManager0'
2010-12-19 15:42:54.292 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 15:42:54.294 DPMS is disabled.
2010-12-19 15:42:54.295 Primary screen: 0.
2010-12-19 15:42:54.296 Connected to database 'mythconverg' at host: localhost
2010-12-19 15:42:54.297 Using screen 0, 1280x960 at 0,0
2010-12-19 15:42:54.309 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 15:42:54.323 MythUI Image Cache size set to 20971520 bytes
2010-12-19 15:42:54.339 Enabled verbose msgs:  important general
2010-12-19 15:42:54.346 Primary screen: 0.
2010-12-19 15:42:54.346 Using screen 0, 1280x960 at 0,0
2010-12-19 15:42:54.347 Using theme base resolution of 800x600
2010-12-19 15:42:54.351 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 15:42:54.352 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 15:42:54.381 Using Frameless Window
2010-12-19 15:42:54.381 Using Full Screen Window
2010-12-19 15:42:54.611 Using the Qt painter
2010-12-19 15:42:54.642 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-19 15:42:54.650 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-19 15:42:54.650 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-19 15:42:54.650 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-19 15:42:54.650 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-19 15:42:54.650 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-19 15:42:54.650 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-19 15:42:54.662 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-19 15:42:54.670 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-19 15:42:54.678 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-19 15:42:54.686 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-19 15:42:54.686 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-19 15:42:54.686 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-19 15:42:54.686 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-19 15:42:54.686 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-19 15:42:54.686 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-19 15:42:54.686 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-19 15:42:54.686 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-19 15:42:54.687 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-19 15:42:54.687 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-19 15:42:54.687 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-19 15:42:54.687 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-19 15:42:54.687 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-19 15:42:54.687 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-19 15:42:54.687 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-19 15:42:54.687 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-19 15:42:54.833 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-19 15:42:54.843 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-19 15:42:54.857 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-19 15:42:54.863 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-19 15:42:54.864 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-19 15:42:54.883 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 15:42:54.889 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 15:42:54.891 New DB connection, total: 2
2010-12-19 15:42:54.892 Connected to database 'mythconverg' at host: localhost
2010-12-19 15:42:55.443 Registering Internal as a media playback plugin.
2010-12-19 15:42:55.468 Cannot load language en_us for module mytharchive
2010-12-19 15:42:55.470 Cannot load language en_us for module mythbrowser
2010-12-19 15:42:55.473 Registering WebBrowser as a media playback plugin.
2010-12-19 15:42:55.473 Cannot load language en_us for module mythbrowser
2010-12-19 15:42:55.499 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 15:42:55.499 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 15:42:55.499 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 15:42:55.500 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 15:42:55.500 Cannot load language en_us for module mythgallery
2010-12-19 15:42:55.506 Cannot load language en_us for module mythgame
2010-12-19 15:42:55.509 Cannot load language en_us for module mythmovies
2010-12-19 15:42:55.522 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 15:42:55.562 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 15:42:55.569 Cannot load language en_us for module mythmusic
2010-12-19 15:42:55.575 Cannot load language en_us for module mythnetvision
2010-12-19 15:42:55.580 Cannot load language en_us for module mythnews
2010-12-19 15:42:55.587 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 15:42:55.614 Cannot load language en_us for module mythvideo
2010-12-19 15:42:55.620 Cannot load language en_us for module mythweather
2010-12-19 15:42:55.623 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-19 15:42:55.630 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-19 15:42:55.635 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-19 15:42:55.723 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-19 15:42:55.731 Found mainmenu.xml for theme 'MythCenter'
2010-12-19 15:42:56.292 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 15:42:56.293 Using protocol version 23056
2010-12-19 15:42:58.750 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-19 15:42:59.969 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 15:43:11.509 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 15:44:43.743 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 15:44:43.743 Using runtime prefix = /usr
2010-12-19 15:44:43.743 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 15:44:44.100 Empty LocalHostName.
2010-12-19 15:44:44.100 Using localhost value of steeleweb
2010-12-19 15:44:44.106 New DB connection, total: 1
2010-12-19 15:44:44.109 Connected to database 'mythconverg' at host: localhost
2010-12-19 15:44:44.110 Closing DB connection named 'DBManager0'
2010-12-19 15:44:44.122 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 15:44:44.123 DPMS is disabled.
2010-12-19 15:44:44.125 Primary screen: 0.
2010-12-19 15:44:44.126 Connected to database 'mythconverg' at host: localhost
2010-12-19 15:44:44.127 Using screen 0, 1280x960 at 0,0
2010-12-19 15:44:44.139 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 15:44:44.154 MythUI Image Cache size set to 20971520 bytes
2010-12-19 15:44:44.170 Enabled verbose msgs:  important general
2010-12-19 15:44:44.176 Primary screen: 0.
2010-12-19 15:44:44.177 Using screen 0, 1280x960 at 0,0
2010-12-19 15:44:44.178 Using theme base resolution of 800x600
2010-12-19 15:44:44.182 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 15:44:44.183 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 15:44:44.212 Using Frameless Window
2010-12-19 15:44:44.212 Using Full Screen Window
2010-12-19 15:44:44.438 Using the Qt painter
2010-12-19 15:44:44.471 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-19 15:44:44.475 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-19 15:44:44.475 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-19 15:44:44.475 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-19 15:44:44.475 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-19 15:44:44.475 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-19 15:44:44.475 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-19 15:44:44.487 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-19 15:44:44.495 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-19 15:44:44.507 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-19 15:44:44.510 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-19 15:44:44.511 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-19 15:44:44.511 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-19 15:44:44.511 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-19 15:44:44.511 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-19 15:44:44.511 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-19 15:44:44.511 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-19 15:44:44.511 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-19 15:44:44.511 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-19 15:44:44.511 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-19 15:44:44.511 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-19 15:44:44.511 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-19 15:44:44.512 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-19 15:44:44.512 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-19 15:44:44.512 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-19 15:44:44.512 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-19 15:44:44.651 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-19 15:44:44.666 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-19 15:44:44.676 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-19 15:44:44.686 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-19 15:44:44.687 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-19 15:44:44.702 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 15:44:44.715 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 15:44:44.719 New DB connection, total: 2
2010-12-19 15:44:44.719 Connected to database 'mythconverg' at host: localhost
2010-12-19 15:44:45.305 Registering Internal as a media playback plugin.
2010-12-19 15:44:45.330 Cannot load language en_us for module mytharchive
2010-12-19 15:44:45.332 Cannot load language en_us for module mythbrowser
2010-12-19 15:44:45.336 Registering WebBrowser as a media playback plugin.
2010-12-19 15:44:45.336 Cannot load language en_us for module mythbrowser
2010-12-19 15:44:45.361 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 15:44:45.361 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 15:44:45.362 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 15:44:45.362 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 15:44:45.363 Cannot load language en_us for module mythgallery
2010-12-19 15:44:45.369 Cannot load language en_us for module mythgame
2010-12-19 15:44:45.372 Cannot load language en_us for module mythmovies
2010-12-19 15:44:45.385 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 15:44:45.424 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 15:44:45.432 Cannot load language en_us for module mythmusic
2010-12-19 15:44:45.438 Cannot load language en_us for module mythnetvision
2010-12-19 15:44:45.443 Cannot load language en_us for module mythnews
2010-12-19 15:44:45.450 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 15:44:45.477 Cannot load language en_us for module mythvideo
2010-12-19 15:44:45.483 Cannot load language en_us for module mythweather
2010-12-19 15:44:45.485 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-19 15:44:45.493 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-19 15:44:45.497 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-19 15:44:45.595 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-19 15:44:45.597 Found mainmenu.xml for theme 'MythCenter'
2010-12-19 15:44:46.152 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 15:44:46.153 Using protocol version 23056
2010-12-19 15:44:48.890 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-12-19 15:44:51.188 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-12-19 15:46:17.263 Received a remote 'Clear Cache' request
2010-12-19 15:46:23.432 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//tv_settings.xml
2010-12-19 15:46:28.712 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//media_settings.xml
2010-12-19 15:46:37.782 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-19 15:46:37.787 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-19 15:46:37.787 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-19 15:46:37.851 Loading menu theme from /usr/share/mythtv/video_settings.xml
2010-12-19 15:46:39.577 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 15:46:39.585 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default/video-ui.xml
2010-12-19 15:46:48.141 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 15:47:15.388 Received a remote 'Clear Cache' request
2010-12-19 15:47:21.650 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-19 15:47:26.835 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 15:47:30.769 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 16:05:31.621 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 16:05:31.621 Using runtime prefix = /usr
2010-12-19 16:05:31.621 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 16:05:32.465 Empty LocalHostName.
2010-12-19 16:05:32.465 Using localhost value of steeleweb
2010-12-19 16:05:32.480 New DB connection, total: 1
2010-12-19 16:05:32.493 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:05:32.494 Closing DB connection named 'DBManager0'
2010-12-19 16:05:32.544 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 16:05:32.546 DPMS is disabled.
2010-12-19 16:05:32.551 Primary screen: 0.
2010-12-19 16:05:32.552 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:05:32.553 Using screen 0, 1280x960 at 0,0
2010-12-19 16:05:32.570 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 16:05:32.585 MythUI Image Cache size set to 20971520 bytes
2010-12-19 16:05:32.603 Enabled verbose msgs:  important general
2010-12-19 16:05:32.609 Primary screen: 0.
2010-12-19 16:05:32.610 Using screen 0, 1280x960 at 0,0
2010-12-19 16:05:32.611 Using theme base resolution of 800x600
2010-12-19 16:05:32.616 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 16:05:32.616 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 16:05:32.737 Using Frameless Window
2010-12-19 16:05:32.737 Using Full Screen Window
2010-12-19 16:05:32.974 Using the Qt painter
2010-12-19 16:05:33.016 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-19 16:05:33.024 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-19 16:05:33.024 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-19 16:05:33.024 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-19 16:05:33.024 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-19 16:05:33.025 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-19 16:05:33.025 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-19 16:05:33.032 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-19 16:05:33.040 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-19 16:05:33.044 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-19 16:05:33.056 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-19 16:05:33.056 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-19 16:05:33.056 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-19 16:05:33.056 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-19 16:05:33.056 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-19 16:05:33.056 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-19 16:05:33.056 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-19 16:05:33.056 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-19 16:05:33.056 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-19 16:05:33.057 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-19 16:05:33.057 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-19 16:05:33.057 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-19 16:05:33.057 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-19 16:05:33.057 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-19 16:05:33.057 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-19 16:05:33.057 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-19 16:05:33.189 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-19 16:05:33.199 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-19 16:05:33.216 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-19 16:05:33.222 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-19 16:05:33.223 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-19 16:05:33.241 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 16:05:33.251 New DB connection, total: 2
2010-12-19 16:05:33.252 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 16:05:33.257 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:05:33.933 Registering Internal as a media playback plugin.
2010-12-19 16:05:33.962 Cannot load language en_us for module mytharchive
2010-12-19 16:05:33.965 Cannot load language en_us for module mythbrowser
2010-12-19 16:05:33.969 Registering WebBrowser as a media playback plugin.
2010-12-19 16:05:33.969 Cannot load language en_us for module mythbrowser
2010-12-19 16:05:34.000 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:05:34.000 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:05:34.000 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:05:34.001 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 16:05:34.001 Cannot load language en_us for module mythgallery
2010-12-19 16:05:34.011 Cannot load language en_us for module mythgame
2010-12-19 16:05:34.017 Cannot load language en_us for module mythmovies
2010-12-19 16:05:34.036 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 16:05:34.087 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 16:05:34.094 Cannot load language en_us for module mythmusic
2010-12-19 16:05:34.101 Cannot load language en_us for module mythnetvision
2010-12-19 16:05:34.108 Cannot load language en_us for module mythnews
2010-12-19 16:05:34.115 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 16:05:34.147 Cannot load language en_us for module mythvideo
2010-12-19 16:05:34.155 Cannot load language en_us for module mythweather
2010-12-19 16:05:34.157 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-19 16:05:34.166 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-19 16:05:34.172 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-19 16:05:34.279 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-19 16:05:34.285 Found mainmenu.xml for theme 'MythCenter'
2010-12-19 16:05:34.859 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 16:05:34.860 Using protocol version 23056
2010-12-19 16:05:37.317 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-19 16:05:38.682 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/video-ui.xml
2010-12-19 16:05:51.006 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 16:09:09.739 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 16:09:09.739 Using runtime prefix = /usr
2010-12-19 16:09:09.739 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 16:09:10.268 Empty LocalHostName.
2010-12-19 16:09:10.268 Using localhost value of steeleweb
2010-12-19 16:09:10.273 New DB connection, total: 1
2010-12-19 16:09:10.277 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:09:10.277 Closing DB connection named 'DBManager0'
2010-12-19 16:09:10.289 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 16:09:10.290 DPMS is disabled.
2010-12-19 16:09:10.292 Primary screen: 0.
2010-12-19 16:09:10.292 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:09:10.294 Using screen 0, 1280x960 at 0,0
2010-12-19 16:09:10.306 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 16:09:10.320 MythUI Image Cache size set to 20971520 bytes
2010-12-19 16:09:10.336 Enabled verbose msgs:  important general
2010-12-19 16:09:10.347 Primary screen: 0.
2010-12-19 16:09:10.349 Using screen 0, 1280x960 at 0,0
2010-12-19 16:09:10.350 Using theme base resolution of 800x600
2010-12-19 16:09:10.361 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 16:09:10.361 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 16:09:10.392 Using Frameless Window
2010-12-19 16:09:10.392 Using Full Screen Window
2010-12-19 16:09:10.618 Using the Qt painter
2010-12-19 16:09:10.650 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 5
            Name: 'basesmall'    Type: 'font'
2010-12-19 16:09:10.660 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 11
            Name: 'basesmaller'    Type: 'font'
2010-12-19 16:09:10.660 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 15
            Name: 'basesmallbold'    Type: 'font'
2010-12-19 16:09:10.660 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 19
            Name: 'basesmallboldblue'    Type: 'font'
2010-12-19 16:09:10.661 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 23
            Name: 'basesmallboldgrey'    Type: 'font'
2010-12-19 16:09:10.661 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 27
            Name: 'basesmallboldgreyhighlight'    Type: 'font'
2010-12-19 16:09:10.661 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 31
            Name: 'small'    Type: 'font'
2010-12-19 16:09:10.664 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 37
            Name: 'basemedium'    Type: 'font'
2010-12-19 16:09:10.672 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 41
            Name: 'baselarge'    Type: 'font'
2010-12-19 16:09:10.680 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 49
            Name: 'baselargenormal'    Type: 'font'
2010-12-19 16:09:10.684 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 53
            Name: 'baseextralarge'    Type: 'font'
2010-12-19 16:09:10.684 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 62
            Name: 'basesmallwhite'    Type: 'font'
2010-12-19 16:09:10.684 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 66
            Name: 'basesmalllightgrey'    Type: 'font'
2010-12-19 16:09:10.684 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 70
            Name: 'basesmallgrey'    Type: 'font'
2010-12-19 16:09:10.684 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 74
            Name: 'basesmallpurple'    Type: 'font'
2010-12-19 16:09:10.684 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 78
            Name: 'basesmallblack'    Type: 'font'
2010-12-19 16:09:10.684 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 82
            Name: 'basesmallyellow'    Type: 'font'
2010-12-19 16:09:10.685 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 86
            Name: 'basesmallgreen'    Type: 'font'
2010-12-19 16:09:10.685 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 90
            Name: 'basesmallblue'    Type: 'font'
2010-12-19 16:09:10.685 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 94
            Name: 'basesmallred'    Type: 'font'
2010-12-19 16:09:10.685 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 98
            Name: 'basemediumwhite'    Type: 'font'
2010-12-19 16:09:10.685 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 102
            Name: 'basemediumlightgrey'    Type: 'font'
2010-12-19 16:09:10.685 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 106
            Name: 'basemediumgrey'    Type: 'font'
2010-12-19 16:09:10.685 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 110
            Name: 'basemediumgreen'    Type: 'font'
2010-12-19 16:09:10.685 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 114
            Name: 'basemediumred'    Type: 'font'
2010-12-19 16:09:10.685 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 118
            Name: 'basemediumyellow'    Type: 'font'
2010-12-19 16:09:10.835 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
            Name: 'small'    Type: 'font'
2010-12-19 16:09:10.841 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
            Name: 'medium'    Type: 'font'
2010-12-19 16:09:10.858 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
            Name: 'large'    Type: 'font'
2010-12-19 16:09:10.872 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
            Name: 'clock'    Type: 'font'
2010-12-19 16:09:10.873 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2010-12-19 16:09:10.886 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 16:09:10.895 New DB connection, total: 2
2010-12-19 16:09:10.896 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 16:09:10.898 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:09:11.447 Registering Internal as a media playback plugin.
2010-12-19 16:09:11.474 Cannot load language en_us for module mytharchive
2010-12-19 16:09:11.476 Cannot load language en_us for module mythbrowser
2010-12-19 16:09:11.479 Registering WebBrowser as a media playback plugin.
2010-12-19 16:09:11.480 Cannot load language en_us for module mythbrowser
2010-12-19 16:09:11.504 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:09:11.505 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:09:11.505 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:09:11.505 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 16:09:11.506 Cannot load language en_us for module mythgallery
2010-12-19 16:09:11.511 Cannot load language en_us for module mythgame
2010-12-19 16:09:11.514 Cannot load language en_us for module mythmovies
2010-12-19 16:09:11.528 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 16:09:11.568 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 16:09:11.575 Cannot load language en_us for module mythmusic
2010-12-19 16:09:11.581 Cannot load language en_us for module mythnetvision
2010-12-19 16:09:11.586 Cannot load language en_us for module mythnews
2010-12-19 16:09:11.593 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 16:09:11.619 Cannot load language en_us for module mythvideo
2010-12-19 16:09:11.626 Cannot load language en_us for module mythweather
2010-12-19 16:09:11.628 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2010-12-19 16:09:11.637 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 5
            Name: 'menufont'    Type: 'font'
2010-12-19 16:09:11.641 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 14
            Name: 'clock'    Type: 'font'
2010-12-19 16:09:11.743 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-19 16:09:11.746 Found mainmenu.xml for theme 'MythCenter'
2010-12-19 16:09:12.297 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 16:09:12.298 Using protocol version 23056
2010-12-19 16:09:19.248 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-12-19 16:09:20.830 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-12-19 16:10:36.864 Received a remote 'Clear Cache' request
2010-12-19 16:10:37.347 Primary screen: 0.
2010-12-19 16:10:37.348 Using screen 0, 1280x960 at 0,0
2010-12-19 16:10:37.349 Using theme base resolution of 1280x720
2010-12-19 16:10:37.369 Using Frameless Window
2010-12-19 16:10:37.369 Using Full Screen Window
2010-12-19 16:10:37.804 Using the Qt painter
2010-12-19 16:10:37.822 Removing stale cache dir: /home/steeleweb/.mythtv/themecache/MythCenter.1280.960
2010-12-19 16:10:38.017 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-12-19 16:10:38.072 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-12-19 16:10:38.080 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 16:10:38.632 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-12-19 16:10:38.643 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-12-19 16:10:38.760 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-12-19 16:10:38.761 Found mainmenu.xml for theme 'Mythbuntu'
2010-12-19 16:10:49.683 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//manage_recordings.xml
2010-12-19 16:10:59.844 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-12-19 16:11:02.418 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-12-19 16:11:07.608 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//media_settings.xml
2010-12-19 16:11:10.624 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-12-19 16:11:10.676 Loading menu theme from /usr/share/mythtv/video_settings.xml
2010-12-19 16:11:14.210 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-12-19 16:11:50.292 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-12-19 16:11:51.997 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-12-19 16:12:03.435 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-12-19 16:12:04.772 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-12-19 16:12:46.541 Received a remote 'Clear Cache' request
2010-12-19 16:12:46.871 Primary screen: 0.
2010-12-19 16:12:46.872 Using screen 0, 1280x960 at 0,0
2010-12-19 16:12:46.873 Using theme base resolution of 1280x720
2010-12-19 16:12:46.895 Using Frameless Window
2010-12-19 16:12:46.895 Using Full Screen Window
2010-12-19 16:12:47.142 Using the Qt painter
2010-12-19 16:12:47.153 Removing stale cache dir: /home/steeleweb/.mythtv/themecache/Mythbuntu.1280.960
2010-12-19 16:12:47.307 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2010-12-19 16:12:47.318 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-12-19 16:12:47.326 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 16:12:48.622 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 16:12:48.714 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//mainmenu.xml
2010-12-19 16:12:48.716 Found mainmenu.xml for theme 'MythCenter-wide'
2010-12-19 16:12:56.866 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//advanced.xml
2010-12-19 16:13:01.603 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/status-ui.xml
2010-12-19 16:13:19.751 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/status-ui.xml
2010-12-19 16:13:37.421 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:13:37.421 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:13:40.092 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:13:40.092 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:13:54.014 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/recordings-ui.xml
2010-12-19 16:13:54.099 PlaybackBox Error: SortedList is Empty
2010-12-19 16:13:54.431 PlaybackBox Error: SortedList is Empty
2010-12-19 16:14:03.318 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:14:03.318 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:14:11.152 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//plugin_menu.xml
2010-12-19 16:14:23.272 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//advanced.xml
2010-12-19 16:14:25.937 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//main_settings.xml
2010-12-19 16:14:30.528 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//media_settings.xml
2010-12-19 16:14:31.899 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 16:14:31.939 Loading menu theme from /usr/share/mythtv/video_settings.xml
2010-12-19 16:15:07.808 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:15:07.808 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:15:13.850 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 16:21:07.881 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 16:21:07.881 Using runtime prefix = /usr
2010-12-19 16:21:07.881 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 16:21:08.292 Empty LocalHostName.
2010-12-19 16:21:08.292 Using localhost value of steeleweb
2010-12-19 16:21:08.299 New DB connection, total: 1
2010-12-19 16:21:08.304 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:21:08.305 Closing DB connection named 'DBManager0'
2010-12-19 16:21:08.318 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 16:21:08.319 DPMS is disabled.
2010-12-19 16:21:08.321 Primary screen: 0.
2010-12-19 16:21:08.322 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:21:08.325 Using screen 0, 1280x960 at 0,0
2010-12-19 16:21:08.338 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 16:21:08.356 MythUI Image Cache size set to 20971520 bytes
2010-12-19 16:21:08.375 Enabled verbose msgs:  important general
2010-12-19 16:21:08.381 Primary screen: 0.
2010-12-19 16:21:08.382 Using screen 0, 1280x960 at 0,0
2010-12-19 16:21:08.383 Using theme base resolution of 1280x720
2010-12-19 16:21:08.388 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 16:21:08.388 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 16:21:08.417 Using Frameless Window
2010-12-19 16:21:08.417 Using Full Screen Window
2010-12-19 16:21:08.665 Using the Qt painter
2010-12-19 16:21:08.901 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2010-12-19 16:21:08.915 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-12-19 16:21:08.930 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 16:21:08.941 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 16:21:08.956 New DB connection, total: 2
2010-12-19 16:21:08.963 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:21:09.448 Registering Internal as a media playback plugin.
2010-12-19 16:21:09.473 Cannot load language en_us for module mytharchive
2010-12-19 16:21:09.475 Cannot load language en_us for module mythbrowser
2010-12-19 16:21:09.479 Registering WebBrowser as a media playback plugin.
2010-12-19 16:21:09.479 Cannot load language en_us for module mythbrowser
2010-12-19 16:21:09.504 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:21:09.504 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:21:09.504 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:21:09.505 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 16:21:09.505 Cannot load language en_us for module mythgallery
2010-12-19 16:21:09.511 Cannot load language en_us for module mythgame
2010-12-19 16:21:09.514 Cannot load language en_us for module mythmovies
2010-12-19 16:21:09.528 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 16:21:09.567 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 16:21:09.573 Cannot load language en_us for module mythmusic
2010-12-19 16:21:09.580 Cannot load language en_us for module mythnetvision
2010-12-19 16:21:09.585 Cannot load language en_us for module mythnews
2010-12-19 16:21:09.592 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 16:21:09.618 Cannot load language en_us for module mythvideo
2010-12-19 16:21:09.625 Cannot load language en_us for module mythweather
2010-12-19 16:21:09.627 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 16:21:09.740 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//mainmenu.xml
2010-12-19 16:21:09.742 Found mainmenu.xml for theme 'MythCenter-wide'
2010-12-19 16:21:10.056 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 16:21:10.057 Using protocol version 23056
2010-12-19 16:21:15.611 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//advanced.xml
2010-12-19 16:21:17.149 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//main_settings.xml
2010-12-19 16:22:44.284 Received a remote 'Clear Cache' request
2010-12-19 16:22:49.114 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 16:23:10.431 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 16:23:10.432 Using runtime prefix = /usr
2010-12-19 16:23:10.432 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 16:23:11.363 Empty LocalHostName.
2010-12-19 16:23:11.363 Using localhost value of steeleweb
2010-12-19 16:23:11.368 New DB connection, total: 1
2010-12-19 16:23:11.372 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:23:11.372 Closing DB connection named 'DBManager0'
2010-12-19 16:23:11.386 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 16:23:11.387 DPMS is disabled.
2010-12-19 16:23:11.388 Primary screen: 0.
2010-12-19 16:23:11.389 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:23:11.391 Using screen 0, 1280x960 at 0,0
2010-12-19 16:23:11.402 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 16:23:11.417 MythUI Image Cache size set to 20971520 bytes
2010-12-19 16:23:11.432 Enabled verbose msgs:  important general
2010-12-19 16:23:11.439 Primary screen: 0.
2010-12-19 16:23:11.440 Using screen 0, 1280x960 at 0,0
2010-12-19 16:23:11.441 Using theme base resolution of 1280x720
2010-12-19 16:23:11.445 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 16:23:11.445 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 16:23:11.474 Using Frameless Window
2010-12-19 16:23:11.474 Using Full Screen Window
2010-12-19 16:23:11.719 Using the Qt painter
2010-12-19 16:23:11.954 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2010-12-19 16:23:11.968 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-12-19 16:23:11.980 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 16:23:11.990 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 16:23:12.013 New DB connection, total: 2
2010-12-19 16:23:12.018 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:23:12.513 Registering Internal as a media playback plugin.
2010-12-19 16:23:12.539 Cannot load language en_us for module mytharchive
2010-12-19 16:23:12.541 Cannot load language en_us for module mythbrowser
2010-12-19 16:23:12.545 Registering WebBrowser as a media playback plugin.
2010-12-19 16:23:12.545 Cannot load language en_us for module mythbrowser
2010-12-19 16:23:12.570 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:23:12.571 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:23:12.571 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:23:12.571 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 16:23:12.572 Cannot load language en_us for module mythgallery
2010-12-19 16:23:12.578 Cannot load language en_us for module mythgame
2010-12-19 16:23:12.581 Cannot load language en_us for module mythmovies
2010-12-19 16:23:12.595 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 16:23:12.637 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 16:23:12.643 Cannot load language en_us for module mythmusic
2010-12-19 16:23:12.650 Cannot load language en_us for module mythnetvision
2010-12-19 16:23:12.655 Cannot load language en_us for module mythnews
2010-12-19 16:23:12.663 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 16:23:12.690 Cannot load language en_us for module mythvideo
2010-12-19 16:23:12.697 Cannot load language en_us for module mythweather
2010-12-19 16:23:12.699 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 16:23:12.807 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//mainmenu.xml
2010-12-19 16:23:12.814 Found mainmenu.xml for theme 'MythCenter-wide'
2010-12-19 16:23:13.121 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 16:23:13.122 Using protocol version 23056
2010-12-19 16:23:16.570 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:23:16.570 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:23:22.895 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//advanced.xml
2010-12-19 16:23:29.058 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//main_settings.xml
2010-12-19 16:23:34.492 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//tv_settings.xml
2010-12-19 16:24:01.846 Received a remote 'Clear Cache' request
2010-12-19 16:24:21.623 Received a remote 'Clear Cache' request
2010-12-19 16:24:51.373 Received a remote 'Clear Cache' request
2010-12-19 16:24:56.542 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 16:35:12.750 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 16:35:12.751 Using runtime prefix = /usr
2010-12-19 16:35:12.751 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 16:35:13.535 Empty LocalHostName.
2010-12-19 16:35:13.536 Using localhost value of steeleweb
2010-12-19 16:35:13.541 New DB connection, total: 1
2010-12-19 16:35:13.544 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:35:13.545 Closing DB connection named 'DBManager0'
2010-12-19 16:35:13.558 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 16:35:13.559 DPMS is disabled.
2010-12-19 16:35:13.561 Primary screen: 0.
2010-12-19 16:35:13.561 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:35:13.563 Using screen 0, 1280x960 at 0,0
2010-12-19 16:35:13.575 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 16:35:13.589 MythUI Image Cache size set to 20971520 bytes
2010-12-19 16:35:13.605 Enabled verbose msgs:  important general
2010-12-19 16:35:13.611 Primary screen: 0.
2010-12-19 16:35:13.611 Using screen 0, 1280x960 at 0,0
2010-12-19 16:35:13.616 Using theme base resolution of 1280x720
2010-12-19 16:35:13.621 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 16:35:13.621 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 16:35:13.650 Using Frameless Window
2010-12-19 16:35:13.650 Using Full Screen Window
2010-12-19 16:35:13.894 Using the Qt painter
2010-12-19 16:35:14.131 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2010-12-19 16:35:14.137 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-12-19 16:35:14.151 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 16:35:14.164 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 16:35:14.167 New DB connection, total: 2
2010-12-19 16:35:14.168 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:35:14.674 Registering Internal as a media playback plugin.
2010-12-19 16:35:14.700 Cannot load language en_us for module mytharchive
2010-12-19 16:35:14.701 Cannot load language en_us for module mythbrowser
2010-12-19 16:35:14.705 Registering WebBrowser as a media playback plugin.
2010-12-19 16:35:14.705 Cannot load language en_us for module mythbrowser
2010-12-19 16:35:14.730 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:35:14.730 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:35:14.730 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:35:14.731 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 16:35:14.731 Cannot load language en_us for module mythgallery
2010-12-19 16:35:14.737 Cannot load language en_us for module mythgame
2010-12-19 16:35:14.740 Cannot load language en_us for module mythmovies
2010-12-19 16:35:14.753 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 16:35:14.792 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 16:35:14.799 Cannot load language en_us for module mythmusic
2010-12-19 16:35:14.805 Cannot load language en_us for module mythnetvision
2010-12-19 16:35:14.810 Cannot load language en_us for module mythnews
2010-12-19 16:35:14.817 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 16:35:14.843 Cannot load language en_us for module mythvideo
2010-12-19 16:35:14.850 Cannot load language en_us for module mythweather
2010-12-19 16:35:14.852 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 16:35:14.963 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//mainmenu.xml
2010-12-19 16:35:14.965 Found mainmenu.xml for theme 'MythCenter-wide'
2010-12-19 16:35:15.272 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 16:35:15.273 Using protocol version 23056
2010-12-19 16:35:19.388 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:35:19.388 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:35:23.310 buildFileList directory = myth://Videos@steeleweb/media/movies/
2010-12-19 16:35:23.312 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@steeleweb/media/movies/)
2010-12-19 16:35:23.315 buildFileList directory = myth://Videos@steeleweb/var/lib/mythtv/videos/
2010-12-19 16:35:23.315 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@steeleweb/var/lib/mythtv/videos/)
2010-12-19 16:35:23.470 Adding :  : Avatar.2009.DvDRip.Dual Audio.Hindi+Eng.XviD.SDR-Release -=![Postarbhai]!=-.avi : NULL
2010-12-19 16:35:29.957 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:35:29.957 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:35:33.478 TV: Attempting to change from None to WatchingVideo
2010-12-19 16:35:34.068 RingBuf(myth://Videos@127.0.0.1:6543/Avatar.2009.DvDRip.Dual Audio.Hindi+Eng.XviD.SDR-Release -=![Postarbhai]!=-.avi) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 16:35:34.068 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Avatar.2009.DvDRip.Dual Audio.Hindi+Eng.XviD.SDR-Release -=![Postarbhai]!=-.avi
2010-12-19 16:35:46.476 TV: Attempting to change from None to WatchingVideo
2010-12-19 16:35:46.967 RingBuf(myth://Videos@127.0.0.1:6543/Avatar.2009.DvDRip.Dual Audio.Hindi+Eng.XviD.SDR-Release -=![Postarbhai]!=-.avi) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 16:35:46.967 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Avatar.2009.DvDRip.Dual Audio.Hindi+Eng.XviD.SDR-Release -=![Postarbhai]!=-.avi
2010-12-19 16:35:58.267 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:35:58.267 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:36:01.873 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:36:01.873 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:36:14.190 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:36:14.190 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:36:23.357 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:36:23.358 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:36:31.195 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:36:31.195 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:36:39.189 buildFileList directory = myth://Videos@steeleweb/media/movies/
2010-12-19 16:36:39.189 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@steeleweb/media/movies/)
2010-12-19 16:36:39.198 buildFileList directory = myth://Videos@steeleweb/var/lib/mythtv/videos/
2010-12-19 16:36:39.198 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@steeleweb/var/lib/mythtv/videos/)
2010-12-19 16:36:41.016 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:36:41.016 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:36:42.197 TV: Attempting to change from None to WatchingVideo
2010-12-19 16:36:42.719 RingBuf(myth://Videos@127.0.0.1:6543/Avatar.2009.DvDRip.Dual Audio.Hindi+Eng.XviD.SDR-Release -=![Postarbhai]!=-.avi) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 16:36:42.719 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Avatar.2009.DvDRip.Dual Audio.Hindi+Eng.XviD.SDR-Release -=![Postarbhai]!=-.avi
2010-12-19 16:36:51.186 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:36:51.186 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:36:55.606 TV: Attempting to change from None to WatchingVideo
2010-12-19 16:36:56.115 RingBuf(myth://Videos@127.0.0.1:6543/Avatar.2009.DvDRip.Dual Audio.Hindi+Eng.XviD.SDR-Release -=![Postarbhai]!=-.avi) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 16:36:56.115 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Avatar.2009.DvDRip.Dual Audio.Hindi+Eng.XviD.SDR-Release -=![Postarbhai]!=-.avi
2010-12-19 16:37:08.218 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 16:40:06.445 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 16:40:06.445 Using runtime prefix = /usr
2010-12-19 16:40:06.445 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 16:40:07.088 Empty LocalHostName.
2010-12-19 16:40:07.089 Using localhost value of steeleweb
2010-12-19 16:40:07.094 New DB connection, total: 1
2010-12-19 16:40:07.097 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:40:07.098 Closing DB connection named 'DBManager0'
2010-12-19 16:40:07.110 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 16:40:07.111 DPMS is disabled.
2010-12-19 16:40:07.113 Primary screen: 0.
2010-12-19 16:40:07.113 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:40:07.115 Using screen 0, 1280x960 at 0,0
2010-12-19 16:40:07.125 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 16:40:07.140 MythUI Image Cache size set to 20971520 bytes
2010-12-19 16:40:07.156 Enabled verbose msgs:  important general
2010-12-19 16:40:07.162 Primary screen: 0.
2010-12-19 16:40:07.162 Using screen 0, 1280x960 at 0,0
2010-12-19 16:40:07.163 Using theme base resolution of 1280x720
2010-12-19 16:40:07.168 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 16:40:07.168 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 16:40:07.198 Using Frameless Window
2010-12-19 16:40:07.198 Using Full Screen Window
2010-12-19 16:40:07.461 Using the Qt painter
2010-12-19 16:40:07.726 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2010-12-19 16:40:07.742 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-12-19 16:40:07.754 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 16:40:07.770 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 16:40:07.782 New DB connection, total: 2
2010-12-19 16:40:07.788 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:40:08.282 Registering Internal as a media playback plugin.
2010-12-19 16:40:08.307 Cannot load language en_us for module mytharchive
2010-12-19 16:40:08.310 Cannot load language en_us for module mythbrowser
2010-12-19 16:40:08.313 Registering WebBrowser as a media playback plugin.
2010-12-19 16:40:08.313 Cannot load language en_us for module mythbrowser
2010-12-19 16:40:08.338 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:40:08.338 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:40:08.338 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:40:08.339 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 16:40:08.339 Cannot load language en_us for module mythgallery
2010-12-19 16:40:08.345 Cannot load language en_us for module mythgame
2010-12-19 16:40:08.348 Cannot load language en_us for module mythmovies
2010-12-19 16:40:08.362 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 16:40:08.402 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 16:40:08.409 Cannot load language en_us for module mythmusic
2010-12-19 16:40:08.415 Cannot load language en_us for module mythnetvision
2010-12-19 16:40:08.420 Cannot load language en_us for module mythnews
2010-12-19 16:40:08.427 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 16:40:08.454 Cannot load language en_us for module mythvideo
2010-12-19 16:40:08.460 Cannot load language en_us for module mythweather
2010-12-19 16:40:08.462 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 16:40:08.569 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//mainmenu.xml
2010-12-19 16:40:08.572 Found mainmenu.xml for theme 'MythCenter-wide'
2010-12-19 16:40:08.886 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 16:40:08.887 Using protocol version 23056
2010-12-19 16:40:10.691 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:40:10.692 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:40:13.846 buildFileList directory = myth://Videos@steeleweb/media/movies/
2010-12-19 16:40:13.851 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@steeleweb/media/movies/)
2010-12-19 16:40:13.854 buildFileList directory = myth://Videos@steeleweb/var/lib/mythtv/videos/
2010-12-19 16:40:13.854 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@steeleweb/var/lib/mythtv/videos/)
2010-12-19 16:40:14.017 Adding :  : Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi) : NULL
2010-12-19 16:40:14.143 Adding :  : Percy Jackson And The Olympians The Lightning Thief 2010 [DVDRip.XviD.AC3-miguel] [Dubbing PL].avi : NULL
2010-12-19 16:40:17.568 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:40:17.568 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:40:19.277 TV: Attempting to change from None to WatchingVideo
2010-12-19 16:40:19.818 RingBuf(myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 16:40:19.818 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)
2010-12-19 16:40:31.417 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:40:31.417 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:40:59.432 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:40:59.433 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:41:26.447 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:41:26.447 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:41:34.662 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:41:34.663 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:41:35.421 TV: Attempting to change from None to WatchingVideo
2010-12-19 16:41:35.914 RingBuf(myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 16:41:35.915 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)
2010-12-19 16:41:49.431 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:41:49.431 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:42:00.781 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:42:00.782 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:42:01.541 TV: Attempting to change from None to WatchingVideo
2010-12-19 16:42:02.026 RingBuf(myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 16:42:02.026 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)
2010-12-19 16:42:11.748 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:42:11.748 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:42:12.481 TV: Attempting to change from None to WatchingVideo
2010-12-19 16:42:12.973 RingBuf(myth://Videos@127.0.0.1:6543/Percy Jackson And The Olympians The Lightning Thief 2010 [DVDRip.XviD.AC3-miguel] [Dubbing PL].avi) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 16:42:12.973 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Percy Jackson And The Olympians The Lightning Thief 2010 [DVDRip.XviD.AC3-miguel] [Dubbing PL].avi
2010-12-19 16:42:22.158 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 16:48:25.069 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 16:48:25.069 Using runtime prefix = /usr
2010-12-19 16:48:25.069 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 16:48:25.619 Empty LocalHostName.
2010-12-19 16:48:25.619 Using localhost value of steeleweb
2010-12-19 16:48:25.625 New DB connection, total: 1
2010-12-19 16:48:25.628 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:48:25.629 Closing DB connection named 'DBManager0'
2010-12-19 16:48:25.643 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 16:48:25.644 DPMS is disabled.
2010-12-19 16:48:25.645 Primary screen: 0.
2010-12-19 16:48:25.646 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:48:25.648 Using screen 0, 1280x960 at 0,0
2010-12-19 16:48:25.658 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 16:48:25.675 MythUI Image Cache size set to 20971520 bytes
2010-12-19 16:48:25.691 Enabled verbose msgs:  important general
2010-12-19 16:48:25.697 Primary screen: 0.
2010-12-19 16:48:25.697 Using screen 0, 1280x960 at 0,0
2010-12-19 16:48:25.698 Using theme base resolution of 1280x720
2010-12-19 16:48:25.703 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 16:48:25.703 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 16:48:25.732 Using Frameless Window
2010-12-19 16:48:25.732 Using Full Screen Window
2010-12-19 16:48:25.977 Using the Qt painter
2010-12-19 16:48:26.233 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2010-12-19 16:48:26.244 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-12-19 16:48:26.258 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 16:48:26.272 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 16:48:26.285 New DB connection, total: 2
2010-12-19 16:48:26.297 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:48:26.775 Registering Internal as a media playback plugin.
2010-12-19 16:48:26.800 Cannot load language en_us for module mytharchive
2010-12-19 16:48:26.802 Cannot load language en_us for module mythbrowser
2010-12-19 16:48:26.806 Registering WebBrowser as a media playback plugin.
2010-12-19 16:48:26.806 Cannot load language en_us for module mythbrowser
2010-12-19 16:48:26.831 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:48:26.831 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:48:26.831 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:48:26.832 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 16:48:26.832 Cannot load language en_us for module mythgallery
2010-12-19 16:48:26.838 Cannot load language en_us for module mythgame
2010-12-19 16:48:26.841 Cannot load language en_us for module mythmovies
2010-12-19 16:48:26.855 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 16:48:26.894 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 16:48:26.901 Cannot load language en_us for module mythmusic
2010-12-19 16:48:26.907 Cannot load language en_us for module mythnetvision
2010-12-19 16:48:26.912 Cannot load language en_us for module mythnews
2010-12-19 16:48:26.919 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 16:48:26.945 Cannot load language en_us for module mythvideo
2010-12-19 16:48:26.952 Cannot load language en_us for module mythweather
2010-12-19 16:48:26.954 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 16:48:27.065 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//mainmenu.xml
2010-12-19 16:48:27.068 Found mainmenu.xml for theme 'MythCenter-wide'
2010-12-19 16:48:27.375 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 16:48:27.376 Using protocol version 23056
2010-12-19 16:48:31.897 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//advanced.xml
2010-12-19 16:48:34.813 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//main_settings.xml
2010-12-19 16:48:37.180 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//media_settings.xml
2010-12-19 16:48:38.266 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 16:48:38.305 Loading menu theme from /usr/share/mythtv/video_settings.xml
2010-12-19 16:48:40.022 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:48:40.022 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:49:02.355 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:49:02.355 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:49:04.082 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:49:04.082 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:49:05.063 TV: Attempting to change from None to WatchingVideo
2010-12-19 16:49:05.575 RingBuf(myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 16:49:05.575 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)
2010-12-19 16:49:14.845 TV: Attempting to change from None to WatchingVideo
2010-12-19 16:49:15.368 RingBuf(myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 16:49:15.368 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)
2010-12-19 16:49:29.018 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:49:29.018 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:49:36.195 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:49:36.195 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:49:37.051 TV: Attempting to change from None to WatchingVideo
2010-12-19 16:49:37.544 RingBuf(myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 16:49:37.544 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)
2010-12-19 16:49:47.562 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 16:53:59.917 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 16:53:59.917 Using runtime prefix = /usr
2010-12-19 16:53:59.917 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 16:54:00.964 Empty LocalHostName.
2010-12-19 16:54:00.964 Using localhost value of steeleweb
2010-12-19 16:54:00.970 New DB connection, total: 1
2010-12-19 16:54:00.973 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:54:00.974 Closing DB connection named 'DBManager0'
2010-12-19 16:54:00.988 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 16:54:00.989 DPMS is disabled.
2010-12-19 16:54:00.995 Primary screen: 0.
2010-12-19 16:54:00.995 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:54:00.997 Using screen 0, 1280x960 at 0,0
2010-12-19 16:54:01.009 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 16:54:01.024 MythUI Image Cache size set to 20971520 bytes
2010-12-19 16:54:01.042 Enabled verbose msgs:  important general
2010-12-19 16:54:01.048 Primary screen: 0.
2010-12-19 16:54:01.049 Using screen 0, 1280x960 at 0,0
2010-12-19 16:54:01.050 Using theme base resolution of 1280x720
2010-12-19 16:54:01.055 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 16:54:01.055 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 16:54:01.087 Using Frameless Window
2010-12-19 16:54:01.087 Using Full Screen Window
2010-12-19 16:54:01.352 Using the Qt painter
2010-12-19 16:54:01.599 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2010-12-19 16:54:01.613 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-12-19 16:54:01.625 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 16:54:01.639 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 16:54:01.676 New DB connection, total: 2
2010-12-19 16:54:01.676 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:54:02.147 Registering Internal as a media playback plugin.
2010-12-19 16:54:02.172 Cannot load language en_us for module mytharchive
2010-12-19 16:54:02.174 Cannot load language en_us for module mythbrowser
2010-12-19 16:54:02.178 Registering WebBrowser as a media playback plugin.
2010-12-19 16:54:02.178 Cannot load language en_us for module mythbrowser
2010-12-19 16:54:02.203 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:54:02.203 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:54:02.203 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:54:02.204 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 16:54:02.204 Cannot load language en_us for module mythgallery
2010-12-19 16:54:02.210 Cannot load language en_us for module mythgame
2010-12-19 16:54:02.213 Cannot load language en_us for module mythmovies
2010-12-19 16:54:02.227 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 16:54:02.266 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 16:54:02.272 Cannot load language en_us for module mythmusic
2010-12-19 16:54:02.279 Cannot load language en_us for module mythnetvision
2010-12-19 16:54:02.284 Cannot load language en_us for module mythnews
2010-12-19 16:54:02.291 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 16:54:02.318 Cannot load language en_us for module mythvideo
2010-12-19 16:54:02.324 Cannot load language en_us for module mythweather
2010-12-19 16:54:02.326 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 16:54:02.431 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//mainmenu.xml
2010-12-19 16:54:02.440 Found mainmenu.xml for theme 'MythCenter-wide'
2010-12-19 16:54:02.753 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 16:54:02.755 Using protocol version 23056
2010-12-19 16:54:06.291 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:54:06.292 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:54:12.184 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//plugin_menu.xml
2010-12-19 16:54:17.901 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//advanced.xml
2010-12-19 16:54:22.637 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//main_settings.xml
2010-12-19 16:54:49.862 Received a remote 'Clear Cache' request
2010-12-19 16:54:54.208 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/appear-ui.xml
2010-12-19 16:54:58.445 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//tv_settings.xml
2010-12-19 16:56:51.411 Received a remote 'Clear Cache' request
2010-12-19 16:56:56.666 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/config-ui.xml
2010-12-19 16:57:33.848 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:57:33.848 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:57:35.419 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:57:35.419 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:57:36.386 TV: Attempting to change from None to WatchingVideo
2010-12-19 16:57:36.886 RingBuf(myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 16:57:36.886 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)
2010-12-19 16:57:47.770 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
Starting mythfrontend.real..
2010-12-19 16:58:49.421 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 16:58:49.422 Using runtime prefix = /usr
2010-12-19 16:58:49.422 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 16:58:49.985 Empty LocalHostName.
2010-12-19 16:58:49.985 Using localhost value of steeleweb
2010-12-19 16:58:49.991 New DB connection, total: 1
2010-12-19 16:58:49.994 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:58:49.995 Closing DB connection named 'DBManager0'
2010-12-19 16:58:50.008 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 16:58:50.009 DPMS is disabled.
2010-12-19 16:58:50.011 Primary screen: 0.
2010-12-19 16:58:50.012 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:58:50.014 Using screen 0, 1280x960 at 0,0
2010-12-19 16:58:50.025 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 16:58:50.039 MythUI Image Cache size set to 20971520 bytes
2010-12-19 16:58:50.055 Enabled verbose msgs:  important general
2010-12-19 16:58:50.062 Primary screen: 0.
2010-12-19 16:58:50.062 Using screen 0, 1280x960 at 0,0
2010-12-19 16:58:50.063 Using theme base resolution of 1280x720
2010-12-19 16:58:50.068 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 16:58:50.068 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 16:58:50.097 Using Frameless Window
2010-12-19 16:58:50.097 Using Full Screen Window
2010-12-19 16:58:50.344 Using the Qt painter
2010-12-19 16:58:50.585 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2010-12-19 16:58:50.599 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-12-19 16:58:50.613 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 16:58:50.623 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 16:58:51.107 Registering Internal as a media playback plugin.
2010-12-19 16:58:51.130 Cannot load language en_us for module mytharchive
2010-12-19 16:58:51.132 Cannot load language en_us for module mythbrowser
2010-12-19 16:58:51.135 Registering WebBrowser as a media playback plugin.
2010-12-19 16:58:51.136 Cannot load language en_us for module mythbrowser
2010-12-19 16:58:51.160 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:58:51.160 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:58:51.160 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 16:58:51.161 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 16:58:51.161 Cannot load language en_us for module mythgallery
2010-12-19 16:58:51.167 Cannot load language en_us for module mythgame
2010-12-19 16:58:51.170 Cannot load language en_us for module mythmovies
2010-12-19 16:58:51.184 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 16:58:51.220 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 16:58:51.227 Cannot load language en_us for module mythmusic
2010-12-19 16:58:51.233 Cannot load language en_us for module mythnetvision
2010-12-19 16:58:51.238 Cannot load language en_us for module mythnews
2010-12-19 16:58:51.245 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 16:58:51.268 Cannot load language en_us for module mythvideo
2010-12-19 16:58:51.275 Cannot load language en_us for module mythweather
2010-12-19 16:58:51.278 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 16:58:51.386 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//mainmenu.xml
2010-12-19 16:58:51.388 Found mainmenu.xml for theme 'MythCenter-wide'
2010-12-19 16:58:51.700 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 16:58:51.701 Using protocol version 23056
2010-12-19 16:58:57.186 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//advanced.xml
2010-12-19 16:58:59.027 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//main_settings.xml
2010-12-19 16:59:01.878 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//media_settings.xml
2010-12-19 16:59:05.175 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 16:59:05.220 Loading menu theme from /usr/share/mythtv/video_settings.xml
2010-12-19 16:59:06.670 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:59:06.670 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:59:40.336 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:59:40.336 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:59:40.464 New DB connection, total: 2
2010-12-19 16:59:40.465 Connected to database 'mythconverg' at host: localhost
2010-12-19 16:59:41.650 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:59:41.650 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 16:59:42.419 TV: Attempting to change from None to WatchingVideo
2010-12-19 16:59:42.923 RingBuf(myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 16:59:42.923 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)
2010-12-19 16:59:56.702 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 16:59:56.702 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 17:00:06.453 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 17:00:06.453 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
sh: internal: not found
sh: internal: not found
2010-12-19 17:00:11.935 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 17:00:11.936 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
sh: internal: not found
2010-12-19 17:00:19.198 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 17:00:19.199 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 17:00:32.749 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 17:00:32.749 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 17:00:33.386 TV: Attempting to change from None to WatchingVideo
2010-12-19 17:00:33.882 RingBuf(myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 17:00:33.882 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)
2010-12-19 17:00:47.019 Deleting UPnP client...
Starting mythfrontend.real..
2010-12-19 17:01:09.695 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 17:01:09.695 Using runtime prefix = /usr
2010-12-19 17:01:09.695 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 17:01:10.541 Empty LocalHostName.
2010-12-19 17:01:10.541 Using localhost value of steeleweb
2010-12-19 17:01:10.547 New DB connection, total: 1
2010-12-19 17:01:10.550 Connected to database 'mythconverg' at host: localhost
2010-12-19 17:01:10.551 Closing DB connection named 'DBManager0'
2010-12-19 17:01:10.563 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 17:01:10.564 DPMS is disabled.
2010-12-19 17:01:10.566 Primary screen: 0.
2010-12-19 17:01:10.567 Connected to database 'mythconverg' at host: localhost
2010-12-19 17:01:10.568 Using screen 0, 1280x960 at 0,0
2010-12-19 17:01:10.579 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 17:01:10.594 MythUI Image Cache size set to 20971520 bytes
2010-12-19 17:01:10.610 Enabled verbose msgs:  important general
2010-12-19 17:01:10.616 Primary screen: 0.
2010-12-19 17:01:10.616 Using screen 0, 1280x960 at 0,0
2010-12-19 17:01:10.617 Using theme base resolution of 1280x720
2010-12-19 17:01:10.622 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 17:01:10.622 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 17:01:10.652 Using Frameless Window
2010-12-19 17:01:10.652 Using Full Screen Window
2010-12-19 17:01:10.896 Using the Qt painter
2010-12-19 17:01:11.143 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2010-12-19 17:01:11.161 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-12-19 17:01:11.172 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 17:01:11.184 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 17:01:11.670 Registering Internal as a media playback plugin.
2010-12-19 17:01:11.693 Cannot load language en_us for module mytharchive
2010-12-19 17:01:11.695 Cannot load language en_us for module mythbrowser
2010-12-19 17:01:11.698 Registering WebBrowser as a media playback plugin.
2010-12-19 17:01:11.698 Cannot load language en_us for module mythbrowser
2010-12-19 17:01:11.722 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 17:01:11.722 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 17:01:11.723 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 17:01:11.723 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 17:01:11.724 Cannot load language en_us for module mythgallery
2010-12-19 17:01:11.730 Cannot load language en_us for module mythgame
2010-12-19 17:01:11.732 Cannot load language en_us for module mythmovies
2010-12-19 17:01:11.747 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 17:01:11.782 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 17:01:11.788 Cannot load language en_us for module mythmusic
2010-12-19 17:01:11.795 Cannot load language en_us for module mythnetvision
2010-12-19 17:01:11.799 Cannot load language en_us for module mythnews
2010-12-19 17:01:11.807 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 17:01:11.830 Cannot load language en_us for module mythvideo
2010-12-19 17:01:11.837 Cannot load language en_us for module mythweather
2010-12-19 17:01:11.839 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 17:01:11.944 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//mainmenu.xml
2010-12-19 17:01:11.956 Found mainmenu.xml for theme 'MythCenter-wide'
2010-12-19 17:01:12.264 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 17:01:12.265 Using protocol version 23056
2010-12-19 17:01:14.915 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//advanced.xml
2010-12-19 17:01:16.595 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//main_settings.xml
2010-12-19 17:01:18.968 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//media_settings.xml
2010-12-19 17:01:19.920 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 17:01:19.961 Loading menu theme from /usr/share/mythtv/video_settings.xml
2010-12-19 17:01:21.404 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 17:01:21.404 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 17:02:37.974 Deleting UPnP client...
Starting mythfrontend.real..
2010-12-19 20:17:16.085 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-12-19 20:17:16.086 Using runtime prefix = /usr
2010-12-19 20:17:16.086 Using configuration directory = /home/steeleweb/.mythtv
2010-12-19 20:17:16.841 Empty LocalHostName.
2010-12-19 20:17:16.841 Using localhost value of steeleweb
2010-12-19 20:17:16.852 New DB connection, total: 1
2010-12-19 20:17:16.856 Connected to database 'mythconverg' at host: localhost
2010-12-19 20:17:16.857 Closing DB connection named 'DBManager0'
2010-12-19 20:17:16.932 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-19 20:17:17.096 DPMS is disabled.
2010-12-19 20:17:17.107 Primary screen: 0.
2010-12-19 20:17:17.107 Connected to database 'mythconverg' at host: localhost
2010-12-19 20:17:17.513 Using screen 0, 1280x960 at 0,0
2010-12-19 20:17:17.620 Desktop video mode: 1280x960 60.0024 Hz
2010-12-19 20:17:17.734 MythUI Image Cache size set to 20971520 bytes
2010-12-19 20:17:17.957 Enabled verbose msgs:  important general
2010-12-19 20:17:18.229 Primary screen: 0.
2010-12-19 20:17:18.229 Using screen 0, 1280x960 at 0,0
2010-12-19 20:17:18.310 Using theme base resolution of 1280x720
2010-12-19 20:17:18.330 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-19 20:17:18.330 JoystickMenuThread Error: Joystick disabled - Failed to read /home/steeleweb/.mythtv/joystickmenurc
2010-12-19 20:17:18.403 Using Frameless Window
2010-12-19 20:17:18.403 Using Full Screen Window
2010-12-19 20:17:20.232 Using the Qt painter
2010-12-19 20:17:20.757 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2010-12-19 20:17:20.772 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-12-19 20:17:20.963 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-12-19 20:17:21.113 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-19 20:17:24.665 Registering Internal as a media playback plugin.
2010-12-19 20:17:24.851 Cannot load language en_us for module mytharchive
2010-12-19 20:17:25.046 Cannot load language en_us for module mythbrowser
2010-12-19 20:17:25.053 Registering WebBrowser as a media playback plugin.
2010-12-19 20:17:25.054 Cannot load language en_us for module mythbrowser
2010-12-19 20:17:25.886 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 20:17:25.887 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 20:17:25.887 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-19 20:17:25.887 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-19 20:17:25.888 Cannot load language en_us for module mythgallery
2010-12-19 20:17:26.004 Cannot load language en_us for module mythgame
2010-12-19 20:17:26.070 Cannot load language en_us for module mythmovies
2010-12-19 20:17:29.148 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-19 20:17:29.248 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-19 20:17:29.271 Cannot load language en_us for module mythmusic
2010-12-19 20:17:29.484 Cannot load language en_us for module mythnetvision
2010-12-19 20:17:29.521 Cannot load language en_us for module mythnews
2010-12-19 20:17:30.210 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-12-19 20:17:30.293 Cannot load language en_us for module mythvideo
2010-12-19 20:17:30.368 Cannot load language en_us for module mythweather
2010-12-19 20:17:30.373 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-12-19 20:17:30.509 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//mainmenu.xml
2010-12-19 20:17:30.520 Found mainmenu.xml for theme 'MythCenter-wide'
2010-12-19 20:17:34.707 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-19 20:17:34.708 Using protocol version 23056
2010-12-19 20:17:37.198 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 20:17:37.198 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 20:17:37.824 New DB connection, total: 2
2010-12-19 20:17:37.825 Connected to database 'mythconverg' at host: localhost
2010-12-19 20:17:41.434 buildFileList directory = myth://Videos@steeleweb/media/movies/
2010-12-19 20:17:41.435 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@steeleweb/media/movies/)
2010-12-19 20:17:41.573 buildFileList directory = myth://Videos@steeleweb/var/lib/mythtv/videos/
2010-12-19 20:17:41.578 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@steeleweb/var/lib/mythtv/videos/)
2010-12-19 20:17:48.894 buildFileList directory = myth://Videos@steeleweb/media/movies/
2010-12-19 20:17:48.895 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@steeleweb/media/movies/)
2010-12-19 20:17:48.897 buildFileList directory = myth://Videos@steeleweb/var/lib/mythtv/videos/
2010-12-19 20:17:48.897 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@steeleweb/var/lib/mythtv/videos/)
2010-12-19 20:17:51.288 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/video-ui.xml
2010-12-19 20:17:51.288 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-12-19 20:17:52.526 TV: Attempting to change from None to WatchingVideo
2010-12-19 20:17:54.109 RingBuf(myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)) Warning: Peek() requested 2048 bytes, but only returning 0
2010-12-19 20:17:54.109 NVP::OpenFile(): Error, couldn't read file: myth://Videos@127.0.0.1:6543/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)
2010-12-19 20:18:03.201 Deleting UPnP client...

---

### Post by nickrout on 2010-12-19
It's hard to pick oyut the relevant bits when you post the complete log, just the bit where you tried to play the file would have sufficed.

however it looks like a problem with the ownership or permissions of the video file.

Please post the output of ```
ls -l "/var/lib/mythtv/videos/Clash of the Titans (2010) DVDRip XviD-MAXSPEED www.torentz.3xforum.ro.avi"
```

---

### Post by steeleweb on 2010-12-19
Here is what i got.


-rwx------ 1 steeleweb mythtv 1358912716 2010-08-01 23:12 /var/lib/mythtv/videos/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)

---

### Post by steeleweb on 2010-12-19
I just changed the permissions and that worked.

---

### Post by nickrout on 2010-12-20
> **steeleweb said:**
> Here is what i got.


-rwx------ 1 steeleweb mythtv 1358912716 2010-08-01 23:12 /var/lib/mythtv/videos/Clash of the Titans (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)

```
cd /var/lib/mythtv/videos
sudo chown  mythtv:mythtv * -R
sudo chmod 775 * -R
```

---

