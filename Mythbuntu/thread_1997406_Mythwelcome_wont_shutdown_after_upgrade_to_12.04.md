---
title: "Mythwelcome wont shutdown after upgrade to 12.04"
date: 2012-06-05
forum: Mythbuntu
---

### Post by trippy21 on 2012-06-05
Hi
I've updated my combined FE/BE from 11.10 to 12.04 over the weekend. Everything is running fine, except for when i exit out of the FE into Mythwelcome, Mythwelcome only counts down to about 480 sec, from 600 secs and then resets. 
If i have a look in the logs for Mythwelcome there seems to be a reschedule happening every few minutes which i am assuming is what is resetting the counter. The myth welcome log below is from when the FE/BE wakes up at midnight to do schedule updates and advert detection.

Mythwelcome.log
[HTML]Jun  5 00:00:37 mythbuntu-M85M-US2H mythwelcome[2563]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythwelcome version: fixes/0.25 [v0.25-137-g3b2103f] www.mythtv.org
Jun  5 00:00:37 mythbuntu-M85M-US2H mythwelcome[2563]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jun  5 00:00:37 mythbuntu-M85M-US2H mythwelcome[2563]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Jun  5 00:00:37 mythbuntu-M85M-US2H mythwelcome[2563]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Jun  5 00:00:37 mythbuntu-M85M-US2H mythwelcome[2563]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Jun  5 00:00:37 mythbuntu-M85M-US2H mythwelcome[2563]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Jun  5 00:00:37 mythbuntu-M85M-US2H mythwelcome[2563]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Jun  5 00:00:37 mythbuntu-M85M-US2H mythwelcome[2563]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Jun  5 00:00:37 mythbuntu-M85M-US2H mythwelcome[2563]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Jun  5 00:00:37 mythbuntu-M85M-US2H mythwelcome[2563]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythbuntu/.mythtv
Jun  5 00:00:37 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_GB.UTF-8
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of mythbuntu-M85M-US2H
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to en_GB
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale en_GB
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1280x720 50.000 Hz
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythtranslation.cpp:66 (load) Loading en_gb translation for module mythfrontend
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/mythbuntu/.mythtv/lircrc' config
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/mythbuntu/.mythtv/joystickmenurc
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext serverpool.cpp:424 (bind) Binding to UDP 127.0.0.1:6948
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext serverpool.cpp:424 (bind) Binding to UDP 192.168.1.65:6948
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext serverpool.cpp:424 (bind) Binding to UDP [::1]:6948
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext serverpool.cpp:424 (bind) Binding to UDP 192.168.1.255:6948
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:948 (Init) Using Frameless Window
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:961 (Init) Using Full Screen Window
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:1013 (Init) Trying the OpenGL painter
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: W CoreContext util-nvctrl.cpp:62 (CheckNVOpenGLSyncToVBlank) NVCtrl: OpenGL Sync to VBlank is disabled.
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: W CoreContext util-nvctrl.cpp:63 (CheckNVOpenGLSyncToVBlank) NVCtrl: For best results enable this in NVidia settings or try running:
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: W CoreContext util-nvctrl.cpp:64 (CheckNVOpenGLSyncToVBlank) NVCtrl: nvidia-settings -a "SyncToVBlank=1"
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: W CoreContext util-nvctrl.cpp:76 (CheckNVOpenGLSyncToVBlank) NVCtrl: Alternatively try setting the '__GL_SYNC_TO_VBLANK' environment variable.
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythrender_opengl1.cpp:77 (InitFeatures) OpenGL1: Fragment program support available
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythrender_opengl.cpp:932 (InitFeatures) OpenGL: OpenGL vendor  : NVIDIA Corporation
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythrender_opengl.cpp:934 (InitFeatures) OpenGL: OpenGL renderer: GeForce 8200/integrated/SSE2
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythrender_opengl.cpp:936 (InitFeatures) OpenGL: OpenGL version : 3.3.0 NVIDIA 295.40
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythrender_opengl.cpp:938 (InitFeatures) OpenGL: Max texture size: 8192 x 8192
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythrender_opengl.cpp:940 (InitFeatures) OpenGL: Max texture units: 4
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythrender_opengl.cpp:942 (InitFeatures) OpenGL: Direct rendering: Yes
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythrender_opengl.cpp:949 (InitFeatures) OpenGL: PixelBufferObject support available
Jun  5 00:00:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythrender_opengl.cpp:127 (Init) OpenGL: Initialised MythRenderOpenGL
Jun  5 00:00:39 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.65:6543 (try 1 of 1)
Jun  5 00:00:39 mythbuntu-M85M-US2H mythwelcome[2563]: E CoreContext mythcorecontext.cpp:441 (ConnectCommandSocket) Connection to master server timed out.#012#011#011#011Either the server is down or the master server settings#012#011#011#011in mythtv-settings does not contain the proper IP address
Jun  5 00:00:39 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:00:39 mythbuntu-M85M-US2H mythwelcome[2563]: N CoreContext welcomedialog.cpp:135 (checkAutoStart) mythshutdown --startup returned: 0
Jun  5 00:00:39 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:00:40 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:00:40 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:00:44 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.65:6543 (try 1 of 1)
Jun  5 00:00:44 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Jun  5 00:00:44 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:00:45 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:00:45 mythbuntu-M85M-US2H mythwelcome[2563]: N CoreContext welcomedialog.cpp:175 (customEvent) MythWelcome received a SCHEDULE_CHANGE event
Jun  5 00:00:45 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:00:46 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:00:46  mythwelcome[2563]: last message repeated 2 times
Jun  5 00:00:46 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:00:47 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:00:51 mythbuntu-M85M-US2H mythwelcome[2563]: N CoreContext welcomedialog.cpp:156 (customEvent) MythWelcome received a recording list change event
Jun  5 00:01:16  mythwelcome[2563]: last message repeated 5 times
Jun  5 00:01:16 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:01:17 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:01:32 mythbuntu-M85M-US2H mythwelcome[2563]: I Socket mythcorecontext.cpp:1103 (readyRead) Received remote 'Clear Cache' request
Jun  5 00:01:32 mythbuntu-M85M-US2H mythwelcome[2563]: N CoreContext welcomedialog.cpp:175 (customEvent) MythWelcome received a SCHEDULE_CHANGE event
Jun  5 00:01:32 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:01:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:01:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:01:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:02:02 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:02:03 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:02:32 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:02:32 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:02:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:02:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:03:03 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:03:04 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:03:32 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:03:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:03:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:03:34 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:04:03 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:04:04 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:04:32 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:04:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:04:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:04:34 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:05:03 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:05:04 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:05:32 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:05:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:05:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:05:34 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:06:03 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:06:04 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:06:32 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:06:32 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:06:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:06:34 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:07:03 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:07:04 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:07:32 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:07:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:07:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:07:34 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:08:03 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:08:04 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:08:32 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:08:32 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:08:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:08:34 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:09:03 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:09:04 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:09:32 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:09:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:09:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:09:34 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:10:03 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:10:04 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:10:32 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:10:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:10:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:10:34 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:11:03 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:11:04 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:11:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:11:34 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:12:03 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:12:04 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:12:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:12:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:12:33 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:12:34 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:12:41 mythbuntu-M85M-US2H mythwelcome[2563]: N CoreContext welcomedialog.cpp:175 (customEvent) MythWelcome received a SCHEDULE_CHANGE event
Jun  5 00:12:41 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:12:42 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:12:42 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:12:43 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:13:12 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:13:13 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:13:41 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:13:42 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:13:42 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:13:43 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:14:12 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:14:13 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:14:41 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:14:42 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:14:42 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:14:43 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:15:12 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:15:13 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:15:41 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:15:42 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:15:42 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:15:43 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:16:06 mythbuntu-M85M-US2H mythwelcome[2563]: N CoreContext welcomedialog.cpp:175 (customEvent) MythWelcome received a SCHEDULE_CHANGE event
Jun  5 00:16:06 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:16:07 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:16:07 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:16:08 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:16:37 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:16:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:17:06 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:17:07 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:17:07 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:17:08 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:17:37 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:17:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:18:06 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:18:07 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:18:07 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:18:08 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:18:37 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:18:38 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:19:06 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:19:07 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:19:07 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:19:08 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:19:27 mythbuntu-M85M-US2H mythwelcome[2563]: N CoreContext welcomedialog.cpp:175 (customEvent) MythWelcome received a SCHEDULE_CHANGE event
Jun  5 00:19:27 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:19:28 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:19:28 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:19:29 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:19:58 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:19:59 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:20:27 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:20:28 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:20:28 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:20:29 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:20:58 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:20:59 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:21:27 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:21:28 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:21:28 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:21:29 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:21:58 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:21:59 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:22:27 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:22:28 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:22:28 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:22:29 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:22:58 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:22:59 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:23:27 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:23:28 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:23:28 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Jun  5 00:23:29 mythbuntu-M85M-US2H mythwelcome[2563]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Jun  5 00:23:36 mythbuntu-M85M-US2H mythwelcome[2563]: N CoreContext welcomedialog.cpp:175 (customEvent) MythWelcome received a SCHEDULE_CHANGE event[/HTML]

