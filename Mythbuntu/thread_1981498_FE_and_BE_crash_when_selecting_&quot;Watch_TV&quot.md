---
title: "FE and BE crash when selecting &quot;Watch TV&quot; or when starting a recording (.25)"
date: 2012-05-16
forum: Mythbuntu
---

### Post by mlrabbitt on 2012-05-16
I am running Mythbuntu 12.04, MythTV .25 BE and FE on the same PC.  I am using a Ceton InfiniTV 4 PCIe card and using SchedulesDirect as an input source.  I can manually tune to channels using the InfiniTV interface and mplayer.  When I open FE though and select "Watch TV", I see the "Please Wait..." screen and then the PC freezes.  Is anyone else experiencing this problem?  I know there is not a lot of documentation about using the InfiniTV card in Linux.

Backend log: 

```
May 16 22:12:13 mtv mythbackend[1765]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythbackend version: fixes/0.25 [v0.25] www.mythtv.org
May 16 22:12:13 mtv mythbackend[1765]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
May 16 22:12:13 mtv mythbackend[1765]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
May 16 22:12:13 mtv mythbackend[1765]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
May 16 22:12:13 mtv mythbackend[1765]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
May 16 22:12:13 mtv mythbackend[1765]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
May 16 22:12:13 mtv mythbackend[1765]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
May 16 22:12:13 mtv mythbackend[1765]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
May 16 22:12:13 mtv mythbackend[1765]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
May 16 22:12:13 mtv mythbackend[1765]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
May 16 22:12:13 mtv mythbackend[1765]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
May 16 22:12:13 mtv mythbackend[1765]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of mtv
May 16 22:12:13 mtv mythbackend[1765]: I CoreContext mythcontext.cpp:608 (TestDBconnection) Testing network connectivity to '192.168.1.142'
May 16 22:12:13 mtv mythbackend[1765]: I SystemManager system-unix.cpp:263 (run) Starting process manager
May 16 22:12:13 mtv mythbackend[1765]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
May 16 22:12:13 mtv mythbackend[1765]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
May 16 22:12:13 mtv mythbackend[1765]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
May 16 22:12:13 mtv mythbackend[1765]: A CoreContext mythcontext.cpp:414 (FindDatabase) Cannot find (ping) database host 192.168.1.142 on the network
May 16 22:12:13 mtv mythbackend[1765]: C CoreContext main.cpp:108 (main) Failed to init MythContext.
May 16 22:12:13 mtv mythbackend[1765]: E CoreContext mmulticastsocketdevice.cpp:62 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:15): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
May 16 22:12:13 mtv mythbackend[1783]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythbackend version: fixes/0.25 [v0.25] www.mythtv.org
May 16 22:12:13 mtv mythbackend[1783]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
May 16 22:12:13 mtv mythbackend[1783]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
May 16 22:12:13 mtv mythbackend[1783]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
May 16 22:12:13 mtv mythbackend[1783]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
May 16 22:12:13 mtv mythbackend[1783]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
May 16 22:12:13 mtv mythbackend[1783]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
May 16 22:12:13 mtv mythbackend[1783]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
May 16 22:12:13 mtv mythbackend[1783]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
May 16 22:12:13 mtv mythbackend[1783]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
May 16 22:12:13 mtv mythbackend[1783]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
May 16 22:12:13 mtv mythbackend[1783]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of mtv
May 16 22:12:13 mtv mythbackend[1783]: I CoreContext mythcontext.cpp:608 (TestDBconnection) Testing network connectivity to '192.168.1.142'
May 16 22:12:13 mtv mythbackend[1783]: I SystemManager system-unix.cpp:263 (run) Starting process manager
May 16 22:12:13 mtv mythbackend[1783]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
May 16 22:12:13 mtv mythbackend[1783]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
May 16 22:12:13 mtv mythbackend[1783]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
May 16 22:12:14 mtv mythbackend[1783]: A CoreContext mythcontext.cpp:414 (FindDatabase) Cannot find (ping) database host 192.168.1.142 on the network
May 16 22:12:14 mtv mythbackend[1783]: C CoreContext main.cpp:108 (main) Failed to init MythContext.
May 16 22:12:14 mtv mythbackend[1783]: E CoreContext mmulticastsocketdevice.cpp:62 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:15): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
May 16 22:12:14 mtv mythbackend[1834]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythbackend version: fixes/0.25 [v0.25] www.mythtv.org
May 16 22:12:14 mtv mythbackend[1834]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
May 16 22:12:14 mtv mythbackend[1834]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
May 16 22:12:14 mtv mythbackend[1834]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
May 16 22:12:14 mtv mythbackend[1834]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
May 16 22:12:14 mtv mythbackend[1834]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
May 16 22:12:14 mtv mythbackend[1834]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
May 16 22:12:14 mtv mythbackend[1834]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
May 16 22:12:14 mtv mythbackend[1834]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
May 16 22:12:14 mtv mythbackend[1834]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
May 16 22:12:14 mtv mythbackend[1834]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
May 16 22:12:14 mtv mythbackend[1834]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of mtv
May 16 22:12:14 mtv mythbackend[1834]: I CoreContext mythcontext.cpp:608 (TestDBconnection) Testing network connectivity to '192.168.1.142'
May 16 22:12:14 mtv mythbackend[1834]: I SystemManager system-unix.cpp:263 (run) Starting process manager
May 16 22:12:14 mtv mythbackend[1834]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
May 16 22:12:14 mtv mythbackend[1834]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
May 16 22:12:14 mtv mythbackend[1834]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
May 16 22:12:15 mtv mythbackend[1834]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to en_US
May 16 22:12:15 mtv mythbackend[1834]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale en_US
May 16 22:12:15 mtv mythbackend[1834]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
May 16 22:12:15 mtv mythbackend[1834]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
May 16 22:12:15 mtv mythbackend[1834]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
May 16 22:12:15 mtv mythbackend[1834]: N CoreContext main_helpers.cpp:556 (run_backend) MythBackend: Starting up as the master server.
May 16 22:12:23 mtv mythbackend[1834]: I CoreContext programinfo.cpp:2052 (CheckProgramIDAuthorities) Found 1 distinct programid authorities
May 16 22:12:23 mtv mythbackend[1834]: I Scheduler mythdbcon.cpp:422 (getStaticCon) New static DB connectionSchedCon
May 16 22:12:23 mtv mythbackend[1834]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6544
May 16 22:12:23 mtv mythbackend[1834]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 192.168.1.142:6544
May 16 22:12:23 mtv mythbackend[1834]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [::1]:6544
May 16 22:12:24 mtv mythbackend[1834]: I CoreContext main_helpers.cpp:626 (run_backend) Main::Registering HttpStatus Extension
May 16 22:12:24 mtv mythbackend[1834]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6543
May 16 22:12:24 mtv mythbackend[1834]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 192.168.1.142:6543
May 16 22:12:24 mtv mythbackend[1834]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [::1]:6543
May 16 22:12:24 mtv mythbackend[1834]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
May 16 22:12:25 mtv mythbackend[1834]: I CoreContext bonjourregister.cpp:100 (BonjourCallback) Bonjour: Service registration complete: name 'Mythbackend on mtv' type '_mythbackend-master._tcp.' domain: 'local.'
May 16 22:12:26 mtv mythbackend[1834]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id -1.
May 16 22:12:26 mtv mythbackend[1834]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 0 items in 0.1 = 0.11 match + 0.04 place
May 16 22:12:26 mtv mythbackend[1834]: I Scheduler scheduler.cpp:2135 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
May 16 22:12:31 mtv mythbackend[1834]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
May 16 22:12:31 mtv mythbackend[1834]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mtv as a client (events: 0)
May 16 22:12:31 mtv mythbackend[1834]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
May 16 22:12:31 mtv mythbackend[1834]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mtv as a client (events: 1)
May 16 22:12:33 mtv mythbackend[1834]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
May 16 22:13:42 mtv mythbackend[1834]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

Frontend log:

```
May 16 22:12:12 mtv mythfrontend[1702]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25] www.mythtv.org
May 16 22:12:12 mtv mythfrontend[1702]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
May 16 22:12:12 mtv mythfrontend[1702]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
May 16 22:12:12 mtv mythfrontend[1702]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
May 16 22:12:12 mtv mythfrontend[1702]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
May 16 22:12:12 mtv mythfrontend[1702]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
May 16 22:12:12 mtv mythfrontend[1702]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
May 16 22:12:12 mtv mythfrontend[1702]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
May 16 22:12:12 mtv mythfrontend[1702]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/matt/.mythtv
May 16 22:12:12 mtv mythfrontend[1702]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
May 16 22:12:12 mtv mythfrontend[1702]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
May 16 22:12:12 mtv mythfrontend[1702]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of mtv
May 16 22:12:12 mtv mythfrontend[1702]: I CoreContext mythcontext.cpp:608 (TestDBconnection) Testing network connectivity to '192.168.1.142'
May 16 22:12:12 mtv mythfrontend[1702]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
May 16 22:12:12 mtv mythfrontend[1702]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
May 16 22:12:12 mtv mythfrontend[1702]: I SystemManager system-unix.cpp:263 (run) Starting process manager
May 16 22:12:12 mtv mythfrontend[1702]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
May 16 22:12:12 mtv mythfrontend[1702]: A CoreContext mythcontext.cpp:414 (FindDatabase) Cannot find (ping) database host 192.168.1.142 on the network
May 16 22:12:12 mtv mythfrontend[1702]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1200 59.950 Hz
May 16 22:12:13 mtv mythfrontend[1702]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
May 16 22:12:13 mtv mythfrontend[1702]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/matt/.mythtv/joystickmenurc
May 16 22:12:13 mtv mythfrontend[1702]: I CoreContext serverpool.cpp:365 (bind) Binding to UDP 127.0.0.1:0
May 16 22:12:13 mtv mythfrontend[1702]: I CoreContext serverpool.cpp:365 (bind) Binding to UDP 192.168.200.2:0
May 16 22:12:13 mtv mythfrontend[1702]: I CoreContext serverpool.cpp:365 (bind) Binding to UDP [::1]:0
May 16 22:12:13 mtv mythfrontend[1702]: I CoreContext serverpool.cpp:365 (bind) Binding to UDP 192.168.200.255:0
May 16 22:12:13 mtv mythfrontend[1702]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
May 16 22:12:13 mtv mythfrontend[1702]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
May 16 22:12:13 mtv mythfrontend[1702]: I CoreContext mythmainwindow.cpp:1050 (Init) Using the Qt painter
May 16 22:12:13 mtv mythfrontend[1702]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to en_US
May 16 22:12:13 mtv mythfrontend[1702]: I CoreContext langsettings.cpp:104 (Load) System Locale (en_US), Country (US), Language (en)
May 16 22:12:28 mtv mythfrontend[1702]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
May 16 22:12:29 mtv mythfrontend[1702]: A CoreContext mythcontext.cpp:503 (PromptForDatabaseParams) User cancelled database configuration
May 16 22:12:29 mtv mythfrontend[1702]: E CoreContext main.cpp:1542 (main) Failed to init MythContext, exiting.
May 16 22:12:29 mtv mythfrontend[1702]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
May 16 22:12:29 mtv mythfrontend[1702]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
May 16 22:12:29 mtv mythfrontend[2261]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25] www.mythtv.org
May 16 22:12:29 mtv mythfrontend[2261]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
May 16 22:12:29 mtv mythfrontend[2261]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
May 16 22:12:29 mtv mythfrontend[2261]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
May 16 22:12:29 mtv mythfrontend[2261]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
May 16 22:12:29 mtv mythfrontend[2261]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
May 16 22:12:29 mtv mythfrontend[2261]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
May 16 22:12:29 mtv mythfrontend[2261]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
May 16 22:12:29 mtv mythfrontend[2261]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/matt/.mythtv
May 16 22:12:29 mtv mythfrontend[2261]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
May 16 22:12:29 mtv mythfrontend[2261]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
May 16 22:12:29 mtv mythfrontend[2261]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of mtv
May 16 22:12:29 mtv mythfrontend[2261]: I CoreContext mythcontext.cpp:608 (TestDBconnection) Testing network connectivity to '192.168.1.142'
May 16 22:12:29 mtv mythfrontend[2261]: I SystemManager system-unix.cpp:263 (run) Starting process manager
May 16 22:12:29 mtv mythfrontend[2261]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
May 16 22:12:29 mtv mythfrontend[2261]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
May 16 22:12:29 mtv mythfrontend[2261]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
May 16 22:12:29 mtv mythfrontend[2261]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to en_US
May 16 22:12:29 mtv mythfrontend[2261]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale en_US
May 16 22:12:29 mtv mythfrontend[2261]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
May 16 22:12:29 mtv mythfrontend[2261]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
May 16 22:12:29 mtv mythfrontend[2261]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
May 16 22:12:29 mtv mythfrontend[2261]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1200 59.950 Hz
May 16 22:12:29 mtv mythfrontend[2261]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6547
May 16 22:12:29 mtv mythfrontend[2261]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 192.168.1.142:6547
May 16 22:12:29 mtv mythfrontend[2261]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [::1]:6547
May 16 22:12:30 mtv mythfrontend[2261]: E CoreContext mythraopconnection.cpp:730 (LoadKey) RAOP Conn: Failed to read key from: /home/matt/.mythtv/RAOPKey.rsa
May 16 22:12:30 mtv mythfrontend[2261]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
May 16 22:12:30 mtv mythfrontend[2261]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
May 16 22:12:30 mtv mythfrontend[2261]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/dev/lircd'#012#011#011#011eno: No such file or directory (2)
May 16 22:12:30 mtv mythfrontend[2261]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/matt/.mythtv/joystickmenurc
May 16 22:12:30 mtv mythfrontend[2261]: I CoreContext serverpool.cpp:365 (bind) Binding to UDP 127.0.0.1:6948
May 16 22:12:30 mtv mythfrontend[2261]: I CoreContext serverpool.cpp:365 (bind) Binding to UDP 192.168.1.142:6948
May 16 22:12:30 mtv mythfrontend[2261]: I CoreContext serverpool.cpp:365 (bind) Binding to UDP [::1]:6948
May 16 22:12:30 mtv mythfrontend[2261]: I CoreContext serverpool.cpp:365 (bind) Binding to UDP 192.168.1.255:6948
May 16 22:12:30 mtv mythfrontend[2261]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
May 16 22:12:30 mtv mythfrontend[2261]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
May 16 22:12:30 mtv mythfrontend[2261]: I CoreContext mythmainwindow.cpp:1050 (Init) Using the Qt painter
May 16 22:12:31 mtv mythfrontend[2261]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
May 16 22:12:31 mtv mythfrontend[2261]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
May 16 22:12:31 mtv mythfrontend[2261]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
May 16 22:12:31 mtv mythfrontend[2261]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
May 16 22:12:31 mtv mythfrontend[2261]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
May 16 22:12:31 mtv mythfrontend[2261]: N CoreContext mythmainwindow.cpp:1859 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
May 16 22:12:31 mtv mythfrontend[2261]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
May 16 22:12:31 mtv mythfrontend[2261]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
May 16 22:12:31 mtv mythfrontend[2261]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
May 16 22:12:31 mtv mythfrontend[2261]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Mythbuntu'
May 16 22:12:31 mtv mythfrontend[2261]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.142:6543 (try 1 of 1)
May 16 22:12:31 mtv mythfrontend[2261]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
May 16 22:12:31 mtv mythfrontend[2261]: I CoreContext bonjourregister.cpp:100 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on mtv' type '_mythfrontend._tcp.' domain: 'local.'
May 16 22:12:34 mtv mythfrontend[2261]: N CoreContext mythmainwindow.cpp:2588 (PauseIdleTimer) Resuming idle timer
May 16 22:12:34 mtv mythfrontend[2261]: N CoreContext mythmainwindow.cpp:2588 (PauseIdleTimer) Resuming idle timer
May 16 22:12:34 mtv mythfrontend[2261]: I CoreContext bonjourregister.cpp:26 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on mtv'
May 16 22:12:34 mtv mythfrontend[2261]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
May 16 22:12:34 mtv mythfrontend[2261]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
May 16 22:12:34 mtv mythfrontend[2261]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
May 16 22:12:35 mtv mythfrontend[2261]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.
```

---

### Post by elliott6 on 2012-05-17
I wouldn't be much help, but glancing through the logs, it looks as if maybe your database is corrupted, or not there?  Or perhaps it's a mysql/configuration issue?  Do videos and other such things work?  Can it record (not live, and through playback) if you set it to record something?

> 
May 16 22:12:13 mtv mythbackend[1765]: A CoreContext mythcontext.cpp:414 (FindDatabase) Cannot find (ping) database host 192.168.1.142 on the network
May 16 22:12:13 mtv mythbackend[1765]: C CoreContext main.cpp:108 (main) Failed to init MythContext.


I personally had a similar problem with my fresh install of 12.04 and conversion of database, but I was also adding in a new HDHomerun Prime at the same time (and thought it was this).  

My suggestion would be to remove your tuners and reinstall (including video lineups) in the myth backend setup, especially if it can not record.  That ended up doing it for me, but took a few tries.  

Other than that, it would be to ensure the network connection, myth configuration with server names, PIN, and passwords are correct, as well as read and write permissions for the users and group to locations of the database and where you are storing your media.

Sorry if the above doesn't help, but just some things I have come across.  There are plenty of others that will chime in with more helpful info, but I know what it's like to wait for no response, so I thought I would give you some items to get started with.

Good luck!

---

### Post by mlrabbitt on 2012-05-17
I am not sure why it throws the line about not being able to find my database.  When I pull up mythfrontend I don't get any errors about connecting to the database and I can pull up database items like all the channel information.  The only change at all I made to MySQL was the fix described here to allow mythfilldatabase to run quicker: [http://ubuntuforums.org/showthread.php?p=11927568](http://ubuntuforums.org/showthread.php?p=11927568) .

If I try to schedule a recording it will crash instantly, even if I try scheduling it from MythWeb.  I am able to playback a video file fine inside mythfrontend.

Sometimes, after I crash and restart the computer it will show a crash log that "mythfrontend.real crashed with SIGSEGV".  I wasn't sure how to find this log though so I can't paste it here.

I already tried doing a full reinstall of Mythbuntu.  I wanted to try installing on a different system but I don't have another system available that has enough room for the InfiniTV card.

---

### Post by mlrabbitt on 2012-05-17
I may have figured it out.  In the capture card settings I had the "Device" set to RTP, which I was following based on the MythTV Wiki page for the InfiniTV 4.  Switching it to 0 (like it instructs you to, d'oh) I believe fixes it.  I can start a recording and tap into the recording now but going to "Watch TV" just throws some sql errors, probably created by me.  I will start from scratch and post an update.

---

### Post by mlrabbitt on 2012-05-17
This did in fact fix it.  Working perfectly now :)

---

### Post by elliott6 on 2012-05-19
Glad you got it working.  And even better was that it was as "easy" as following the instructions from the Wiki!

Sometimes it's the simplest solutions.

---

### Post by Socrates1013 on 2012-05-23
The wiki is due for an update. I had this same problem, mlrabbitt's solution did it for me. I also had to repair the database though afterword w/ mysqlcheck --auto-repair -A -u mythtv -pmysqlpass, replacing "mysqlpass" w/ the password to the database, which can be found in the setup pages of mythfrontend. Got that repair database command from here [http://www.pantz.org/software/mysql/fixingmysqlcrashedtables.html](http://www.pantz.org/software/mysql/fixingmysqlcrashedtables.html)

---

