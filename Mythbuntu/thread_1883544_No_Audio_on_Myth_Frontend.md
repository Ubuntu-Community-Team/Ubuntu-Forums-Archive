---
title: "No Audio on Myth Frontend"
date: 2011-11-19
forum: Mythbuntu
---

### Post by fullmoonguru on 2011-11-19
I'm installing a frontend on our netbook to play files from our main backend.  The problem is that there's no audio.  Also, when I press esc to get out of the video it goes to a black screen.  This is on 10.04 & the frontend audio settings are ALSA:Default.  I tried looking at the the Mythtv How To to configure settings but I didn't see the Line slider in alsamixer that is discussed.  Here is my log file:

```
2011-11-19 10:39:12.345 UPnPautoconf() - Found one UPnP backend
2011-11-19 10:39:12.485 Testing network connectivity to '192.168.0.194'
2011-11-19 10:39:12.590 Closing DB connection named 'DBManager0'
2011-11-19 10:39:12.624 Connected to database 'mythconverg' at host: 192.168.0.194
2011-11-19 10:39:12.638 Closing DB connection named 'DBManager0'
2011-11-19 10:39:12.643 Connected to database 'mythconverg' at host: 192.168.0.194
2011-11-19 10:39:12.650 Current locale EN_US
2011-11-19 10:39:12.690 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-11-19 10:39:12.891 ScreenSaverX11Private: Gnome screen saver support enabled
2011-11-19 10:39:12.893 DPMS is active.
2011-11-19 10:39:13.047 Desktop video mode: 1366x768 60.031 Hz
2011-11-19 10:39:13.137 Enabled verbose msgs:  important general
2011-11-19 10:39:13.192 Loading en_us translation for module mythfrontend
2011-11-19 10:39:13.351 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
            eno: No such file or directory (2)
2011-11-19 10:39:13.352 JoystickMenuThread: Joystick disabled - Failed to read /home/beautybooty/.mythtv/joystickmenurc
2011-11-19 10:39:13.531 Using Frameless Window
2011-11-19 10:39:13.532 Using Full Screen Window
2011-11-19 10:39:14.054 Using the OpenGL painter
2011-11-19 10:39:14.464 OpenGL: OpenGL vendor  : NVIDIA Corporation
2011-11-19 10:39:14.464 OpenGL: OpenGL renderer: ION/PCI/SSE2
2011-11-19 10:39:14.464 OpenGL: OpenGL version : 3.2.0 NVIDIA 195.36.24
2011-11-19 10:39:14.464 OpenGL: Max texture size: 8192 x 8192
2011-11-19 10:39:14.464 OpenGL: Max texture units: 4
2011-11-19 10:39:14.464 OpenGL: Direct rendering: Yes
2011-11-19 10:39:14.464 OpenGL: Initialised MythRenderOpenGL
2011-11-19 10:39:16.080 New DB connection, total: 2
2011-11-19 10:39:16.086 Connected to database 'mythconverg' at host: 192.168.0.194
2011-11-19 10:39:16.092 Current MythTV Schema Version (DBSchemaVer): 1264
2011-11-19 10:39:16.128 New DB connection, total: 3
2011-11-19 10:39:16.128 New DB connection, total: 4
2011-11-19 10:39:16.133 Connected to database 'mythconverg' at host: 192.168.0.194
2011-11-19 10:39:16.139 Connected to database 'mythconverg' at host: 192.168.0.194
2011-11-19 10:39:17.277 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-11-19 10:39:17.278 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-11-19 10:39:17.352 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-11-19 10:39:17.352 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-11-19 10:39:17.962 Pulse: PulseAudio suspend OK
2011-11-19 10:39:18.155 Pulse: PulseAudio resume OK
2011-11-19 10:39:18.937 Registering Internal as a media playback plugin.
2011-11-19 10:39:18.996 Registering WebBrowser as a media playback plugin.
2011-11-19 10:39:19.005 Loading en_us translation for module mythbrowser
2011-11-19 10:39:19.165 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-11-19 10:39:19.233 Loading en_us translation for module mythgallery
2011-11-19 10:39:19.743 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-11-19 10:39:19.962 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-11-19 10:39:20.049 Loading en_us translation for module mythmusic
2011-11-19 10:39:20.181 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-11-19 10:39:20.351 Loading en_us translation for module mythvideo
2011-11-19 10:39:20.417 Loading en_us translation for module mythweather
2011-11-19 10:39:20.502 Found mainmenu.xml for theme 'blue-abstract-wide'
2011-11-19 10:39:20.795 MythCoreContext: Connecting to backend server: 192.168.0.194:6543 (try 1 of 1)
2011-11-19 10:39:20.798 Using protocol version 63
2011-11-19 10:39:39.217 MythUIHelper, Error: LoadScaleImage(myth://Coverart@192.168.0.194:6543/No Cover) failed to load image
2011-11-19 10:39:48.096 TV: Attempting to change from None to WatchingVideo
2011-11-19 10:39:48.677 Pulse: PulseAudio suspend OK
2011-11-19 10:39:49.467 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-11-19 10:39:49.467 AFD: Opened codec 0x7f1cc1ad8790, id(H264) type(Video)
2011-11-19 10:39:49.468 AFD: codec AAC has 2 channels
2011-11-19 10:39:49.472 AFD: Opened codec 0x7f1cc1ae1ba0, id(AAC) type(Audio)
2011-11-19 10:39:49.678 Pulse: PulseAudio resume OK
2011-11-19 10:39:49.878 Pulse: PulseAudio suspend OK
2011-11-19 10:39:49.915 AO: Opening audio device 'default' ch 2(2) sr 88200 sf signed 16 bit reenc 0
2011-11-19 10:39:49.964 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2011-11-19 10:39:49.971 AudioPlayer: Enabling Audio
2011-11-19 10:39:50.066 Clearing OpenGL painter cache.
2011-11-19 10:39:50.912 VDPAU: Created 2 output surfaces.
2011-11-19 10:39:50.912 VDPAU: Version 1
2011-11-19 10:39:50.912 VDPAU: Information NVIDIA VDPAU Driver Shared Library  195.36.24  Thu Apr 22 19:52:55 PDT 2010
2011-11-19 10:39:50.912 VDPAU: Created VDPAU render device 1366x768
2011-11-19 10:39:51.112 Player(0): Forcing decode extra audio option on (Video method requires it).
2011-11-19 10:39:51.118 OSD: Base theme size: 1280x720
2011-11-19 10:39:51.118 OSD: Scaling factors: 1.06562x1.06667
2011-11-19 10:39:51.302 OSD: Base theme size: 1280x720
2011-11-19 10:39:51.302 OSD: Scaling factors: 1.06562x1.06667
2011-11-19 10:39:51.315 Player(0): Video timing method: USleep with busy wait
2011-11-19 10:39:51.316 TV: Changing from None to WatchingVideo
2011-11-19 10:39:51.338 ScreenSaverX11Private: DPMS Deactivated 1
2011-11-19 10:39:51.346 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-11-19 10:40:01.481 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAff
2011-11-19 10:40:06.530 pause_active: 0
2011-11-19 10:40:10.761 Clearing OpenGL painter cache.
2011-11-19 10:40:11.833 Player(0): Waited 100ms for video buffers AAAAAAAAffAAAAAAA
2011-11-19 10:40:21.121 Player(0): Waited 100ms for video buffers ffAAAAAAAAAAAAAAA
2011-11-19 10:40:21.127 Player(0): Waited 100ms for video buffers FFUuLAAAAAAAAAAAA
2011-11-19 10:40:25.562 Marking recording as watched using offset 4 minutes
2011-11-19 10:40:25.605 TV: Attempting to change from WatchingVideo to None
2011-11-19 10:40:25.677 VDPAU Painter: Clearing VDPAU painter cache.
2011-11-19 10:40:25.680 MythPainter: 2 images not yet de-allocated.
2011-11-19 10:41:13.205 Pulse: PulseAudio resume OK
2011-11-19 10:41:13.222 TV: Changing from WatchingVideo to None
2011-11-19 10:41:13.546 ScreenSaverX11Private: DPMS Reactivated 1
2011-11-19 10:41:20.603 MythSocket(7f1cc26f0c00:42): readStringList: Error, timed out after 7000 ms.
2011-11-19 10:41:20.603 Remote file timeout.
2011-11-19 10:41:49.250 OpenGL: Deleting OpenGL Resources
2011-11-19 10:41:49.333 Pulse: Cleaning up PulseHandler
2011-11-19 10:41:49.334 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit
```

---

### Post by nickrout on 2011-11-19
scan for audio devices in frontend |settings|general and use one of the scanned devices.

Also check using alsamixer that the device is not muted and the volume is not too low.

---

### Post by fullmoonguru on 2011-11-21
Thanks that worked.  It's so funny, I've been using Myth for so long & I never realized that was a button!  It's so big that it looks like a Title to the page or something.

---

### Post by nickrout on 2011-11-21
> **fullmoonguru said:**
> Thanks that worked.  It's so funny, I've been using Myth for so long & I never realized that was a button!  It's so big that it looks like a Title to the page or something.

It was introduced in 0.24 I think.

---

### Post by fullmoonguru on 2011-11-21
Ahhh-

---

