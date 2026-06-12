---
title: "HD Homerun TV tuner show as unavailable"
date: 2014-05-26
forum: Mythbuntu
---

### Post by nainsurvolte on 2014-05-26
Possibly the last chapter of my saga to get my MythTv up and running
Got the Backend up and running
Got MythWeb up and running

But now I have issues with the Tv Tuners...

I manage to go through the full setup of Myth Backend including the scan of the channels. When exiting I have no error message.

I first tried to connect via my client (XBMC) but it did not work.
I then tried to record something via MythWeb, but it did not work. In addition, all currently scheduled recording were deactivated.  The ones I tried to do manually were showing up with blank dates and time (0000-00-00 00:00:00)
I then tried the Myth Frontend, and in the status, the tuners show as unavailable.
Finally, I have no issues watching TV from those same tuners using Quick TV.
The Tuners are not behind a firewall, on the same network as all the machines.

Here is the last entry to the "**mythtv-setup.log**" 

```
ay 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handlerMay 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythtv-setup version: fixes/0.27 [v0.27-232-gf4825ca] www.mythtv.org
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/owner/.mythtv
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_CA.UTF-8
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I Logger logging.cpp:315 (run) Added logging to the console
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of TV-server
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to EN_CA
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale EN_CA
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
May 26 08:00:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1280x1024 60.020 Hz
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for module mythfrontend
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/dev/lircd'#012#011#011#011eno: No such file or directory (2)
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/owner/.mythtv/joystickmenurc
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: E CoreContext cecadapter.cpp:146 (Open) CECAdapter: Failed to find any CEC devices.
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext cecadapter.cpp:216 (Close) CECAdapter: Closing down CEC.
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 127.0.0.1:6948
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 192.168.1.111:6948
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [::1]:6948
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP [fe80::2e0:4cff:fe68:f71c%eth2]:6948
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext serverpool.cpp:494 (bind) Binding to UDP 192.168.1.255:6948
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext mythmainwindow.cpp:980 (Init) Using Frameless Window
May 26 08:00:14 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext mythmainwindow.cpp:993 (Init) Using Full Screen Window
May 26 08:00:15 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext mythmainwindow.cpp:1089 (Init) Using the Qt painter
May 26 08:00:19 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext mythuiwebbrowser.cpp:1078 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
May 26 08:00:19 TV-server mythtv-setup.real: mythtv-setup[23388]: E CoreContext mythuiwebbrowser.cpp:962 (Init) MythUIWebBrowser: failed to find our parent screen
May 26 08:00:19 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext mythuiwebbrowser.cpp:991 (Init) MythUIWebBrowser: enabling plugins
May 26 08:00:19 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
May 26 08:00:36 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext cardutil.cpp:2421 (GetHDHRdesc) CardUtil::GetHDHRdescription(10312338) - trying to locate device
May 26 08:02:05  mythtv-setup.real: last message repeated 3 times
May 26 08:02:09 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext mythmainwindow.cpp:2633 (LockInputDevices) Locking input devices
May 26 08:02:09 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext mythmainwindow.cpp:2681 (PauseIdleTimer) Suspending idle timer
May 26 08:02:09 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext videosource.cpp:591 (Load) XMLTVConfig::Load: Running 'tv_find_grabbers baseline'.
May 26 08:02:14 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext videosource.cpp:609 (Load) XMLTVConfig::Load: Finished running tv_find_grabbers
May 26 08:02:14 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext mythmainwindow.cpp:2635 (LockInputDevices) Unlocking input devices
May 26 08:02:14 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext mythmainwindow.cpp:2686 (PauseIdleTimer) Resuming idle timer
May 26 08:03:48 TV-server mythtv-setup.real: mythtv-setup[23388]: E ImageLoad mythuihelper.cpp:1364 (LoadScaleImage) MythUIHelper: LoadScaleImage(/home/owner/.mythtv/channels/) failed to load image
May 26 08:04:13  mythtv-setup.real: last message repeated 206 times
May 26 08:04:13 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext importicons.cpp:38 (ImportIconsWizard) Fetch Icons for channel 
May 26 08:04:14 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 1 of 24
May 26 08:04:14 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 2 of 24
May 26 08:04:15 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 3 of 24
May 26 08:04:16 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 4 of 24
May 26 08:04:17 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 5 of 24
May 26 08:04:18 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 6 of 24
May 26 08:04:19 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 7 of 24
May 26 08:04:19 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 8 of 24
May 26 08:04:20 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 9 of 24
May 26 08:04:21 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 10 of 24
May 26 08:04:22 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 11 of 24
May 26 08:04:23 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 12 of 24
May 26 08:04:23 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 13 of 24
May 26 08:04:24 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 14 of 24
May 26 08:04:25 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 15 of 24
May 26 08:04:26 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 16 of 24
May 26 08:04:27 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 17 of 24
May 26 08:04:27 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 18 of 24
May 26 08:04:28 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 19 of 24
May 26 08:04:29 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 20 of 24
May 26 08:04:30 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 21 of 24
May 26 08:04:30 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 22 of 24
May 26 08:04:31 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 23 of 24
May 26 08:04:34 TV-server mythtv-setup.real: mythtv-setup[23388]: N CoreContext importicons.cpp:415 (initialLoad) Downloading 24 of 24
May 26 08:04:35 TV-server mythtv-setup.real: mythtv-setup[23388]: E CoreContext importicons.cpp:642 (search) Error from search : #
May 26 08:04:39 TV-server mythtv-setup.real: mythtv-setup[23388]: E CoreContext importicons.cpp:642 (search) Error from search : 
May 26 08:04:41 TV-server mythtv-setup.real: mythtv-setup[23388]: E CoreContext importicons.cpp:642 (search) Error from search : #
May 26 08:04:42 TV-server mythtv-setup.real: mythtv-setup[23388]: E ImageLoad mythuihelper.cpp:1364 (LoadScaleImage) MythUIHelper: LoadScaleImage(/home/owner/.mythtv/channels/) failed to load image
May 26 08:05:46  mythtv-setup.real: last message repeated 577 times
May 26 08:06:21  mythtv-setup.real: last message repeated 59 times
May 26 08:06:21 TV-server mythtv-setup.real: mythtv-setup[23388]: W CoreContext virtualkeyboard_qt.cpp:46 (SwitchLayout) VirtualKeyboard: Cannot find layout for 'en'
May 26 08:06:21 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext xmlparse.cpp:58 (LoadTheme) XMLParse: LoadTheme using '/usr/share/mythtv/themes/default/keyboard/en_us_ui.xml'
May 26 08:06:24 TV-server mythtv-setup.real: mythtv-setup[23388]: E ImageLoad mythuihelper.cpp:1364 (LoadScaleImage) MythUIHelper: LoadScaleImage(/home/owner/.mythtv/channels/) failed to load image
May 26 08:06:56  mythtv-setup.real: last message repeated 23 times
May 26 08:06:56 TV-server mythtv-setup.real: mythtv-setup[23388]: W CoreContext virtualkeyboard_qt.cpp:46 (SwitchLayout) VirtualKeyboard: Cannot find layout for 'en'
May 26 08:06:56 TV-server mythtv-setup.real: mythtv-setup[23388]: I CoreContext xmlparse.cpp:58 (LoadTheme) XMLParse: LoadTheme using '/usr/share/mythtv/themes/default/keyboard/en_us_ui.xml'
May 26 08:07:02 TV-server mythtv-setup.real: mythtv-setup[23388]: E ImageLoad mythuihelper.cpp:1364 (LoadScaleImage) MythUIHelper: LoadScaleImage(/home/owner/.mythtv/channels/) failed to load image
May 26 08:08:05  mythtv-setup.real: last message repeated 120 times
May 26 08:08:34 TV-server mythtv-setup.real: mythtv-setup[23388]: E CoreContext mythmainwindow.cpp:1368 (detach) Could not find widget to detach
May 26 08:08:34 TV-server mythtv-setup.real: mythtv-setup[23388]: E CoreContext mythmainwindow.cpp:1368 (detach) Could not find widget to detach
```


