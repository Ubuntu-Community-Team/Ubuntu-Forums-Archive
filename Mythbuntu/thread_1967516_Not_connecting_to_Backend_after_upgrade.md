---
title: "Not connecting to Backend after upgrade"
date: 2012-04-28
forum: Mythbuntu
---

### Post by timswait on 2012-04-28
I've just upgraded my Mythbuntu to 12.04 and my MythTV to 0.25, but it no longer works:(
I was getting the error "Could not connect to the master backend server" I found this thread:
[http://ubuntuforums.org/showthread.php?t=1959953&highlight=master+backend+server.+running%3F&page=2](http://ubuntuforums.org/showthread.php?t=1959953&highlight=master+backend+server.+running%3F&page=2)
Which solved the problem by changing IFACE!=lo to IFACE=lo in the mythtv-backend.conf file.
I tried doing that and I no longer get the "Could not connect to the master backend server" error, but it still doesn't work, whenever I try to watch TV it says "all tuners are currently busy" and nothing else seems to work so I think it's still not properly connecting.
Here's a section of the backend log if it helps:
```
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/trilby/.mythtv
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_GB.UTF-8
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of trilby-myth
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_GB
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_GB
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 59.939 Hz
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/dev/lircd'#012#011#011#011eno: No such file or directory (2)
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/trilby/.mythtv/joystickmenurc
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP 127.0.0.1:6948
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP [::1]:6948
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I CoreContext mythmainwindow.cpp:1050 (Init) Using the Qt painter
Apr 28 12:40:23 trilby-myth mythtv-setup[3606]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
```

---

### Post by SchneiderIS on 2012-06-14
You have this marked as solved but there is nothing showing what the solution was.  Could you post how you solved this problem?

---

### Post by timswait on 2012-06-20
It turned out the solution in[http://ubuntuforums.org/showthread.p...ning%3F&page=2]("http://ubuntuforums.org/showthread.p...ning%3F&page=2") had worked after all. The reason I was still getting an "All tuners busy" message was because I also needed to upgrade my tuner drivers. When I did that it all worked again :)

---

