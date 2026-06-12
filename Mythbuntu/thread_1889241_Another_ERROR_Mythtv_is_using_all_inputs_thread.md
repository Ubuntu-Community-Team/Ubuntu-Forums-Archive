---
title: "Another ERROR: Mythtv is using all inputs thread"
date: 2011-12-01
forum: Mythbuntu
---

### Post by trevs.bronco on 2011-12-01
Hi Everyone,

I have a fresh install of 11.10 in my machine using my old database. The only hardware change is a new hard drive. Most posts I have seen on the issue have a database connection problem or the tuners are not configured correctly. I don't appear to have those problems from what I can see. Here is my frontend log.

```
shaw@Myth-Hybrid:~$ mythfrontend
QGtkStyle was unable to detect the current GTK+ theme.
2011-11-30 21:38:21.448 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
2011-11-30 21:38:21.448 Using runtime prefix = /usr
2011-11-30 21:38:21.448 Using configuration directory = /home/shaw/.mythtv
2011-11-30 21:38:21.449 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-11-30 21:38:22.393 Empty LocalHostName.
2011-11-30 21:38:22.393 Using localhost value of Myth-Hybrid
2011-11-30 21:38:22.441 New DB connection, total: 1
2011-11-30 21:38:22.448 Connected to database 'mythconverg' at host: Myth-Hybrid
2011-11-30 21:38:22.454 Closing DB connection named 'DBManager0'
2011-11-30 21:38:22.456 Connected to database 'mythconverg' at host: Myth-Hybrid
2011-11-30 21:38:22.458 Current locale en_CA
2011-11-30 21:38:22.459 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
2011-11-30 21:38:22.680 ScreenSaverX11Private: XScreenSaver support enabled
2011-11-30 21:38:22.682 DPMS is disabled.
2011-11-30 21:38:22.700 Desktop video mode: 1360x768 60.015 Hz
2011-11-30 21:38:22.732 Enabled verbose msgs:  important general
2011-11-30 21:38:22.737 Loading en_ca translation for module mythfrontend
2011-11-30 21:38:22.750 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-11-30 21:38:22.751 JoystickMenuThread: Joystick disabled - Failed to read /home/shaw/.mythtv/joystickmenurc
2011-11-30 21:38:22.804 Using Frameless Window
2011-11-30 21:38:22.805 Using Full Screen Window
2011-11-30 21:38:22.994 Using the Qt painter
2011-11-30 21:38:23.102 Current MythTV Schema Version (DBSchemaVer): 1264
2011-11-30 21:38:23.166 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-11-30 21:38:23.166 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-11-30 21:38:23.167 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-11-30 21:38:23.167 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-11-30 21:38:23.481 Registering Internal as a media playback plugin.
2011-11-30 21:38:23.535 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-30 21:38:23.536 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-30 21:38:23.536 MediaMonitorUnix::AddDevice() - empty device path.
2011-11-30 21:38:23.538 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-11-30 21:38:23.538 Loading en_ca translation for module mythgallery
2011-11-30 21:38:23.649 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-11-30 21:38:23.671 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-11-30 21:38:23.676 Loading en_ca translation for module mythmusic
2011-11-30 21:38:23.687 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-11-30 21:38:23.696 Loading en_ca translation for module mythvideo
2011-11-30 21:38:23.705 Starting update of BBC-Current-XML
2011-11-30 21:38:23.706 BBC-Current-XML recently updated, skipping.
2011-11-30 21:38:23.706 Starting update of ENVCAN
2011-11-30 21:38:23.707 ENVCAN recently updated, skipping.
2011-11-30 21:38:23.707 Starting update of ENVCAN
2011-11-30 21:38:23.707 ENVCAN recently updated, skipping.
2011-11-30 21:38:23.708 Starting update of wunderground
2011-11-30 21:38:23.708 wunderground recently updated, skipping.
2011-11-30 21:38:23.708 Loading en_ca translation for module mythweather
2011-11-30 21:38:23.832 Found mainmenu.xml for theme 'Mythbuntu'
2011-11-30 21:38:23.964 MythCoreContext: Connecting to backend server: Myth-Hybrid:6543 (try 1 of 1)
2011-11-30 21:38:23.965 Using protocol version 63
2011-11-30 21:38:30.618 Deleting UPnP client...

```
Any one have any ideas of what or where I should look at?
Thanks,

Trev

---

### Post by tgm4883 on 2011-12-01
> **trevs.bronco said:**
> Hi Everyone,

<snip>

Any one have any ideas of what or where I should look at?
Thanks,

Trev

You should look in the backend log at /var/log/mythtv/mythbackend.log

---

### Post by trevs.bronco on 2011-12-01
Thanks for the suggestion, there is not much happening in the backend when the front end starts and I try to watch livetv. This is all that comes up, is the absence of information an indication of anything? 

```
2011-12-01 20:35:50.837 MainServer::ANN Monitor
2011-12-01 20:35:50.938 adding: Myth-Hybrid as a client (events: 0)
2011-12-01 20:35:51.056 MainServer::ANN Monitor
2011-12-01 20:35:51.155 adding: Myth-Hybrid as a client (events: 1)
```

Trev

---

### Post by tgm4883 on 2011-12-02
> **trevs.bronco said:**
> Thanks for the suggestion, there is not much happening in the backend when the front end starts and I try to watch livetv. This is all that comes up, is the absence of information an indication of anything? 

```
2011-12-01 20:35:50.837 MainServer::ANN Monitor
2011-12-01 20:35:50.938 adding: Myth-Hybrid as a client (events: 0)
2011-12-01 20:35:51.056 MainServer::ANN Monitor
2011-12-01 20:35:51.155 adding: Myth-Hybrid as a client (events: 1)
```

Trev

Not in the slightest. Anything happening when the backend starts? Can you post the whole log?

---

### Post by trevs.bronco on 2011-12-02
To try ad solve this issue I deleted all my capture cards and re-entered them.

