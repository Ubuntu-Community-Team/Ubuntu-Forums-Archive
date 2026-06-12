---
title: "frontend ICE error and/or problems drawing menu items"
date: 2012-09-09
forum: Mythbuntu
---

### Post by crbnrod on 2012-09-09
I have a script that switches between XBMC and mythtv FE that had been working great for a few weeks now. This morning I switched out of XBMC and when the mythtv FE restarted, I got the blue background screen and then the FE (program, not machine) locked up. I now can't seem to get the FE to start through any "conventional" (ie "things my wife could do") means - the best I can do is get the background to draw and then sit there. 
The following may be more info than is needed.

Running 12.04/.25.

Here is mythfrontend log from reboot:
```
Sep  9 09:40:04 myth-lr mythfrontend[1845]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25.2-18-g05a3d73] www.mythtv.org
Sep  9 09:40:04 myth-lr mythfrontend[1845]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Sep  9 09:40:04 myth-lr mythfrontend[1845]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Sep  9 09:40:04 myth-lr mythfrontend[1845]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Sep  9 09:40:04 myth-lr mythfrontend[1845]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Sep  9 09:40:04 myth-lr mythfrontend[1845]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Sep  9 09:40:04 myth-lr mythfrontend[1845]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/brain/.mythtv
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
Sep  9 09:40:04 myth-lr mythfrontend[1845]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of myth-lr
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I CoreContext mythcontext.cpp:608 (TestDBconnection) Testing network connectivity to '192.168.0.2'
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Sep  9 09:40:04 myth-lr mythfrontend[1845]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
Sep  9 09:40:04 myth-lr mythfrontend[1845]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
Sep  9 09:40:04 myth-lr mythfrontend[1845]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 127.0.0.1:6547
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 192.168.0.3:6547
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [::1]:6547
Sep  9 09:40:04 myth-lr mythfrontend[1845]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [fe80::16da:e9ff:fe74:5500%eth2]:6547
Sep  9 09:40:05 myth-lr mythfrontend[1845]: E CoreContext mythraopconnection.cpp:1276 (LoadKey) RAOP Conn: Failed to read key from: /home/brain/.mythtv/RAOPKey.rsa
Sep  9 09:40:05 myth-lr mythfrontend[1845]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/brain/.mythtv/lircrc' config
Sep  9 09:40:05 myth-lr mythfrontend[1845]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/brain/.mythtv/joystickmenurc
Sep  9 09:40:05 myth-lr mythfrontend[1845]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP 127.0.0.1:6948
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP 192.168.0.3:6948
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP [::1]:6948
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP [fe80::16da:e9ff:fe74:5500%eth2]:6948
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP 192.168.0.255:6948
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext mythmainwindow.cpp:948 (Init) Using Frameless Window
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext mythmainwindow.cpp:961 (Init) Using Full Screen Window
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext mythmainwindow.cpp:1013 (Init) Trying the OpenGL painter
Sep  9 09:40:05 myth-lr mythfrontend[1845]: W CoreContext util-nvctrl.cpp:62 (CheckNVOpenGLSyncToVBlank) NVCtrl: OpenGL Sync to VBlank is disabled.
Sep  9 09:40:05 myth-lr mythfrontend[1845]: W CoreContext util-nvctrl.cpp:63 (CheckNVOpenGLSyncToVBlank) NVCtrl: For best results enable this in NVidia settings or try running:
Sep  9 09:40:05 myth-lr mythfrontend[1845]: W CoreContext util-nvctrl.cpp:64 (CheckNVOpenGLSyncToVBlank) NVCtrl: nvidia-settings -a "SyncToVBlank=1"
Sep  9 09:40:05 myth-lr mythfrontend[1845]: W CoreContext util-nvctrl.cpp:76 (CheckNVOpenGLSyncToVBlank) NVCtrl: Alternatively try setting the '__GL_SYNC_TO_VBLANK' environment variable.
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext mythrender_opengl1.cpp:77 (InitFeatures) OpenGL1: Fragment program support available
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext mythrender_opengl.cpp:932 (InitFeatures) OpenGL: OpenGL vendor  : NVIDIA Corporation
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext mythrender_opengl.cpp:934 (InitFeatures) OpenGL: OpenGL renderer: GeForce GT 430/PCIe/SSE2
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext mythrender_opengl.cpp:936 (InitFeatures) OpenGL: OpenGL version : 4.2.0 NVIDIA 295.40
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext mythrender_opengl.cpp:938 (InitFeatures) OpenGL: Max texture size: 16384 x 16384
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext mythrender_opengl.cpp:940 (InitFeatures) OpenGL: Max texture units: 4
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext mythrender_opengl.cpp:942 (InitFeatures) OpenGL: Direct rendering: Yes
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext mythrender_opengl.cpp:949 (InitFeatures) OpenGL: PixelBufferObject support available
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext mythrender_opengl.cpp:127 (Init) OpenGL: Initialised MythRenderOpenGL
Sep  9 09:40:05 myth-lr mythfrontend[1845]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Sep  9 09:40:06 myth-lr mythfrontend[1845]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Sep  9 09:40:06 myth-lr mythfrontend[1845]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Sep  9 09:40:06 myth-lr mythfrontend[1845]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Sep  9 09:40:06 myth-lr mythfrontend[1845]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Sep  9 09:40:06 myth-lr mythfrontend[1845]: N CoreContext mythmainwindow.cpp:1862 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Sep  9 09:40:06 myth-lr mythfrontend[1845]: W CoreContext mythplugin.cpp:164 (MythPluginManager) No plugins directory /usr/lib/mythtv/plugins
Sep  9 09:40:06 myth-lr mythfrontend[1845]: I CoreContext hardwareprofile.cpp:164 (NeedsUpdate) Last hardware profile update was > 30 days ago, update required...
Sep  9 09:40:06 myth-lr mythfrontend[1845]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Sep  9 09:41:12 myth-lr mythfrontend[1845]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'MythCenter-wide'
Sep  9 09:41:12 myth-lr mythfrontend[1845]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
```

