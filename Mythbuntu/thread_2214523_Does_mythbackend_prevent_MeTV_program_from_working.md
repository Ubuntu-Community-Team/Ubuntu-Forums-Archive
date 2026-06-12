---
title: "Does mythbackend prevent MeTV program from working?"
date: 2014-04-01
forum: Mythbuntu
---

### Post by sdowney717 on 2014-04-01
MeTV when I start it gives me a warning failed to get frontend.

I think the backend is hogging my tuner card?

---

### Post by aelfric55 on 2014-04-01
> **sdowney717 said:**
> MeTV when I start it gives me a warning failed to get frontend.

I think the backend is hogging my tuner card?

In the backend setup is the DVB tuner card set up with the option "open DVB tuner on demand"? If this is left unchecked, mythbackend doesn't free the tuner for other programs.

---

### Post by sdowney717 on 2014-04-02
I went back and looked and do not see it.
Where exactly is that in the backend?

You can get backend to run smaller by setting the size, so now I can take screen shots.

---

### Post by sdowney717 on 2014-04-02
I found it under recording options on that page.

I have some kind of new error as you can see on the picture.
MeTv also shows same error and cant watch TV

MythTV shows that error in backend setup, but CAN watch TV.

Any ideas? Reboot?

---

### Post by aelfric55 on 2014-04-02
If you suspect mythbackend is hogging the tuner card so that me-tv doesn't work, kill the mythbackend process from a terminal. If the me-tv viewer still can't access the card with mythbackend killed, then the issue is either with the me-tv program itself, or the driver load for the tuner card. Perhaps even something as simple-minded as me-tv running from your main user account with the wrong permissions to access or tune the card. 

Otherwise, check dmesg output for issues occurring when the driver loads at boot, as well as checking the mythbackend log (or enabling logging in mythbackend if it happens to be disabled) to find out what mythbackend thinks is happenning when it starts up, or when it tunes a channel. I don't use Me-TV, but it does not appear to be to have logging or debugging of its own.

You do not need to fuss around with sizing to deal with a combination both of full-screen mythtv-setup, mythfrontend, and other windowed applications. You can run mythbackend (sudo) from a desktop termininal, fullscreen mythtv-setup and/or mythfrontend also from desktop terminals, and then cheerily jump from app to app or desktop as necessary with alt-tab (in XFCE) or ctrl-esc (in KDE) or whatever the shortcut is in whatever environment you use.

---

### Post by sdowney717 on 2014-04-02
I am running Trusty - beta

Myth is till working, I can watch TV

But I notice now this error in myth backend
Also the error in Me-TV has changed to  'There are no DVB devices available'

So now something is affecting both mythtv and metv 

