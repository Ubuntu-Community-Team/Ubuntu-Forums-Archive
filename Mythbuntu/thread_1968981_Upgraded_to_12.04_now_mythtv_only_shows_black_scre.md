---
title: "Upgraded to 12.04 now mythtv only shows black screen"
date: 2012-04-29
forum: Mythbuntu
---

### Post by lanewaves on 2012-04-29
I was on 11.10 with .25+ fixes and things were mostly fine. I could watch all programming.

I upgraded to 12.04 and now upon boot I see that mythfrontend starts to run (shows blue screen briefly) but then the entire screen is painted black and unresponsive. 

Any thoughts?  I can kill mythfrontend remotely but the auto crash feature restarts mythfrontend and the same thing happens...the entire screen is painted black.

All schedules continue to function; I can stream old and new recordings via Mythweb and my frontend in the basement works fine also (after upgrading to 12.04). If I'm quick at boot time, I can click on the Applications menu drop down and get an app (terminal, update manager, etc) to appear on top of mythfrontend. I can even load Firefox and watch movies on amazon.com.

[IMG]http://www.lanewaves.com/wp-content/uploads/2012/04/frontendblack.jpg[/IMG]

Thanks.

---

### Post by whosmatt on 2012-04-29
Same problem; started my thread here:  [http://ubuntuforums.org/showthread.php?p=11889311#post11889311](http://ubuntuforums.org/showthread.php?p=11889311#post11889311)

I'll monitor this one as well.

---

### Post by tgm4883 on 2012-04-29
if you kill the frontend (killall mythfrontend) then run the frontend from a terminal (mythfrontend) does it show any indication as to what is wrong in the terminal messages?

---

### Post by lanewaves on 2012-04-29
I'm unable to actually kill mythfrontend for any length of time as the autocrash keeps restarting it. Is there a service that I can kill to prevent that?

Thanks.

---

### Post by lanewaves on 2012-04-29
Sorry, missed your killall comment, that worked.

Here is my output:

matt@MythBunt1:~$ mythfrontend
2012-04-29 22:14:48.348054 C  mythfrontend version: fixes/0.25 [v0.25-59-gae7ac79] [www.mythtv.org](www.mythtv.org)
2012-04-29 22:14:48.348101 N  Enabled verbose msgs:  general
2012-04-29 22:14:48.348156 N  Setting Log Level to LOG_INFO
2012-04-29 22:14:48.348282 I  Added logging to the console
2012-04-29 22:14:48.348336 I  Added syslogging to facility local7
2012-04-29 22:14:48.348353 I  Added database logging to table logging
2012-04-29 22:14:48.348555 N  Setting up SIGHUP handler
2012-04-29 22:14:48.348920 N  Using runtime prefix = /usr
2012-04-29 22:14:48.348977 N  Using configuration directory = /home/matt/.mythtv
2012-04-29 22:14:48.349384 I  Assumed character encoding: en_US.UTF-8
2012-04-29 22:14:48.368766 N  Empty LocalHostName.
2012-04-29 22:14:48.368803 I  Using localhost value of MythBunt1
2012-04-29 22:14:48.450015 N  Setting QT default locale to en_US
2012-04-29 22:14:48.450189 I  Current locale en_US
2012-04-29 22:14:48.450308 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2012-04-29 22:14:48.501895 I  Starting IO manager (write)
2012-04-29 22:14:48.502280 I  Starting IO manager (read)
2012-04-29 22:14:48.502982 I  Starting process signal handler
2012-04-29 22:14:48.506605 I  Starting process manager
2012-04-29 22:14:48.653534 I  ScreenSaverX11Private: XScreenSaver support enabled
2012-04-29 22:14:48.664000 I  ScreenSaverX11Private: DPMS is disabled.
2012-04-29 22:14:48.838984 N  Desktop video mode: 1024x768 75.029 Hz
2012-04-29 22:14:49.194846 I  Listening on TCP 127.0.0.1:6547
2012-04-29 22:14:49.204624 I  Listening on TCP 10.0.5.7:6547
2012-04-29 22:14:49.204852 I  Listening on TCP [::1]:6547
2012-04-29 22:14:50.205329 E  RAOP Conn: Failed to read key from: /home/matt/.mythtv/RAOPKey.rsa
2012-04-29 22:14:50.205354 E  RAOP Device: Aborting startup - no key found.
2012-04-29 22:14:50.245263 I  Loading en_us translation for module mythfrontend
2012-04-29 22:14:50.337299 I  LIRC: Successfully initialized '/dev/lircd' using '/home/matt/.mythtv/lircrc' config
2012-04-29 22:14:50.337520 E  JoystickMenuThread: Joystick disabled - Failed to read /home/matt/.mythtv/joystickmenurc
cannot find libcec.solibcec.so: cannot open shared object file: No such file or directory
2012-04-29 22:14:50.366515 E  CECAdapter: Failed to load libcec.
2012-04-29 22:14:50.384865 I  Binding to UDP 127.0.0.1:6948
2012-04-29 22:14:50.385076 I  Binding to UDP 10.0.5.7:6948
2012-04-29 22:14:50.385330 I  Binding to UDP [::1]:6948
2012-04-29 22:14:50.385558 I  Binding to UDP 10.0.5.255:6948
2012-04-29 22:14:50.479562 I  Using Frameless Window
2012-04-29 22:14:50.479701 I  Using Full Screen Window
2012-04-29 22:14:51.194767 I  Trying the OpenGL painter
2012-04-29 22:14:51.271785 W  NVCtrl: OpenGL Sync to VBlank is disabled.
2012-04-29 22:14:51.271809 W  NVCtrl: For best results enable this in NVidia settings or try running:
2012-04-29 22:14:51.271823 W  NVCtrl: nvidia-settings -a "SyncToVBlank=1"
2012-04-29 22:14:51.271868 W  NVCtrl: Alternatively try setting the '__GL_SYNC_TO_VBLANK' environment variable.
2012-04-29 22:14:51.485203 I  OpenGL1: Fragment program support available
2012-04-29 22:14:51.485353 I  OpenGL: OpenGL vendor  : NVIDIA Corporation
2012-04-29 22:14:51.485384 I  OpenGL: OpenGL renderer: GeForce 6200/PCI/SSE2
2012-04-29 22:14:51.485403 I  OpenGL: OpenGL version : 2.1.2 NVIDIA 295.40
2012-04-29 22:14:51.485433 I  OpenGL: Max texture size: 4096 x 4096
2012-04-29 22:14:51.485453 I  OpenGL: Max texture units: 4
2012-04-29 22:14:51.485506 I  OpenGL: Direct rendering: Yes
2012-04-29 22:14:51.485526 I  OpenGL: PixelBufferObject support available
2012-04-29 22:14:51.485543 I  OpenGL: Initialised MythRenderOpenGL
2012-04-29 22:14:52.279278 I  Current MythTV Schema Version (DBSchemaVer): 1299
2012-04-29 22:14:52.969471 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2012-04-29 22:14:52.969500 E  ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2012-04-29 22:14:52.993831 W  ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2012-04-29 22:14:52.993865 E  ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2012-04-29 22:14:53.491042 N  Registering Internal as a media playback plugin.
2012-04-29 22:14:53.727006 I  Loading en_us translation for module mytharchive
2012-04-29 22:14:53.739415 N  Registering WebBrowser as a media playback plugin.
2012-04-29 22:14:53.747768 I  Loading en_us translation for module mythbrowser
2012-04-29 22:14:53.835075 I  Loading en_us translation for module mythgallery
2012-04-29 22:14:53.880738 I  Loading en_us translation for module mythgame
2012-04-29 22:14:54.167842 I  Current MythMusic Schema Version (MusicDBSchemaVer): 1019
2012-04-29 22:14:54.214321 I  Loading en_us translation for module mythmusic
2012-04-29 22:14:54.233280 I  Loading en_us translation for module mythnetvision
2012-04-29 22:14:54.266968 I  Loading en_us translation for module mythnews
2012-04-29 22:14:54.297724 I  Loading en_us translation for module mythweather
2012-04-29 22:14:54.308267 I  Listening on TCP 127.0.0.1:6546
2012-04-29 22:14:54.308440 I  Listening on TCP 10.0.5.7:6546
2012-04-29 22:14:54.308616 I  Listening on TCP [::1]:6546
2012-04-29 22:14:54.560985 N  Found mainmenu.xml for theme 'MythCenter-wide'
2012-04-29 22:14:56.429169 I  MythCoreContext: Connecting to backend server: 10.0.5.7:6543 (try 1 of 1)
2012-04-29 22:14:56.431295 I  Using protocol version 72
2012-04-29 22:14:57.252765 I  Bonjour: Service registration complete: name 'Mythfrontend on MythBunt1' type '_mythfrontend._tcp.' domain: 'local.'
2012-04-29 22:15:09.714739 I  Using protocol version 72
2012-04-29 22:15:09.717401 I  Using protocol version 72


Thanks.

---

### Post by tgm4883 on 2012-04-29
So here is a couple things to try.

Start the frontend using the QT ThemePainter
```
mythfrontend -O ThemePainter=qt
```

Start the frontend using the OpenGL ThemePainter
```
mythfrontend -O ThemePainter=opengl
```

Start the frontend with the Mythbuntu theme
```
mythfrontend -O Theme=mythbuntu
```

:EDIT:

Should probably check if the Mythbuntu theme is installed for that last one to work
```
dpkg -l mythtv-theme-mythbuntu
```

---

### Post by whosmatt on 2012-04-29
I'm having the same problem; using themepainter=qt works for me.

Edit:  selecting QT as the theme painter from the Appearance setup works fine. "Auto" and "OpenGL" both paint a black screen, presumably because "Auto" is also choosing OpenGL.  Mine was previously set to OpenGL.

---

### Post by lanewaves on 2012-04-29
Only mythfrontend -O ThemePainter=qt works.  The other two resulted in the black screen after a second of blue.

---

### Post by nickrout on 2012-04-29
what video card do you have and is its driver installed properly?

---

### Post by lanewaves on 2012-04-30
My card is an older Nvidia...don't remember the exact model (6000 series I think) off the top of my head but I'll look when I'm home later.

To that end however, I don't have problems viewing the raw recordings via VLC on the same box.

---

### Post by nickrout on 2012-04-30
> **lanewaves said:**
> My card is an older Nvidia...don't remember the exact model (6000 series I think) off the top of my head but I'll look when I'm home later.

To that end however, I don't have problems viewing the raw recordings via VLC on the same box.

I thought we were talking about display of the gui, not playback?

There appears to be something wrong with your opengl installation. Thats why I asked about your video drivers.

---

### Post by lanewaves on 2012-04-30
> **nickrout said:**
> I thought we were talking about display of the gui, not playback?

There appears to be something wrong with your opengl installation. Thats why I asked about your video drivers.
You are correct, the gui goes black. It *does *work now when choosing QT instead of OpenGL. I have not messed with the drivers (on purpose) and it was working fine previous to the upgrade. I'll check on that tonight. 

In my output above it says:

2012-04-29 22:14:51.271785 W NVCtrl: OpenGL Sync to VBlank is disabled.
2012-04-29 22:14:51.271809 W NVCtrl: For best results enable this in NVidia settings or try running:
2012-04-29 22:14:51.271823 W NVCtrl: nvidia-settings -a "SyncToVBlank=1"
2012-04-29 22:14:51.271868 W NVCtrl: Alternatively try setting the '__GL_SYNC_TO_VBLANK' environment variable.

Would that actually contribute to my problem?

Thanks for your help.

---

### Post by nickrout on 2012-04-30
> **lanewaves said:**
> You are correct, the gui goes black. It *does *work now when choosing QT instead of OpenGL. I have not messed with the drivers (on purpose) and it was working fine previous to the upgrade. I'll check on that tonight. 

In my output above it says:

2012-04-29 22:14:51.271785 W NVCtrl: OpenGL Sync to VBlank is disabled.
2012-04-29 22:14:51.271809 W NVCtrl: For best results enable this in NVidia settings or try running:
2012-04-29 22:14:51.271823 W NVCtrl: nvidia-settings -a "SyncToVBlank=1"
2012-04-29 22:14:51.271868 W NVCtrl: Alternatively try setting the '__GL_SYNC_TO_VBLANK' environment variable.

Would that actually contribute to my problem?

Thanks for your help.

I do not know

what does glxinfo tell you?

---

### Post by BicyclerBoy on 2012-05-01
The latest nVidia driver seems to be causing trouble for old cards.
[http://www.nvnews.net/vbulletin/showthread.php?t=178460](http://www.nvnews.net/vbulletin/showthread.php?t=178460)

Are there any alternative (old stable) nVidia video drivers available in mythbuntu ?

---