Here's the output from terminal if I try to force the opengl painter:
```
brain@myth-lr:~$ mythfrontend -O ThemePainter=opengl -O UIPainter=opengl
QGtkStyle was unable to detect the current GTK+ theme.
2012-09-09 09:29:38.050442 C  mythfrontend version: fixes/0.25 [v0.25.2-18-g05a3d73] www.mythtv.org
2012-09-09 09:29:38.050467 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2012-09-09 09:29:38.050470 N  Enabled verbose msgs:  general
2012-09-09 09:29:38.050493 N  Setting Log Level to LOG_INFO
2012-09-09 09:29:38.050530 I  Added logging to the console
2012-09-09 09:29:38.050558 I  Added syslogging to facility local7
2012-09-09 09:29:38.050563 I  Added database logging to table logging
2012-09-09 09:29:38.050661 N  Setting up SIGHUP handler
2012-09-09 09:29:38.050720 N  Using runtime prefix = /usr
2012-09-09 09:29:38.050731 N  Using configuration directory = /home/brain/.mythtv
2012-09-09 09:29:38.050873 I  Assumed character encoding: en_US.UTF-8
2012-09-09 09:29:38.051376 N  Empty LocalHostName.
2012-09-09 09:29:38.051384 I  Using localhost value of myth-lr
2012-09-09 09:29:38.051488 I  Testing network connectivity to '192.168.0.2'
2012-09-09 09:29:38.058606 I  Starting process signal handler
2012-09-09 09:29:38.058709 I  Starting IO manager (read)
2012-09-09 09:29:38.061817 I  Starting process manager
2012-09-09 09:29:38.063970 I  Starting IO manager (write)
2012-09-09 09:29:38.242615 N  Setting QT default locale to EN_US
2012-09-09 09:29:38.242796 I  Current locale EN_US
2012-09-09 09:29:38.242893 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2012-09-09 09:29:38.410043 I  ScreenSaverX11Private: XScreenSaver support enabled
2012-09-09 09:29:38.412281 I  ScreenSaverX11Private: DPMS is disabled.
2012-09-09 09:29:38.444400 N  Desktop video mode: 1920x1080 60.000 Hz
2012-09-09 09:29:38.515543 N  Setting 'ThemePainter' being forced to 'opengl'
2012-09-09 09:29:38.515578 N  Setting 'UIPainter' being forced to 'opengl'
2012-09-09 09:29:38.526346 I  Listening on TCP 127.0.0.1:6547
2012-09-09 09:29:38.526526 I  Listening on TCP 192.168.0.3:6547
2012-09-09 09:29:38.526682 I  Listening on TCP [::1]:6547
2012-09-09 09:29:38.526845 I  Listening on TCP [fe80::16da:e9ff:fe74:5500%eth2]:6547
2012-09-09 09:29:39.362740 E  RAOP Conn: Failed to read key from: /home/brain/.mythtv/RAOPKey.rsa
2012-09-09 09:29:39.362752 E  RAOP Device: Aborting startup - no key found.
cannot find libcec.solibcec.so: cannot open shared object file: No such file or directory
2012-09-09 09:29:39.369538 I  Loading en_us translation for module mythfrontend
2012-09-09 09:29:39.390268 I  LIRC: Successfully initialized '/dev/lircd' using '/home/brain/.mythtv/lircrc' config
2012-09-09 09:29:39.390384 E  JoystickMenuThread: Joystick disabled - Failed to read /home/brain/.mythtv/joystickmenurc
2012-09-09 09:29:39.410838 E  CECAdapter: Failed to load libcec.
2012-09-09 09:29:39.412163 I  Binding to UDP 127.0.0.1:6948
2012-09-09 09:29:39.412199 I  Binding to UDP 192.168.0.3:6948
2012-09-09 09:29:39.412245 I  Binding to UDP [::1]:6948
2012-09-09 09:29:39.412284 I  Binding to UDP [fe80::16da:e9ff:fe74:5500%eth2]:6948
2012-09-09 09:29:39.412321 I  Binding to UDP 192.168.0.255:6948
2012-09-09 09:29:39.522772 I  Using Frameless Window
2012-09-09 09:29:39.522871 I  Using Full Screen Window
2012-09-09 09:29:39.684258 I  Trying the OpenGL painter
2012-09-09 09:29:39.701796 W  NVCtrl: OpenGL Sync to VBlank is disabled.
2012-09-09 09:29:39.701806 W  NVCtrl: For best results enable this in NVidia settings or try running:
2012-09-09 09:29:39.701809 W  NVCtrl: nvidia-settings -a "SyncToVBlank=1"
2012-09-09 09:29:39.701822 W  NVCtrl: Alternatively try setting the '__GL_SYNC_TO_VBLANK' environment variable.
2012-09-09 09:29:39.767102 I  OpenGL1: Fragment program support available
2012-09-09 09:29:39.767155 I  OpenGL: OpenGL vendor  : NVIDIA Corporation
2012-09-09 09:29:39.767160 I  OpenGL: OpenGL renderer: GeForce GT 430/PCIe/SSE2
2012-09-09 09:29:39.767163 I  OpenGL: OpenGL version : 4.2.0 NVIDIA 295.40
2012-09-09 09:29:39.767169 I  OpenGL: Max texture size: 16384 x 16384
2012-09-09 09:29:39.767172 I  OpenGL: Max texture units: 4
2012-09-09 09:29:39.767184 I  OpenGL: Direct rendering: Yes
2012-09-09 09:29:39.767187 I  OpenGL: PixelBufferObject support available
2012-09-09 09:29:39.767189 I  OpenGL: Initialised MythRenderOpenGL
2012-09-09 09:29:39.854463 I  Current MythTV Schema Version (DBSchemaVer): 1299
2012-09-09 09:29:40.026224 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2012-09-09 09:29:40.026250 E  ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2012-09-09 09:29:40.027718 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2012-09-09 09:29:40.027735 E  ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2012-09-09 09:29:40.632360 N  Registering Internal as a media playback plugin.
2012-09-09 09:29:40.690805 W  No plugins directory /usr/lib/mythtv/plugins
2012-09-09 09:29:40.696705 I  Last hardware profile update was > 30 days ago, update required...
2012-09-09 09:29:40.696819 I  Locking input devices
2012-09-09 09:30:46.855047 N  Found mainmenu.xml for theme 'MythCenter-wide'
2012-09-09 09:30:46.879459 I  Unlocking input devices
ICE default IO error handler doing an exit(), pid = 2085, errno = 32
QWaitCondition: cv destroy failure: Device or resource busy
QWaitCondition: mutex destroy failure: Device or resource busy

```