Thanks,

---

### Post by nainsurvolte on 2014-05-26
Made a quick search and I had each card set to record 2 shows at the same time. Apparently it could have been a reason for the problem, but it did not fix the problem. It only made more sense by showing only 2 tuners instead of 4.

---

### Post by blm-ubunet on 2014-05-27
Unless the card is configured for "open on demand", mythTV requires exclusive access to tuner h/w.
Scheduling (esp. power up record scenarios) is almost impossible with exclusive access.

Your tuners are network devices right..
Do they have consistent IP addresses or other mechanism (MAC etc) to be located by?
Are you using the tuners with some other s/w or DLNA client etc.

There must be debugging info on MythTV wiki..

---

### Post by nainsurvolte on 2014-05-27
There is no other software using the HD Homerun Tuner. My XBMC client goes through MythTv, and the tests I did with Quick TV (soft. from the manufacturer installed on my Win7 machine) were done for a few second and never at the same time as I was running my the test for the MythTV Backend.

I also saw some thread where people had issues at startup where the tuners were not ready. This is not the case or at least, I cannot say right now if it applies since I have the issue when the backend starts after a complete setup.

HD Homerun is indeed a network Tuner. Its IP address is lock  through the mac address in the IP table of my router, therefore I always have a consistent address.

I did some extensive search before posting, the Wiki does not say much on troubleshooting HD Homerun tuners. Even the Troubleshooting guide of Silicon Dust, the company behind the HD Homerun, does not cover this case.

