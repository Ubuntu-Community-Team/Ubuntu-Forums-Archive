---
title: "16 sec pause before mythtvfrontend loads"
date: 2012-05-02
forum: Multimedia Software
---

### Post by graysky on 2012-05-02
Seems that mythfrontend take about 15 sec to load on a pretty fast C2D machine.  Below are the errors in my logfile.  Any ideas what might be causing this?

```
$ mythfrontend --logpath /tmp
...
2012-04-26 17:18:08.655238 C [4245/4245] thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) - mythfrontend version:  [v0.25pre] www.mythtv.org
2012-04-26 17:18:08.655254 N [4245/4245] thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) - Enabled verbose msgs:  general
2012-04-26 17:18:08.655321 N [4245/4245] thread_unknown logging.cpp:1176 (logStart) - Setting Log Level to LOG_INFO
2012-04-26 17:18:08.655361 I [4245/4245] thread_unknown logging.cpp:229 (FileLogger) - Added logging to the console
2012-04-26 17:18:08.655377 I [4245/4245] thread_unknown logging.cpp:238 (FileLogger) - Added logging to /tmp/mythfrontend.20120426171808.4245.log
2012-04-26 17:18:08.655383 I [4245/4245] thread_unknown logging.cpp:425 (DatabaseLogger) - Added database logging to table logging
2012-04-26 17:18:08.655465 N [4245/4245] thread_unknown logging.cpp:1215 (logStart) - Setting up SIGHUP handler
2012-04-26 17:18:08.655647 N [4245/4245] thread_unknown mythdirs.cpp:51 (InitializeMythDirs) - Using runtime prefix = /usr
2012-04-26 17:18:08.655656 N [4245/4245] thread_unknown mythdirs.cpp:64 (InitializeMythDirs) - Using configuration directory = /home/facade/.mythtv
2012-04-26 17:18:08.655760 I [4245/4245] CoreContext mythcorecontext.cpp:227 (Init) - Assumed character encoding: en_US.utf8
2012-04-26 17:18:08.655765 W [4245/4245] CoreContext mythcorecontext.cpp:234 (Init) - This application expects to be running a locale that specifies a UTF-8 codeset, and many features may behave improperly with your current language settings. Please set the LC_ALL or LC_CTYPE, and LANG variable(s) in the environment in which this program is executed to include a UTF-8 codeset (such as 'en_US.UTF-8').
2012-04-26 17:18:08.656115 N [4245/4245] CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) - Empty LocalHostName.
2012-04-26 17:18:08.656122 I [4245/4245] CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) - Using localhost value of arch-mythtv
2012-04-26 17:18:08.676304 N [4245/4245] CoreContext mythcorecontext.cpp:1270 (InitLocale) - Setting QT default locale to en_US
2012-04-26 17:18:08.676314 I [4245/4245] CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) - Current locale en_US
2012-04-26 17:18:08.676348 N [4245/4245] CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) - Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2012-04-26 17:18:08.680630 I [4245/4251] SystemManager system-unix.cpp:263 (run) - Starting process manager
2012-04-26 17:18:08.681900 I [4245/4254] SystemIOHandlerW system-unix.cpp:90 (run) - Starting IO manager (write)
2012-04-26 17:18:08.681976 I [4245/4253] SystemIOHandlerR system-unix.cpp:90 (run) - Starting IO manager (read)
2012-04-26 17:18:08.682040 I [4245/4252] SystemSignalManager system-unix.cpp:485 (run) - Starting process signal handler
2012-04-26 17:18:08.782364 I [4245/4245] CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) - ScreenSaverX11Private: XScreenSaver support enabled
2012-04-26 17:18:08.782833 I [4245/4245] CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) - ScreenSaverX11Private: DPMS is active.
2012-04-26 17:18:08.792200 N [4245/4245] CoreContext DisplayRes.cpp:64 (Initialize) - Desktop video mode: 1920x1080 60.000 Hz
2012-04-26 17:18:08.803500 I [4245/4245] CoreContext serverpool.cpp:306 (listen) - Listening on TCP 127.0.0.1:6547
2012-04-26 17:18:08.803565 I [4245/4245] CoreContext serverpool.cpp:306 (listen) - Listening on TCP 192.168.0.102:6547
2012-04-26 17:18:08.803621 I [4245/4245] CoreContext serverpool.cpp:306 (listen) - Listening on TCP [::1]:6547
2012-04-26 17:18:24.028925 E [4245/4245] CoreContext bonjourregister.cpp:53 (Register) - Bonjour: Error: -65537
2012-04-26 17:18:24.028935 E [4245/4245] CoreContext bonjourregister.cpp:68 (Register) - Bonjour: Failed to register service.
2012-04-26 17:18:24.029024 E [4245/4245] CoreContext mythraopconnection.cpp:730 (LoadKey) - RAOP Conn: Failed to read key from: /home/facade/.mythtv/RAOPKey.rsa
2012-04-26 17:18:24.029036 E [4245/4245] CoreContext mythraopdevice.cpp:26 (Create) - RAOP Device: Aborting startup - no key found.
2012-04-26 17:18:24.031998 I [4245/4245] CoreContext mythtranslation.cpp:66 (load) - Loading en_us translation for module mythfrontend
2012-04-26 17:18:24.040260 I [4245/4245] CoreContext lirc.cpp:308 (Init) - LIRC: Successfully initialized '/dev/lircd' using '/home/facade/.mythtv/lircrc' config
2012-04-26 17:18:24.040326 E [4245/4245] CoreContext jsmenu.cpp:91 (Init) - JoystickMenuThread: Joystick disabled - Failed to read /home/facade/.mythtv/joystickmenurc
2012-04-26 17:18:24.046298 E [4245/4245] CoreContext cecadapter.cpp:128 (Open) - CECAdapter: Failed to load libcec.
2012-04-26 17:18:24.047051 I [4245/4245] CoreContext serverpool.cpp:365 (bind) - Binding to UDP 127.0.0.1:6948
2012-04-26 17:18:24.047113 I [4245/4245] CoreContext serverpool.cpp:365 (bind) - Binding to UDP 192.168.0.102:6948
2012-04-26 17:18:24.047195 I [4245/4245] CoreContext serverpool.cpp:365 (bind) - Binding to UDP [::1]:6948
2012-04-26 17:18:24.047251 I [4245/4245] CoreContext serverpool.cpp:365 (bind) - Binding to UDP 192.168.0.255:6948
2012-04-26 17:18:24.078268 I [4245/4245] CoreContext mythmainwindow.cpp:947 (Init) - Using Frameless Window
2012-04-26 17:18:24.078305 I [4245/4245] CoreContext mythmainwindow.cpp:960 (Init) - Using Full Screen Window
2012-04-26 17:18:24.144553 I [4245/4245] CoreContext mythmainwindow.cpp:1012 (Init) - Trying the OpenGL painter
2012-04-26 17:18:24.146615 W [4245/4245] CoreContext util-nvctrl.cpp:62 (CheckNVOpenGLSyncToVBlank) - NVCtrl: OpenGL Sync to VBlank is disabled.
2012-04-26 17:18:24.146623 W [4245/4245] CoreContext util-nvctrl.cpp:63 (CheckNVOpenGLSyncToVBlank) - NVCtrl: For best results enable this in NVidia settings or try running:
2012-04-26 17:18:24.146626 W [4245/4245] CoreContext util-nvctrl.cpp:64 (CheckNVOpenGLSyncToVBlank) - NVCtrl: nvidia-settings -a "SyncToVBlank=1"
2012-04-26 17:18:24.146638 W [4245/4245] CoreContext util-nvctrl.cpp:76 (CheckNVOpenGLSyncToVBlank) - NVCtrl: Alternatively try setting the '__GL_SYNC_TO_VBLANK' environment variable.
2012-04-26 17:18:24.202820 I [4245/4245] CoreContext mythrender_opengl1.cpp:77 (InitFeatures) - OpenGL1: Fragment program support available
2012-04-26 17:18:24.202899 I [4245/4245] CoreContext mythrender_opengl.cpp:932 (InitFeatures) - OpenGL: OpenGL vendor  : NVIDIA Corporation
2012-04-26 17:18:24.202905 I [4245/4245] CoreContext mythrender_opengl.cpp:934 (InitFeatures) - OpenGL: OpenGL renderer: GeForce GT 520/PCIe/SSE2
2012-04-26 17:18:24.202908 I [4245/4245] CoreContext mythrender_opengl.cpp:936 (InitFeatures) - OpenGL: OpenGL version : 4.2.0 NVIDIA 295.40
2012-04-26 17:18:24.202916 I [4245/4245] CoreContext mythrender_opengl.cpp:938 (InitFeatures) - OpenGL: Max texture size: 16384 x 16384
2012-04-26 17:18:24.202920 I [4245/4245] CoreContext mythrender_opengl.cpp:940 (InitFeatures) - OpenGL: Max texture units: 4
2012-04-26 17:18:24.202936 I [4245/4245] CoreContext mythrender_opengl.cpp:942 (InitFeatures) - OpenGL: Direct rendering: Yes
2012-04-26 17:18:24.202940 I [4245/4245] CoreContext mythrender_opengl.cpp:949 (InitFeatures) - OpenGL: PixelBufferObject support available
2012-04-26 17:18:24.202947 I [4245/4245] CoreContext mythrender_opengl.cpp:127 (Init) - OpenGL: Initialised MythRenderOpenGL
2012-04-26 17:18:24.319589 I [4245/4245] CoreContext schemawizard.cpp:117 (Compare) - Current MythTV Schema Version (DBSchemaVer): 1299
2012-04-26 17:18:24.369965 W [4245/4245] CoreContext themeinfo.cpp:74 (parseThemeInfo) - ThemeInfo: Unable to open themeinfo.xml for /home/facade/.mythtv/themes/Willi/themeinfo.xml
2012-04-26 17:18:24.369972 E [4245/4245] CoreContext themeinfo.cpp:34 (ThemeInfo) - ThemeInfo: The theme (/home/facade/.mythtv/themes/Willi) is missing a themeinfo.xml file.
2012-04-26 17:18:24.464028 N [4245/4245] CoreContext mythmainwindow.cpp:1859 (RegisterMediaPlugin) - Registering Internal as a media playback plugin.
2012-04-26 17:18:24.481622 W [4245/4245] CoreContext mythplugin.cpp:164 (MythPluginManager) - No plugins directory /usr/lib/mythtv/plugins
2012-04-26 17:18:24.488690 N [4245/4245] CoreContext main.cpp:1074 (RunMenu) - Found mainmenu.xml for theme 'TintedGlass'
2012-04-26 17:18:24.626541 I [4245/4245] CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) - MythCoreContext: Connecting to backend server: 192.168.0.102:6543 (try 1 of 1)
2012-04-26 17:18:24.627623 I [4245/4245] CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) - Using protocol version 72
```

---