The backend log shows that the backend is running a housekeeping thread which appears to be causing a reschedule, which i assume is what is causing the mythfrontend to reset its timer, what do you guys think?

Mythbackend.log
[HTML]Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythbackend version: fixes/0.25 [v0.25-137-g3b2103f] www.mythtv.org
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_GB.UTF-8
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of mythbuntu-M85M-US2H
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to en_GB
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale en_GB
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext mythtranslation.cpp:66 (load) Loading en_gb translation for module mythfrontend
Jun  5 00:00:34 mythbuntu-M85M-US2H mythbackend[2031]: N CoreContext main_helpers.cpp:556 (run_backend) MythBackend: Starting up as the master server.
Jun  5 00:00:38 mythbuntu-M85M-US2H mythbackend[2031]: W CoreContext dvbchannel.cpp:347 (CheckFrequency) DVBChan(2:/dev/dvb/adapter1/frontend0): Your frequency setting (10817500) is out of range. (min/max:950000/2150000)
Jun  5 00:00:40 mythbuntu-M85M-US2H mythbackend[2031]: W CoreContext dvbchannel.cpp:347 (CheckFrequency) DVBChan(6:/dev/dvb/adapter2/frontend0): Your frequency setting (10832250) is out of range. (min/max:950000/2150000)
Jun  5 00:00:41 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext programinfo.cpp:2052 (CheckProgramIDAuthorities) Found 41 distinct programid authorities
Jun  5 00:00:41 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler mythdbcon.cpp:422 (getStaticCon) New static DB connectionSchedCon
Jun  5 00:00:41 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 127.0.0.1:6544
Jun  5 00:00:41 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 192.168.1.65:6544
Jun  5 00:00:41 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP [::1]:6544
Jun  5 00:00:42 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext main_helpers.cpp:626 (run_backend) Main::Registering HttpStatus Extension
Jun  5 00:00:42 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 127.0.0.1:6543
Jun  5 00:00:42 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 192.168.1.65:6543
Jun  5 00:00:42 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP [::1]:6543
Jun  5 00:00:42 mythbuntu-M85M-US2H mythbackend[2031]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Jun  5 00:00:42 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun  5 00:00:42 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 0)
Jun  5 00:00:43 mythbuntu-M85M-US2H mythbackend[2031]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythbackend on mythbuntu-M85M-US2H' type '_mythbackend-master._tcp.' domain: 'local.'
Jun  5 00:00:44 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun  5 00:00:44 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 0)
Jun  5 00:00:44 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun  5 00:00:44 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 1)
Jun  5 00:00:44 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id -1.
Jun  5 00:00:44 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 28 items in 0.4 = 0.29 match + 0.07 place
Jun  5 00:00:44 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2126 (HandleRunSchedulerStartup) Scheduler: AUTO-Startup assumed
Jun  5 00:00:51 mythbuntu-M85M-US2H mythbackend[2031]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun  5 00:00:51 mythbuntu-M85M-US2H mythbackend[2031]: I HouseKeeping housekeeper.cpp:299 (RunHouseKeeping) Running mythfilldatabase
Jun  5 00:00:51 mythbuntu-M85M-US2H mythbackend[2031]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Jun  5 00:00:51 mythbuntu-M85M-US2H mythbackend[2031]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Jun  5 00:00:51 mythbuntu-M85M-US2H mythbackend[2031]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Jun  5 00:00:51 mythbuntu-M85M-US2H mythbackend[2031]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Jun  5 00:00:51 mythbuntu-M85M-US2H mythbackend[2031]: I Metadata_100 jobqueue.cpp:2151 (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for "Heir Hunters":Luckarift/Paine recorded from channel 7302 at 2012-06-04T14:58:00
Jun  5 00:00:52 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Jun  5 00:00:52 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 0)
Jun  5 00:00:52 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun  5 00:00:52 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 1)
Jun  5 00:00:53 mythbuntu-M85M-US2H mythbackend[2031]: I HouseKeeping housekeeper.cpp:809 (UpdateRecordedArtwork) Performing Artwork Refresh: /usr/bin/mythmetadatalookup --refresh-all-artwork  --verbose general --loglevel info --syslog local7
Jun  5 00:00:54 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Jun  5 00:00:54 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 0)
Jun  5 00:00:54 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun  5 00:00:54 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 1)
Jun  5 00:00:56 mythbuntu-M85M-US2H mythbackend[2031]: I Metadata_101 jobqueue.cpp:2151 (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for "The Diamond Jubilee Concert":"The Diamond Jubilee Concert" recorded from channel 11354 at 2012-06-04T19:28:00
Jun  5 00:00:57 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Jun  5 00:00:57 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 0)
Jun  5 00:00:57 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun  5 00:00:57 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 1)
Jun  5 00:01:01 mythbuntu-M85M-US2H mythbackend[2031]: I HouseKeeping housekeeper.cpp:816 (UpdateRecordedArtwork) Artwork Refresh Complete
Jun  5 00:01:32 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Jun  5 00:01:32 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 0)
Jun  5 00:01:32 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun  5 00:01:32 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 1)
Jun  5 00:01:32 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id -1.
Jun  5 00:01:32 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 28 items in 0.1 = 0.01 match + 0.06 place
Jun  5 00:02:01 mythbuntu-M85M-US2H mythbackend[2031]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Jun  5 00:06:01 mythbuntu-M85M-US2H mythbackend[2031]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun  5 00:11:05 mythbuntu-M85M-US2H mythbackend[2031]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun  5 00:11:32 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun  5 00:11:32 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 0)
Jun  5 00:11:32 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun  5 00:11:32 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 1)
Jun  5 00:12:41 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id -1.
Jun  5 00:12:41 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 28 items in 0.1 = 0.03 match + 0.06 place
Jun  5 00:16:06 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id -1.
Jun  5 00:16:06 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 28 items in 0.1 = 0.03 match + 0.07 place
Jun  5 00:16:08 mythbuntu-M85M-US2H mythbackend[2031]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun  5 00:17:01 mythbuntu-M85M-US2H mythbackend[2031]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Jun  5 00:17:05 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Jun  5 00:17:05 mythbuntu-M85M-US2H mythbackend[2031]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu-M85M-US2H as a client (events: 0)
Jun  5 00:19:27 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id -1.
Jun  5 00:19:27 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 28 items in 0.1 = 0.03 match + 0.05 place
Jun  5 00:21:10 mythbuntu-M85M-US2H mythbackend[2031]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun  5 00:23:36 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id -1.
Jun  5 00:23:36 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 28 items in 0.1 = 0.03 match + 0.08 place
Jun  5 00:26:11 mythbuntu-M85M-US2H mythbackend[2031]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jun  5 00:28:32 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id -1.
Jun  5 00:28:32 mythbuntu-M85M-US2H mythbackend[2031]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 28 items in 0.1 = 0.02 match + 0.04 place[/HTML]