Did some more troubleshooting...

I rebooted the tuner... Did not improve
I completely uninstalled anything that can be related to HD Homerun on my machine... Did not improve
I used the hdhomerun-config command line to make sure I could see (discover) the device and the different tuners ( get /tuner<n>/status). Device is there and I can access both tuners, which is consistent with the fact I can see them in Mythbackend setup and even trigger a channel scan.

My guess is that remnant information of old configuration of the tuner is bugging it... My lead is that not so long ago, the tuners were IDed as 1 and 3. Now, they are IDed as 5 and 7, as if there is some ghost Tuner information somewhere. That is in addition to me, using the "Delete all Tuner card" in the setup to wipe all information.

If I could know where the tuner information is located I may be able to look at it. Or, if I could wipe it clean and start again a setup it would be better.

Thanks.

---

### Post by blm-ubunet on 2014-05-27
If you have old tuner setup to clear out (shows with broken tuners & incrementing numbered new tuners)..you need to "delete all tuners on all hosts"

If you have more than one HDHomerun device (connected to mythtv) you have to identify them by using the device ID serial number (written on device label).

I know you have restarted the BE after the reboot process but there can be startup timing issues with the BE starting before network interfaces are up.
The mythtv wiki example of upstart-job configuration has some clues.

---

### Post by nainsurvolte on 2014-05-28
I managed to generated a more complete log. Don't know if it is good or bad, but at least I see clearly the stuff related to the tuners. 10312338 is the ID of the HD Homerun device, and the -0 and -1 are the two tuners. Just don't know if it means something. I am still curious as to where the information of those tuners is located. I would like to see if there is some conflicting information in that file.

