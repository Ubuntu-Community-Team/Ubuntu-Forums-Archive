---
title: "Playing avis from camera"
date: 2009-12-31
forum: Mythbuntu
---

### Post by timswait on 2009-12-31
I've got a load of pictures and videos taken with a compact digital camera. The videos are low quality avi, they play fine when I open them in a browser window with vlc. However they won't play with Myth. Other video files taken on another camera as mpg do play fine in Myth. I've tried setting the avi file type in video settings to play with the internal player, in this case nothing happens when the file is opened, the screen goes momentarily blank and then back to where I was. I've tried```
vlc file://%s vlc:quit 
```, and in this case vlc comes up with an error message to the effect of the file can't be opened. I've tried opening them in the Image Gallery in Myth, and in this case Mythtv just shuts down. Here's an output from this case:
```
2009-12-31 11:30:34.205 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-12-31 11:30:34.223 Using runtime prefix = /usr
2009-12-31 11:30:34.223 Using configuration directory = /home/rosebank/.mythtv
2009-12-31 11:30:34.913 Empty LocalHostName.
2009-12-31 11:30:34.913 Using localhost value of rosebank-myth
2009-12-31 11:30:34.919 New DB connection, total: 1
2009-12-31 11:30:34.923 Connected to database 'mythconverg' at host: localhost
2009-12-31 11:30:34.923 Closing DB connection named 'DBManager0'
2009-12-31 11:30:34.934 ScreenSaverX11Private: Gnome screen saver support enabled
2009-12-31 11:30:34.935 DPMS is disabled.
2009-12-31 11:30:34.937 Primary screen: 0.
2009-12-31 11:30:34.937 Connected to database 'mythconverg' at host: localhost
2009-12-31 11:30:34.938 Using screen 0, 1920x1080 at 0,0
2009-12-31 11:30:34.956 MythUI Image Cache size set to 20971520 bytes
2009-12-31 11:30:34.957 Enabled verbose msgs:  important general
2009-12-31 11:30:34.962 Primary screen: 0.
2009-12-31 11:30:34.962 Using screen 0, 1920x1080 at 0,0
2009-12-31 11:30:34.963 Using theme base resolution of 1280x720
2009-12-31 11:30:34.969 LIRC: Successfully initialized '/dev/lircd' using '/home/rosebank/.mythtv/lircrc' config
2009-12-31 11:30:34.969 JoystickMenuThread Error: Joystick disabled - Failed to read /home/rosebank/.mythtv/joystickmenurc
2009-12-31 11:30:35.249 Using the OpenGL painter
2009-12-31 11:30:35.428 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-12-31 11:30:35.433 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-12-31 11:30:35.452 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-12-31 11:30:35.452 Unable to load window 'backgroundwindow' from base
2009-12-31 11:30:35.459 Current MythTV Schema Version (DBSchemaVer): 1244
2009-12-31 11:30:35.460 New DB connection, total: 2
2009-12-31 11:30:35.464 Connected to database 'mythconverg' at host: localhost
2009-12-31 11:30:35.735 Desktop video mode: 1920x1080 60.0024 Hz
2009-12-31 11:30:35.889 Registering Internal as a media playback plugin.
2009-12-31 11:30:35.914 Cannot load language en_gb for module mytharchive
2009-12-31 11:30:35.949 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-12-31 11:30:35.957 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-12-31 11:30:35.961 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-12-31 11:30:35.966 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-12-31 11:30:35.966 Cannot load language en_gb for module mythgallery
2009-12-31 11:30:35.969 Cannot load language en_gb for module mythmovies
2009-12-31 11:30:35.989 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-12-31 11:30:36.032 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-12-31 11:30:36.038 Cannot load language en_gb for module mythmusic
2009-12-31 11:30:36.044 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-12-31 11:30:36.084 Cannot load language en_gb for module mythvideo
2009-12-31 11:30:36.090 Cannot load language en_gb for module mythweather
2009-12-31 11:30:36.097 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-12-31 11:30:36.159 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-12-31 11:30:36.161 Found mainmenu.xml for theme 'Mythbuntu'
2009-12-31 11:30:37.593 Using NV NPOT texture extension
2009-12-31 11:30:37.812 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-12-31 11:30:37.813 Using protocol version 50
2009-12-31 11:30:40.094 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2009-12-31 11:30:41.723 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2009-12-31 11:30:42.184 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@rosebank-myth/mnt/windocs/daysout/)
2009-12-31 11:30:43.157 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@rosebank-myth/mnt/windocs/pictures/)
2009-12-31 11:30:46.083 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@rosebank-myth/var/lib/mythtv/oldrecordings/)
2009-12-31 11:30:46.090 MythVideo::ScanVideoDirectory Scanning (/var/lib/oldrecordings)
2009-12-31 11:30:46.090 MythVideo::ScanVideoDirectory failed to scan /var/lib/oldrecordings
2009-12-31 11:30:46.090 MythVideo::ScanVideoDirectory Scanning (/ /mnt/windocs/films)
2009-12-31 11:30:46.090 MythVideo::ScanVideoDirectory failed to scan / /mnt/windocs/films
2009-12-31 11:30:46.090 MythVideo::ScanVideoDirectory Scanning (/ /mnt/windocs/daysout)
2009-12-31 11:30:46.090 MythVideo::ScanVideoDirectory failed to scan / /mnt/windocs/daysout
2009-12-31 11:30:46.090 MythVideo::ScanVideoDirectory Scanning (/ /mnt/windocs/pictures)
2009-12-31 11:30:46.090 MythVideo::ScanVideoDirectory failed to scan / /mnt/windocs/pictures
2009-12-31 11:30:57.482 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
sh: internal: not found
2009-12-31 11:31:06.935 Deleting UPnP client...
Error in my_thread_global_
```
I don't understand why it's saying "failed to scan directory", because all the video files appear there. The "sh: internal: not found" bit is a problem I assume, but why is it having a problem with avi files when it plays mpg fine? (and as I say the avi files play fine in vlc).
Oh, and I have all the proprietary codecs enabled.

---