...and if I force QT:
```
brain@myth-lr:~$ mythfrontend -O ThemePainter=qt -O UIPainter=qt
QGtkStyle was unable to detect the current GTK+ theme.
2012-09-09 09:35:36.731924 C  mythfrontend version: fixes/0.25 [v0.25.2-18-g05a3d73] www.mythtv.org
2012-09-09 09:35:36.731978 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2012-09-09 09:35:36.731988 N  Enabled verbose msgs:  general
2012-09-09 09:35:36.732044 N  Setting Log Level to LOG_INFO
2012-09-09 09:35:36.732163 I  Added logging to the console
2012-09-09 09:35:36.732217 I  Added syslogging to facility local7
2012-09-09 09:35:36.732234 I  Added database logging to table logging
2012-09-09 09:35:36.732454 N  Setting up SIGHUP handler
2012-09-09 09:35:36.732681 N  Using runtime prefix = /usr
2012-09-09 09:35:36.732716 N  Using configuration directory = /home/brain/.mythtv
2012-09-09 09:35:36.733075 I  Assumed character encoding: en_US.UTF-8
2012-09-09 09:35:36.734069 N  Empty LocalHostName.
2012-09-09 09:35:36.734087 I  Using localhost value of myth-lr
2012-09-09 09:35:36.734433 I  Testing network connectivity to '192.168.0.2'
2012-09-09 09:35:36.735610 I  Starting process manager
2012-09-09 09:35:36.737063 I  Starting process signal handler
2012-09-09 09:35:36.737145 I  Starting IO manager (read)
2012-09-09 09:35:36.737271 I  Starting IO manager (write)
2012-09-09 09:35:36.870708 N  Setting QT default locale to EN_US
2012-09-09 09:35:36.870785 I  Current locale EN_US
2012-09-09 09:35:36.870826 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2012-09-09 09:35:36.937940 I  ScreenSaverX11Private: XScreenSaver support enabled
2012-09-09 09:35:36.940685 I  ScreenSaverX11Private: DPMS is disabled.
2012-09-09 09:35:36.985609 N  Desktop video mode: 1920x1080 60.000 Hz
2012-09-09 09:35:37.049139 N  Setting 'ThemePainter' being forced to 'qt'
2012-09-09 09:35:37.049175 N  Setting 'UIPainter' being forced to 'qt'
2012-09-09 09:35:37.062169 I  Listening on TCP 127.0.0.1:6547
2012-09-09 09:35:37.062350 I  Listening on TCP 192.168.0.3:6547
2012-09-09 09:35:37.062514 I  Listening on TCP [::1]:6547
2012-09-09 09:35:37.062675 I  Listening on TCP [fe80::16da:e9ff:fe74:5500%eth2]:6547
cannot find libcec.solibcec.so: cannot open shared object file: No such file or directory
2012-09-09 09:35:37.769075 E  RAOP Conn: Failed to read key from: /home/brain/.mythtv/RAOPKey.rsa
2012-09-09 09:35:37.769105 E  RAOP Device: Aborting startup - no key found.
2012-09-09 09:35:37.778950 I  Loading en_us translation for module mythfrontend
2012-09-09 09:35:37.806835 I  LIRC: Successfully initialized '/dev/lircd' using '/home/brain/.mythtv/lircrc' config
2012-09-09 09:35:37.807033 E  JoystickMenuThread: Joystick disabled - Failed to read /home/brain/.mythtv/joystickmenurc
2012-09-09 09:35:37.832547 E  CECAdapter: Failed to load libcec.
2012-09-09 09:35:37.834637 I  Binding to UDP 127.0.0.1:6948
2012-09-09 09:35:37.834785 I  Binding to UDP 192.168.0.3:6948
2012-09-09 09:35:37.834935 I  Binding to UDP [::1]:6948
2012-09-09 09:35:37.835081 I  Binding to UDP [fe80::16da:e9ff:fe74:5500%eth2]:6948
2012-09-09 09:35:37.835206 I  Binding to UDP 192.168.0.255:6948
2012-09-09 09:35:37.956364 I  Using Frameless Window
2012-09-09 09:35:37.956464 I  Using Full Screen Window
2012-09-09 09:35:38.136644 I  Using the Qt painter
2012-09-09 09:35:38.227390 I  Current MythTV Schema Version (DBSchemaVer): 1299
2012-09-09 09:35:38.400355 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2012-09-09 09:35:38.400381 E  ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2012-09-09 09:35:38.401881 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2012-09-09 09:35:38.401898 E  ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2012-09-09 09:35:39.035434 N  Registering Internal as a media playback plugin.
2012-09-09 09:35:39.088126 W  No plugins directory /usr/lib/mythtv/plugins
2012-09-09 09:35:39.093769 I  Last hardware profile update was > 30 days ago, update required...
2012-09-09 09:35:39.093837 I  Locking input devices
2012-09-09 09:36:44.977085 N  Found mainmenu.xml for theme 'MythCenter-wide'
ICE default IO error handler doing an exit(), pid = 2272, errno = 32

```