```
2014-05-28 20:52:48.933478 C [8204/8204] thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) - mythbackend version: fixes/0.27 [v0.27.1-4-g81c77ba] www.mythtv.org2014-05-28 20:52:48.933510 C [8204/8204] thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) - Qt version: compile: 4.8.1, runtime: 4.8.1
2014-05-28 20:52:48.933518 N [8204/8204] thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) - Enabled verbose msgs: all
2014-05-28 20:52:48.933638 N [8204/8204] thread_unknown logging.cpp:914 (logStart) - Setting Log Level to LOG_INFO
2014-05-28 20:52:48.945524 I [8204/8204] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Interrupt handler
2014-05-28 20:52:48.945541 I [8204/8204] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Terminated handler
2014-05-28 20:52:48.945554 I [8204/8204] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Segmentation fault handler
2014-05-28 20:52:48.945566 I [8204/8204] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Aborted handler
2014-05-28 20:52:48.945579 I [8204/8204] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Bus error handler
2014-05-28 20:52:48.945591 I [8204/8204] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Floating point exception handler
2014-05-28 20:52:48.945603 I [8204/8204] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Illegal instruction handler
2014-05-28 20:52:48.945621 I [8204/8204] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Real-time signal 0 handler
2014-05-28 20:52:48.945683 N [8204/8204] thread_unknown mythdirs.cpp:55 (InitializeMythDirs) - Using runtime prefix = /usr
2014-05-28 20:52:48.945704 N [8204/8204] thread_unknown mythdirs.cpp:68 (InitializeMythDirs) - Using configuration directory = /home/owner/.mythtv
2014-05-28 20:52:48.945819 I [8204/8204] CoreContext mythcorecontext.cpp:254 (Init) - Assumed character encoding: en_CA.UTF-8
2014-05-28 20:52:48.946338 N [8204/8204] CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) - Empty LocalHostName.
2014-05-28 20:52:48.946349 I [8204/8204] CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) - Using localhost value of TV-server
2014-05-28 20:52:48.946366 I [8204/8204] CoreContext mythdb.cpp:845 (ClearSettingsCache) - Clearing Settings Cache.
2014-05-28 20:52:48.946398 I [8204/8204] CoreContext mythcontext.cpp:882 (DefaultUPnP) - DefaultUPnP() - No default UPnP backend
2014-05-28 20:52:48.946431 I [8204/8204] CoreContext mythdb.cpp:845 (ClearSettingsCache) - Clearing Settings Cache.
2014-05-28 20:52:48.947986 I [8204/8207] Logger logging.cpp:315 (run) - Added logging to the console
2014-05-28 20:52:48.980041 I [8204/8204] CoreContext mythdbcon.cpp:76 (MSqlDatabase) - Database connection created: DBManager0
2014-05-28 20:52:48.980081 I [8204/8204] CoreContext mythdbcon.cpp:312 (popConnection) - New DB connection, total: 1
2014-05-28 20:52:48.983615 I [8204/8204] CoreContext mythdbcon.cpp:180 (OpenDatabase) - Connected to database 'mythconverg' at host: localhost
2014-05-28 20:52:48.988439 I [8204/8204] CoreContext mythdbcon.cpp:467 (CloseDatabases) - Closing DB connection named 'DBManager0'
2014-05-28 20:52:48.988524 I [8204/8204] CoreContext mythdb.cpp:845 (ClearSettingsCache) - Clearing Settings Cache.
2014-05-28 20:52:48.988596 I [8204/8204] CoreContext mythdbcon.cpp:76 (MSqlDatabase) - Database connection created: DBManager1
2014-05-28 20:52:48.988611 I [8204/8204] CoreContext mythdbcon.cpp:312 (popConnection) - New DB connection, total: 1
2014-05-28 20:52:48.989114 I [8204/8204] CoreContext mythdbcon.cpp:180 (OpenDatabase) - Connected to database 'mythconverg' at host: localhost
2014-05-28 20:52:48.990412 N [8204/8204] CoreContext mythcorecontext.cpp:1328 (InitLocale) - Setting QT default locale to EN_CA
2014-05-28 20:52:48.990506 I [8204/8204] CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) - Current locale EN_CA
2014-05-28 20:52:48.990581 N [8204/8204] CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) - Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
2014-05-28 20:52:48.996974 I [8204/8204] CoreContext mythdb.cpp:876 (ActivateSettingsCache) - Enabling Settings Cache.
2014-05-28 20:52:48.996987 I [8204/8204] CoreContext mythdb.cpp:845 (ClearSettingsCache) - Clearing Settings Cache.
2014-05-28 20:52:48.997094 E [8204/8204] CoreContext mythmiscutil.cpp:930 (setHttpProxy) - setHttpProxy() - failed to find a network proxy
2014-05-28 20:52:48.998769 I [8204/8204] CoreContext mythdb.cpp:878 (ActivateSettingsCache) - Disabling Settings Cache.
2014-05-28 20:52:48.998780 I [8204/8204] CoreContext mythdb.cpp:845 (ClearSettingsCache) - Clearing Settings Cache.
2014-05-28 20:52:49.000128 I [8204/8204] CoreContext schemawizard.cpp:118 (Compare) - Current MythTV Schema Version (DBSchemaVer): 1317
2014-05-28 20:52:49.000147 I [8204/8204] CoreContext mythdb.cpp:876 (ActivateSettingsCache) - Enabling Settings Cache.
2014-05-28 20:52:49.000153 I [8204/8204] CoreContext mythdb.cpp:845 (ClearSettingsCache) - Clearing Settings Cache.
2014-05-28 20:52:49.000843 I [8204/8204] CoreContext mythtranslation.cpp:65 (load) - Loading en_us translation for module mythfrontend
2014-05-28 20:52:49.001611 N [8204/8204] CoreContext main_helpers.cpp:582 (run_backend) - MythBackend: Starting up as the master server.
2014-05-28 20:52:49.011026 I [8204/8204] CoreContext tv_rec.cpp:701 (SetRecordingStatus) - TVRec[5]: SetRecordingStatus(Unknown->Unknown) on line 156
2014-05-28 20:52:49.011369 I [8204/8204] CoreContext tv_rec.cpp:1666 (GetStartChannel) - TVRec[5]: GetStartChannel(5, 'MPEG2TS')
2014-05-28 20:52:49.011649 I [8204/8204] CoreContext tv_rec.cpp:1688 (GetStartChannel) - TVRec[5]: Start channel: 2_1.
2014-05-28 20:52:49.011682 I [8204/8204] CoreContext tv_rec.cpp:130 (CreateChannel) - TVRec[5]: CreateChannel(2_1)
2014-05-28 20:52:49.011775 I [8204/8204] CoreContext recorders/hdhrchannel.cpp:57 (Open) - HDHRChan[5](10312338-0): Opening HDHR channel
2014-05-28 20:52:49.055327 I [8204/8206] LogForward loggingserver.cpp:1372 (forwardMessage) - New Client:  (#1)
2014-05-28 20:52:49.055589 I [8204/8206] LogForward loggingserver.cpp:142 (FileLogger) - Added logging to /var/log/mythtv/mythbackend.20140529005248.8204.log
2014-05-28 20:52:49.229918 I [8204/8204] CoreContext recorders/hdhrstreamhandler.cpp:341 (Connect) - HDHRSH(10312338-0): Successfully connected to device
2014-05-28 20:52:49.230356 I [8204/8204] CoreContext recorders/hdhrstreamhandler.cpp:43 (Get) - HDHRSH: Creating new stream handler 10312338-0 for 10312338-0
2014-05-28 20:52:49.241605 I [8204/8204] CoreContext recorders/channelbase.cpp:990 (InitializeInputs) - ChannelBase[5]: Input #5: 'MPEG2TS' schan(2_1) sourceid(1) ccid(5)
2014-05-28 20:52:49.241631 I [8204/8204] CoreContext recorders/channelbase.cpp:993 (InitializeInputs) - ChannelBase[5]: Current Input #5: 'MPEG2TS'
2014-05-28 20:52:49.242470 I [8204/8204] CoreContext recorders/dtvchannel.cpp:181 (SetChannelByString) - DTVChan[5](10312338-0): SetChannelByString(2_1): 
2014-05-28 20:52:49.244011 I [8204/8204] CoreContext recorders/hdhrchannel.cpp:170 (Tune) - HDHRChan[5](10312338-0): Tuning to 8vsb:503000000
2014-05-28 20:52:49.247376 I [8204/8204] CoreContext recorders/hdhrstreamhandler.cpp:461 (TuneChannel) - HDHRSH(10312338-0): Tuning channel 8vsb:503000000 (was none)
2014-05-28 20:52:49.249197 I [8204/8204] CoreContext recorders/dtvchannel.cpp:343 (SetChannelByString) - DTVChan[5](10312338-0): SetChannelByString(2_1): success
2014-05-28 20:52:49.249667 I [8204/8204] CoreContext recorders/hdhrstreamhandler.cpp:461 (TuneChannel) - HDHRSH(10312338-0): Tuning channel none (was 8vsb:503000000)
2014-05-28 20:52:49.260440 I [8204/8213] TVRecEvent tv_rec.cpp:4319 (SetFlags) - TVRec[5]: SetFlags(RunMainLoop,) -> RunMainLoop,
2014-05-28 20:52:49.260476 I [8204/8213] TVRecEvent tv_rec.cpp:4328 (ClearFlags) - TVRec[5]: ClearFlags(ExitPlayer,FinishRecording,) -> RunMainLoop,
2014-05-28 20:52:49.260980 I [8204/8213] TVRecEvent mythdbcon.cpp:76 (MSqlDatabase) - Database connection created: DBManager2
2014-05-28 20:52:49.261128 I [8204/8213] TVRecEvent mythdbcon.cpp:312 (popConnection) - New DB connection, total: 2
2014-05-28 20:52:49.261730 I [8204/8213] TVRecEvent mythdbcon.cpp:180 (OpenDatabase) - Connected to database 'mythconverg' at host: localhost
2014-05-28 20:52:49.268439 I [8204/8204] CoreContext tv_rec.cpp:701 (SetRecordingStatus) - TVRec[7]: SetRecordingStatus(Unknown->Unknown) on line 156
2014-05-28 20:52:49.268807 I [8204/8204] CoreContext tv_rec.cpp:1666 (GetStartChannel) - TVRec[7]: GetStartChannel(7, 'MPEG2TS')
2014-05-28 20:52:49.269093 I [8204/8204] CoreContext tv_rec.cpp:1688 (GetStartChannel) - TVRec[7]: Start channel: 2_1.
2014-05-28 20:52:49.269184 I [8204/8204] CoreContext tv_rec.cpp:130 (CreateChannel) - TVRec[7]: CreateChannel(2_1)
2014-05-28 20:52:49.269230 I [8204/8204] CoreContext recorders/hdhrchannel.cpp:57 (Open) - HDHRChan[7](10312338-1): Opening HDHR channel
2014-05-28 20:52:49.296603 I [8204/8204] CoreContext recorders/hdhrstreamhandler.cpp:341 (Connect) - HDHRSH(10312338-1): Successfully connected to device
2014-05-28 20:52:49.297021 I [8204/8204] CoreContext recorders/hdhrstreamhandler.cpp:43 (Get) - HDHRSH: Creating new stream handler 10312338-1 for 10312338-1
2014-05-28 20:52:49.311252 I [8204/8204] CoreContext recorders/channelbase.cpp:990 (InitializeInputs) - ChannelBase[7]: Input #6: 'MPEG2TS' schan(2_1) sourceid(1) ccid(7)
2014-05-28 20:52:49.311272 I [8204/8204] CoreContext recorders/channelbase.cpp:993 (InitializeInputs) - ChannelBase[7]: Current Input #6: 'MPEG2TS'
2014-05-28 20:52:49.343630 I [8204/8204] CoreContext recorders/dtvchannel.cpp:181 (SetChannelByString) - DTVChan[7](10312338-1): SetChannelByString(2_1): 
2014-05-28 20:52:49.357185 I [8204/8204] CoreContext recorders/hdhrchannel.cpp:170 (Tune) - HDHRChan[7](10312338-1): Tuning to 8vsb:503000000
2014-05-28 20:52:49.357591 I [8204/8204] CoreContext recorders/hdhrstreamhandler.cpp:461 (TuneChannel) - HDHRSH(10312338-1): Tuning channel 8vsb:503000000 (was none)
2014-05-28 20:52:49.359918 I [8204/8204] CoreContext recorders/dtvchannel.cpp:343 (SetChannelByString) - DTVChan[7](10312338-1): SetChannelByString(2_1): success
2014-05-28 20:52:49.360409 I [8204/8204] CoreContext recorders/hdhrstreamhandler.cpp:461 (TuneChannel) - HDHRSH(10312338-1): Tuning channel none (was 8vsb:503000000)
2014-05-28 20:52:49.379828 I [8204/8219] TVRecEvent tv_rec.cpp:4319 (SetFlags) - TVRec[7]: SetFlags(RunMainLoop,) -> RunMainLoop,
2014-05-28 20:52:49.379857 I [8204/8219] TVRecEvent tv_rec.cpp:4328 (ClearFlags) - TVRec[7]: ClearFlags(ExitPlayer,FinishRecording,) -> RunMainLoop,
2014-05-28 20:52:49.380376 I [8204/8219] TVRecEvent mythdbcon.cpp:76 (MSqlDatabase) - Database connection created: DBManager3
2014-05-28 20:52:49.380394 I [8204/8219] TVRecEvent mythdbcon.cpp:312 (popConnection) - New DB connection, total: 3
2014-05-28 20:52:49.380955 I [8204/8219] TVRecEvent mythdbcon.cpp:180 (OpenDatabase) - Connected to database 'mythconverg' at host: localhost
2014-05-28 20:52:49.387365 I [8204/8204] CoreContext scheduler.cpp:5238 (CreateConflictLists) - Assigning input 5 to conflict set 1
2014-05-28 20:52:49.387404 I [8204/8204] CoreContext scheduler.cpp:5238 (CreateConflictLists) - Assigning input 6 to conflict set 2
2014-05-28 20:52:49.396132 I [8204/8204] CoreContext programinfo.cpp:2136 (CheckProgramIDAuthorities) - Found 1 distinct programid authorities

```