```
scott@scott-P5QC:~$ mythbackend
2014-04-02 08:30:47.448891 C  mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
2014-04-02 08:30:47.448909 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2014-04-02 08:30:47.448912 N  Enabled verbose msgs:  general
2014-04-02 08:30:47.448921 N  Setting Log Level to LOG_INFO
2014-04-02 08:30:47.459567 I  Added logging to the console
2014-04-02 08:30:47.460200 I  Setup Interrupt handler
2014-04-02 08:30:47.460215 I  Setup Terminated handler
2014-04-02 08:30:47.460228 I  Setup Segmentation fault handler
2014-04-02 08:30:47.460241 I  Setup Aborted handler
2014-04-02 08:30:47.460253 I  Setup Bus error handler
2014-04-02 08:30:47.460266 I  Setup Floating point exception handler
2014-04-02 08:30:47.460279 I  Setup Illegal instruction handler
2014-04-02 08:30:47.460294 I  Setup Real-time signal 0 handler
2014-04-02 08:30:47.460338 N  Using runtime prefix = /usr
2014-04-02 08:30:47.460354 N  Using configuration directory = /home/scott/.mythtv
2014-04-02 08:30:47.460432 I  Assumed character encoding: en_US.UTF-8
2014-04-02 08:30:47.460860 N  Empty LocalHostName.
2014-04-02 08:30:47.460872 I  Using localhost value of scott-P5QC
2014-04-02 08:30:47.501667 N  Setting QT default locale to EN_US
2014-04-02 08:30:47.501724 I  Current locale EN_US
2014-04-02 08:30:47.501769 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2014-04-02 08:30:47.506550 I  Current MythTV Schema Version (DBSchemaVer): 1317
2014-04-02 08:30:47.506855 I  Loading en_us translation for module mythfrontend
2014-04-02 08:30:47.507208 N  MythBackend: Starting up as the master server.
2014-04-02 08:30:47.509038 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:47.559135 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:47.561722 I  New Client:  (#1)
2014-04-02 08:30:47.609300 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:47.659442 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:47.709602 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:47.759702 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:47.809853 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:47.859994 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:47.910150 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:47.960275 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.010433 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.060565 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.110722 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.160822 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.210973 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.261113 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.311268 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.361376 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.411526 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.461657 W  DVBChan[1](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.461671 E  DVBChan[1](/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2014-04-02 08:30:48.461691 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2014-04-02 08:30:48.461773 E  Problem with capture cardsCard 1failed init
2014-04-02 08:30:48.462687 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.512844 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.562944 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.613099 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.663201 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.713350 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.763447 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.813600 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.863750 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.913908 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:48.964036 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:49.014190 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:49.064316 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:49.114473 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:49.164574 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:49.214731 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:49.264847 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:49.315004 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:49.365115 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:49.415268 W  DVBChan[2](/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
			eno: Device or resource busy (16)
2014-04-02 08:30:49.415284 E  DVBChan[2](/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2014-04-02 08:30:49.415294 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2014-04-02 08:30:49.415332 E  Problem with capture cardsCard 2failed init
2014-04-02 08:30:49.415355 W  MythBackend: No valid capture cards are defined in the database.
2014-04-02 08:30:49.416236 W  Scheduler: Listings source '' is defined, but is not attached to a card input.
2014-04-02 08:30:49.417728 I  Found 0 distinct programid authorities
2014-04-02 08:30:49.418035 I  Registering HouseKeeperTask 'LogClean'.
2014-04-02 08:30:49.418148 I  Registering HouseKeeperTask 'DBCleanup'.
2014-04-02 08:30:49.418176 I  Registering HouseKeeperTask 'ThemeUpdateNotifications'.
2014-04-02 08:30:49.418209 I  Registering HouseKeeperTask 'RecordedArtworkUpdate'.
2014-04-02 08:30:49.418414 I  New static DB connectionSchedCon
2014-04-02 08:30:49.420880 I  Registering HouseKeeperTask 'MythFillDB'.
2014-04-02 08:30:49.420913 I  Registering HouseKeeperTask 'JobQueueRecover'.
2014-04-02 08:30:49.420931 I  Registering HouseKeeperTask 'HardwareProfiler'.
2014-04-02 08:30:49.422936 I  Starting HouseKeeper.
2014-04-02 08:30:49.428087 E  Failed listening on TCP 127.0.0.1:6544 - Error 8: The bound address is already in use
2014-04-02 08:30:49.428126 E  MediaServer::HttpServer Create Error
2014-04-02 08:30:49.430812 E  Failed listening on TCP 127.0.0.1:6543 - Error 8: The bound address is already in use
2014-04-02 08:30:49.430836 C  Backend exiting, MainServer initialization error.
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2014-04-02
mythfrontend can watch TV even with that mythbackend error?


```
scott@scott-P5QC:~$ mythfrontend -w --geometry 1024x768
2014-04-02 08:39:00.059438 I  Setup Interrupt handler
2014-04-02 08:39:00.059463 I  Setup Terminated handler
2014-04-02 08:39:00.059470 I  Setup Segmentation fault handler
2014-04-02 08:39:00.059477 I  Setup Aborted handler
2014-04-02 08:39:00.059483 I  Setup Bus error handler
2014-04-02 08:39:00.059491 I  Setup Floating point exception handler
2014-04-02 08:39:00.059498 I  Setup Illegal instruction handler
2014-04-02 08:39:00.059506 I  Setup Real-time signal 0 handler
2014-04-02 08:39:00.059515 I  Setup User defined signal 1 handler
2014-04-02 08:39:00.059521 I  Setup User defined signal 2 handler
2014-04-02 08:39:00.059620 C  mythfrontend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
2014-04-02 08:39:00.059625 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2014-04-02 08:39:00.059628 N  Enabled verbose msgs:  general
2014-04-02 08:39:00.059638 N  Setting Log Level to LOG_INFO
2014-04-02 08:39:00.070324 I  Added logging to the console
2014-04-02 08:39:00.070445 I  MythUIHelper: Overriding GUI size: width=1024 height=768
2014-04-02 08:39:00.070496 N  Using runtime prefix = /usr
2014-04-02 08:39:00.070509 N  Using configuration directory = /home/scott/.mythtv
2014-04-02 08:39:00.070587 I  Assumed character encoding: en_US.UTF-8
2014-04-02 08:39:00.071121 N  Empty LocalHostName.
2014-04-02 08:39:00.071132 I  Using localhost value of scott-P5QC
2014-04-02 08:39:00.082249 N  Setting QT default locale to EN_US
2014-04-02 08:39:00.082321 I  Current locale EN_US
2014-04-02 08:39:00.082418 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2014-04-02 08:39:00.084894 I  Starting process manager
2014-04-02 08:39:00.087333 I  Starting process signal handler
2014-04-02 08:39:00.087422 I  Starting IO manager (write)
2014-04-02 08:39:00.087507 I  Starting IO manager (read)
2014-04-02 08:39:00.171540 I  New Client:  (#1)
2014-04-02 08:39:00.171578 I  Added syslogging
2014-04-02 08:39:00.188913 I  ScreenSaverX11Private: DPMS is active.
2014-04-02 08:39:00.202391 N  Desktop video mode: 1680x1050 59.883 Hz
2014-04-02 08:39:00.385333 N  Setting 'RunFrontendInWindow' being forced to '1'
2014-04-02 08:39:00.387985 I  Listening on TCP 127.0.0.1:6547
2014-04-02 08:39:00.388049 I  Listening on TCP [::1]:6547
2014-04-02 08:39:00.388136 I  Listening on TCP [fe80::222:15ff:fe54:faa6%eth1]:6547
Got bus address:  "unix:abstract=/tmp/dbus-AxBkNHUlkj,guid=dd0e4e814444ecf64ef4ca3f533bf45c" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-AxBkNHUlkj,guid=dd0e4e814444ecf64ef4ca3f533bf45c" 
Registered DEC:  true 
2014-04-02 08:39:01.089494 I  Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
2014-04-02 08:39:01.090160 I  Loading en_us translation for module mythfrontend
2014-04-02 08:39:01.090543 W  MythUIHelper: No theme dir: '/usr/share/mythtv/themes/Mythbuntu'
2014-04-02 08:39:01.090563 E  MythUIHelper: Could not find theme: Mythbuntu - Switching to Terra
2014-04-02 08:39:01.097104 E  LIRC: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2014-04-02 08:39:01.097162 E  JoystickMenuThread: Joystick disabled - Failed to read /home/scott/.mythtv/joystickmenurc
2014-04-02 08:39:01.097175 I  UDPListener: Enabling
2014-04-02 08:39:01.097741 I  Binding to UDP 127.0.0.1:6948
2014-04-02 08:39:01.097844 I  Binding to UDP [::1]:6948
2014-04-02 08:39:01.097944 I  Binding to UDP [fe80::222:15ff:fe54:faa6%eth1]:6948
2014-04-02 08:39:01.134847 I  Using the Qt painter
2014-04-02 08:39:01.288742 I  MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2014-04-02 08:39:01.289740 I  Using protocol version 77
2014-04-02 08:39:01.508329 I  MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
2014-04-02 08:39:01.508807 E  MythUIWebBrowser: failed to find our parent screen
2014-04-02 08:39:01.509800 I  MythUIWebBrowser: enabling plugins
2014-04-02 08:39:01.539840 E  RAOP Device: Aborting startup - no key found.
2014-04-02 08:39:01.540206 I  AirPlay: Created airplay objects.
2014-04-02 08:39:01.541438 I  Current MythTV Schema Version (DBSchemaVer): 1317
2014-04-02 08:39:01.543109 I  Listening on TCP 127.0.0.1:5100
2014-04-02 08:39:01.543184 I  Listening on TCP [::1]:5100
2014-04-02 08:39:01.543250 I  Listening on TCP [fe80::222:15ff:fe54:faa6%eth1]:5100
2014-04-02 08:39:01.565046 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2014-04-02 08:39:01.565057 E  ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2014-04-02 08:39:01.565497 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2014-04-02 08:39:01.565503 E  ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2014-04-02 08:39:01.645678 N  Registering Internal as a media playback plugin.
2014-04-02 08:39:01.666645 W  No plugins directory /usr/lib/mythtv/plugins
Registered event listener change listener:  true 
2014-04-02 08:39:01.744041 N  Found mainmenu.xml for theme 'Terra'
2014-04-02 08:39:01.746333 I  Registering HouseKeeperTask 'HardwareProfiler'.
2014-04-02 08:39:01.746950 I  Starting HouseKeeper.
2014-04-02 08:39:01.968037 I  Bonjour: Service registration complete: name 'Mythfrontend on scott-P5QC' type '_mythfrontend._tcp.' domain: 'local.'
2014-04-02 08:39:02.519761 I  Bonjour: Service registration complete: name 'MythTV on scott-P5QC' type '_airplay._tcp.' domain: 'local.'
2014-04-02 08:39:04.254780 I  TV: Creating TV object
2014-04-02 08:39:04.263317 N  Suspending idle timer
2014-04-02 08:39:04.267742 I  TV: Created TvPlayWindow.
2014-04-02 08:39:04.288874 I  TV: Attempting to change from None to WatchingLiveTV
2014-04-02 08:39:04.289711 I  MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
2014-04-02 08:39:04.296056 N  TV: Spawning LiveTV Recorder -- begin
2014-04-02 08:39:04.373795 N  TV: Spawning LiveTV Recorder -- end
2014-04-02 08:39:04.375988 I  TV: playbackURL(/var/lib/mythtv/recordings/2101_20140402123904.mpg) cardtype(DUMMY)
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2014-04-02 08:39:04.420772 E  ALSA: snd_pcm_info_get_card: Operation not permitted
2014-04-02 08:39:04.439209 N  AudioPlayer: Enabling Audio
2014-04-02 08:39:04.453484 I  Setup Interrupt handler
2014-04-02 08:39:04.453493 I  Setup Terminated handler
2014-04-02 08:39:04.453576 I  VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2014-04-02 08:39:04.470328 I  OSD: Base theme size: 1280x720
2014-04-02 08:39:04.470349 I  OSD: Scaling factors: 0.5625x0.8
2014-04-02 08:39:04.513239 I  OSD: Base theme size: 1280x720
2014-04-02 08:39:04.513251 I  OSD: Scaling factors: 0.5625x0.8
2014-04-02 08:39:04.518018 I  Player(0): Video timing method: USleep with busy wait
2014-04-02 08:39:04.518626 I  TV: Created player.
2014-04-02 08:39:04.518658 I  TV: Changing from None to WatchingLiveTV
2014-04-02 08:39:04.518665 I  TV: State is LiveTV & mctx == ctx
2014-04-02 08:39:04.519373 I  TV: UpdateOSDInput done
2014-04-02 08:39:04.519381 I  TV: UpdateLCD done
2014-04-02 08:39:04.519499 I  TV: ITVRestart done
2014-04-02 08:39:04.523002 I  TV: Main UI disabled.
2014-04-02 08:39:04.523031 I  TV: Entering main playback loop.
2014-04-02 08:39:04.530577 I  ScreenSaverX11Private: DPMS Deactivated 1
2014-04-02 08:39:04.584647 I  VideoOutput: Created YV12 OSD.
2014-04-02 08:39:04.901861 E  Failed to mount /dev/sr0.
2014-04-02 08:39:06.283489 I  AFD: codec AC3 has 6 channels
2014-04-02 08:39:06.283741 I  AFD: Opened codec 0x360b8c0, id(AC3) type(Audio)
2014-04-02 08:39:06.283930 I  AFD: codec AC3 has 1 channels
2014-04-02 08:39:06.284124 I  AFD: Opened codec 0x3764340, id(AC3) type(Audio)
2014-04-02 08:39:06.287277 I  Setup Interrupt handler
2014-04-02 08:39:06.287290 I  Setup Terminated handler
2014-04-02 08:39:06.291581 I  Setup Interrupt handler
2014-04-02 08:39:06.291593 I  Setup Terminated handler
2014-04-02 08:39:06.291692 I  VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2014-04-02 08:39:06.368401 I  OSD: Base theme size: 1280x720
2014-04-02 08:39:06.368415 I  OSD: Scaling factors: 1.12422x1.5
2014-04-02 08:39:06.410766 I  AFD: Opened codec 0x35de0a0, id(MPEG2VIDEO) type(Video)
2014-04-02 08:39:06.410905 I  AOBase: Opening audio device 'default' ch 2(6) sr 48000 sf 32 bit floating point reenc 0
2014-04-02 08:39:06.426396 E  ALSA: no playback control PCM found on mixer device default
2014-04-02 08:39:06.426406 E  ALSA: Unable to open audio mixer. Volume control disabled
2014-04-02 08:39:06.573859 I  VideoOutput: Created YV12 OSD.
2014-04-02 08:39:07.082014 N  Player(0): Waited 102ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUUuLP
2014-04-02 08:39:07.331176 N  Player(0): Waited 104ms for video buffers UUuUULuAAAAAAAAAAAAAAAAAAAUUUUUP
2014-04-02 08:39:07.856878 N  Player(0): Waited 104ms for video buffers AAAAAAAAAAAUUUUUUuUULUuAAAAAAAAP


```

---

### Post by sdowney717 on 2014-04-02
> **aelfric55 said:**
> If you suspect mythbackend is hogging the tuner card so that me-tv doesn't work, kill the mythbackend process from a terminal. If the me-tv viewer still can't access the card with mythbackend killed, then the issue is either with the me-tv program itself, or the driver load for the tuner card. **Perhaps even something as simple-minded as me-tv running from your main user account with the wrong permissions to access or tune the card. **

Otherwise, check dmesg output for issues occurring when the driver loads at boot, as well as checking the mythbackend log (or enabling logging in mythbackend if it happens to be disabled) to find out what mythbackend thinks is happenning when it starts up, or when it tunes a channel. I don't use Me-TV, but it does not appear to be to have logging or debugging of its own.

You do not need to fuss around with sizing to deal with a combination both of full-screen mythtv-setup, mythfrontend, and other windowed applications. You can run mythbackend (sudo) from a desktop termininal, fullscreen mythtv-setup and/or mythfrontend also from desktop terminals, and then cheerily jump from app to app or desktop as necessary with alt-tab (in XFCE) or ctrl-esc (in KDE) or whatever the shortcut is in whatever environment you use.

yes, something has happened to permissions on the tuner!
If I run 'sudo me-tv', it works fine.
Not sure I did anything to permissions, all I did was configure mythtv.
I found this as a clue in launchpad bugs, mentions

> And now I figured it out properly.

The DVB adapters were in accessible by a special "video" group only. The MythTV daemon account was a member of this group.

My interactive a/c that I was using to test MeTV wasn't.

Either the MythTV setup did this itself, or I did it some ages ago and forgot about it.

When I added the interactive a/c to the right group it works without sudo.

My bug. Close as invalid.

[https://bugs.launchpad.net/me-tv/+bug/619530](https://bugs.launchpad.net/me-tv/+bug/619530)

Does mythtv do something  affecting groups, permissions?
So what do i assign to what group to let me-tv work again without needing sudo?

---

### Post by aelfric55 on 2014-04-02
Note that mythbackend runs with root permissions to access hardware ; if you start it from your user's regular terminal, it's done sudo  after the already-running mythbackend (or in Ubuntu mythbackend.real) has been stopped This is the error problem in your first mythbackend screen dump, where it looks like mythbackend was run as your regular user.

Since me-tv works when run sudo, that's its problem too --insufficient normal user account permissions. If such a "video" group exists on your machine, as mentioned by the poster on your launchpad excerpt, then this group must have root access to hardware if this is how mythbackend is running. If you intend to run me-tv always from your main user account and me-tv needs to access video hardware, then logically your main user's account will need to be added to the video group. 

If, however, mythbackend (or mythbackend.real) is simply running as root, without a "video" group to belong to, then you'll likely want to create such a group yourself, using the user/group tools provided by your desktop (generally easier than editing files in /etc). This "video" group will need to be given appropriate hardware access to be able to tune the card, and then your main user will need to be added to that group. Logout, log back in, and the main user (and therefore me-tv) should be able to access the tuner card.

---

### Post by tgm4883 on 2014-04-02
> **aelfric55 said:**
> If you suspect mythbackend is hogging the tuner card so that me-tv doesn't work, kill the mythbackend process from a terminal. 


No, don't do that. It's much better to stop the mythbackend process properly (eg. 'sudo service mythtv-backend stop'). If you kill the process, it should attempt to restart automatically.

---

### Post by sdowney717 on 2014-04-02
My problem is not the myth backend.

Somehow my tuner now needs sudo for Me-TV to run.

What group does metv need to be in, or does the tuner need to be added to a group?

I suppose I can uninstall mythtv and see if it starts working again. My guess is that it wont.

I notice in myth backend setup, for tuners, several options, like, removing all tuners, removing myth tuners. Would doing one of those help?

---

### Post by aelfric55 on 2014-04-02
To recap what I posted earlier:

By default, hardware is accessible in linux only by root.

In your installation, mythbackend accesses the tuner card with root permissions. When you tried running it from a terminal as your normal user, it could not access the DVB card because you were not running it sudo.

Me-TV cannot access the tuner card, because it is running as your regular user without root access to hardware. When you run it sudo, it works. Your choices are therefore to continue to run me-tv sudo, or to give your user account the necessary root access to the tuner card by adding your user account to the "Video" group (if you have one), which "video" group has already been granted permissions to access the hardware. If your installation lacks a "video" group (or similar) with appropriate permissions, then you should create such a group yourself (preferably using the graphical user/group tools provided by your environment), and add your main user account to this newly-created user group.

There is no shortage of manuals on users and groups on the web, for every flavor of linux and every conceivable desktop environment. A couple of minutes searching should give you dozens to choose from. I tend to be fond of this one from Arch: [https://wiki.archlinux.org/index.php/users_and_groups](https://wiki.archlinux.org/index.php/users_and_groups)

---

### Post by sdowney717 on 2014-04-02
```
scott@scott-P5QC:~$ sudo -s
[sudo] password for scott: 

root@scott-P5QC:~# useradd -G video scott
useradd: user 'scott' already exists

root@scott-P5QC:~# id scott
uid=1000(scott) gid=1000(scott) groups=1000(scott),4(adm),24(cdrom),27(sudo),30(dip),44(video),46(plugdev),112(lpadmin),124(sambashare),130(mythtv)

root@scott-P5QC:~# groups scott
scott : scott adm cdrom sudo dip video plugdev lpadmin sambashare mythtv

root@scott-P5QC:~# ^C
root@scott-P5QC:~# 

```

I think this says I am part of the video group now
Then I did this
```
scott@scott-P5QC:~$ sudo service mythtv-backend stop
[sudo] password for scott: 
mythtv-backend stop/waiting
scott@scott-P5QC:~$ me-tv
Me TV 1.3.7
scott@scott-P5QC:~$ 

```

and me-tv still says no tuners

What am I doing wrong?

---

### Post by sdowney717 on 2014-04-02
here it is working as sudo.
Is there some other group it needs more than video?

running as sudo means recordings will be owned by root which is bad.

---

### Post by sdowney717 on 2014-04-02
Well I have destroyed my system.
I tried adding myself to the group audio since mythtv belongs and I dont.
so I ran

usermod -G audio scott

then to show groups I belong to 

```
root@scott-P5QC:~# groups scott
scott : scott audio
root@scott-P5QC:~#
```

So I lost the groups I had before

 adm cdrom sudo dip video plugdev lpadmin sambashare mythtv 

I tried then to go to user graphical and since I am no longer belonging to admin, I cant make any changes at all.
I better not log out till it is fixed or I will likely be totally locked out.
When it rains it pours.

---

### Post by sdowney717 on 2014-04-02
root@scott-P5QC:~# usermod -G adm, cdrom, sudo, dip, video, plugdev, lpadmin, sambashare, mythtv scott 
usermod: group '' does not exist
root@scott-P5QC:~# 


root@scott-P5QC:~# useradd -G adm, cdrom, sudo, dip, video, plugdev, lpadmin, sambashare, mythtv scott 
useradd: group '' does not exist
root@scott-P5QC:~# 

that does not work, but that is what that website says will work, use commas
[http://www.cyberciti.biz/faq/ubuntu-add-user-to-group/](http://www.cyberciti.biz/faq/ubuntu-add-user-to-group/)

---

### Post by sdowney717 on 2014-04-02
ok, I got it back using a different command!

```
root@scott-P5QC:~# useradd -G adm, cdrom, sudo, dip, video, plugdev, lpadmin, sambashare, mythtv scott 
useradd: group '' does not exist
root@scott-P5QC:~# useradd -G adm, cdrom, sudo scott useradd: group '' does not exist
root@scott-P5QC:~# useradd -G adm scott 
useradd: user 'scott' already exists
root@scott-P5QC:~# usermod -G adm, cdrom, sudo, dip, video, plugdev, lpadmin, sambashare, mythtv scott 
usermod: group '' does not exist
root@scott-P5QC:~# useradd -G adm, cdrom, sudo, dip, video, plugdev, lpadmin, sambashare, mythtv scott 
useradd: group '' does not exist
root@scott-P5QC:~# sudo addgroup scott sudo
Adding user `scott' to group `sudo' ...
Adding user scott to group sudo
Done.
root@scott-P5QC:~# groups scott
scott : scott sudo audio
root@scott-P5QC:~# sudo addgroup scott cdrom
Adding user `scott' to group `cdrom' ...
Adding user scott to group cdrom
Done.
root@scott-P5QC:~# sudo addgroup scott adm
Adding user `scott' to group `adm' ...
Adding user scott to group adm
Done.
root@scott-P5QC:~# sudo addgroup scott dip
Adding user `scott' to group `dip' ...
Adding user scott to group dip
Done.
root@scott-P5QC:~# sudo addgroup scott video
Adding user `scott' to group `video' ...
Adding user scott to group video
Done.
root@scott-P5QC:~# sudo addgroup scott plugdev
Adding user `scott' to group `plugdev' ...
Adding user scott to group plugdev
Done.
root@scott-P5QC:~# sudo addgroup scott lpadmin
Adding user `scott' to group `lpadmin' ...
Adding user scott to group lpadmin
Done.
root@scott-P5QC:~# sudo addgroup scott sambashare
Adding user `scott' to group `sambashare' ...
Adding user scott to group sambashare
Done.
root@scott-P5QC:~# sudo addgroup scott mythtv
Adding user `scott' to group `mythtv' ...
Adding user scott to group mythtv
Done.
root@scott-P5QC:~# groups scott
scott : scott adm cdrom sudo audio dip video plugdev lpadmin sambashare mythtv
root@scott-P5QC:~# 

```

---

### Post by sdowney717 on 2014-04-02
adding myself to the audio group still will not let me-tv run, do I need to be a part of dialout?

```
scott@scott-P5QC:~$ sudo -s
[sudo] password for scott: 

root@scott-P5QC:~# groups mythtv
mythtv : mythtv dialout cdrom audio video

root@scott-P5QC:~# groups scott
scott : scott adm cdrom sudo audio dip video plugdev lpadmin sambashare mythtv
root@scott-P5QC:~# 

```

---

### Post by sdowney717 on 2014-04-02
OK, after you make changes, you have to log out and in again.

It now runs me-tv as me the user.:D

BUT, I have lost my desktop, all it shows is a black screen, I am running gnome..
Pitch Black!

Next I will reboot.

Edit adding that a reboot restored the desktop view.

---

### Post by aelfric55 on 2014-04-02
Well done! Looks like you got it licked.

---

### Post by sdowney717 on 2014-04-02
> **aelfric55 said:**
> Well done! Looks like you got it licked.

yes, thanks for pointing me to the permissions as the problem.:D

---