[LIST]
[*]Initial results no change
[*]Reboot the machine, frontend can't connect to the backend
[*]Shut down backend to enter setup, check address all is still the same.
[*]start backend and frontend, now frontend tries to connect to livetv, but after waiting comes back to menu
[*]Restart machine now frontend freezes for a while if I try to watch TV.
[/LIST]
```

=== Mythfrontend Log ===


[LIST=1]
[*]Restarting mythfrontend.real...
[*]2011-12-02 10:04:18.989 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
[*]2011-12-02 10:04:18.989 Using runtime prefix = /usr
[*]2011-12-02 10:04:18.989 Using configuration directory = /home/shaw/.mythtv
[*]2011-12-02 10:04:18.990 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
[*]2011-12-02 10:04:19.936 Empty LocalHostName.
[*]2011-12-02 10:04:19.936 Using localhost value of Myth-Hybrid
[*]2011-12-02 10:04:19.982 New DB connection, total: 1
[*]2011-12-02 10:04:19.990 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:04:19.996 Closing DB connection named 'DBManager0'
[*]2011-12-02 10:04:19.998 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:04:20.000 Current locale en_CA
[*]2011-12-02 10:04:20.001 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
[*]2011-12-02 10:04:20.217 ScreenSaverX11Private: XScreenSaver support enabled
[*]2011-12-02 10:04:20.220 DPMS is disabled.
[*]2011-12-02 10:04:20.238 Desktop video mode: 1360x768 60.015 Hz
[*]2011-12-02 10:04:20.269 Enabled verbose msgs:  important general
[*]2011-12-02 10:04:20.274 Loading en_ca translation for module mythfrontend
[*]2011-12-02 10:04:20.289 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
[*]                        eno: No such file or directory (2)
[*]2011-12-02 10:04:20.290 JoystickMenuThread: Joystick disabled - Failed to read /home/shaw/.mythtv/joystickmenurc
[*]2011-12-02 10:04:20.348 Using Frameless Window
[*]2011-12-02 10:04:20.348 Using Full Screen Window
[*]2011-12-02 10:04:20.546 Using the Qt painter
[*]2011-12-02 10:04:20.726 New DB connection, total: 2
[*]2011-12-02 10:04:20.727 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:04:20.728 Current MythTV Schema Version (DBSchemaVer): 1264
[*]2011-12-02 10:04:20.797 ThemeInfo,  Warning: Unable to open themeinfo.xml for  /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
[*]2011-12-02 10:04:20.797 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
[*]2011-12-02 10:04:20.797 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
[*]2011-12-02 10:04:20.797 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
[*]2011-12-02 10:04:21.058 Registering Internal as a media playback plugin.
[*]2011-12-02 10:04:21.089 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:04:21.089 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:04:21.090 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:04:21.090 MonitorRegisterExtensions(0x100, gif,jpg,png)
[*]2011-12-02 10:04:21.090 Loading en_ca translation for module mythgallery
[*]2011-12-02 10:04:21.159 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
[*]2011-12-02 10:04:21.189  MonitorRegisterExtensions(0x40,  mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
[*]2011-12-02 10:04:21.192 Loading en_ca translation for module mythmusic
[*]2011-12-02 10:04:21.211 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
[*]2011-12-02 10:04:21.224 Loading en_ca translation for module mythvideo
[*]2011-12-02 10:04:21.240 Starting update of BBC-Current-XML
[*]2011-12-02 10:04:21.247 Starting update of ENVCAN
[*]2011-12-02 10:04:21.255 Starting update of ENVCAN
[*]2011-12-02 10:04:21.265 Starting update of wunderground
[*]2011-12-02 10:04:21.275 Loading en_ca translation for module mythweather
[*]2011-12-02 10:04:21.417 Found mainmenu.xml for theme 'Mythbuntu'
[*]2011-12-02 10:04:21.619 MythCoreContext: Connecting to backend server: Myth-Hybrid:6543 (try 1 of 1)
[*]2011-12-02 10:04:21.623 Using protocol version 63
[*]2011-12-02 10:04:22.330 'nice  /usr/share/mythtv/mythweather/scripts/uk_bbc/bbccurrentxml.pl -u ENG -d  /home/shaw/.mythtv/MythWeather/BBC-Current-XML 3778' has exited
[*]2011-12-02 10:04:22.415 'nice  /usr/share/mythtv/mythweather/scripts/ca_envcan/envcan.pl -u SI -d  /home/shaw/.mythtv/MythWeather/ENVCAN bc-74' has exited
[*]2011-12-02 10:04:22.855 'nice  /usr/share/mythtv/mythweather/scripts/wunderground/wunderground.pl -u SI  -d /home/shaw/.mythtv/MythWeather/wunderground Vancouver, British  Columbia' has exited
[*]2011-12-02 10:04:24.309 'nice  /usr/share/mythtv/mythweather/scripts/ca_envcan/envcan.pl -u ENG -d  /home/shaw/.mythtv/MythWeather/ENVCAN bc-74' has exited
[*]2011-12-02 10:04:40.572 MythUIHelper,  Error: LoadScaleImage(myth://Coverart@Myth-Hybrid:6543/penguins  christmas caper cover 2.jpg) failed to load image
[*]2011-12-02 10:07:28.195 Deleting UPnP client...
[*]Error in my_thread_global_end(): 1 threads didn't exit
[*]Starting mythfrontend.real..
[*]2011-12-02 10:12:13.717 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
[*]2011-12-02 10:12:13.717 Using runtime prefix = /usr
[*]2011-12-02 10:12:13.717 Using configuration directory = /home/shaw/.mythtv
[*]2011-12-02 10:12:13.717 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
[*]2011-12-02 10:12:14.661 Empty LocalHostName.
[*]2011-12-02 10:12:14.661 Using localhost value of Myth-Hybrid
[*]2011-12-02 10:12:14.693 New DB connection, total: 1
[*]2011-12-02 10:12:14.701 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:12:14.706 Closing DB connection named 'DBManager0'
[*]2011-12-02 10:12:14.708 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:12:14.711 Current locale en_CA
[*]2011-12-02 10:12:14.711 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
[*]2011-12-02 10:12:14.935 ScreenSaverX11Private: XScreenSaver support enabled
[*]2011-12-02 10:12:14.936 DPMS is disabled.
[*]2011-12-02 10:12:14.955 Desktop video mode: 1360x768 60.015 Hz
[*]2011-12-02 10:12:14.988 Enabled verbose msgs:  important general
[*]2011-12-02 10:12:14.994 Loading en_ca translation for module mythfrontend
[*]2011-12-02 10:12:15.007 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
[*]                        eno: No such file or directory (2)
[*]2011-12-02 10:12:15.007 JoystickMenuThread: Joystick disabled - Failed to read /home/shaw/.mythtv/joystickmenurc
[*]2011-12-02 10:12:15.054 Using Frameless Window
[*]2011-12-02 10:12:15.055 Using Full Screen Window
[*]2011-12-02 10:12:15.239 Using the Qt painter
[*]2011-12-02 10:12:15.343 New DB connection, total: 2
[*]2011-12-02 10:12:15.343 New DB connection, total: 3
[*]2011-12-02 10:12:15.345 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:12:15.346 Current MythTV Schema Version (DBSchemaVer): 1264
[*]2011-12-02 10:12:15.351 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:12:15.453 ThemeInfo,  Warning: Unable to open themeinfo.xml for  /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
[*]2011-12-02 10:12:15.453 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
[*]2011-12-02 10:12:15.454 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
[*]2011-12-02 10:12:15.454 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
[*]2011-12-02 10:12:15.883 Registering Internal as a media playback plugin.
[*]2011-12-02 10:12:16.004 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:12:16.004 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:12:16.005 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:12:16.006 MonitorRegisterExtensions(0x100, gif,jpg,png)
[*]2011-12-02 10:12:16.006 Loading en_ca translation for module mythgallery
[*]2011-12-02 10:12:16.276 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
[*]2011-12-02 10:12:16.343  MonitorRegisterExtensions(0x40,  mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
[*]2011-12-02 10:12:16.353 Loading en_ca translation for module mythmusic
[*]2011-12-02 10:12:16.415 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
[*]2011-12-02 10:12:16.446 Loading en_ca translation for module mythvideo
[*]2011-12-02 10:12:16.499 Starting update of BBC-Current-XML
[*]2011-12-02 10:12:16.500 BBC-Current-XML recently updated, skipping.
[*]2011-12-02 10:12:16.501 Starting update of ENVCAN
[*]2011-12-02 10:12:16.502 ENVCAN recently updated, skipping.
[*]2011-12-02 10:12:16.520 Starting update of ENVCAN
[*]2011-12-02 10:12:16.521 ENVCAN recently updated, skipping.
[*]2011-12-02 10:12:16.521 Starting update of wunderground
[*]2011-12-02 10:12:16.522 wunderground recently updated, skipping.
[*]2011-12-02 10:12:16.522 Loading en_ca translation for module mythweather
[*]2011-12-02 10:12:16.705 Found mainmenu.xml for theme 'Mythbuntu'
[*]2011-12-02 10:12:16.828 MythCoreContext: Connecting to backend server: Myth-Hybrid:6543 (try 1 of 1)
[*]2011-12-02 10:12:16.830 Using protocol version 63
[*]2011-12-02 10:12:33.147 Deleting UPnP client...
[*]Error in my_thread_global_end(): 2 threads didn't exit
[*]Starting mythfrontend.real..
[*]2011-12-02 10:14:28.723 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
[*]2011-12-02 10:14:28.723 Using runtime prefix = /usr
[*]2011-12-02 10:14:28.723 Using configuration directory = /home/shaw/.mythtv
[*]2011-12-02 10:14:28.742 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
[*]2011-12-02 10:14:29.712 Empty LocalHostName.
[*]2011-12-02 10:14:29.712 Using localhost value of Myth-Hybrid
[*]2011-12-02 10:14:29.730 New DB connection, total: 1
[*]2011-12-02 10:14:29.733 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:14:29.736 Closing DB connection named 'DBManager0'
[*]2011-12-02 10:14:29.736 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:14:29.737 Current locale en_CA
[*]2011-12-02 10:14:29.738 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
[*]2011-12-02 10:14:29.947 ScreenSaverX11Private: XScreenSaver support enabled
[*]2011-12-02 10:14:29.947 DPMS is disabled.
[*]2011-12-02 10:14:29.984 Desktop video mode: 1360x768 60.015 Hz
[*]2011-12-02 10:14:29.998 Enabled verbose msgs:  important general
[*]2011-12-02 10:14:30.033 Loading en_ca translation for module mythfrontend
[*]2011-12-02 10:14:30.146 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
[*]                        eno: No such file or directory (2)
[*]2011-12-02 10:14:30.146 JoystickMenuThread: Joystick disabled - Failed to read /home/shaw/.mythtv/joystickmenurc
[*]2011-12-02 10:14:30.209 Using Frameless Window
[*]2011-12-02 10:14:30.209 Using Full Screen Window
[*]2011-12-02 10:14:30.421 Using the Qt painter
[*]2011-12-02 10:14:30.917 Current MythTV Schema Version (DBSchemaVer): 1264
[*]2011-12-02 10:14:31.702 ThemeInfo,  Warning: Unable to open themeinfo.xml for  /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
[*]2011-12-02 10:14:31.703 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
[*]2011-12-02 10:14:31.733 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
[*]2011-12-02 10:14:31.733 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
[*]2011-12-02 10:14:32.140 Registering Internal as a media playback plugin.
[*]2011-12-02 10:14:32.214 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:14:32.214 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:14:32.214 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:14:32.215 MonitorRegisterExtensions(0x100, gif,jpg,png)
[*]2011-12-02 10:14:32.228 Loading en_ca translation for module mythgallery
[*]2011-12-02 10:14:32.535 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
[*]2011-12-02 10:14:32.577  MonitorRegisterExtensions(0x40,  mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
[*]2011-12-02 10:14:32.594 Loading en_ca translation for module mythmusic
[*]2011-12-02 10:14:32.657 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
[*]2011-12-02 10:14:32.686 Loading en_ca translation for module mythvideo
[*]2011-12-02 10:14:32.728 Starting update of BBC-Current-XML
[*]2011-12-02 10:14:32.729 BBC-Current-XML recently updated, skipping.
[*]2011-12-02 10:14:32.757 Starting update of ENVCAN
[*]2011-12-02 10:14:32.758 ENVCAN recently updated, skipping.
[*]2011-12-02 10:14:32.759 Starting update of ENVCAN
[*]2011-12-02 10:14:32.759 ENVCAN recently updated, skipping.
[*]2011-12-02 10:14:32.759 Starting update of wunderground
[*]2011-12-02 10:14:32.760 wunderground recently updated, skipping.
[*]2011-12-02 10:14:32.762 Loading en_ca translation for module mythweather
[*]2011-12-02 10:14:32.931 Found mainmenu.xml for theme 'Mythbuntu'
[*]2011-12-02 10:14:33.142 MythCoreContext: Connecting to backend server: Myth-Hybrid:6543 (try 1 of 1)
[*]2011-12-02 10:14:33.144 Using protocol version 63
[*]2011-12-02 10:14:41.800 Deleting UPnP client...
[*]Starting mythfrontend.real..
[*]2011-12-02 10:19:10.221 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
[*]2011-12-02 10:19:10.221 Using runtime prefix = /usr
[*]2011-12-02 10:19:10.221 Using configuration directory = /home/shaw/.mythtv
[*]2011-12-02 10:19:10.221 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
[*]2011-12-02 10:19:11.166 Empty LocalHostName.
[*]2011-12-02 10:19:11.166 Using localhost value of Myth-Hybrid
[*]2011-12-02 10:19:11.210 New DB connection, total: 1
[*]2011-12-02 10:19:11.218 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:19:11.223 Closing DB connection named 'DBManager0'
[*]2011-12-02 10:19:11.225 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:19:11.228 Current locale en_CA
[*]2011-12-02 10:19:11.228 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
[*]2011-12-02 10:19:11.450 ScreenSaverX11Private: XScreenSaver support enabled
[*]2011-12-02 10:19:11.452 DPMS is disabled.
[*]2011-12-02 10:19:11.472 Desktop video mode: 1360x768 60.015 Hz
[*]2011-12-02 10:19:11.504 Enabled verbose msgs:  important general
[*]2011-12-02 10:19:11.510 Loading en_ca translation for module mythfrontend
[*]2011-12-02 10:19:11.522 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
[*]                        eno: No such file or directory (2)
[*]2011-12-02 10:19:11.523 JoystickMenuThread: Joystick disabled - Failed to read /home/shaw/.mythtv/joystickmenurc
[*]2011-12-02 10:19:11.570 Using Frameless Window
[*]2011-12-02 10:19:11.571 Using Full Screen Window
[*]2011-12-02 10:19:11.768 Using the Qt painter
[*]2011-12-02 10:19:11.938 New DB connection, total: 2
[*]2011-12-02 10:19:11.939 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:19:11.941 Current MythTV Schema Version (DBSchemaVer): 1264
[*]2011-12-02 10:19:12.020 ThemeInfo,  Warning: Unable to open themeinfo.xml for  /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
[*]2011-12-02 10:19:12.020 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
[*]2011-12-02 10:19:12.021 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
[*]2011-12-02 10:19:12.021 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
[*]2011-12-02 10:19:12.352 Registering Internal as a media playback plugin.
[*]2011-12-02 10:19:12.415 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:19:12.416 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:19:12.416 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:19:12.418 MonitorRegisterExtensions(0x100, gif,jpg,png)
[*]2011-12-02 10:19:12.418 Loading en_ca translation for module mythgallery
[*]2011-12-02 10:19:12.540 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
[*]2011-12-02 10:19:12.604  MonitorRegisterExtensions(0x40,  mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
[*]2011-12-02 10:19:12.614 Loading en_ca translation for module mythmusic
[*]2011-12-02 10:19:12.644 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
[*]2011-12-02 10:19:12.673 Loading en_ca translation for module mythvideo
[*]2011-12-02 10:19:12.701 Starting update of BBC-Current-XML
[*]2011-12-02 10:19:12.702 BBC-Current-XML recently updated, skipping.
[*]2011-12-02 10:19:12.703 Starting update of ENVCAN
[*]2011-12-02 10:19:12.714 Starting update of ENVCAN
[*]2011-12-02 10:19:12.726 Starting update of wunderground
[*]2011-12-02 10:19:12.727 wunderground recently updated, skipping.
[*]2011-12-02 10:19:12.728 Loading en_ca translation for module mythweather
[*]2011-12-02 10:19:12.948 Found mainmenu.xml for theme 'Mythbuntu'
[*]2011-12-02 10:19:13.070 MythCoreContext: Connecting to backend server: Myth-Hybrid:6543 (try 1 of 1)
[*]2011-12-02 10:19:13.071 Connection to master server timed out.
[*]                        Either the server is down or the master server settings
[*]                        in mythtv-settings does not contain the proper IP address
[*]2011-12-02 10:19:13.071 Unable to  determine master backend time zone settings.  If those settings differ  from local settings, some functionality will fail.
[*]2011-12-02 10:19:14.207 'nice  /usr/share/mythtv/mythweather/scripts/ca_envcan/envcan.pl -u ENG -d  /home/shaw/.mythtv/MythWeather/ENVCAN bc-74' has exited
[*]2011-12-02 10:19:14.272 'nice  /usr/share/mythtv/mythweather/scripts/ca_envcan/envcan.pl -u SI -d  /home/shaw/.mythtv/MythWeather/ENVCAN bc-74' has exited
[*]2011-12-02 10:19:24.404 MythCoreContext: Connecting to backend server: Myth-Hybrid:6543 (try 1 of 1)
[*]2011-12-02 10:19:24.404 Connection to master server timed out.
[*]                        Either the server is down or the master server settings
[*]                        in mythtv-settings does not contain the proper IP address
[*]2011-12-02 10:19:24.405 MythCoreContext: Connecting to backend server: Myth-Hybrid:6543 (try 1 of 1)
[*]2011-12-02 10:19:24.405 Connection to master server timed out.
[*]                        Either the server is down or the master server settings
[*]                        in mythtv-settings does not contain the proper IP address
[*]2011-12-02 10:19:24.448 MythCoreContext: Connecting to backend server: Myth-Hybrid:6543 (try 1 of 1)
[*]2011-12-02 10:19:24.449 Connection to master server timed out.
[*]                        Either the server is down or the master server settings
[*]                        in mythtv-settings does not contain the proper IP address
[*]2011-12-02 10:19:24.459 MythCoreContext: Connecting to backend server: Myth-Hybrid:6543 (try 1 of 1)
[*]2011-12-02 10:19:24.459 Connection to master server timed out.
[*]                        Either the server is down or the master server settings
[*]                        in mythtv-settings does not contain the proper IP address
[*]2011-12-02 10:19:29.654 MythCoreContext: Connecting to backend server: Myth-Hybrid:6543 (try 1 of 1)
[*]2011-12-02 10:19:29.654 Connection to master server timed out.
[*]                        Either the server is down or the master server settings
[*]                        in mythtv-settings does not contain the proper IP address
[*]2011-12-02 10:19:33.200 Deleting UPnP client...
[*]Starting mythfrontend.real..
[*]2011-12-02 10:29:00.114 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
[*]2011-12-02 10:29:00.114 Using runtime prefix = /usr
[*]2011-12-02 10:29:00.114 Using configuration directory = /home/shaw/.mythtv
[*]2011-12-02 10:29:00.131 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
[*]2011-12-02 10:29:01.106 Empty LocalHostName.
[*]2011-12-02 10:29:01.107 Using localhost value of Myth-Hybrid
[*]2011-12-02 10:29:01.139 New DB connection, total: 1
[*]2011-12-02 10:29:01.146 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:29:01.152 Closing DB connection named 'DBManager0'
[*]2011-12-02 10:29:01.154 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:29:01.156 Current locale en_CA
[*]2011-12-02 10:29:01.156 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
[*]2011-12-02 10:29:01.374 ScreenSaverX11Private: XScreenSaver support enabled
[*]2011-12-02 10:29:01.376 DPMS is disabled.
[*]2011-12-02 10:29:01.464 Desktop video mode: 1360x768 60.015 Hz
[*]2011-12-02 10:29:01.497 Enabled verbose msgs:  important general
[*]2011-12-02 10:29:01.535 Loading en_ca translation for module mythfrontend
[*]2011-12-02 10:29:01.675 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
[*]                        eno: No such file or directory (2)
[*]2011-12-02 10:29:01.675 JoystickMenuThread: Joystick disabled - Failed to read /home/shaw/.mythtv/joystickmenurc
[*]2011-12-02 10:29:01.759 Using Frameless Window
[*]2011-12-02 10:29:01.759 Using Full Screen Window
[*]2011-12-02 10:29:02.099 Using the Qt painter
[*]2011-12-02 10:29:02.669 Current MythTV Schema Version (DBSchemaVer): 1264
[*]2011-12-02 10:29:02.672 New DB connection, total: 2
[*]2011-12-02 10:29:02.683 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:29:03.627 ThemeInfo,  Warning: Unable to open themeinfo.xml for  /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
[*]2011-12-02 10:29:03.628 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
[*]2011-12-02 10:29:03.667 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
[*]2011-12-02 10:29:03.667 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
[*]2011-12-02 10:29:04.331 Registering Internal as a media playback plugin.
[*]2011-12-02 10:29:04.435 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:29:04.435 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:29:04.436 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:29:04.438 MonitorRegisterExtensions(0x100, gif,jpg,png)
[*]2011-12-02 10:29:04.452 Loading en_ca translation for module mythgallery
[*]2011-12-02 10:29:04.844 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
[*]2011-12-02 10:29:04.925  MonitorRegisterExtensions(0x40,  mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
[*]2011-12-02 10:29:04.951 Loading en_ca translation for module mythmusic
[*]2011-12-02 10:29:05.060 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
[*]2011-12-02 10:29:05.101 Loading en_ca translation for module mythvideo
[*]2011-12-02 10:29:05.169 Starting update of BBC-Current-XML
[*]2011-12-02 10:29:05.171 BBC-Current-XML recently updated, skipping.
[*]2011-12-02 10:29:05.198 Starting update of ENVCAN
[*]2011-12-02 10:29:05.199 ENVCAN recently updated, skipping.
[*]2011-12-02 10:29:05.216 Starting update of ENVCAN
[*]2011-12-02 10:29:05.217 ENVCAN recently updated, skipping.
[*]2011-12-02 10:29:05.217 Starting update of wunderground
[*]2011-12-02 10:29:05.218 wunderground recently updated, skipping.
[*]2011-12-02 10:29:05.220 Loading en_ca translation for module mythweather
[*]2011-12-02 10:29:05.488 Found mainmenu.xml for theme 'Mythbuntu'
[*]2011-12-02 10:29:05.727 MythCoreContext: Connecting to backend server: Myth-Hybrid:6543 (try 1 of 1)
[*]2011-12-02 10:29:05.729 Using protocol version 63
[*]2011-12-02 10:29:10.248 TV: Attempting to change from None to WatchingLiveTV
[*]2011-12-02 10:29:10.249 MythCoreContext: Connecting to backend server: Myth-Hybrid:6543 (try 1 of 1)
[*]2011-12-02 10:29:10.250 Using protocol version 63
[*]2011-12-02 10:29:10.337 Spawning LiveTV Recorder -- begin
[*]2011-12-02 10:29:10.666 Spawning LiveTV Recorder -- end
[*]2011-12-02 10:29:10.676 We have a playbackURL(/var/lib/mythtv/livetv/2002_20111202102910.nuv) & cardtype(DUMMY)
[*]2011-12-02 10:29:10.676 We have a RingBuffer
[*]2011-12-02 10:29:50.679 TV Error: StartRecorder() -- timed out waiting for recorder to start
[*]2011-12-02 10:29:50.679 TV Error: LiveTV not successfully started
[*]Restarting mythfrontend.real...
[*]2011-12-02 10:29:51.540 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
[*]2011-12-02 10:29:51.540 Using runtime prefix = /usr
[*]2011-12-02 10:29:51.540 Using configuration directory = /home/shaw/.mythtv
[*]2011-12-02 10:29:51.540 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
[*]2011-12-02 10:29:52.485 Empty LocalHostName.
[*]2011-12-02 10:29:52.485 Using localhost value of Myth-Hybrid
[*]2011-12-02 10:29:52.517 New DB connection, total: 1
[*]2011-12-02 10:29:52.524 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:29:52.530 Closing DB connection named 'DBManager0'
[*]2011-12-02 10:29:52.532 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:29:52.534 Current locale en_CA
[*]2011-12-02 10:29:52.534 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
[*]2011-12-02 10:29:52.751 ScreenSaverX11Private: XScreenSaver support enabled
[*]2011-12-02 10:29:52.753 DPMS is disabled.
[*]2011-12-02 10:29:52.771 Desktop video mode: 1360x768 60.015 Hz
[*]2011-12-02 10:29:52.798 Enabled verbose msgs:  important general
[*]2011-12-02 10:29:52.802 Loading en_ca translation for module mythfrontend
[*]2011-12-02 10:29:52.813 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
[*]                        eno: No such file or directory (2)
[*]2011-12-02 10:29:52.813 JoystickMenuThread: Joystick disabled - Failed to read /home/shaw/.mythtv/joystickmenurc
[*]2011-12-02 10:29:52.860 Using Frameless Window
[*]2011-12-02 10:29:52.861 Using Full Screen Window
[*]2011-12-02 10:29:53.053 Using the Qt painter
[*]2011-12-02 10:29:53.163 New DB connection, total: 2
[*]2011-12-02 10:29:53.163 Current MythTV Schema Version (DBSchemaVer): 1264
[*]2011-12-02 10:29:53.164 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:29:53.164 New DB connection, total: 3
[*]2011-12-02 10:29:53.166 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:29:53.241 ThemeInfo,  Warning: Unable to open themeinfo.xml for  /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
[*]2011-12-02 10:29:53.241 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
[*]2011-12-02 10:29:53.242 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
[*]2011-12-02 10:29:53.242 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
[*]2011-12-02 10:29:53.493 Registering Internal as a media playback plugin.
[*]2011-12-02 10:29:53.524 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:29:53.525 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:29:53.525 MediaMonitorUnix::AddDevice() - empty device path.
[*]2011-12-02 10:29:53.526 MonitorRegisterExtensions(0x100, gif,jpg,png)
[*]2011-12-02 10:29:53.526 Loading en_ca translation for module mythgallery
[*]2011-12-02 10:29:53.594 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
[*]2011-12-02 10:29:53.625  MonitorRegisterExtensions(0x40,  mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
[*]2011-12-02 10:29:53.629 Loading en_ca translation for module mythmusic
[*]2011-12-02 10:29:53.645 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
[*]2011-12-02 10:29:53.658 Loading en_ca translation for module mythvideo
[*]2011-12-02 10:29:53.672 Starting update of BBC-Current-XML
[*]2011-12-02 10:29:53.672 BBC-Current-XML recently updated, skipping.
[*]2011-12-02 10:29:53.673 Starting update of ENVCAN
[*]2011-12-02 10:29:53.673 ENVCAN recently updated, skipping.
[*]2011-12-02 10:29:53.674 Starting update of ENVCAN
[*]2011-12-02 10:29:53.674 ENVCAN recently updated, skipping.
[*]2011-12-02 10:29:53.675 Starting update of wunderground
[*]2011-12-02 10:29:53.675 wunderground recently updated, skipping.
[*]2011-12-02 10:29:53.675 Loading en_ca translation for module mythweather
[*]2011-12-02 10:29:53.839 Found mainmenu.xml for theme 'Mythbuntu'
[*]2011-12-02 10:29:53.984 MythCoreContext: Connecting to backend server: Myth-Hybrid:6543 (try 1 of 1)
[*]2011-12-02 10:29:53.985 Using protocol version 63
[*]2011-12-02 10:30:50.326 Deleting UPnP client...
[*]Error in my_thread_global_end(): 2 threads didn't exit
[*]
[/LIST]

```
```


[LIST=1]
[*]=== Mythbackend Log ===
[*]=== /var/log/mythtv/mythbackend.log ===
[*]2011-12-02 10:06:18.051 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:18.084 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:18.212 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440c5ae0)
[*]2011-12-02 10:06:18.219 MainServer::ANN Playback
[*]2011-12-02 10:06:18.285 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:18.253 MythSocket(7f9c440c5ae0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:18.323 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:18.385 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:18.431 MainServer::ANN Playback
[*]2011-12-02 10:06:18.477 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:18.513 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:18.544 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:19.074 MainServer::ANN Playback
[*]2011-12-02 10:06:19.077 MainServer::ANN Playback
[*]2011-12-02 10:06:19.119 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:19.161 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:19.206 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:19.248 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:19.286 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:19.338 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:19.428 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440d4de0)
[*]2011-12-02 10:06:19.489 MythSocket(7f9c440d4de0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:19.542 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440b9990)
[*]2011-12-02 10:06:19.581 MythSocket(7f9c440b9990:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:19.651 MainServer::ANN Playback
[*]2011-12-02 10:06:19.688 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:19.698 MainServer::ANN Playback
[*]2011-12-02 10:06:19.731 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:19.763 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:19.797 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:19.841 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:19.914 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:19.977 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440e9c80)
[*]2011-12-02 10:06:20.015 MythSocket(7f9c440e9c80:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:20.862 MainServer::ANN Playback
[*]2011-12-02 10:06:20.864 MainServer::ANN Playback
[*]2011-12-02 10:06:20.897 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:20.930 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:20.967 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:21.000 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:21.031 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:21.064 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:21.339 MainServer::ANN Playback
[*]2011-12-02 10:06:21.373 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:21.408 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:21.439 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:21.606 MainServer::ANN Playback
[*]2011-12-02 10:06:21.640 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:21.675 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:21.706 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:22.482 MainServer::ANN Playback
[*]2011-12-02 10:06:22.486 MainServer::ANN Playback
[*]2011-12-02 10:06:22.523 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:22.556 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:22.593 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:22.627 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:22.657 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:22.690 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:22.788 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440e4d70)
[*]2011-12-02 10:06:22.856 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440cd460)
[*]2011-12-02 10:06:22.858 MythSocket(7f9c440e4d70:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:22.891 MythSocket(7f9c440cd460:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:22.947 MainServer::ANN Playback
[*]2011-12-02 10:06:22.948 MainServer::ANN Playback
[*]2011-12-02 10:06:22.991 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:23.024 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:23.059 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:23.094 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:23.124 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:23.158 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:23.260 MainServer, Warning: Unknown socket closing MythSocket(0x1f38fd0)
[*]2011-12-02 10:06:23.301 MythSocket(1f38fd0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:24.025 MainServer::ANN Playback
[*]2011-12-02 10:06:24.026 MainServer::ANN Playback
[*]2011-12-02 10:06:24.083 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:24.125 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:24.170 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:24.211 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:24.250 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:24.292 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:24.388 MainServer, Warning: Unknown socket closing MythSocket(0x1f213d0)
[*]2011-12-02 10:06:24.435 MythSocket(1f213d0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:24.445 MainServer, Warning: Unknown socket closing MythSocket(0x1d67de0)
[*]2011-12-02 10:06:24.518 MythSocket(1d67de0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:24.548 MainServer::ANN Playback
[*]2011-12-02 10:06:24.588 MainServer::ANN Playback
[*]2011-12-02 10:06:24.600 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:24.642 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:24.686 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:24.728 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:24.769 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:24.802 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:24.870 MainServer, Warning: Unknown socket closing MythSocket(0x1eccf30)
[*]2011-12-02 10:06:24.912 MythSocket(1eccf30:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:26.268 MainServer::ANN Playback
[*]2011-12-02 10:06:26.269 MainServer::ANN Playback
[*]2011-12-02 10:06:26.344 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:26.302 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:26.389 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:26.431 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:26.461 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:26.494 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:26.620 MainServer, Warning: Unknown socket closing MythSocket(0x1e6d4e0)
[*]2011-12-02 10:06:26.654 MythSocket(1e6d4e0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:26.726 MainServer::ANN Playback
[*]2011-12-02 10:06:26.761 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:26.797 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:26.828 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:26.995 MainServer::ANN Playback
[*]2011-12-02 10:06:27.028 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:27.064 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:27.095 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:29.027 MainServer::ANN Playback
[*]2011-12-02 10:06:29.029 MainServer::ANN Playback
[*]2011-12-02 10:06:29.070 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:29.103 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:29.140 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:29.174 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:29.203 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:29.237 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:29.362 MainServer, Warning: Unknown socket closing MythSocket(0x1f30a20)
[*]2011-12-02 10:06:29.405 MythSocket(1f30a20:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:29.513 MainServer::ANN Playback
[*]2011-12-02 10:06:29.545 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:29.582 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:29.584 MainServer::ANN Playback
[*]2011-12-02 10:06:29.612 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:29.646 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:29.724 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:29.788 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:30.677 MainServer::ANN Playback
[*]2011-12-02 10:06:30.677 MainServer::ANN Playback
[*]2011-12-02 10:06:30.721 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:30.763 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:30.808 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:30.849 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:30.888 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:30.929 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:31.209 MainServer::ANN Playback
[*]2011-12-02 10:06:31.210 MainServer::ANN Playback
[*]2011-12-02 10:06:31.246 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:31.288 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:31.332 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:31.375 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:31.413 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:31.455 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:31.579 MainServer, Warning: Unknown socket closing MythSocket(0x1ec24f0)
[*]2011-12-02 10:06:31.600 MainServer, Warning: Unknown socket closing MythSocket(0x1ec3310)
[*]2011-12-02 10:06:31.623 MythSocket(1ec24f0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:31.665 MythSocket(1ec3310:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:31.794 MainServer::ANN Playback
[*]2011-12-02 10:06:31.795 MainServer::ANN Playback
[*]2011-12-02 10:06:31.839 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:31.889 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:31.933 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:31.967 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:31.998 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:32.031 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:32.160 MainServer, Warning: Unknown socket closing MythSocket(0x1f1ba70)
[*]2011-12-02 10:06:32.217 MythSocket(1f1ba70:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:32.319 MainServer::ANN Playback
[*]2011-12-02 10:06:32.333 MainServer::ANN Playback
[*]2011-12-02 10:06:32.349 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:32.383 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:32.418 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:32.477 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:32.508 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:32.542 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:32.820 MainServer::ANN Playback
[*]2011-12-02 10:06:32.821 MainServer::ANN Playback
[*]2011-12-02 10:06:32.850 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:32.884 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:32.919 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:32.954 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:32.984 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:33.017 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:33.105 MainServer, Warning: Unknown socket closing MythSocket(0x1f1c870)
[*]2011-12-02 10:06:33.135 MythSocket(1f1c870:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:33.156 MainServer, Warning: Unknown socket closing MythSocket(0x1f2cbc0)
[*]2011-12-02 10:06:33.227 MythSocket(1f2cbc0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:33.314 MainServer::ANN Playback
[*]2011-12-02 10:06:33.347 MainServer::ANN Playback
[*]2011-12-02 10:06:33.351 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:33.385 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:33.420 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:33.453 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:33.485 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:33.518 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:33.640 MainServer, Warning: Unknown socket closing MythSocket(0x1f2a750)
[*]2011-12-02 10:06:33.687 MythSocket(1f2a750:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:33.814 MainServer::ANN Playback
[*]2011-12-02 10:06:33.815 MainServer::ANN Playback
[*]2011-12-02 10:06:33.852 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:33.894 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:33.937 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:33.981 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:34.019 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:34.061 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:34.157 MainServer, Warning: Unknown socket closing MythSocket(0x1efbc80)
[*]2011-12-02 10:06:34.204 MythSocket(1efbc80:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:34.216 MainServer, Warning: Unknown socket closing MythSocket(0x1f14ec0)
[*]2011-12-02 10:06:34.287 MythSocket(1f14ec0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:34.338 MainServer::ANN Playback
[*]2011-12-02 10:06:34.369 MainServer::ANN Playback
[*]2011-12-02 10:06:34.378 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:34.420 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:34.464 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:34.507 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:34.545 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:34.587 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:34.708 MainServer, Warning: Unknown socket closing MythSocket(0x1f30e80)
[*]2011-12-02 10:06:34.755 MythSocket(1f30e80:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:35.152 MainServer::ANN Playback
[*]2011-12-02 10:06:35.153 MainServer::ANN Playback
[*]2011-12-02 10:06:35.187 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:35.221 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:35.256 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:35.291 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:35.321 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:35.354 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:35.460 MainServer, Warning: Unknown socket closing MythSocket(0x1f1f9e0)
[*]2011-12-02 10:06:35.506 MythSocket(1f1f9e0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:35.520 MainServer, Warning: Unknown socket closing MythSocket(0x1f327e0)
[*]2011-12-02 10:06:35.572 MythSocket(1f327e0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:35.684 MainServer::ANN Playback
[*]2011-12-02 10:06:35.714 MainServer::ANN Playback
[*]2011-12-02 10:06:35.722 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:35.764 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:35.817 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:35.850 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:35.882 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:35.915 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:36.020 MainServer, Warning: Unknown socket closing MythSocket(0x1f211e0)
[*]2011-12-02 10:06:36.020 MainServer, Warning: Unknown socket closing MythSocket(0x1f39110)
[*]2011-12-02 10:06:36.058 MythSocket(1f211e0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:36.092 MythSocket(1f39110:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:37.220 MainServer::ANN Playback
[*]2011-12-02 10:06:37.220 MainServer::ANN Playback
[*]2011-12-02 10:06:37.265 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:37.299 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:37.335 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:37.369 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:37.399 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:37.459 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:37.624 MainServer, Warning: Unknown socket closing MythSocket(0x1f0cbc0)
[*]2011-12-02 10:06:37.634 MainServer, Warning: Unknown socket closing MythSocket(0x1f26010)
[*]2011-12-02 10:06:37.667 MythSocket(1f0cbc0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:37.700 MythSocket(1f26010:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:37.821 MainServer::ANN Playback
[*]2011-12-02 10:06:37.866 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:37.910 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:37.985 MainServer::ANN Playback
[*]2011-12-02 10:06:37.991 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:38.033 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:38.132 MainServer, Warning: Unknown socket closing MythSocket(0x1f2ff60)
[*]2011-12-02 10:06:38.154 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:38.242 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:38.193 MythSocket(1f2ff60:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:38.324 MainServer, Warning: Unknown socket closing MythSocket(0x1f13260)
[*]2011-12-02 10:06:38.401 MythSocket(1f13260:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:38.451 MainServer::ANN Playback
[*]2011-12-02 10:06:38.452 MainServer::ANN Playback
[*]2011-12-02 10:06:38.517 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:38.559 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:38.604 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:38.647 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:38.684 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:38.726 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:38.801 MainServer, Warning: Unknown socket closing MythSocket(0x1f323c0)
[*]2011-12-02 10:06:38.860 MainServer, Warning: Unknown socket closing MythSocket(0x1f131d0)
[*]2011-12-02 10:06:38.861 MythSocket(1f323c0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:38.902 MythSocket(1f131d0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:39.023 MainServer::ANN Playback
[*]2011-12-02 10:06:39.025 MainServer::ANN Playback
[*]2011-12-02 10:06:39.060 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:39.093 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:39.128 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:39.162 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:39.193 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:39.227 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:39.820 MainServer::ANN Playback
[*]2011-12-02 10:06:39.828 MainServer::ANN Playback
[*]2011-12-02 10:06:39.860 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:39.894 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:39.930 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:39.964 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:39.994 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:40.027 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:40.168 MainServer, Warning: Unknown socket closing MythSocket(0x1f37450)
[*]2011-12-02 10:06:40.178 MainServer, Warning: Unknown socket closing MythSocket(0x1f29200)
[*]2011-12-02 10:06:40.204 MythSocket(1f37450:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:40.237 MythSocket(1f29200:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:40.262 MainServer::ANN Playback
[*]2011-12-02 10:06:40.336 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:40.372 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:40.383 MainServer::ANN Playback
[*]2011-12-02 10:06:40.436 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:40.470 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:40.539 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:40.570 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:40.548 MainServer, Warning: Unknown socket closing MythSocket(0x1f349b0)
[*]2011-12-02 10:06:40.648 MythSocket(1f349b0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:40.877 MainServer::ANN Playback
[*]2011-12-02 10:06:40.877 MainServer::ANN Playback
[*]2011-12-02 10:06:40.914 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:40.947 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:40.982 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:41.024 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:41.064 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:41.106 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:41.188 MainServer, Warning: Unknown socket closing MythSocket(0x1f1ada0)
[*]2011-12-02 10:06:41.249 MythSocket(1f1ada0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:41.326 MainServer, Warning: Unknown socket closing MythSocket(0x1f38f30)
[*]2011-12-02 10:06:41.374 MythSocket(1f38f30:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:41.376 MainServer::ANN Playback
[*]2011-12-02 10:06:41.456 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:41.500 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:41.540 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:41.551 MainServer::ANN Playback
[*]2011-12-02 10:06:41.623 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:41.667 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:41.707 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:41.768 MainServer, Warning: Unknown socket closing MythSocket(0x1f297e0)
[*]2011-12-02 10:06:41.808 MythSocket(1f297e0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:41.821 MainServer::ANN Playback
[*]2011-12-02 10:06:41.887 MainServer::ANN Playback
[*]2011-12-02 10:06:41.891 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:41.932 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:41.976 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:42.019 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:42.058 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:42.099 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:42.244 MainServer, Warning: Unknown socket closing MythSocket(0x1f38320)
[*]2011-12-02 10:06:42.276 MythSocket(1f38320:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:42.349 MainServer::ANN Playback
[*]2011-12-02 10:06:42.383 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:42.419 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:42.475 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:42.730 MainServer::ANN Playback
[*]2011-12-02 10:06:42.767 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:42.802 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:42.834 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:43.578 MainServer::ANN Playback
[*]2011-12-02 10:06:43.580 MainServer::ANN Playback
[*]2011-12-02 10:06:43.617 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:43.650 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:43.685 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:43.721 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:43.751 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:43.784 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:43.915 MainServer, Warning: Unknown socket closing MythSocket(0x1f48160)
[*]2011-12-02 10:06:43.934 MainServer::ANN Playback
[*]2011-12-02 10:06:43.952 MythSocket(1f48160:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:43.954 MainServer::ANN Playback
[*]2011-12-02 10:06:43.985 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:44.051 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:44.089 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:44.122 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:44.152 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:44.185 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:44.265 MainServer, Warning: Unknown socket closing MythSocket(0x1f3d660)
[*]2011-12-02 10:06:44.292 MainServer, Warning: Unknown socket closing MythSocket(0x1f45720)
[*]2011-12-02 10:06:44.293 MainServer, Warning: Unknown socket closing MythSocket(0x1f32a80)
[*]2011-12-02 10:06:44.303 MythSocket(1f3d660:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:44.336 MythSocket(1f45720:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:44.370 MythSocket(1f32a80:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 34 bytes with 1 errors
[*]2011-12-02 10:06:44.377 MainServer::ANN Playback
[*]2011-12-02 10:06:44.378 MainServer::ANN Playback
[*]2011-12-02 10:06:44.503 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:44.554 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:44.599 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:44.641 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:44.688 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:44.729 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:44.848 MainServer, Warning: Unknown socket closing MythSocket(0x1f23b50)
[*]2011-12-02 10:06:44.870 MainServer::ANN Playback
[*]2011-12-02 10:06:44.889 MainServer::ANN Playback
[*]2011-12-02 10:06:44.906 MythSocket(1f23b50:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:44.946 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:44.996 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:45.091 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:45.134 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:45.180 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:45.222 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:45.340 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c38058c20)
[*]2011-12-02 10:06:45.381 MythSocket(7f9c38058c20:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:45.428 MainServer::ANN Playback
[*]2011-12-02 10:06:45.429 MainServer::ANN Playback
[*]2011-12-02 10:06:45.472 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:45.522 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:45.567 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:45.610 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:45.639 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:45.673 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:45.792 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c4405e440)
[*]2011-12-02 10:06:45.815 MainServer::ANN Playback
[*]2011-12-02 10:06:45.832 MythSocket(7f9c4405e440:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:45.837 MainServer::ANN Playback
[*]2011-12-02 10:06:45.865 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:45.932 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:45.969 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:46.007 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:46.032 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:46.065 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:46.168 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440c0ce0)
[*]2011-12-02 10:06:46.200 MythSocket(7f9c440c0ce0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:46.273 MainServer::ANN Playback
[*]2011-12-02 10:06:46.275 MainServer::ANN Playback
[*]2011-12-02 10:06:46.307 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:46.341 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:46.377 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:46.411 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:46.441 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:46.474 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:46.576 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440ca090)
[*]2011-12-02 10:06:46.605 MainServer::ANN Playback
[*]2011-12-02 10:06:46.609 MythSocket(7f9c440ca090:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:46.611 MainServer::ANN Playback
[*]2011-12-02 10:06:46.642 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:46.717 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:46.754 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:46.787 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:46.817 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:46.850 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:46.952 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440c52e0)
[*]2011-12-02 10:06:46.985 MythSocket(7f9c440c52e0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:47.183 MainServer::ANN Playback
[*]2011-12-02 10:06:47.187 MainServer::ANN Playback
[*]2011-12-02 10:06:47.218 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:47.251 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:47.288 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:47.322 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:47.351 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:47.385 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:47.512 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440d9e90)
[*]2011-12-02 10:06:47.553 MythSocket(7f9c440d9e90:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:47.563 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440daf10)
[*]2011-12-02 10:06:47.565 MainServer::ANN Playback
[*]2011-12-02 10:06:47.611 MainServer::ANN Playback
[*]2011-12-02 10:06:47.628 MythSocket(7f9c440daf10:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:47.670 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:47.712 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:47.799 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:47.841 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:47.879 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:47.921 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:47.994 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440ca730)
[*]2011-12-02 10:06:48.047 MythSocket(7f9c440ca730:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:48.142 MainServer::ANN Playback
[*]2011-12-02 10:06:48.148 MainServer::ANN Playback
[*]2011-12-02 10:06:48.179 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:48.213 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:48.250 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:48.283 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:48.313 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:48.346 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:48.416 MainServer, Warning: Unknown socket closing MythSocket(0x1f347c0)
[*]2011-12-02 10:06:48.455 MainServer::ANN Playback
[*]2011-12-02 10:06:48.456 MythSocket(1f347c0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:48.489 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:48.524 MainServer::ANN Playback
[*]2011-12-02 10:06:48.559 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:48.589 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:48.622 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:48.660 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:48.723 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:48.768 MainServer, Warning: Unknown socket closing MythSocket(0x1f42a70)
[*]2011-12-02 10:06:48.788 MainServer, Warning: Unknown socket closing MythSocket(0x1f2aaa0)
[*]2011-12-02 10:06:48.816 MythSocket(1f42a70:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:48.849 MythSocket(1f2aaa0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:48.871 MainServer::ANN Playback
[*]2011-12-02 10:06:48.874 MainServer::ANN Playback
[*]2011-12-02 10:06:48.948 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:48.982 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:49.019 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:49.053 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:49.082 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:49.115 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:49.220 MainServer, Warning: Unknown socket closing MythSocket(0x1f45120)
[*]2011-12-02 10:06:49.245 MainServer::ANN Playback
[*]2011-12-02 10:06:49.258 MythSocket(1f45120:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:49.274 MainServer::ANN Playback
[*]2011-12-02 10:06:49.291 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:49.358 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:49.395 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:49.428 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:49.458 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:49.491 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:49.683 MainServer::ANN Playback
[*]2011-12-02 10:06:49.683 MainServer::ANN Playback
[*]2011-12-02 10:06:49.716 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:49.750 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:49.787 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:49.821 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:49.850 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:49.883 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:49.943 MainServer, Warning: Unknown socket closing MythSocket(0x1f3b0e0)
[*]2011-12-02 10:06:49.985 MainServer::ANN Playback
[*]2011-12-02 10:06:50.002 MythSocket(1f3b0e0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:50.015 MainServer::ANN Playback
[*]2011-12-02 10:06:50.042 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:50.126 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:50.171 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:50.212 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:50.251 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:50.293 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:50.495 MainServer::ANN Playback
[*]2011-12-02 10:06:50.505 MainServer::ANN Playback
[*]2011-12-02 10:06:50.535 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:50.577 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:50.623 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:50.657 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:50.687 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:50.720 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:50.780 MainServer, Warning: Unknown socket closing MythSocket(0x1f3f560)
[*]2011-12-02 10:06:50.818 MainServer::ANN Playback
[*]2011-12-02 10:06:50.838 MythSocket(1f3f560:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:50.870 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:50.905 MainServer::ANN Playback
[*]2011-12-02 10:06:50.942 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:50.971 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:51.004 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:51.042 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:51.113 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:51.141 MainServer, Warning: Unknown socket closing MythSocket(0x1f38d40)
[*]2011-12-02 10:06:51.181 MythSocket(1f38d40:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:51.261 MainServer::ANN Playback
[*]2011-12-02 10:06:51.266 MainServer::ANN Playback
[*]2011-12-02 10:06:51.297 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:51.330 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:51.368 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:51.399 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:51.430 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:51.464 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:51.563 MainServer, Warning: Unknown socket closing MythSocket(0x1f3fea0)
[*]2011-12-02 10:06:51.596 MainServer, Warning: Unknown socket closing MythSocket(0x1f25c70)
[*]2011-12-02 10:06:51.598 MythSocket(1f3fea0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:51.599 MainServer::ANN Playback
[*]2011-12-02 10:06:51.632 MythSocket(1f25c70:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:51.633 MainServer::ANN Playback
[*]2011-12-02 10:06:51.698 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:51.764 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:51.801 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:51.835 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:51.865 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:51.898 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:51.993 MainServer, Warning: Unknown socket closing MythSocket(0x1f3bc60)
[*]2011-12-02 10:06:51.998 MainServer, Warning: Unknown socket closing MythSocket(0x1f45000)
[*]2011-12-02 10:06:52.006 MainServer, Warning: Unknown socket closing MythSocket(0x1f3efb0)
[*]2011-12-02 10:06:52.024 MythSocket(1f3bc60:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:52.058 MythSocket(1f45000:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 33 bytes with 1 errors
[*]2011-12-02 10:06:52.091 MythSocket(1f3efb0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:52.098 MainServer::ANN Playback
[*]2011-12-02 10:06:52.098 MainServer::ANN Playback
[*]2011-12-02 10:06:52.241 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:52.282 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:52.327 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:52.369 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:52.408 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:52.556 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:52.684 MainServer, Warning: Unknown socket closing MythSocket(0x1f3edf0)
[*]2011-12-02 10:06:52.726 MythSocket(1f3edf0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:52.735 MainServer::ANN Playback
[*]2011-12-02 10:06:52.808 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:52.818 MainServer::ANN Playback
[*]2011-12-02 10:06:52.854 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:52.892 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:52.933 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:52.978 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:53.067 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:53.141 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c4406df00)
[*]2011-12-02 10:06:53.186 MythSocket(7f9c4406df00:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:54.233 MainServer::ANN Playback
[*]2011-12-02 10:06:54.235 MainServer::ANN Playback
[*]2011-12-02 10:06:54.275 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:54.318 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:54.370 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:54.404 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:54.434 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:54.477 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:54.584 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440c3500)
[*]2011-12-02 10:06:54.619 MainServer::ANN Playback
[*]2011-12-02 10:06:54.620 MythSocket(7f9c440c3500:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:54.634 MainServer::ANN Playback
[*]2011-12-02 10:06:54.652 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:54.719 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:54.756 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:54.790 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:54.820 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:54.853 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:55.189 MainServer::ANN Playback
[*]2011-12-02 10:06:55.193 MainServer::ANN Playback
[*]2011-12-02 10:06:55.228 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:55.262 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:55.299 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:55.332 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:55.362 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:55.395 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:55.484 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440c4b00)
[*]2011-12-02 10:06:55.523 MythSocket(7f9c440c4b00:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:55.529 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c4406ee30)
[*]2011-12-02 10:06:55.532 MainServer::ANN Playback
[*]2011-12-02 10:06:55.576 MainServer::ANN Playback
[*]2011-12-02 10:06:55.589 MythSocket(7f9c4406ee30:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:55.621 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:55.655 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:55.724 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:55.758 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:55.788 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:55.821 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:55.952 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440b2b20)
[*]2011-12-02 10:06:55.998 MythSocket(7f9c440b2b20:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:56.484 MainServer::ANN Playback
[*]2011-12-02 10:06:56.530 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:56.575 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:56.614 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:56.684 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440ccec0)
[*]2011-12-02 10:06:56.723 MythSocket(7f9c440ccec0:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:56.787 MainServer::ANN Playback
[*]2011-12-02 10:06:56.831 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:56.875 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:56.914 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:56.985 MainServer, Warning: Unknown socket closing MythSocket(0x7f9c440d5790)
[*]2011-12-02 10:06:57.024 MythSocket(7f9c440d5790:-1): writeStringList: Error, socket went unconnected.
[*]                        We wrote 0 of 10 bytes with 1 errors
[*]2011-12-02 10:06:58.636 MainServer::ANN Playback
[*]2011-12-02 10:06:58.672 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:58.717 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:58.755 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:59.404 MainServer::ANN Playback
[*]2011-12-02 10:06:59.439 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:59.483 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:59.522 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:06:59.796 MainServer::ANN Playback
[*]2011-12-02 10:06:59.831 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:06:59.867 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:06:59.897 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:07:00.420 MainServer::ANN Playback
[*]2011-12-02 10:07:00.456 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:07:00.492 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:07:00.523 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:07:07.965 MainServer::ANN Playback
[*]2011-12-02 10:07:08.002 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:07:08.045 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:07:08.087 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:07:11.783 MainServer::ANN Playback
[*]2011-12-02 10:07:11.860 adding: myth-hybrid as a client (events: 0)
[*]2011-12-02 10:07:11.939 MainServer::HandleAnnounce FileTransfer
[*]2011-12-02 10:07:11.977 adding: myth-hybrid as a remote file transfer
[*]2011-12-02 10:11:41.885 mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
[*]2011-12-02 10:11:41.956 Using runtime prefix = /usr
[*]2011-12-02 10:11:41.989 Using configuration directory = /home/mythtv/.mythtv
[*]2011-12-02 10:11:42.048 Empty LocalHostName.
[*]2011-12-02 10:11:42.099 Using localhost value of Myth-Hybrid
[*]2011-12-02 10:11:42.202 New DB connection, total: 1
[*]2011-12-02 10:11:42.256 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:11:42.295 Closing DB connection named 'DBManager0'
[*]2011-12-02 10:11:42.334 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:11:42.368 Current locale en_CA
[*]2011-12-02 10:11:42.399 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
[*]2011-12-02 10:11:42.447 Current MythTV Schema Version (DBSchemaVer): 1264
[*]2011-12-02 10:11:42.490 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
[*]2011-12-02 10:11:42.609 Enabling Upnpmedia rebuild thread.
[*]2011-12-02 10:11:43.873 MythBackend: Starting up as the master server.
[*]2011-12-02 10:11:43.950 New DB connection, total: 2
[*]2011-12-02 10:11:44.008 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:11:44.051 mythbackend: MythBackend started as master server
[*]2011-12-02 10:11:44.225 TVRec(7) Error: Problem finding starting channel, setting to default of '3'.
[*]2011-12-02 10:11:44.275 ChannelBase(7) Error: InitializeInputs():
[*]                        Could not get inputs for the capturecard.
[*]                        Perhaps you have forgotten to bind video
[*]                        sources to your card's inputs?
[*]2011-12-02 10:11:44.317 New DB connection, total: 3
[*]2011-12-02 10:11:44.358 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:11:44.400 mythbackend: Problem with capture cards: Card 7failed init
[*]2011-12-02 10:11:44.443 New DB scheduler connection
[*]2011-12-02 10:11:44.483 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:11:44.525 Scheduler, Warning: Listings source 'SD' is defined, but is not attached to a card input.
[*]2011-12-02 10:11:44.603 Main::Registering HttpStatus Extension
[*]2011-12-02 10:11:44.681 Enabled verbose msgs:  important general
[*]2011-12-02 10:11:44.850 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
[*]2011-12-02 10:11:47.605 Reschedule requested for id -1.
[*]2011-12-02 10:11:47.884 Scheduled 0 items in 0.3 = 0.08 match + 0.19 place
[*]2011-12-02 10:11:47.922 scheduler: Scheduled items: Scheduled 0 items in 0.3 = 0.08 match + 0.19 place
[*]2011-12-02 10:11:48.039 Seem to be woken up by USER
[*]2011-12-02 10:11:49.044 MainServer::ANN Monitor
[*]2011-12-02 10:11:49.092 adding: Myth-Hybrid as a client (events: 0)
[*]2011-12-02 10:11:49.127 MainServer::ANN Monitor
[*]2011-12-02 10:11:49.167 adding: Myth-Hybrid as a client (events: 1)
[*]2011-12-02 10:11:49.203 Reschedule requested for id -1.
[*]2011-12-02 10:11:49.350 Scheduled 0 items in 0.1 = 0.04 match + 0.10 place
[*]2011-12-02 10:11:49.389 scheduler: Scheduled items: Scheduled 0 items in 0.1 = 0.04 match + 0.10 place
[*]2011-12-02 10:11:52.776 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
[*]2011-12-02 10:11:53.163 UPnpMedia: BuildMediaMap Done. Found 531 objects
[*]2011-12-02 10:11:53.200 UPnpMedia: BuildMediaMap VIDEO scan starting in :/mnt/HD2/videos:
[*]2011-12-02 10:11:53.542 UPnpMedia: BuildMediaMap Done. Found 488 objects
[*]2011-12-02 10:11:54.608 New DB connection, total: 4
[*]2011-12-02 10:11:54.667 mythbackend: Running housekeeping thread
[*]2011-12-02 10:11:54.669 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:12:16.830 MainServer::ANN Monitor
[*]2011-12-02 10:12:16.887 adding: Myth-Hybrid as a client (events: 0)
[*]2011-12-02 10:12:16.929 MainServer::ANN Monitor
[*]2011-12-02 10:12:16.979 adding: Myth-Hybrid as a client (events: 1)
[*]2011-12-02 10:13:39.417 mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
[*]2011-12-02 10:13:39.515 Using runtime prefix = /usr
[*]2011-12-02 10:13:39.782 Using configuration directory = /home/mythtv/.mythtv
[*]2011-12-02 10:13:39.849 Empty LocalHostName.
[*]2011-12-02 10:13:40.213 Using localhost value of Myth-Hybrid
[*]2011-12-02 10:13:40.444 New DB connection, total: 1
[*]2011-12-02 10:13:40.537 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:13:40.662 Closing DB connection named 'DBManager0'
[*]2011-12-02 10:13:40.753 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:13:40.871 Current locale en_CA
[*]2011-12-02 10:13:41.028 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
[*]2011-12-02 10:13:41.410 Current MythTV Schema Version (DBSchemaVer): 1264
[*]2011-12-02 10:13:41.600 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
[*]2011-12-02 10:13:41.741 Enabling Upnpmedia rebuild thread.
[*]2011-12-02 10:13:42.995 MythBackend: Starting up as the master server.
[*]2011-12-02 10:13:43.092 New DB connection, total: 2
[*]2011-12-02 10:13:43.147 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:13:43.185 mythbackend: MythBackend started as master server
[*]2011-12-02 10:13:43.832 TVRec(7) Error: Problem finding starting channel, setting to default of '3'.
[*]2011-12-02 10:13:44.132 ChannelBase(7) Error: InitializeInputs():
[*]                        Could not get inputs for the capturecard.
[*]                        Perhaps you have forgotten to bind video
[*]                        sources to your card's inputs?
[*]2011-12-02 10:13:44.197 New DB connection, total: 3
[*]2011-12-02 10:13:44.303 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:13:44.419 mythbackend: Problem with capture cards: Card 7failed init
[*]2011-12-02 10:13:44.514 New DB scheduler connection
[*]2011-12-02 10:13:44.561 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:13:44.646 Scheduler, Warning: Listings source 'SD' is defined, but is not attached to a card input.
[*]2011-12-02 10:13:44.740 Main::Registering HttpStatus Extension
[*]2011-12-02 10:13:44.844 Enabled verbose msgs:  important general
[*]2011-12-02 10:13:44.937 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
[*]2011-12-02 10:13:47.707 Reschedule requested for id -1.
[*]2011-12-02 10:13:47.920 Scheduled 0 items in 0.2 = 0.12 match + 0.09 place
[*]2011-12-02 10:13:47.957 scheduler: Scheduled items: Scheduled 0 items in 0.2 = 0.12 match + 0.09 place
[*]2011-12-02 10:13:48.008 Seem to be woken up by USER
[*]2011-12-02 10:13:48.719 MainServer::ANN Monitor
[*]2011-12-02 10:13:48.763 adding: Myth-Hybrid as a client (events: 0)
[*]2011-12-02 10:13:51.093 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
[*]2011-12-02 10:13:51.358 UPnpMedia: BuildMediaMap Done. Found 531 objects
[*]2011-12-02 10:13:51.394 UPnpMedia: BuildMediaMap VIDEO scan starting in :/mnt/HD2/videos:
[*]2011-12-02 10:13:51.628 UPnpMedia: BuildMediaMap Done. Found 488 objects
[*]2011-12-02 10:13:53.933 mythbackend: Running housekeeping thread
[*]2011-12-02 10:14:33.144 MainServer::ANN Monitor
[*]2011-12-02 10:14:33.204 adding: Myth-Hybrid as a client (events: 0)
[*]2011-12-02 10:14:33.247 MainServer::ANN Monitor
[*]2011-12-02 10:14:33.321 adding: Myth-Hybrid as a client (events: 1)
[*]2011-12-02 10:20:10.292 mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
[*]2011-12-02 10:20:10.358 Using runtime prefix = /usr
[*]2011-12-02 10:20:10.399 Using configuration directory = /home/mythtv/.mythtv
[*]2011-12-02 10:20:10.433 Empty LocalHostName.
[*]2011-12-02 10:20:10.466 Using localhost value of Myth-Hybrid
[*]2011-12-02 10:20:10.524 New DB connection, total: 1
[*]2011-12-02 10:20:10.565 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:20:10.605 Closing DB connection named 'DBManager0'
[*]2011-12-02 10:20:10.635 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:20:10.669 Current locale en_CA
[*]2011-12-02 10:20:10.700 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
[*]2011-12-02 10:20:10.748 Current MythTV Schema Version (DBSchemaVer): 1264
[*]2011-12-02 10:20:10.790 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
[*]2011-12-02 10:20:10.844 Enabling Upnpmedia rebuild thread.
[*]2011-12-02 10:20:12.082 MythBackend: Starting up as the master server.
[*]2011-12-02 10:20:12.131 New DB connection, total: 2
[*]2011-12-02 10:20:12.184 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:20:12.218 mythbackend: MythBackend started as master server
[*]2011-12-02 10:20:12.277 New DB connection, total: 3
[*]2011-12-02 10:20:12.318 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:20:12.450 Channel(/dev/video1) Warning: You have not set an external channel changing
[*]                        script for a composite or s-video input. Channel changing will do nothing.
[*]2011-12-02 10:20:12.501 New DB scheduler connection
[*]2011-12-02 10:20:12.543 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:20:12.585 Scheduler, Warning: Listings source 'SD' is defined, but is not attached to a card input.
[*]2011-12-02 10:20:12.626 Scheduler, Warning: Listings source 'stb' is defined, but is not attached to a card input.
[*]2011-12-02 10:20:12.671 Main::Registering HttpStatus Extension
[*]2011-12-02 10:20:12.717 Enabled verbose msgs:  important general
[*]2011-12-02 10:20:12.766 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
[*]2011-12-02 10:20:15.675 Reschedule requested for id -1.
[*]2011-12-02 10:20:15.833 Scheduled 0 items in 0.2 = 0.05 match + 0.10 place
[*]2011-12-02 10:20:15.879 scheduler: Scheduled items: Scheduled 0 items in 0.2 = 0.05 match + 0.10 place
[*]2011-12-02 10:20:15.947 Seem to be woken up by USER
[*]2011-12-02 10:20:20.976 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
[*]2011-12-02 10:20:21.407 UPnpMedia: BuildMediaMap Done. Found 531 objects
[*]2011-12-02 10:20:21.447 UPnpMedia: BuildMediaMap VIDEO scan starting in :/mnt/HD2/videos:
[*]2011-12-02 10:20:21.918 UPnpMedia: BuildMediaMap Done. Found 488 objects
[*]2011-12-02 10:20:22.677 mythbackend: Running housekeeping thread
[*]2011-12-02 10:20:30.450 MainServer::ANN Monitor
[*]2011-12-02 10:20:30.484 adding: Myth-Hybrid as a client (events: 0)
[*]2011-12-02 10:20:30.518 MainServer::ANN Monitor
[*]2011-12-02 10:20:30.567 adding: Myth-Hybrid as a client (events: 1)
[*]2011-12-02 10:20:42.561 MainServer::ANN Playback
[*]2011-12-02 10:20:42.610 adding: Myth-Hybrid as a client (events: 0)
[*]2011-12-02 10:20:42.650 TVRec(8): Changing from None to WatchingLiveTV
[*]2011-12-02 10:20:42.690 TVRec(8): HW Tuner: 8->8
[*]2011-12-02 10:20:42.759 LoadFromScheduler(): Error, called from backend.
[*]2011-12-02 10:20:42.763 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]2011-12-02 10:20:43.049 Finished recording Unknown: channel 2002
[*]2011-12-02 10:20:43.125 scheduler: Finished recording: Unknown: channel 2002
[*]2011-12-02 10:20:43.212 New DB connection, total: 4
[*]2011-12-02 10:20:43.256 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:20:43.266 LoadFromScheduler(): Error, called from backend.
[*]2011-12-02 10:20:43.298 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]2011-12-02 10:20:43.346 Finished recording Unknown: channel 2002
[*]2011-12-02 10:20:43.639  NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings,  Recording Profiles and setup the four 'Software Encoders' profiles.   Assuming RTjpeg for now.
[*]2011-12-02 10:20:43.687 NVR(/dev/video0) Error: Unknown audio codec
[*]2011-12-02 10:20:43.740 AudioInALSA(default) Error: pcm open failed: No such file or directory
[*]2011-12-02 10:20:43.830 NVR(/dev/video0) Error: Failed to open audio device ALSA:default
[*]2011-12-02 10:20:43.939 NVR(/dev/video0) Error: Failed to init audio input device
[*]2011-12-02 10:20:43.990 NVR(/dev/video0): Won't work with the streaming interface, falling back
[*]VIDIOCGCAP:: Invalid argument
[*]2011-12-02 10:20:44.075 AudioInALSA(default) Error: pcm open failed: No such file or directory
[*]2011-12-02 10:20:44.172 NVR(/dev/video0) Error: Failed to open audio device ALSA:default
[*]2011-12-02 10:20:54.317 TVRec(8): Changing from WatchingLiveTV to None
[*]2011-12-02 10:20:54.500 MainServer::ANN Playback
[*]2011-12-02 10:20:54.550 adding: Myth-Hybrid as a client (events: 0)
[*]2011-12-02 10:20:54.594 TVRec(8): Changing from None to WatchingLiveTV
[*]2011-12-02 10:20:54.638 TVRec(8): HW Tuner: 8->8
[*]2011-12-02 10:20:54.704 LoadFromScheduler(): Error, called from backend.
[*]2011-12-02 10:20:54.709 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]2011-12-02 10:20:54.785 TVRec(8): Changing from WatchingLiveTV to None
[*]2011-12-02 10:21:00.908 MainServer::ANN Playback
[*]2011-12-02 10:21:00.947 adding: Myth-Hybrid as a client (events: 0)
[*]2011-12-02 10:21:01.001 TVRec(8): Changing from None to WatchingLiveTV
[*]2011-12-02 10:21:01.036 TVRec(8): HW Tuner: 8->8
[*]2011-12-02 10:21:01.094 LoadFromScheduler(): Error, called from backend.
[*]2011-12-02 10:21:01.100 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]2011-12-02 10:21:01.269 Finished recording Unknown: channel 2002
[*]2011-12-02 10:21:01.333 LoadFromScheduler(): Error, called from backend.
[*]2011-12-02 10:21:01.336 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]2011-12-02 10:21:01.376 recording already exists...
[*]2011-12-02 10:21:01.449 Finished recording Unknown: channel 2002
[*]2011-12-02 10:21:01.599  NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings,  Recording Profiles and setup the four 'Software Encoders' profiles.   Assuming RTjpeg for now.
[*]2011-12-02 10:21:01.640 NVR(/dev/video0) Error: Unknown audio codec
[*]2011-12-02 10:21:01.675 AudioInALSA(default) Error: pcm open failed: No such file or directory
[*]2011-12-02 10:21:01.707 NVR(/dev/video0) Error: Failed to open audio device ALSA:default
[*]2011-12-02 10:21:01.740 NVR(/dev/video0) Error: Failed to init audio input device
[*]2011-12-02 10:21:01.781 NVR(/dev/video0): Won't work with the streaming interface, falling back
[*]VIDIOCGCAP:: Invalid argument
[*]2011-12-02 10:21:01.831 AudioInALSA(default) Error: pcm open failed: No such file or directory
[*]2011-12-02 10:21:01.916 NVR(/dev/video0) Error: Failed to open audio device ALSA:default
[*]2011-12-02 10:21:12.114 TVRec(8): Changing from WatchingLiveTV to None
[*]2011-12-02 10:21:12.288 MainServer::ANN Playback
[*]2011-12-02 10:21:12.327 adding: Myth-Hybrid as a client (events: 0)
[*]2011-12-02 10:21:12.364 TVRec(8): Changing from None to WatchingLiveTV
[*]2011-12-02 10:21:12.399 TVRec(8): HW Tuner: 8->8
[*]2011-12-02 10:21:12.464 LoadFromScheduler(): Error, called from backend.
[*]2011-12-02 10:21:12.469 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]2011-12-02 10:21:12.540 TVRec(8): Changing from WatchingLiveTV to None
[*]2011-12-02 10:21:32.674 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
[*]2011-12-02 10:22:57.951 mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
[*]2011-12-02 10:22:58.062 Using runtime prefix = /usr
[*]2011-12-02 10:22:58.171 Using configuration directory = /home/mythtv/.mythtv
[*]2011-12-02 10:22:58.213 Empty LocalHostName.
[*]2011-12-02 10:22:58.254 Using localhost value of Myth-Hybrid
[*]2011-12-02 10:22:58.298 New DB connection, total: 1
[*]2011-12-02 10:22:58.484 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:22:58.573 Closing DB connection named 'DBManager0'
[*]2011-12-02 10:22:58.680 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:22:58.719 Current locale en_CA
[*]2011-12-02 10:22:58.771 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
[*]2011-12-02 10:22:58.856 Current MythTV Schema Version (DBSchemaVer): 1264
[*]2011-12-02 10:22:58.892 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
[*]2011-12-02 10:22:58.986 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
[*]2011-12-02 10:22:59.049 Enabling Upnpmedia rebuild thread.
[*]2011-12-02 10:22:59.083 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
[*]2011-12-02 10:23:00.480 MythBackend: Starting up as the master server.
[*]2011-12-02 10:23:00.895 New DB connection, total: 2
[*]2011-12-02 10:23:01.064 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:23:01.214 mythbackend: MythBackend started as master server
[*]2011-12-02 10:23:01.556 New DB connection, total: 3
[*]2011-12-02 10:23:01.633 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:23:02.167 Channel(/dev/video1) Warning: You have not set an external channel changing
[*]                        script for a composite or s-video input. Channel changing will do nothing.
[*]2011-12-02 10:23:02.277 New DB scheduler connection
[*]2011-12-02 10:23:02.632 Connected to database 'mythconverg' at host: Myth-Hybrid
[*]2011-12-02 10:23:02.725 Scheduler, Warning: Listings source 'SD' is defined, but is not attached to a card input.
[*]2011-12-02 10:23:02.850 Scheduler, Warning: Listings source 'stb' is defined, but is not attached to a card input.
[*]2011-12-02 10:23:02.996 Main::Registering HttpStatus Extension
[*]2011-12-02 10:23:03.048 Enabled verbose msgs:  important general
[*]2011-12-02 10:23:03.138 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
[*]2011-12-02 10:23:03.893 MainServer::ANN Monitor
[*]2011-12-02 10:23:03.991 adding: Myth-Hybrid as a client (events: 0)
[*]2011-12-02 10:23:05.968 Reschedule requested for id -1.
[*]2011-12-02 10:23:06.169 Scheduled 0 items in 0.2 = 0.06 match + 0.14 place
[*]2011-12-02 10:23:06.227 scheduler: Scheduled items: Scheduled 0 items in 0.2 = 0.06 match + 0.14 place
[*]2011-12-02 10:23:06.278 Seem to be woken up by USER
[*]2011-12-02 10:23:09.166 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
[*]2011-12-02 10:23:09.398 UPnpMedia: BuildMediaMap Done. Found 531 objects
[*]2011-12-02 10:23:09.433 UPnpMedia: BuildMediaMap VIDEO scan starting in :/mnt/HD2/videos:
[*]2011-12-02 10:23:09.664 UPnpMedia: BuildMediaMap Done. Found 488 objects
[*]2011-12-02 10:23:12.998 mythbackend: Running housekeeping thread
[*]2011-12-02 10:24:22.999 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
[*]2011-12-02 10:24:23.138 Expiring 0 MB for 2002 at 2011-12-02T10:20:42 => Unknown
[*]2011-12-02 10:24:23.180 autoexpire: Expiring Program: Expiring 0 MB for 2002 at 2011-12-02T10:20:42 => Unknown
[*]2011-12-02 10:24:23.227 Expiring 0 MB for 2002 at 2011-12-02T10:20:43 => Unknown
[*]2011-12-02 10:24:23.264 autoexpire: Expiring Program: Expiring 0 MB for 2002 at 2011-12-02T10:20:43 => Unknown
[*]2011-12-02 10:24:23.294 Expiring 0 MB for 2002 at 2011-12-02T10:20:54 => Unknown
[*]2011-12-02 10:24:23.331 autoexpire: Expiring Program: Expiring 0 MB for 2002 at 2011-12-02T10:20:54 => Unknown
[*]2011-12-02 10:24:23.361 Expiring 0 MB for 2002 at 2011-12-02T10:21:01 => Unknown
[*]2011-12-02 10:24:23.398 autoexpire: Expiring Program: Expiring 0 MB for 2002 at 2011-12-02T10:21:01 => Unknown
[*]2011-12-02 10:24:23.428 Expiring 0 MB for 2002 at 2011-12-02T10:21:02 => Unknown
[*]2011-12-02 10:24:23.465 autoexpire: Expiring Program: Expiring 0 MB for 2002 at 2011-12-02T10:21:02 => Unknown
[*]2011-12-02 10:24:23.503 Expiring 0 MB for 2002 at 2011-12-02T10:21:12 => Unknown
[*]2011-12-02 10:24:23.540 autoexpire: Expiring Program: Expiring 0 MB for 2002 at 2011-12-02T10:21:12 => Unknown
[*]2011-12-02 10:29:05.729 MainServer::ANN Monitor
[*]2011-12-02 10:29:05.782 adding: Myth-Hybrid as a client (events: 0)
[*]2011-12-02 10:29:05.824 MainServer::ANN Monitor
[*]2011-12-02 10:29:05.898 adding: Myth-Hybrid as a client (events: 1)
[*]2011-12-02 10:29:10.250 MainServer::ANN Playback
[*]2011-12-02 10:29:10.301 adding: Myth-Hybrid as a client (events: 0)
[*]2011-12-02 10:29:10.340 TVRec(8): Changing from None to WatchingLiveTV
[*]2011-12-02 10:29:10.390 TVRec(8): HW Tuner: 8->8
[*]2011-12-02 10:29:10.459 LoadFromScheduler(): Error, called from backend.
[*]2011-12-02 10:29:10.462 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]2011-12-02 10:29:10.672 Finished recording Unknown: channel 2002
[*]2011-12-02 10:29:10.714 scheduler: Finished recording: Unknown: channel 2002
[*]2011-12-02 10:29:10.792 LoadFromScheduler(): Error, called from backend.
[*]2011-12-02 10:29:10.798 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[*]2011-12-02 10:29:10.833 recording already exists...
[*]2011-12-02 10:29:10.914 Finished recording Unknown: channel 2002
[*]2011-12-02 10:29:11.216  NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings,  Recording Profiles and setup the four 'Software Encoders' profiles.   Assuming RTjpeg for now.
[*]2011-12-02 10:29:11.286 NVR(/dev/video0) Error: Unknown audio codec
[*]2011-12-02 10:29:11.347 AudioInALSA(default) Error: pcm open failed: No such file or directory
[*]2011-12-02 10:29:11.402 NVR(/dev/video0) Error: Failed to open audio device ALSA:default
[*]2011-12-02 10:29:11.444 NVR(/dev/video0) Error: Failed to init audio input device
[*]2011-12-02 10:29:11.503 NVR(/dev/video0): Won't work with the streaming interface, falling back
[*]VIDIOCGCAP:: Invalid argument
[*]2011-12-02 10:29:11.562 AudioInALSA(default) Error: pcm open failed: No such file or directory
[*]2011-12-02 10:29:11.652 NVR(/dev/video0) Error: Failed to open audio device ALSA:default
[*]2011-12-02 10:29:50.687 TVRec(8): Changing from WatchingLiveTV to None
[*]2011-12-02 10:29:53.985 MainServer::ANN Monitor
[*]2011-12-02 10:29:54.083 adding: Myth-Hybrid as a client (events: 0)
[*]2011-12-02 10:29:54.126 MainServer::ANN Monitor
[*]2011-12-02 10:29:54.175 adding: Myth-Hybrid as a client (events: 1)
[/LIST]

```
One thing I noticed in the backend log was
 " Unknown video codec.  Please go into the TV Settings,  Recording Profiles and setup the four 'Software Encoders' profiles."
Could this be the problem? I don't remember ever having to do this before. Where is the best info on how to set these up?
Thanks,


Trev

---

### Post by nickrout on 2011-12-02
What tuner card do you have?

---

### Post by trevs.bronco on 2011-12-02
I have a couple of Hauppauge HVR-150's

---

### Post by nickrout on 2011-12-02
> **trevs.bronco said:**
> I have a couple of Hauppauge HVR-150's

Did you set them up as v4l or as ivtv mpeg encoder?

---

### Post by trevs.bronco on 2011-12-02
I tried both as I seem to them needing to be vl4, not their probed value of ivtv.

Now that I am thing about it, I tried the vl4 first and then the ivtv. I didn't do the restart on the system until after switching to ivtv. I think i should try the vl4 again.

Tev

---

### Post by trevs.bronco on 2011-12-02
Oops I got it backwards I tried the ivtv first and then the v4l. I switched it around and now all is good.

Thanks For the help nickrout and tgm4883,

Trevor

---