---

### Post by dannyboy79 on 2014-05-29
may i suggest you delete all tuners on all backends and start over? i see something at the end of your log that says it's assigning input 5 and input 6. does the hdhr have 6 tuners? what's the problem after all anyway? are you not able to see any video output from any of your frontends?

---

### Post by nainsurvolte on 2014-05-29
I tried it and it did not work. It is about the 5th time I delete the tuners and start again and every time I delete the tuner configuration, there numbers increment as if I could create new but not delete the previous (and I am not talking about those listed in /dev). When everything was ok I was at 1 and 3. Now, I am at 11 and 13.

It is definitely a ownership issue. Instead of starting the service the regular way, I ran the mythbackend as root, and it works. The tuners are recognized and ready to record.

What are the specification for the ownership for the different users to run mythtv?

The mythtv user exists and was recreated by associating the old UID of the deleted mythtv user. Also, it is part of the following groups: mythtv, dialout, cdrom, audio and video.

Is root suppose to have special privileges?

Thanks

---

### Post by nainsurvolte on 2014-05-29
> **dannyboy79 said:**
> ... does the hdhr have 6 tuners? what's the problem after all anyway? are you not able to see any video output from any of your frontends?

No, I have 1 device with 2 tuners.

Problem is that none of my Frontend can connect to the tuners. Mythtv Frontend sees them as unavailable, Mythweb as currently not connected and XBMC cannot connect to them. But, if I use the little software from the manufacturer I can easily listen to TV on my Windows machine. Thus, the device is ok, the network access to the device is ok. It is aomething in the configuration of Mythtv.

