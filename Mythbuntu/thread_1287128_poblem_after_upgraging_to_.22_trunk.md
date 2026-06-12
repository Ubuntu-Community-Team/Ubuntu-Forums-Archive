---
title: "poblem after upgraging to .22 trunk"
date: 2009-10-09
forum: Mythbuntu
---

### Post by texklemer on 2009-10-09
i just upgraded to .22 to take advangatge of my HDPVR   i'm getting the following when i try to start mythtv any ideas?

2009-10-09 18:38:28.485 mythfrontend version: trunk [22322] [www.mythtv.org](www.mythtv.org)
2009-10-09 18:38:28.517 Using runtime prefix = /usr
2009-10-09 18:38:28.517 Using configuration directory = /home/tycen/.mythtv
2009-10-09 18:38:29.213 Empty LocalHostName.
2009-10-09 18:38:29.213 Using localhost value of mythtvlr
2009-10-09 18:38:29.225 New DB connection, total: 1
2009-10-09 18:38:29.232 Connected to database 'mythconverg' at host: localhost
2009-10-09 18:38:29.234 Closing DB connection named 'DBManager0'
2009-10-09 18:38:29.258 ScreenSaverX11Private: Gnome screen saver support enabled
2009-10-09 18:38:29.260 DPMS is active.
2009-10-09 18:38:29.263 Primary screen: 0.
2009-10-09 18:38:29.265 Connected to database 'mythconverg' at host: localhost
2009-10-09 18:38:29.267 Using screen 0, 1920x1080 at 0,0
2009-10-09 18:38:29.289 MythUI Image Cache size set to 20971520 bytes
2009-10-09 18:38:29.291 Enabled verbose msgs:  important general
2009-10-09 18:38:29.327 Connecting to lcd server: localhost:6545 (try 1 of 10)
2009-10-09 18:38:29.348 Primary screen: 0.
2009-10-09 18:38:29.350 Using screen 0, 1920x1080 at 0,0
2009-10-09 18:38:29.352 Using theme base resolution of 1280x720
2009-10-09 18:38:29.367 LIRC: Successfully initialized '/dev/lircd' using '/home/tycen/.mythtv/lircrc' config
2009-10-09 18:38:29.367 JoystickMenuThread Error: Joystick disabled - Failed to read /home/tycen/.mythtv/joystickmenurc
2009-10-09 18:38:29.714 Using the Qt painter
2009-10-09 18:38:29.778 Theme error: Font needs a face
Type: 'font'
Name: 'clock'
Line: 8
2009-10-09 18:38:29.779 Theme error: Font needs a face
Type: 'font'
Name: 'small'
Line: 16
2009-10-09 18:38:29.779 Theme error: Font needs a face
Type: 'font'
Name: 'medium'
Line: 24
2009-10-09 18:38:29.779 Theme error: Font needs a face
Type: 'font'
Name: 'large'
Line: 32
2009-10-09 18:38:29.783 Loaded base theme from /usr/share/mythtv/themes/blootube-wide/base.xml
2009-10-09 18:38:29.790 Current MythTV Schema Version (DBSchemaVer): 1244
2009-10-09 18:38:30.607 Desktop video mode: 1920x1080 60.0024 Hz
2009-10-09 18:38:30.911 Registering Internal as a media playback plugin.
2009-10-09 18:38:30.959 Registering WebBrowser as a media playback plugin.
2009-10-09 18:38:31.061 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
            eno: No such file or directory (2)
2009-10-09 18:38:31.070 MMUnix::AddDevice() Error: failed to stat /dev/power, 
            eno: No such file or directory (2)
2009-10-09 18:38:31.077 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-10-09 18:38:31.126 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-10-09 18:38:31.189 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-10-09 18:38:31.203 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-10-09 18:38:31.242 Loading window theme from /usr/share/mythtv/themes/blootube-wide/menu-ui.xml
2009-10-09 18:38:31.242 Loading window theme from /usr/share/mythtv/themes/default-wide/menu-ui.xml
2009-10-09 18:38:31.242 Loading window theme from /usr/share/mythtv/themes/default/menu-ui.xml
2009-10-09 18:38:31.242 Loading window theme from /tmp/menu-ui.xml
2009-10-09 18:38:31.242 Unable to load window 'mainmenu' from menu-ui.xml
2009-10-09 18:38:31.242 Couldn't find mainmenu.xml for theme 'blootube-wide'
2009-10-09 18:38:31.243 Overridding broken theme 'blootube-wide' with 'Terra'
2009-10-09 18:38:31.244 Primary screen: 0.
2009-10-09 18:38:31.245 Using screen 0, 1920x1080 at 0,0
2009-10-09 18:38:31.246 Using theme base resolution of 1280x720
2009-10-09 18:38:31.253 Using the Qt painter
2009-10-09 18:38:31.255 Theme error: Font needs a face
Type: 'font'
Name: 'clock'
Line: 8
2009-10-09 18:38:31.255 Theme error: Font needs a face
Type: 'font'
Name: 'small'
Line: 16
2009-10-09 18:38:31.255 Theme error: Font needs a face
Type: 'font'
Name: 'medium'
Line: 24
2009-10-09 18:38:31.255 Theme error: Font needs a face
Type: 'font'
Name: 'large'
Line: 32
2009-10-09 18:38:31.256 Loaded base theme from /usr/share/mythtv/themes/blootube-wide/base.xml
2009-10-09 18:38:31.258 Loading window theme from /usr/share/mythtv/themes/blootube-wide/menu-ui.xml
2009-10-09 18:38:31.258 Loading window theme from /usr/share/mythtv/themes/default-wide/menu-ui.xml
2009-10-09 18:38:31.258 Loading window theme from /usr/share/mythtv/themes/default/menu-ui.xml
2009-10-09 18:38:31.258 Loading window theme from /tmp/menu-ui.xml
2009-10-09 18:38:31.258 Unable to load window 'mainmenu' from menu-ui.xml
2009-10-09 18:38:31.258 Couldn't find mainmenu.xml for theme 'Terra'
2009-10-09 18:38:31.258 Deleting UPnP client...
QWaitCondition: cv destroy failure: 
QWaitCondition: mutex destroy failure:

---

### Post by dano1 on 2009-10-10
looks like an unsupported theme. I believe all OSD themes are supported, others will crash. Am using avenards repos with .22 trunk update and was noted on his website to disable all themes except osd for this reason. 


[http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/8/27_Trunk___MythTV.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/8/27_Trunk___MythTV.html)

hth, danny

---

### Post by Nikas on 2009-10-10
> **dano1 said:**
> looks like an unsupported theme. I believe all OSD themes are supported, others will crash. Am using avenards repos with .22 trunk update and was noted on his website to disable all themes except osd for this reason. 


[http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/8/27_Trunk___MythTV.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/8/27_Trunk___MythTV.html)

hth, danny

Where is the .22 repo? Cant find it.

---

### Post by dano1 on 2009-10-10
> **Nikas said:**
> Where is the .22 repo? Cant find it.

read notes on how to upgrade and repos to activate.

hth, danny

---