...ok so to fix the ICE error I delete ~/.ICEauthority and then restart, which return to first log posting and FE hangs at blue background screen.

However, if I delete ~/.ICEauthority and then manually start mythfrontend from terminal, it eventually runs, however it seems to be thinking real, real hard based on the timestamps:
```
2012-09-09 09:44:55.046846 I  Last hardware profile update was > 30 days ago, update required...
2012-09-09 09:44:55.046962 I  Locking input devices
2012-09-09 09:46:00.947191 N  Found mainmenu.xml for theme 'MythCenter-wide'
2012-09-09 09:46:00.971261 I  Unlocking input devices
2012-09-09 09:46:01.151759 I  MythCoreContext: Connecting to backend server: 192.168.0.2:6543 (try 1 of 1)
2012-09-09 09:46:01.152870 I  Using protocol version 72
2012-09-09 09:46:01.201960 I  Bonjour: Service registration complete: name 'Mythfrontend on myth-lr' type '_mythfrontend._tcp.' domain: 'local.'
2012-09-09 09:46:16.025105 I  Using protocol version 72
2012-09-09 09:46:16.028876 I  Using protocol version 72
```
Taking a little over a minute to go from locking input devices to finding the mainmenu.xml file.

So I can run it this way, but if I ever reboot or quit out of the FE (which I tend to do to switch to XBMC) it looks like I'm going to get the ICE error...anyone have any ideas on how I can avoid this or why I get that big delay when it locks the input devices?

---