---

### Post by nainsurvolte on 2014-05-29
I found the answer to my own question...:)

The tuner information is in the mythconverg database (thanks to a mysql crash course with Google) and the increment is normal as the device id parameter in the table is auto-increment... I also made some cleaning in the mythtv user in the mythconverg database. At some point I must have created all possibilities and I feared some conflict between localhost and the other which may have been considered the same (127.0.0.1 for ex) as the grant seemed different. Access to mythconverg is still good but still have the same issue with the tuners.

This morning I changed the user to run mythbackend to my own and it works. So again, must be a privilege issue. As far as rights goes, I can guarantee that /home/user/mythtv and all its content is owned by user mythtv and group mythtv. So is the folder where everything gets recorded and the /var/lib/mythtv.

Are they any other places (folders) or files that need to checked out?

Thanks.

---

### Post by blm-ubunet on 2014-05-29
Any localhost name changes between the users: mythtv, <other-FE-user> & root can mean that different setup profile is used.

You can use different config.xml file contents to expt with different frontend profiles.
But the contents of that file (or some other copy with same name) also effects the BE profile.

AFAIK the tuners belong to the localhostname profile named from the contents of config.xml.
AFAIK A blank localhostname then makes localhostname == localhost.

You can (easily) query the dBase for all hostnames.
(could post something later)
There is bound to be a unsafe way to deleted cruft but a safe way could be:
- change the localhostname to all these (old/previous) names by manipulating the config.xml file that is used by mythtv-setup
- & then delete all tuners on all hosts.
- decide on the localhostname
- sort out the config.xml files 
- Re-add tuners fresh with the right hostname.

---

### Post by nainsurvolte on 2014-05-31
Finally done....\\:D/ 

Had this post running in parallel

[https://forum.mythtv.org/viewtopic.php?f=36&t=188](https://forum.mythtv.org/viewtopic.php?f=36&t=188)

and finally managed to fix the issue without knowing what really caused it. Log files when running the application as mythtv or as my user had one difference I noticed (maybe more but one caught my eyes): the config folder /home/[user]/.mythtv.

I deleted the one of mythtv and replaced with the one in my own directory, changed the permissions of everything and voilà...

Thanks to all...

---