One thought i have had is that currently i'm recording a series show on BBC One from freesat. This is also shown on BBC One HD, could the Mythtv scheduler be getting its self confused trying to swap between the two? 

I've just updated this morning to the latest fixes for 0.25, but it hasn't made any difference. 

[HTML]MythTV Version : v0.25-145-g6628925
MythTV Branch : fixes/0.25
Network Protocol : 72
Library API : 0.25.20120506-1
QT Version : 4.8.1
Options compiled in:
 linux profile use_hidesyms using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_bindings_php using_crystalhd using_dvb using_firewire using_frontend using_hdhomerun using_ceton using_hdpvr using_iptv using_ivtv using_joystick_menu using_libcec using_libcrypto using_libdns_sd using_libxml2 using_lirc using_mheg using_opengl_video using_qtwebkit using_qtscript using_qtdbus using_v4l2 using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_bindings_php using_mythtranscode using_opengl using_vaapi using_vdpau using_ffmpeg_threads using_live using_mheg using_libass using_libxml2
[/HTML]

Any thoughts on what is causing the Mythwelcome timer to reset are greatly received. Thanks.

---

### Post by Lester_Burnham on 2012-06-06
Hi,

Are you using EIT for guide data?
I'm in AU, but used to have shutdown set to less than 300 sec when using EIT, otherwise scanning would keep it awake. This was back in myth 0.22

I doubt it's your problem, if you were using 600.
Set it to 450 sec and see what happens :)

Lester

---

### Post by trippy21 on 2012-06-07
I'm using XMLTV for my main guide but have EIT enabled in case of live updates for programmes.  

I set the time-out to 300 seconds with my crawl time-out still set to 660 and it worked. Its a bit odd as none of these settings changed from my 11.10 install and it worked fine on there!

But will keep an eye on it over the next few days and see if it keep behaving.

Thanks

---

