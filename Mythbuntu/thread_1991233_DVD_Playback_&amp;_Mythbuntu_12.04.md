---
title: "DVD Playback &amp; Mythbuntu 12.04"
date: 2012-05-30
forum: Mythbuntu
---

### Post by jlp_engineer on 2012-05-30
I have continued to make progress with MythTV 0.25 and Ubuntu has allowed me to get further than other distributions.  I keep resolving issues I run into with the good help from the fine folks in this forum. ):P

I ran into some issues with my analog tuners (PVR-150's), and was able to resolve them both. :)  The first was a resolution issue with the default playback settings for MPEG-2 encoders.  Funny, the screen says that any other setting (720) may result in problems, and I sure had problems.  Then I had issues getting my analog tuners on my slave backend to display LiveTV on my remote frontends.  It worked fine on an FE installed on the slave, but nowhere else.  The culprit there was an incorrect IP setting on my slave.  Had to use the actual IP of the machine instead of the default setting of the local loop back address (thank you Nick).

But now I have another issue on the path to media server nirvana. :guitar: 

I have a bunch of DVD ISO's that I ripped using DVDfab (in Windows) and K9Copy and others in Liunx.  They play fine under 0.24 fixes, but now when I try to play them on any of my Frontends or even FE's installed on either backend, I get a pause after telling the interface to play the movie that lasts several seconds, but the screen does not change (just see the movie information, with the play and done selections).  Once the pause is over, control of the interface returns, but no movie gets played.  It doesn't even seem like it tries to play it, but it seems like something is happening in the background when the pause occurs.  I have tried old ISO's and new ones - no change.  :(

I have a video storage group defined, and the ISO's are in the correct directory, as evidenced by the ISO's showing up during a video scan.  I have also checked the third party software, and it is installed.  I even tried to play an actual DVD (instead of just an ISO), but I cannot get that to play either.  I tried VLC to play the same DVD, and it works without any issues, so I know the issue is isolated to MythTV.  Does anyone have any suggestions?

Thanks in advance.

---

### Post by klc5555 on 2012-05-30
First step is to check the frontend log.

Second step is to run the frontend manually from a command prompt. When the DVD playback fails, force to the foreground the terminal window from which mythfrontend is running, and you may get some error information  from the terminal that is useful for diagnosing the problem.

---

### Post by jlp_engineer on 2012-05-30
> **klc5555 said:**
> First step is to check the frontend log.  

The FE log doesn't show much, but here it is:

```


May 30 12:37:38 MYTHFE1 mythfrontend[4095]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25] www.mythtv.org
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/jpreston/.mythtv
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of MYTHFE1
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I CoreContext mythcontext.cpp:608 (TestDBconnection) Testing network connectivity to '192.168.1.100'
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I SystemManager system-unix.cpp:263 (run) Starting process manager
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to en_US
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale en_US
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1440x900 59.887 Hz
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6547
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 192.168.1.9:6547
May 30 12:37:38 MYTHFE1 mythfrontend[4095]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [::1]:6547
May 30 12:37:39 MYTHFE1 mythfrontend[4095]: E CoreContext mythraopconnection.cpp:730 (LoadKey) RAOP Conn: Failed to read key from: /home/jpreston/.mythtv/RAOPKey.rsa
May 30 12:37:39 MYTHFE1 mythfrontend[4095]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
May 30 12:37:39 MYTHFE1 mythfrontend[4095]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
May 30 12:37:39 MYTHFE1 mythfrontend[4095]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/jpreston/.mythtv/lircrc' config
May 30 12:37:39 MYTHFE1 mythfrontend[4095]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/jpreston/.mythtv/joystickmenurc
May 30 12:37:39 MYTHFE1 mythfrontend[4095]: I CoreContext serverpool.cpp:365 (bind) Binding to UDP 127.0.0.1:6948
May 30 12:37:39 MYTHFE1 mythfrontend[4095]: I CoreContext serverpool.cpp:365 (bind) Binding to UDP 192.168.1.9:6948
May 30 12:37:39 MYTHFE1 mythfrontend[4095]: I CoreContext serverpool.cpp:365 (bind) Binding to UDP [::1]:6948
May 30 12:37:39 MYTHFE1 mythfrontend[4095]: I CoreContext serverpool.cpp:365 (bind) Binding to UDP 192.168.1.255:6948
May 30 12:37:39 MYTHFE1 mythfrontend[4095]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
May 30 12:37:39 MYTHFE1 mythfrontend[4095]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
May 30 12:37:40 MYTHFE1 mythfrontend[4095]: I CoreContext mythmainwindow.cpp:1050 (Init) Using the Qt painter
May 30 12:37:40 MYTHFE1 mythfrontend[4095]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
May 30 12:37:40 MYTHFE1 mythfrontend[4095]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
May 30 12:37:40 MYTHFE1 mythfrontend[4095]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
May 30 12:37:40 MYTHFE1 mythfrontend[4095]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
May 30 12:37:40 MYTHFE1 mythfrontend[4095]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
May 30 12:37:41 MYTHFE1 mythfrontend[4095]: N CoreContext mythmainwindow.cpp:1859 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
May 30 12:37:41 MYTHFE1 mythfrontend[4095]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
May 30 12:37:41 MYTHFE1 mythfrontend[4095]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
May 30 12:37:41 MYTHFE1 mythfrontend[4095]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
May 30 12:37:41 MYTHFE1 mythfrontend[4095]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Mythbuntu'
May 30 12:37:41 MYTHFE1 mythfrontend[4095]: I Reconnect mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
May 30 12:37:41 MYTHFE1 mythfrontend[4095]: I Reconnect mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
May 30 12:37:41 MYTHFE1 mythfrontend[4095]: I CoreContext bonjourregister.cpp:100 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on MYTHFE1' type '_mythfrontend._tcp.' domain: 'local.'
May 30 12:37:54 MYTHFE1 mythfrontend[4095]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
May 30 12:37:54 MYTHFE1 mythfrontend[4095]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
May 30 12:37:54 MYTHFE1 mythfrontend[4095]: E CoreContext fileringbuffer.cpp:805 (Seek) FileRingBuf(myth://Videos@192.168.1.100:6543/CAPTAIN_AMERICA.iso): Seek(524288, SEEK_SET) Failed#012#011#011#011eno: Invalid argument (22)
May 30 12:37:54 MYTHFE1 mythfrontend[4095]: E CoreContext fileringbuffer.cpp:805 (Seek) FileRingBuf(myth://Videos@192.168.1.100:6543/CAPTAIN_AMERICA.iso): Seek(524288, SEEK_SET) Failed#012#011#011#011eno: Invalid argument (22)
May 30 12:38:04 MYTHFE1 mythfrontend[4095]: E CoreContext dvdringbuffer.cpp:53 (DVDInfo) DVDInfo: Failed to open device at myth://Videos@192.168.1.100:6543/CAPTAIN_AMERICA.iso
May 30 12:38:14 MYTHFE1 mythfrontend[4095]: N CoreContext mythmainwindow.cpp:2588 (PauseIdleTimer) Resuming idle timer
May 30 12:38:14 MYTHFE1 mythfrontend[4095]: N CoreContext mythmainwindow.cpp:2588 (PauseIdleTimer) Resuming idle timer
May 30 12:38:14 MYTHFE1 mythfrontend[4095]: I CoreContext bonjourregister.cpp:26 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on MYTHFE1'
May 30 12:38:14 MYTHFE1 mythfrontend[4095]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
May 30 12:38:14 MYTHFE1 mythfrontend[4095]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
May 30 12:38:14 MYTHFE1 mythfrontend[4095]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
May 30 12:38:14 MYTHFE1 mythfrontend[4095]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.


```

Hopefully you can spot something I might have missed.

---

### Post by jlp_engineer on 2012-05-30
> **klc5555 said:**
> 
Second step is to run the frontend manually from a command prompt. When the DVD playback fails, force to the foreground the terminal window from which mythfrontend is running, and you may get some error information  from the terminal that is useful for diagnosing the problem.

OK, here is the output from the terminal.  A good amount of information, but I don't see anything telling me why it will not play the file other than the "comment" about not being able to open the IFO files, once it begins to open the ISO.  I guess that would be a top level explanation as to why playback is not occurring, but WHY can't the files be opened?

```



QGtkStyle was unable to detect the current GTK+ theme.
2012-05-30 12:44:28.443015 C  mythfrontend version: fixes/0.25 [v0.25] www.mythtv.org
2012-05-30 12:44:28.443093 N  Enabled verbose msgs:  general
2012-05-30 12:44:28.443231 N  Setting Log Level to LOG_INFO
2012-05-30 12:44:28.443401 I  Added logging to the console
2012-05-30 12:44:28.443490 I  Added syslogging to facility local7
2012-05-30 12:44:28.443517 I  Added database logging to table logging
2012-05-30 12:44:28.443879 N  Setting up SIGHUP handler
2012-05-30 12:44:28.444264 N  Using runtime prefix = /usr
2012-05-30 12:44:28.444385 N  Using configuration directory = /home/jpreston/.mythtv
2012-05-30 12:44:28.445214 I  Assumed character encoding: en_US.UTF-8
2012-05-30 12:44:28.447708 N  Empty LocalHostName.
2012-05-30 12:44:28.447758 I  Using localhost value of MYTHFE1
2012-05-30 12:44:28.448538 I  Testing network connectivity to '192.168.1.100'
2012-05-30 12:44:28.454157 I  Starting IO manager (read)
2012-05-30 12:44:28.454191 I  Starting IO manager (write)
2012-05-30 12:44:28.454226 I  Starting process manager
2012-05-30 12:44:28.454279 I  Starting process signal handler
2012-05-30 12:44:28.623541 N  Setting QT default locale to en_US
2012-05-30 12:44:28.623735 I  Current locale en_US
2012-05-30 12:44:28.623895 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2012-05-30 12:44:28.755477 I  ScreenSaverX11Private: XScreenSaver support enabled
2012-05-30 12:44:28.757467 I  ScreenSaverX11Private: DPMS is disabled.
2012-05-30 12:44:28.787419 N  Desktop video mode: 1440x900 59.887 Hz
2012-05-30 12:44:28.845770 I  Listening on TCP 127.0.0.1:6547
2012-05-30 12:44:28.846066 I  Listening on TCP 192.168.1.9:6547
2012-05-30 12:44:28.846349 I  Listening on TCP [::1]:6547
2012-05-30 12:44:29.187418 E  RAOP Conn: Failed to read key from: /home/jpreston/.mythtv/RAOPKey.rsa
2012-05-30 12:44:29.187458 E  RAOP Device: Aborting startup - no key found.
2012-05-30 12:44:29.194054 I  Loading en_us translation for module mythfrontend
2012-05-30 12:44:29.214442 I  LIRC: Successfully initialized '/dev/lircd' using '/home/jpreston/.mythtv/lircrc' config
2012-05-30 12:44:29.214782 E  JoystickMenuThread: Joystick disabled - Failed to read /home/jpreston/.mythtv/joystickmenurc
2012-05-30 12:44:29.216720 I  Binding to UDP 127.0.0.1:6948
2012-05-30 12:44:29.216873 I  Binding to UDP 192.168.1.9:6948
2012-05-30 12:44:29.217067 I  Binding to UDP [::1]:6948
2012-05-30 12:44:29.217202 I  Binding to UDP 192.168.1.255:6948
2012-05-30 12:44:29.299450 I  Using Frameless Window
2012-05-30 12:44:29.299566 I  Using Full Screen Window
2012-05-30 12:44:29.634348 I  Using the Qt painter
2012-05-30 12:44:29.978205 I  Current MythTV Schema Version (DBSchemaVer): 1299
2012-05-30 12:44:30.202957 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2012-05-30 12:44:30.202994 E  ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2012-05-30 12:44:30.204870 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2012-05-30 12:44:30.204902 E  ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2012-05-30 12:44:30.615442 N  Registering Internal as a media playback plugin.
2012-05-30 12:44:30.731137 I  Loading en_us translation for module mythgallery
2012-05-30 12:44:30.750937 I  Current MythMusic Schema Version (MusicDBSchemaVer): 1019
2012-05-30 12:44:30.790911 I  Loading en_us translation for module mythmusic
2012-05-30 12:44:30.936281 N  Found mainmenu.xml for theme 'Mythbuntu'
2012-05-30 12:44:31.009805 I  MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2012-05-30 12:44:31.012591 I  Using protocol version 72
2012-05-30 12:44:31.288634 I  Bonjour: Service registration complete: name 'Mythfrontend on MYTHFE1' type '_mythfrontend._tcp.' domain: 'local.'
libdvdnav: Using dvdnav version svnR1215
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
2012-05-30 12:44:54.594410 I  Using protocol version 72
2012-05-30 12:44:54.596484 I  Using protocol version 72
2012-05-30 12:44:54.600714 E  FileRingBuf(myth://Videos@192.168.1.100:6543/CAPTAIN_AMERICA.iso): Seek(524288, SEEK_SET) Failed
			eno: Invalid argument (22)
2012-05-30 12:44:54.601662 E  FileRingBuf(myth://Videos@192.168.1.100:6543/CAPTAIN_AMERICA.iso): Seek(524288, SEEK_SET) Failed
			eno: Invalid argument (22)
2012-05-30 12:45:04.614064 E  DVDInfo: Failed to open device at myth://Videos@192.168.1.100:6543/CAPTAIN_AMERICA.iso


```

Could it be that the ISO is encrypted, and playing encrypted ISO's using the internal player is not supported?  But this makes no sense, because this was working under 0.24 using the internal player.  But now I cannot remember if I was using storage groups or not.  

Question: Can the internal player play back encrypted DVD ISO's if they are not stored in storage groups?  If so, do you just delete the video storage group and define the path to the ISO's folder in the FE setup?

Question: If the trouble "IS" that the encrypted DVD ISO will not play, then does this mean playing a physical DVD optical disc "ALSO" will not work?  Right now I am also unable to play DVD's discs.

Question: If the issue is playback of encrypted DVD ISO's is not supported, is there a way to remove the encryption from the ISO to test that theory?

---

### Post by jlp_engineer on 2012-05-30
Update:

I mentioned in my first post that VLC works well, and it does.  It will play the entire DVD disc (not ISO this time, the actual disc).  When I tried the internal player, the notices and warnings will play just fine, and the menu is displayed, but when I select the option to play the movie, I get tossed out to the MythTV menus.  

Below is the Frontend log for this:

```


May 30 14:00:14 MYTHFE1 mythfrontend[1975]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
May 30 14:00:14 MYTHFE1 mythfrontend[1975]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
May 30 14:00:14 MYTHFE1 mythfrontend[1975]: N CoreContext avformatdecoder.cpp:750 (SetEof) AFD: Resetting byte context eof (livetv 1 was eof 0)
May 30 14:00:14 MYTHFE1 mythfrontend[1975]: E Decoder ringbuffer.cpp:259 (Reset) RingBuf(myth://192.168.1.110:6543/1030_20120530140000.mpg): RingBuffer::Reset() nonzero readpos.  toAdjust: 1 readpos: -288704 readAdjust: 726820800
May 30 14:00:14 MYTHFE1 mythfrontend[1975]: N Decoder avformatdecoder.cpp:750 (SetEof) AFD: Resetting byte context eof (livetv 1 was eof 0)
May 30 14:09:53 MYTHFE1 mythfrontend[1975]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
May 30 14:09:53 MYTHFE1 mythfrontend[1975]: I CoreContext mythpainter_vdpau.cpp:111 (ClearCache) VDPAU Painter: Clearing VDPAU painter cache.
May 30 14:09:57 MYTHFE1 mythfrontend[1975]: I CoreContext tv_play.cpp:2358 (HandleStateChange) TV: Changing from WatchingLiveTV to None
May 30 14:09:57 MYTHFE1 mythfrontend[1975]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
May 30 14:09:58 MYTHFE1 mythfrontend[1975]: N CoreContext mythmainwindow.cpp:2583 (PauseIdleTimer) Suspending idle timer
May 30 14:10:10 MYTHFE1 mythfrontend[1975]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
May 30 14:10:10 MYTHFE1 mythfrontend[1975]: N CoreContext mythmainwindow.cpp:2588 (PauseIdleTimer) Resuming idle timer
May 30 14:10:10 MYTHFE1 mythfrontend[1975]: N CoreContext mythmainwindow.cpp:2583 (PauseIdleTimer) Suspending idle timer
May 30 14:10:10 MYTHFE1 mythfrontend[1975]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
May 30 14:10:10 MYTHFE1 mythfrontend[1975]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingDVD
May 30 14:10:10 MYTHFE1 mythfrontend[1975]: I CoreContext dvdringbuffer.cpp:338 (OpenFile) DVDRB: Opened DVD device at //dev/sr0
May 30 14:10:10 MYTHFE1 mythfrontend[1975]: I CoreContext dvdringbuffer.cpp:366 (OpenFile) DVDRB: There are 2 titles on the disk
May 30 14:10:10 MYTHFE1 mythfrontend[1975]: I CoreContext dvdringbuffer.cpp:382 (OpenFile) DVDRB: Title 1: chapters 16 duration 6504
May 30 14:10:10 MYTHFE1 mythfrontend[1975]: I CoreContext dvdringbuffer.cpp:408 (OpenFile) DVDRB: Starting with title 1
May 30 14:10:11 MYTHFE1 mythfrontend[1975]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
May 30 14:10:11 MYTHFE1 mythfrontend[1975]: I CoreContext dvdringbuffer.cpp:446 (StartFromBeginning) DVDRB: Resetting DVD device.
May 30 14:10:11 MYTHFE1 mythfrontend[1975]: I CoreContext avformatdecoder.cpp:2100 (ScanStreams) AFD: Opened codec 0x12f5770, id(MPEG2VIDEO) type(Video)
May 30 14:10:11 MYTHFE1 mythfrontend[1975]: I CoreContext avformatdecoder.cpp:1958 (ScanStreams) AFD: codec AC3 has 6 channels
May 30 14:10:11 MYTHFE1 mythfrontend[1975]: I CoreContext avformatdecoder.cpp:2100 (ScanStreams) AFD: Opened codec 0x4db42d0, id(AC3) type(Audio)
May 30 14:10:11 MYTHFE1 mythfrontend[1975]: I CoreContext avformatdecoder.cpp:1958 (ScanStreams) AFD: codec AC3 has 2 channels
May 30 14:10:11 MYTHFE1 mythfrontend[1975]: I CoreContext avformatdecoder.cpp:2100 (ScanStreams) AFD: Opened codec 0x4db7d30, id(AC3) type(Audio)
May 30 14:10:11 MYTHFE1 mythfrontend[1975]: I CoreContext audio/audiooutputbase.cpp:764 (Reconfigure) AO: Opening audio device 'default' ch 2(6) sr 48000 sf signed 32 bit reenc 0
May 30 14:10:11 MYTHFE1 mythfrontend[1975]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 192
May 30 14:10:11 MYTHFE1 mythfrontend[1975]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
May 30 14:10:11 MYTHFE1 mythfrontend[1975]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 192 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
May 30 14:10:11 MYTHFE1 mythfrontend[1975]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
May 30 14:10:12 MYTHFE1 mythfrontend[1975]: I CoreContext mythrender_vdpau.cpp:1675 (CreatePresentationSurfaces) VDPAU: Created 2 output surfaces.
May 30 14:10:12 MYTHFE1 mythfrontend[1975]: I CoreContext mythrender_vdpau.cpp:401 (Create) VDPAU: Created VDPAU render device 1440x900
May 30 14:10:12 MYTHFE1 mythfrontend[1975]: N CoreContext mythplayer.cpp:506 (CheckExtraAudioDecode) Player(1): Forcing decode extra audio option on (Video method requires it).
May 30 14:10:12 MYTHFE1 mythfrontend[1975]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(1): Video timing method: USleep with busy wait
May 30 14:10:12 MYTHFE1 mythfrontend[1975]: I CoreContext tv_play.cpp:5167 (StartPlayer) TV: Created player.
May 30 14:10:12 MYTHFE1 mythfrontend[1975]: I CoreContext tv_play.cpp:2358 (HandleStateChange) TV: Changing from None to WatchingDVD
May 30 14:10:12 MYTHFE1 mythfrontend[1975]: I CoreContext tv_play.cpp:2449 (HandleStateChange) TV: Main UI disabled.
May 30 14:10:12 MYTHFE1 mythfrontend[1975]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
May 30 14:10:12 MYTHFE1 mythfrontend[1975]: I CoreContext mythrender_vdpau.cpp:587 (CheckOutputSurfaces) VDPAU: Added 2 output surfaces (total 4, max 4)
May 30 14:10:12 MYTHFE1 mythfrontend[1975]: N Decoder audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
May 30 14:10:44 MYTHFE1 mythfrontend[1975]: I Decoder avformatdecoder.cpp:1958 (ScanStreams) AFD: codec AC3 has 0 channels
May 30 14:10:44 MYTHFE1 mythfrontend[1975]: I Decoder avformatdecoder.cpp:2100 (ScanStreams) AFD: Opened codec 0x7f47fc0102c0, id(AC3) type(Audio)
May 30 14:10:44 MYTHFE1 mythfrontend[1975]: I Decoder audio/audiooutputbase.cpp:764 (Reconfigure) AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
May 30 14:10:51 MYTHFE1 mythfrontend[1975]: I Decoder avformatdecoder.cpp:2100 (ScanStreams) AFD: Opened codec 0x7f47fc0f7500, id(DVD_SUBTITLE) type(Subtitle)
May 30 14:10:51 MYTHFE1 mythfrontend[1975]: N Decoder audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
May 30 14:10:56 MYTHFE1 mythfrontend[1975]: I Decoder dvdringbuffer.cpp:983 (safe_read) DVDRB: DVDNAV_STOP
May 30 14:10:56 MYTHFE1 mythfrontend[1975]: E Decoder avformatdecoder.cpp:4374 (GetFrame) decoding error#012#011#011#011eno: Broken pipe (32)
May 30 14:10:57 MYTHFE1 mythfrontend[1975]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingDVD to None
May 30 14:10:57 MYTHFE1 mythfrontend[1975]: I CoreContext mythpainter_vdpau.cpp:111 (ClearCache) VDPAU Painter: Clearing VDPAU painter cache.
May 30 14:10:57 MYTHFE1 mythfrontend[1975]: I CoreContext tv_play.cpp:2358 (HandleStateChange) TV: Changing from WatchingDVD to None
May 30 14:10:57 MYTHFE1 mythfrontend[1975]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
May 30 14:10:57 MYTHFE1 mythfrontend[1975]: N CoreContext mythmainwindow.cpp:2583 (PauseIdleTimer) Suspending idle timer
May 30 14:11:03 MYTHFE1 mythfrontend[1975]: N CoreContext mythmainwindow.cpp:2588 (PauseIdleTimer) Resuming idle timer
May 30 14:11:03 MYTHFE1 mythfrontend[1975]: N CoreContext mythmainwindow.cpp:2588 (PauseIdleTimer) Resuming idle timer
May 30 14:11:03 MYTHFE1 mythfrontend[1975]: I CoreContext bonjourregister.cpp:26 (~BonjourRegister) Bonjour: De-registering service '' on ''
May 30 14:11:03 MYTHFE1 mythfrontend[1975]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
May 30 14:11:03 MYTHFE1 mythfrontend[1975]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
May 30 14:11:03 MYTHFE1 mythfrontend[1975]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
May 30 14:11:05 MYTHFE1 mythfrontend[1975]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.


```

---

### Post by klc5555 on 2012-05-30
For the actual disc, I see > libdvdread: Encrypted DVD support unavailable.

Do you have libdvdcss2 installed? It generally has to be installed separately, from the medibuntu repository. [http://packages.medibuntu.org/precise/libdvdcss2.html](http://packages.medibuntu.org/precise/libdvdcss2.html)

The new Paramount DVD you were trying to play (Captain America) requires this current version of libdvdcss2 (1.2.12) along with the current libdvdread/libdvdnav (4.2.0 --which 12.04 provides) to play properly. Paramount discs issued since last summer break the earlier libdvdread 4.13 /libdvdcss2 1.2.11 combo.

---

### Post by jlp_engineer on 2012-05-30
> **klc5555 said:**
> For the actual disc, I see 

Do you have libdvdcss2 installed? It generally has to be installed separately, from the medibuntu repository. [http://packages.medibuntu.org/precise/libdvdcss2.html](http://packages.medibuntu.org/precise/libdvdcss2.html)

The new Paramount DVD you were trying to play (Captain America) requires this current version of libdvdcss2 (1.2.12) along with the current libdvdread/libdvdnav (4.2.0 --which 12.04 provides) to play properly. Paramount discs issued since last summer break the earlier libdvdread 4.13 /libdvdcss2 1.2.11 combo.

Yes, both libdvdread (version 4.2.0) and libdvdcss2 (version 1.2.12-0.0) are installed.  At least that is what both Ubutnu Software Center and Synaptic tell me.  

Should I remove and re-install them?  The files must be from a stock 12.04 install, since I did not install them separately.  Is that possible?  I did select the option to install third party software during the installation process.

As for the Captain America ISO, I have tried other (older) ISO's as well...same issue.

---

### Post by klc5555 on 2012-05-30
With regard to playing the actual Captain America disc, your log shows your playback blowing up with > May 30 14:10:56 MYTHFE1 mythfrontend[1975]: I Decoder dvdringbuffer.cpp:983 (safe_read) DVDRB: DVDNAV_STOP
May 30 14:10:56 MYTHFE1 mythfrontend[1975]: E Decoder avformatdecoder.cpp:4374 (GetFrame) decoding error#012#011#011#011eno: Broken pipe (32) but I don't know what is going on at this precise point. It could be that the internal player, though better than it used to be, can't handle these problematical newer Paramount discs.

With regard to iso playback (encrypted or unencrypted), this has a fairly spotty track record from within storage groups, so follow-ups include:

Do your older iso's (not Captain America) play in myth from a non-storage-group directory, or can they be played in myth from an NFS mounted volume? Can non-iso rips be played from within the storage groups? (--that is, things either transcoded to avi, mkv, mpg or whatever, or things "perfect ripped" to vob files with vobcopy or similar utility) If your problem turns out to point not to playback in general, but specifically to iso's and storage groups in combination, then this will have to be dealt with.

---

### Post by jlp_engineer on 2012-05-30
OK, how do I get the internal player to pick up files that are NOT stored in the video storage group???  I can see that the setup for the frontend has media settings for videos, and that you can put paths in there, but does the creation of a video storage group override the paths there, and if so, does the deletion of the video storage group allow the paths in the video section of media settings to assert themselves???

Thanks.

---

### Post by klc5555 on 2012-05-31
c.f. here: [http://www.mythtv.org/wiki/Video_Library#Setting_Up_Video.2FImage_Storage_Groups](http://www.mythtv.org/wiki/Video_Library#Setting_Up_Video.2FImage_Storage_Groups)

In particular: > Optional Step: If you would like to use a combination of Storage Group and locally hosted video, you can do the following. On the frontends, go to Utilities/Setup->Setup->Media Settings->Video Settings->General. Change "Directories that hold videos" to point at a directory that is not the same as the one the Storage Group points at. If the local video setting and the Storage Group setting point at the same path, the video library will prefer the Storage Group path and ignore the local one. 

This should give you a point from which to test whether the problem is playback in general, playback of iso's in general or of a particular type, an issue with your video storage group in general, or an issue with iso's and your video storage group in combination.

---

### Post by jlp_engineer on 2012-06-01
Some progress....  :)

I had neglected to apply the latest updates to MythTV, and once I did, DVD's and even ISO's started working just fine.  I can see why some don't use the internal player, since some of them menus stutter and pause (like Iron Man 2), but for the most part it seems to be working.  My ISO's are stored on local directories, so now the test will be to throw them all back on the Master BE, in a storage group, and see if everything still works.  [-o<

Will report back later...

---

### Post by klc5555 on 2012-06-01
Looks like you might have got it! :)

I confess I've never been overly fond of the whole iso business. Never wanted anything from my DVDs other than the actual shows or movies. So the stored media files on my machines from my discs have always been so-called "perfect rips" to vob files with the old myth ripper or vobcopy where possible, or rips to mpg, mkv, or avi when the various vob copying tools couldn't handle the disc. 

But everyone has their own preferences :)

---

