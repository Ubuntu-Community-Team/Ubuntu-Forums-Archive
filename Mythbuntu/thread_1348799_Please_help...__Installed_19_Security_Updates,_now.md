---
title: "Please help...  Installed 19 Security Updates, now themes are broken/lost"
date: 2009-12-07
forum: Mythbuntu
---

### Post by jjuzwik on 2009-12-07
...and mythfrontend is unable to start:(

From the logs:

[SIZE="1"]Starting mythfrontend.real..
2009-12-07 15:59:43.258 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-12-07 15:59:43.258 Using runtime prefix = /usr/local
2009-12-07 15:59:43.258 Using configuration directory = /home/jjuzwik/.mythtv
2009-12-07 15:59:44.189 Empty LocalHostName.
2009-12-07 15:59:44.189 Using localhost value of mythtv-01.summerlook.net
2009-12-07 15:59:44.194 New DB connection, total: 1
2009-12-07 15:59:44.197 Connected to database 'mythconverg' at host: 10.0.0.130
2009-12-07 15:59:44.198 Closing DB connection named 'DBManager0'
2009-12-07 15:59:44.205 ScreenSaverX11Private: Gnome screen saver support enabled
2009-12-07 15:59:44.206 DPMS is active.
2009-12-07 15:59:44.207 Primary screen: 0.
2009-12-07 15:59:44.207 Connected to database 'mythconverg' at host: 10.0.0.130
2009-12-07 15:59:44.208 Using screen 0, 1920x1080 at 0,0
2009-12-07 15:59:44.225 MythUI Image Cache size set to 20971520 bytes
2009-12-07 15:59:44.225 Enabled verbose msgs:  important general
2009-12-07 15:59:44.228 Primary screen: 0.
2009-12-07 15:59:44.228 Using screen 0, 1920x1080 at 0,0
2009-12-07 15:59:44.229 Using theme base resolution of 1280x720
2009-12-07 15:59:44.231 Could not find theme: defaultmenu - Switching to default
2009-12-07 15:59:44.235 LIRC: Successfully initialized '/var/run/lirc/lircd' using '/home/jjuzwik/.mythtv/lircrc' config
2009-12-07 15:59:44.235 JoystickMenuThread Error: Joystick disabled - Failed to read /home/jjuzwik/.mythtv/joystickmenurc
2009-12-07 15:59:44.345 Using the Qt painter
2009-12-07 15:59:44.346 Removing stale cache dir: /home/jjuzwik/.mythtv/themecache/Terra.1920.1080
2009-12-07 15:59:44.386 Loaded base theme from /usr/local/share/mythtv/themes/Mythbuntu/base.xml
2009-12-07 15:59:44.387 Unable to load window 'backgroundwindow' from base
2009-12-07 15:59:44.388 New DB connection, total: 2
2009-12-07 15:59:44.389 Connected to database 'mythconverg' at host: 10.0.0.130
2009-12-07 15:59:44.389 Current MythTV Schema Version (DBSchemaVer): 1244
2009-12-07 15:59:44.488 Desktop video mode: 1920x1080 60.0024 Hz
2009-12-07 15:59:44.562 Unable to find image file: lb-rtarrow-reg.png
2009-12-07 15:59:44.562 Unable to find image file: lb-rtarrow-sel.png
2009-12-07 15:59:44.562 Unable to find image file: lb-ltarrow-reg.png
2009-12-07 15:59:44.562 Unable to find image file: lb-ltarrow-sel.png
2009-12-07 15:59:44.562 Unable to find image file: lb-rtarrow-reg.png
2009-12-07 15:59:44.562 Unable to find image file: lb-rtarrow-sel.png
2009-12-07 15:59:44.562 Unable to find image file: lb-ltarrow-reg.png
2009-12-07 15:59:44.562 Unable to find image file: lb-ltarrow-sel.png
2009-12-07 15:59:44.562 Unable to find image file: cursor.png
2009-12-07 15:59:44.562 Unable to find image file: progressbar_fill.png
2009-12-07 15:59:44.562 Unable to find image file: progressbar_background.png
2009-12-07 15:59:44.707 Unable to find image file: progressbar_background.png
2009-12-07 15:59:44.708 Unable to find image file: progressbar_fill.png
2009-12-07 15:59:44.708 Unable to find image file: cursor.png
2009-12-07 15:59:44.708 Unable to find image file: cursor.png
2009-12-07 15:59:44.708 Unable to find image file: cursor.png
2009-12-07 15:59:44.708 Unable to find image file: shared/directory.png
2009-12-07 15:59:44.709 Unable to find image file: shared/updirectory.png
2009-12-07 15:59:44.709 Unable to find image file: shared/directory.png
2009-12-07 15:59:44.709 Unable to find image file: shared/executable.png
2009-12-07 15:59:44.709 Unable to find image file: shared/directory.png
2009-12-07 15:59:44.709 Unable to find image file: shared/directory.png
2009-12-07 15:59:44.709 Unable to find image file: shared/directory.png
2009-12-07 15:59:44.709 Unable to find image file: shared/updirectory.png
2009-12-07 15:59:44.709 Unable to find image file: shared/file.png
2009-12-07 15:59:44.709 Unable to find image file: shared/executable.png
2009-12-07 15:59:44.709 Unable to find image file: shared/file.png
2009-12-07 15:59:44.709 Unable to find image file: shared/directory.png
2009-12-07 15:59:44.709 Unable to find image file: shared/updirectory.png
2009-12-07 15:59:44.709 Unable to find image file: shared/executable.png
2009-12-07 15:59:44.709 Unable to find image file: shared/file.png
2009-12-07 15:59:45.014 Registering Internal as a media playback plugin.
2009-12-07 15:59:45.031 Registering WebBrowser as a media playback plugin.
2009-12-07 15:59:45.075 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
                        eno: No such file or directory (2)
2009-12-07 15:59:45.077 MMUnix::AddDevice() Error: failed to stat /dev/power, 
                        eno: No such file or directory (2)
2009-12-07 15:59:45.079 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
                        eno: No such file or directory (2)
2009-12-07 15:59:45.117 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
                        eno: No such file or directory (2)
2009-12-07 15:59:45.122 MMUnix::AddDevice() Error: failed to stat /dev/power, 
                        eno: No such file or directory (2)
2009-12-07 15:59:45.125 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
                        eno: No such file or directory (2)
2009-12-07 15:59:45.128 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-12-07 15:59:45.140 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-12-07 15:59:45.170 Starting update of NWS-XML
2009-12-07 15:59:45.184 Starting update of NDFD-6_day
2009-12-07 15:59:45.188 Starting update of Animated-Map-Download
2009-12-07 15:59:45.191 Starting update of Map-Download
2009-12-07 15:59:45.228 Loading window theme from /usr/local/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-12-07 15:59:45.245 MythThemedMenu: Couldn't read menu file mainmenu.xml
2009-12-07 15:59:45.245 Couldn't find mainmenu.xml for theme 'Mythbuntu'
2009-12-07 15:59:51.533 Overriding broken theme 'Mythbuntu' with 'Terra'
2009-12-07 15:59:51.533 Could not find theme: Terra
2009-12-07 15:59:51.535 Primary screen: 0.
2009-12-07 15:59:51.535 Using screen 0, 1920x1080 at 0,0
2009-12-07 15:59:51.535 Could not find theme: Terra
2009-12-07 15:59:51.535 WARNING: The theme () is missing a themeinfo.xml file, ignoring.
2009-12-07 15:59:51.536 Using theme base resolution of 800x600
2009-12-07 15:59:51.539 Could not find theme: defaultmenu - Switching to default
2009-12-07 15:59:51.547 Using the Qt painter
2009-12-07 15:59:51.551 Unable to load window 'backgroundwindow' from base
2009-12-07 15:59:51.552 Error loading image to scale, from file: /
2009-12-07 15:59:51.552 Removing stale cache dir: /home/jjuzwik/.mythtv/themecache/Mythbuntu.1920.1080
2009-12-07 15:59:51.563 Loading window theme from /menu-ui.xml
2009-12-07 15:59:51.563 Loading window theme from /usr/local/share/mythtv/themes/default/menu-ui.xml
2009-12-07 15:59:51.563 Loading window theme from /tmp/menu-ui.xml
2009-12-07 15:59:51.563 Unable to load window 'mainmenu' from menu-ui.xml
2009-12-07 15:59:51.563 Couldn't find mainmenu.xml for theme 'Terra'
2009-12-07 15:59:51.563 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
QWaitCondition: cv destroy failure: 
QWaitCondition: mutex destroy failure:[/SIZE]

I verified that the theme directories, and all the usual themes are there!

arrrrrrrghhhhh!

---

