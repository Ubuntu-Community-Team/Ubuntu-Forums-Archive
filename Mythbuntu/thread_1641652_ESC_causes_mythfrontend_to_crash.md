---
title: "ESC causes mythfrontend to crash"
date: 2010-12-09
forum: Mythbuntu
---

### Post by MonsterMaxx on 2010-12-09
Weird, it was working fine, but now on every machine (windows and ubuntu) an esc to exit a recording or live TV will crash the frontend every single time.

Anyone else having this problem?

backend is on ubuntu 10.10, it's a frontend too.  myth is 0.24
most of my frontends are on win7-64, but one is a win7-32

Code clipped from a windoze frontend
```
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/base.xml @ 111
                        Name: 'basemedium_normal'       Type: 'fontdef'
2010-12-09 11:35:10.456 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/base.xml @ 114
                        Name: 'basemedium_normal_selected'      Type: 'fontdef'
2010-12-09 11:35:10.456 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/base.xml @ 117
                        Name: 'basemedium_disabled'     Type: 'fontdef'
2010-12-09 11:35:10.457 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/base.xml @ 120
                        Name: 'basemedium_highlight'    Type: 'fontdef'
2010-12-09 11:35:10.457 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/base.xml @ 123
                        Name: 'basemedium_normal_button'        Type: 'fontdef'
2010-12-09 11:35:10.458 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/base.xml @ 126
                        Name: 'basemedium_selected_button'      Type: 'fontdef'
2010-12-09 11:35:10.458 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/base.xml @ 129
                        Name: 'basemedium_disabled_button'      Type: 'fontdef'
2010-12-09 11:35:10.459 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/base.xml @ 134
                        Name: 'deleterecordings_filesize_font'  Type: 'fontdef'
2010-12-09 11:35:10.460 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/base.xml @ 139
                        Name: 'baseguide'       Type: 'fontdef'
2010-12-09 11:35:10.619 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/base.xml @ 1126
                        Name: 'medium'  Type: 'fontdef'
2010-12-09 11:35:10.620 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/base.xml @ 1132
                        Name: 'large'   Type: 'fontdef'
2010-12-09 11:35:10.620 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/base.xml @ 1138
                        Name: 'clock'   Type: 'fontdef'
2010-12-09 11:35:10.627 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default-wide/base.xml @ 32
                        Name: 'basesmallgrey'   Type: 'fontdef'
2010-12-09 11:35:10.628 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default-wide/base.xml @ 36
                        Name: 'basesmallpurple' Type: 'fontdef'
2010-12-09 11:35:10.628 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default-wide/base.xml @ 40
                        Name: 'basesmallblack'  Type: 'fontdef'
2010-12-09 11:35:10.629 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default-wide/base.xml @ 44
                        Name: 'basesmallyellow' Type: 'fontdef'
2010-12-09 11:35:10.629 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default-wide/base.xml @ 48
                        Name: 'basesmallgreen'  Type: 'fontdef'
2010-12-09 11:35:10.630 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default-wide/base.xml @ 52
                        Name: 'basesmallblue'   Type: 'fontdef'
2010-12-09 11:35:10.631 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default-wide/base.xml @ 56
                        Name: 'basesmallred'    Type: 'fontdef'
2010-12-09 11:35:10.631 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default-wide/base.xml @ 60
                        Name: 'basemediumgrey'  Type: 'fontdef'
2010-12-09 11:35:10.632 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default-wide/base.xml @ 64
                        Name: 'basemediumgreen' Type: 'fontdef'
2010-12-09 11:35:10.632 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default-wide/base.xml @ 68
                        Name: 'basemediumred'   Type: 'fontdef'
2010-12-09 11:35:10.633 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default-wide/base.xml @ 72
                        Name: 'basemediumpurple'        Type: 'fontdef'
2010-12-09 11:35:10.641 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default/base.xml @ 11
                        Name: 'basetiny'        Type: 'fontdef'
2010-12-09 11:35:10.642 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default/base.xml @ 36
                        Name: 'basetinyred'     Type: 'fontdef'
2010-12-09 11:35:10.642 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/default/base.xml @ 80
                        Name: 'basemediumyellow'        Type: 'fontdef'
2010-12-09 11:35:10.649 New DB connection, total: 2
2010-12-09 11:35:10.651 New DB connection, total: 3
2010-12-09 11:35:10.652 Connected to database 'mythconverg' at host: 192.168.0.2
15
2010-12-09 11:35:10.652 Connected to database 'mythconverg' at host: 192.168.0.2
15
2010-12-09 11:35:10.653 Current MythTV Schema Version (DBSchemaVer): 1264
2010-12-09 11:35:11.074 Registering Internal as a media playback plugin.
2010-12-09 11:35:11.125 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-09 11:35:11.125 Loading en_us translation for module mythgallery
2010-12-09 11:35:11.142 Current MythVideo Schema Version (mythvideo.DBSchemaVer)
: 1038
2010-12-09 11:35:11.184 Loading en_us translation for module mythvideo
2010-12-09 11:35:11.191 MythFontProperties, Error: Failed to load 'Liberation Sa
ns', got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/menu-ui.xml @ 8
                        Name: 'menufont'        Type: 'fontdef'
2010-12-09 11:35:11.192 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/menu-ui.xml @ 17
                        Name: 'clock'   Type: 'fontdef'
2010-12-09 11:35:12.070 Found mainmenu.xml for theme 'MythCenter-wide'
Unrecognised OpenGL version
2010-12-09 11:35:12.089 MythCoreContext: Connecting to backend server: 192.168.0
.215:6543 (try 1 of 1)
2010-12-09 11:35:12.090 Using protocol version 63
2010-12-09 11:35:12.092 MythRenderD3D9: Default Adaptor Format X8R8G8B8 - Hardwa
re YV12 to RGB supported
2010-12-09 11:35:12.092 MythRenderD3D9: Using A8R8G8B8 surface format.
2010-12-09 11:35:12.134 MythRenderD3D9: Hardware YV12 to RGB conversion enabled.

2010-12-09 11:35:12.135 MythRenderD3D9: Device: NVIDIA GeForce GTX 465
2010-12-09 11:35:12.135 MythRenderD3D9: Driver: 7.14.10.304
2010-12-09 11:35:12.374 Unable to determine local time zone settings. If local t
ime zone settings differ from master backend settings, some functionality will f
ail.
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
2010-12-09 11:35:19.187 TV: Attempting to change from None to WatchingPreRecorde
d
2010-12-09 11:35:20.365 AFD: Opened codec 0x4310d960, id(H264) type(Video)
2010-12-09 11:35:20.365 AFD: codec AAC has 2 channels
2010-12-09 11:35:20.366 AFD: Opened codec 0x42fe3570, id(AAC) type(Audio)
2010-12-09 11:35:20.368 AO: Opening audio device 'Windows:' ch 2(2) sr 48000 sf
signed 16 bit reenc 0
2010-12-09 11:35:20.463 AudioPlayer: Enabling Audio
2010-12-09 11:35:20.513 OpenGL: OpenGL vendor  : NVIDIA Corporation
2010-12-09 11:35:20.513 OpenGL: OpenGL renderer: GeForce GTX 465/PCI/SSE2
2010-12-09 11:35:20.513 OpenGL: OpenGL version : 4.0.0
2010-12-09 11:35:20.514 OpenGL: Max texture size: 16384 x 16384
2010-12-09 11:35:20.514 OpenGL: Max texture units: 4
2010-12-09 11:35:20.514 OpenGL: Direct rendering: Yes
2010-12-09 11:35:20.514 OpenGL: Initialised MythRenderOpenGL
2010-12-09 11:35:20.514 VidOutGL: Created MythRenderOpenGL device.
2010-12-09 11:35:20.568 OpenGL painter using existing OpenGL context.
2010-12-09 11:35:20.568 OpenGL painter using existing QGLWidget.
2010-12-09 11:35:20.687 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/osd.xml @ 246
                        Name: 'medium'  Type: 'fontdef'
2010-12-09 11:35:20.693 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/osd.xml @ 228
                        Name: 'medium'  Type: 'fontdef'
2010-12-09 11:35:20.700 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/osd.xml @ 7
                        Name: 'small'   Type: 'fontdef'
2010-12-09 11:35:20.701 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/osd.xml @ 11
                        Name: 'medium'  Type: 'fontdef'
2010-12-09 11:35:20.702 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/osd.xml @ 14
                        Name: 'large'   Type: 'fontdef'
2010-12-09 11:35:20.714 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/osd.xml @ 179
                        Name: 'small'   Type: 'fontdef'
2010-12-09 11:35:20.715 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/osd.xml @ 183
                        Name: 'medium'  Type: 'fontdef'
2010-12-09 11:35:20.715 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/osd.xml @ 187
                        Name: 'large'   Type: 'fontdef'
2010-12-09 11:35:20.723 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/osd.xml @ 132
                        Name: 'medium'  Type: 'fontdef'
2010-12-09 11:35:20.729 MythFontProperties, Error: Failed to load 'Droid Sans',
got 'Arial' instead
                        Location: C:/Program Files (x86)/mythtv/share/mythtv/the
mes/MythCenter-wide/osd.xml @ 386
                        Name: 'medium'  Type: 'fontdef'
2010-12-09 11:35:20.741 VideoOutput, Error: Couldn't load deinterlace filter
2010-12-09 11:35:20.741 Player(0): Video timing method: USleep with busy wait
2010-12-09 11:35:20.841 TV: Changing from None to WatchingPreRecorded
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
2010-12-09 11:35:20.944 VideoOutput, Error: Couldn't load deinterlace filter
2010-12-09 11:35:20.944 Player(0): Failed to enable deinterlacing
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
QEventDispatcherWin32::unregisterTimer: invalid argument
2010-12-09 11:35:25.996 TV: Attempting to change from WatchingPreRecorded to Non
e
2010-12-09 11:35:26.022 Clearing OpenGL painter cache.
2010-12-09 11:35:26.022 MythPainter: 16 images not yet de-allocated.
2010-12-09 11:35:26.022 OpenGL: Deleting OpenGL Resources
2010-12-09 11:35:26.042 TV: Changing from WatchingPreRecorded to None
QEventDispatcherWin32::unregisterTimer: invalid argument
ASSERT failure in QCoreApplication::sendEvent: "Cannot send events to objects ow
ned by a different thread. Current thread 38342a0. Receiver '' (of type 'Preview
Generator') was created in thread 34464e50", file kernel\qcoreapplication.cpp, l
ine 348

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.


```

---

### Post by MonsterMaxx on 2010-12-09
Update: I've found a reproduceable way to make it crash.

Under TV Settings -> Playback there's a setting for
on exit, set this from just 'exit' to 'save position and exit'.
Also there's a checkbox to prompt at the end of recording.

Enabling either of these or both of them will cause Mythfrontend to crash every time on ESC

This did not help the backend which runs the frontend (boots Linux) but it did stop all the ones on Windoze from crashing on ESC.

---

### Post by MonsterMaxx on 2010-12-11
no one has any ideas on this one?

---

### Post by MonsterMaxx on 2010-12-14
update: I can bookmark a video {spacebar} with the 'save on exit turned off', exit with esc (no crash) and when relaunched will go to that bookmark.  This on a windoze front end.

Using native mythbuntu front end it locks up on ESC no matter what the settings are.

---

### Post by azmyth on 2010-12-15
I don't know anything about Windows but your log file shows a lot of errors. Don't know if these are common or if solving these will fix your crashes. On the Ubuntu FE, what does the log file say. I like to ssh in and export the display and run it from there so you can see everything scroll in front of you.

---

### Post by MonsterMaxx on 2010-12-16
ok.  Launched from a terminal window on the ubuntu myth frontend

```
robin@MythTV-SRV:~$ mythfrontend
2010-12-16 12:44:40.620 mythfrontend version: fixes/0.24 [f3ddc58] www.mythtv.org
2010-12-16 12:44:40.620 Using runtime prefix = /usr
2010-12-16 12:44:40.620 Using configuration directory = /home/robin/.mythtv
2010-12-16 12:44:40.668 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2010-12-16 12:44:41.406 Empty LocalHostName.
2010-12-16 12:44:41.406 Using localhost value of MythTV-SRV
2010-12-16 12:44:41.443 New DB connection, total: 1
2010-12-16 12:44:41.448 Connected to database 'mythconverg' at host: localhost
2010-12-16 12:44:41.470 Closing DB connection named 'DBManager0'
2010-12-16 12:44:41.471 Connected to database 'mythconverg' at host: localhost
2010-12-16 12:44:41.483 Current locale EN_US
2010-12-16 12:44:41.502 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2010-12-16 12:44:41.731 ScreenSaverX11Private: Gnome screen saver support enabled
2010-12-16 12:44:41.746 DPMS is active.
2010-12-16 12:44:41.917 Desktop video mode: 1600x1200 60.000 Hz
2010-12-16 12:44:42.088 Enabled verbose msgs:  important general
2010-12-16 12:44:42.119 Loading en_us translation for module mythfrontend
2010-12-16 12:44:42.225 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-12-16 12:44:42.226 JoystickMenuThread: Joystick disabled - Failed to read /home/robin/.mythtv/joystickmenurc
2010-12-16 12:44:42.429 Using Frameless Window
2010-12-16 12:44:42.429 Using Full Screen Window
2010-12-16 12:44:42.873 Using the Qt painter
2010-12-16 12:44:43.245 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 6
			Name: 'basesmall'	Type: 'fontdef'
2010-12-16 12:44:43.253 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 12
			Name: 'basesmaller'	Type: 'fontdef'
2010-12-16 12:44:43.253 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 16
			Name: 'basesmallbold'	Type: 'fontdef'
2010-12-16 12:44:43.253 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 20
			Name: 'basesmallboldblue'	Type: 'fontdef'
2010-12-16 12:44:43.253 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 24
			Name: 'basesmallboldgrey'	Type: 'fontdef'
2010-12-16 12:44:43.254 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 28
			Name: 'basesmallboldgreyhighlight'	Type: 'fontdef'
2010-12-16 12:44:43.254 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 32
			Name: 'small'	Type: 'fontdef'
2010-12-16 12:44:43.262 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 38
			Name: 'basemedium'	Type: 'fontdef'
2010-12-16 12:44:43.270 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 42
			Name: 'baselarge'	Type: 'fontdef'
2010-12-16 12:44:43.278 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 50
			Name: 'baselargenormal'	Type: 'fontdef'
2010-12-16 12:44:43.286 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 54
			Name: 'baseextralarge'	Type: 'fontdef'
2010-12-16 12:44:43.286 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 63
			Name: 'basesmallwhite'	Type: 'fontdef'
2010-12-16 12:44:43.286 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 67
			Name: 'basesmalllightgrey'	Type: 'fontdef'
2010-12-16 12:44:43.287 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 71
			Name: 'basesmallgrey'	Type: 'fontdef'
2010-12-16 12:44:43.287 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 75
			Name: 'basesmallpurple'	Type: 'fontdef'
2010-12-16 12:44:43.287 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 79
			Name: 'basesmallblack'	Type: 'fontdef'
2010-12-16 12:44:43.287 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 83
			Name: 'basesmallyellow'	Type: 'fontdef'
2010-12-16 12:44:43.288 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 87
			Name: 'basesmallgreen'	Type: 'fontdef'
2010-12-16 12:44:43.288 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 91
			Name: 'basesmallblue'	Type: 'fontdef'
2010-12-16 12:44:43.288 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 95
			Name: 'basesmallred'	Type: 'fontdef'
2010-12-16 12:44:43.288 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 99
			Name: 'basemediumwhite'	Type: 'fontdef'
2010-12-16 12:44:43.288 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 103
			Name: 'basemediumlightgrey'	Type: 'fontdef'
2010-12-16 12:44:43.289 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 107
			Name: 'basemediumgrey'	Type: 'fontdef'
2010-12-16 12:44:43.289 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 111
			Name: 'basemediumgreen'	Type: 'fontdef'
2010-12-16 12:44:43.289 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 115
			Name: 'basemediumred'	Type: 'fontdef'
2010-12-16 12:44:43.289 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 119
			Name: 'basemediumyellow'	Type: 'fontdef'
2010-12-16 12:44:44.000 MythFontProperties, Warning: Attempting to define 'small'
			with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1006
			Name: 'small'	Type: 'fontdef'
2010-12-16 12:44:44.038 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1012
			Name: 'medium'	Type: 'fontdef'
2010-12-16 12:44:44.053 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1018
			Name: 'large'	Type: 'fontdef'
2010-12-16 12:44:44.064 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1024
			Name: 'clock'	Type: 'fontdef'
2010-12-16 12:44:44.092 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/default/base.xml @ 11
			Name: 'basetiny'	Type: 'fontdef'
2010-12-16 12:44:44.092 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/default/base.xml @ 36
			Name: 'basetinyred'	Type: 'fontdef'
2010-12-16 12:44:44.187 Current MythTV Schema Version (DBSchemaVer): 1264
2010-12-16 12:44:44.223 New DB connection, total: 2
2010-12-16 12:44:44.224 Connected to database 'mythconverg' at host: localhost
2010-12-16 12:44:46.510 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2010-12-16 12:44:46.510 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2010-12-16 12:44:46.567 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2010-12-16 12:44:46.567 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2010-12-16 12:44:47.111 Pulse: PulseAudio suspend OK
2010-12-16 12:44:47.496 Pulse: PulseAudio resume OK
2010-12-16 12:44:47.714 Registering Internal as a media playback plugin.
2010-12-16 12:44:47.828 Loading en_us translation for module mytharchive
2010-12-16 12:44:47.849 Registering WebBrowser as a media playback plugin.
2010-12-16 12:44:47.857 Loading en_us translation for module mythbrowser
2010-12-16 12:44:48.018 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-16 12:44:48.018 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-16 12:44:48.018 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-16 12:44:48.019 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-16 12:44:48.032 Loading en_us translation for module mythgallery
2010-12-16 12:44:48.126 Loading en_us translation for module mythgame
2010-12-16 12:44:48.483 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-16 12:44:48.542 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-16 12:44:48.559 Loading en_us translation for module mythmusic
2010-12-16 12:44:48.617 Loading en_us translation for module mythnetvision
2010-12-16 12:44:48.659 Loading en_us translation for module mythnews
2010-12-16 12:44:48.742 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2010-12-16 12:44:48.789 Loading en_us translation for module mythvideo
2010-12-16 12:44:49.054 Starting update of NDFD-18_Hour
2010-12-16 12:44:49.119 Starting update of NWS-XML
2010-12-16 12:44:49.130 Starting update of NDFD-6_day
2010-12-16 12:44:49.146 Starting update of wunderground-animaps
2010-12-16 12:44:49.163 Starting update of wunderground-maps
2010-12-16 12:44:49.226 Loading en_us translation for module mythweather
2010-12-16 12:44:49.281 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 7
			Name: 'menufont'	Type: 'fontdef'
2010-12-16 12:44:49.298 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 16
			Name: 'clock'	Type: 'fontdef'
2010-12-16 12:44:54.111 Found mainmenu.xml for theme 'MythCenter'
2010-12-16 12:44:54.447 MythCoreContext: Connecting to backend server: 192.168.0.215:6543 (try 1 of 1)
2010-12-16 12:44:54.448 Using protocol version 63
2010-12-16 12:44:54.897 'nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/robin/.mythtv/MythWeather/NWS-XML KGMU' has exited
2010-12-16 12:44:55.398 'nice /usr/share/mythtv/mythweather/scripts/wunderground/wunderground-animaps.pl -u ENG -d /home/robin/.mythtv/MythWeather/wunderground-animaps GSP' has exited
2010-12-16 12:44:55.494 'nice /usr/share/mythtv/mythweather/scripts/wunderground/wunderground-maps.pl -u ENG -d /home/robin/.mythtv/MythWeather/wunderground-maps GSP' has exited
2010-12-16 12:44:56.140 'nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd18.pl -u ENG -d /home/robin/.mythtv/MythWeather/NDFD-18_Hour 34.85,-82.35' has exited
2010-12-16 12:44:56.854 'nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.pl -u ENG -d /home/robin/.mythtv/MythWeather/NDFD-6_day 34.85,-82.35' has exited
2010-12-16 12:46:56.064 TV: Attempting to change from None to WatchingPreRecorded
2010-12-16 12:46:56.305 Pulse: PulseAudio suspend OK
2010-12-16 12:46:56.530 AFD: Opened codec 0x7f7c6d59eda0, id(H264) type(Video)
2010-12-16 12:46:56.530 AFD: codec AAC has 2 channels
2010-12-16 12:46:56.532 AFD: Opened codec 0x7f7c6c5c1df0, id(AAC) type(Audio)
2010-12-16 12:46:56.705 Pulse: PulseAudio resume OK
2010-12-16 12:46:56.905 Pulse: PulseAudio suspend OK
2010-12-16 12:46:56.938 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2010-12-16 12:46:56.942 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2010-12-16 12:46:57.074 ALSA, Error: no playback control PCM found on mixer device default
2010-12-16 12:46:57.074 ALSA, Error: Unable to open audio mixer. Volume control disabled
2010-12-16 12:46:57.074 AudioPlayer: Enabling Audio
2010-12-16 12:46:57.323 VDPAU: Created 2 output surfaces.
2010-12-16 12:46:57.324 VDPAU: Version 1
2010-12-16 12:46:57.324 VDPAU: Information NVIDIA VDPAU Driver Shared Library  260.19.06  Mon Sep 13 04:58:44 PDT 2010
2010-12-16 12:46:57.324 VDPAU: Created VDPAU render device 1600x1200
2010-12-16 12:46:57.607 Player(0): Forcing decode extra audio option on (Video method requires it).
2010-12-16 12:46:57.740 Player(0): Video timing method: USleep with busy wait
2010-12-16 12:46:57.741 TV: Changing from None to WatchingPreRecorded
2010-12-16 12:46:57.749 ScreenSaverX11Private: DPMS Deactivated 1
2010-12-16 12:46:57.876 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-12-16 12:47:01.511 Marking recording as unwatched
2010-12-16 12:47:01.898 TV: Attempting to change from WatchingPreRecorded to None
2010-12-16 12:47:01.913 VDPAU Painter: Clearing VDPAU painter cache.
2010-12-16 12:47:01.913 MythPainter: 2 images not yet de-allocated.

```
at this point it is hung, I'm seeing a black screen and nothing else ever happens.

Also run as root with the same results

---

### Post by MonsterMaxx on 2010-12-21
This is from the backend machine running the frontend.  Mythbuntu 10.10 & 0.24-fixes

Seems to work fine except ESC causes it to stop doing anything (no actual crash, just a black screen and nothing ever happens again.)

```
$ mythfrontend
2010-12-21 12:09:10.684 mythfrontend version: fixes/0.24 [f3ddc58] www.mythtv.org
2010-12-21 12:09:10.685 Using runtime prefix = /usr
2010-12-21 12:09:10.685 Using configuration directory = /home/robin/.mythtv
2010-12-21 12:09:10.708 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2010-12-21 12:09:11.142 Empty LocalHostName.
2010-12-21 12:09:11.142 Using localhost value of MythTV-SRV
2010-12-21 12:09:11.173 New DB connection, total: 1
2010-12-21 12:09:11.181 Connected to database 'mythconverg' at host: localhost
2010-12-21 12:09:11.202 Closing DB connection named 'DBManager0'
2010-12-21 12:09:11.203 Connected to database 'mythconverg' at host: localhost
2010-12-21 12:09:11.205 Current locale EN_US
2010-12-21 12:09:11.217 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2010-12-21 12:09:11.449 ScreenSaverX11Private: Gnome screen saver support enabled
2010-12-21 12:09:11.477 DPMS is active.
2010-12-21 12:09:11.622 Desktop video mode: 1600x1200 60.000 Hz
2010-12-21 12:09:11.712 Enabled verbose msgs:  important general
2010-12-21 12:09:11.742 Loading en_us translation for module mythfrontend
2010-12-21 12:09:11.823 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-12-21 12:09:11.834 JoystickMenuThread: Joystick disabled - Failed to read /home/robin/.mythtv/joystickmenurc
2010-12-21 12:09:11.894 Using Frameless Window
2010-12-21 12:09:11.894 Using Full Screen Window
2010-12-21 12:09:12.357 Using the Qt painter
2010-12-21 12:09:12.668 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 6
			Name: 'basesmall'	Type: 'fontdef'
2010-12-21 12:09:12.676 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 12
			Name: 'basesmaller'	Type: 'fontdef'
2010-12-21 12:09:12.677 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 16
			Name: 'basesmallbold'	Type: 'fontdef'
2010-12-21 12:09:12.677 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 20
			Name: 'basesmallboldblue'	Type: 'fontdef'
2010-12-21 12:09:12.677 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 24
			Name: 'basesmallboldgrey'	Type: 'fontdef'
2010-12-21 12:09:12.677 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 28
			Name: 'basesmallboldgreyhighlight'	Type: 'fontdef'
2010-12-21 12:09:12.677 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 32
			Name: 'small'	Type: 'fontdef'
2010-12-21 12:09:12.685 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 38
			Name: 'basemedium'	Type: 'fontdef'
2010-12-21 12:09:12.693 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 42
			Name: 'baselarge'	Type: 'fontdef'
2010-12-21 12:09:12.702 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 50
			Name: 'baselargenormal'	Type: 'fontdef'
2010-12-21 12:09:12.709 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 54
			Name: 'baseextralarge'	Type: 'fontdef'
2010-12-21 12:09:12.710 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 63
			Name: 'basesmallwhite'	Type: 'fontdef'
2010-12-21 12:09:12.710 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 67
			Name: 'basesmalllightgrey'	Type: 'fontdef'
2010-12-21 12:09:12.710 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 71
			Name: 'basesmallgrey'	Type: 'fontdef'
2010-12-21 12:09:12.710 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 75
			Name: 'basesmallpurple'	Type: 'fontdef'
2010-12-21 12:09:12.711 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 79
			Name: 'basesmallblack'	Type: 'fontdef'
2010-12-21 12:09:12.711 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 83
			Name: 'basesmallyellow'	Type: 'fontdef'
2010-12-21 12:09:12.711 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 87
			Name: 'basesmallgreen'	Type: 'fontdef'
2010-12-21 12:09:12.711 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 91
			Name: 'basesmallblue'	Type: 'fontdef'
2010-12-21 12:09:12.712 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 95
			Name: 'basesmallred'	Type: 'fontdef'
2010-12-21 12:09:12.712 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 99
			Name: 'basemediumwhite'	Type: 'fontdef'
2010-12-21 12:09:12.712 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 103
			Name: 'basemediumlightgrey'	Type: 'fontdef'
2010-12-21 12:09:12.712 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 107
			Name: 'basemediumgrey'	Type: 'fontdef'
2010-12-21 12:09:12.713 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 111
			Name: 'basemediumgreen'	Type: 'fontdef'
2010-12-21 12:09:12.713 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 115
			Name: 'basemediumred'	Type: 'fontdef'
2010-12-21 12:09:12.713 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 119
			Name: 'basemediumyellow'	Type: 'fontdef'
2010-12-21 12:09:13.381 MythFontProperties, Warning: Attempting to define 'small'
			with face 'DejaVu Sans', but it already exists with face 'Liberation Sans'
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1006
			Name: 'small'	Type: 'fontdef'
2010-12-21 12:09:13.434 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1012
			Name: 'medium'	Type: 'fontdef'
2010-12-21 12:09:13.449 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1018
			Name: 'large'	Type: 'fontdef'
2010-12-21 12:09:13.463 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1024
			Name: 'clock'	Type: 'fontdef'
2010-12-21 12:09:13.527 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/default/base.xml @ 11
			Name: 'basetiny'	Type: 'fontdef'
2010-12-21 12:09:13.531 MythFontProperties, Error: Failed to load 'Arial', got 'Liberation Sans' instead
			Location: /usr/share/mythtv/themes/default/base.xml @ 36
			Name: 'basetinyred'	Type: 'fontdef'
2010-12-21 12:09:13.551 New DB connection, total: 2
2010-12-21 12:09:13.552 Current MythTV Schema Version (DBSchemaVer): 1264
2010-12-21 12:09:13.553 Connected to database 'mythconverg' at host: localhost
2010-12-21 12:09:14.516 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2010-12-21 12:09:14.516 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2010-12-21 12:09:14.556 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2010-12-21 12:09:14.556 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2010-12-21 12:09:15.105 Pulse: PulseAudio suspend OK
2010-12-21 12:09:15.512 Pulse: PulseAudio resume OK
2010-12-21 12:09:15.677 Registering Internal as a media playback plugin.
2010-12-21 12:09:15.784 Loading en_us translation for module mytharchive
2010-12-21 12:09:15.805 Registering WebBrowser as a media playback plugin.
2010-12-21 12:09:15.813 Loading en_us translation for module mythbrowser
2010-12-21 12:09:15.914 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-21 12:09:15.914 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-21 12:09:15.914 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-21 12:09:15.915 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-21 12:09:15.922 Loading en_us translation for module mythgallery
2010-12-21 12:09:16.066 Loading en_us translation for module mythgame
2010-12-21 12:09:16.454 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-21 12:09:16.508 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-21 12:09:16.523 Loading en_us translation for module mythmusic
2010-12-21 12:09:16.557 Loading en_us translation for module mythnetvision
2010-12-21 12:09:16.590 Loading en_us translation for module mythnews
2010-12-21 12:09:16.665 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2010-12-21 12:09:16.712 Loading en_us translation for module mythvideo
2010-12-21 12:09:16.775 Starting update of NDFD-18_Hour
2010-12-21 12:09:16.825 Starting update of NWS-XML
2010-12-21 12:09:16.836 Starting update of NDFD-6_day
2010-12-21 12:09:16.853 Starting update of wunderground-animaps
2010-12-21 12:09:16.866 Starting update of wunderground-maps
2010-12-21 12:09:16.965 Loading en_us translation for module mythweather
2010-12-21 12:09:16.999 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 7
			Name: 'menufont'	Type: 'fontdef'
2010-12-21 12:09:17.008 MythFontProperties, Error: Failed to load 'Trebuchet MS', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/menu-ui.xml @ 16
			Name: 'clock'	Type: 'fontdef'
2010-12-21 12:09:18.837 Found mainmenu.xml for theme 'MythCenter'
2010-12-21 12:09:19.012 MythCoreContext: Connecting to backend server: 192.168.0.215:6543 (try 1 of 1)
2010-12-21 12:09:19.013 Using protocol version 63
2010-12-21 12:09:19.195 'nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/robin/.mythtv/MythWeather/NWS-XML KGMU' has exited
2010-12-21 12:09:19.322 'nice /usr/share/mythtv/mythweather/scripts/wunderground/wunderground-animaps.pl -u ENG -d /home/robin/.mythtv/MythWeather/wunderground-animaps GSP' has exited
2010-12-21 12:09:19.390 'nice /usr/share/mythtv/mythweather/scripts/wunderground/wunderground-maps.pl -u ENG -d /home/robin/.mythtv/MythWeather/wunderground-maps GSP' has exited
2010-12-21 12:09:21.814 'nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd18.pl -u ENG -d /home/robin/.mythtv/MythWeather/NDFD-18_Hour 34.85,-82.35' has exited
2010-12-21 12:09:22.387 'nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.pl -u ENG -d /home/robin/.mythtv/MythWeather/NDFD-6_day 34.85,-82.35' has exited
2010-12-21 12:10:26.480 TV: Attempting to change from None to WatchingPreRecorded
2010-12-21 12:10:26.774 Pulse: PulseAudio suspend OK
2010-12-21 12:10:27.097 AFD: Opened codec 0x7f21ad046010, id(H264) type(Video)
2010-12-21 12:10:27.097 AFD: codec AAC has 2 channels
2010-12-21 12:10:27.098 AFD: Opened codec 0x7f21ad046470, id(AAC) type(Audio)
2010-12-21 12:10:27.275 Pulse: PulseAudio resume OK
2010-12-21 12:10:27.475 Pulse: PulseAudio suspend OK
2010-12-21 12:10:27.502 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2010-12-21 12:10:27.506 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2010-12-21 12:10:27.646 ALSA, Error: no playback control PCM found on mixer device default
2010-12-21 12:10:27.647 ALSA, Error: Unable to open audio mixer. Volume control disabled
2010-12-21 12:10:27.647 AudioPlayer: Enabling Audio
2010-12-21 12:10:27.909 VDPAU: Created 2 output surfaces.
2010-12-21 12:10:27.909 VDPAU: Version 1
2010-12-21 12:10:27.909 VDPAU: Information NVIDIA VDPAU Driver Shared Library  260.19.06  Mon Sep 13 04:58:44 PDT 2010
2010-12-21 12:10:27.909 VDPAU: Created VDPAU render device 1600x1200
2010-12-21 12:10:28.174 Player(0): Forcing decode extra audio option on (Video method requires it).
2010-12-21 12:10:28.290 Player(0): Video timing method: USleep with busy wait
2010-12-21 12:10:28.291 TV: Changing from None to WatchingPreRecorded
2010-12-21 12:10:28.300 ScreenSaverX11Private: DPMS Deactivated 1
2010-12-21 12:10:28.387 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-12-21 12:10:30.229 Marking recording as unwatched
2010-12-21 12:10:30.607 TV: Attempting to change from WatchingPreRecorded to None
2010-12-21 12:10:30.615 VDPAU Painter: Clearing VDPAU painter cache.
2010-12-21 12:10:30.616 MythPainter: 2 images not yet de-allocated.


```

---

### Post by jaysonb485 on 2010-12-27
same thing happens with me. my terminal output has similar messages.

---

### Post by MonsterMaxx on 2010-12-27
> **jaysonb485 said:**
> same thing happens with me. my terminal output has similar messages.

Hey Hey, we have a winner.  Now, let's figure out what we have in common.
What's your setup?

---

### Post by coronafire on 2011-01-04
Hey Guys,
I've got the same problem, did you ever figure out how to fix it?

Cheers,
Andrew

---

### Post by MonsterMaxx on 2011-01-04
no, but with you that makes 3

Maybe we should report it as a bug

---

### Post by rgbiernat on 2011-01-05
So - let's count to four then. I am having the same bug. Not sure if it is related to the "restart from scratch" from today or the latest ppa 0.24 update.

---

### Post by MonsterMaxx on 2011-01-05
Mine was a clean install too, a new database too. Totally fresh start. 10.10 and 0.24fixes

---

### Post by BicyclerBoy on 2011-01-06
The important errors in one of the previous posts is audio..
Did you rescan your audio devices after 0.24 upgrade..
Fresh install with imported old database will still need audio rescan.
This can cause your symptoms (in Linux).

Exit of recording cause audio & video configuration stuff to occur.
The error here kicks you out..

---

### Post by MonsterMaxx on 2011-01-06
yes, have done a rescan of audio, no difference

Database is NEW, lost old one in a crash.

---

### Post by BicyclerBoy on 2011-01-07
Still think there is something not right with the audio on the linux box.

The nvidia 260.19.29 is the latest stable release.
But you are not using hdmi audio are you ?

The timer error looks serious on the windoze box.

---

### Post by MonsterMaxx on 2011-01-07
Using latest stable release of nvidia.  NOT using hdmi.

The windoze boxes actually run much better than a pure linux box does.  the linux boxes freeze completely on exit of recorded programs no matter what i do.  the windoze boxes will continue most of the time and are much more reliable than the pure myth/ubuntu machines.
Bookmarking and deleting while viewing will cause a crash on exit on windoze boxes, linux will not even get that far.

I'm convinced this is a backend issue, but that's all I'm convinced of.

---

### Post by wjohnsaunders on 2011-01-10
Try going to Setup/General and select the "Scan for audio devices" button at the top. Scroll through the audio output devices and select "ALSA: pulse", set audio options below to suit your speaker setup. Then on the next page set your Mixer device to "software".

My theory is that mythtv and pulseaudio have a contention issue with direct access to the audio hardware, via ALSA. By configuring mythtv to direct audio via pulseaudio the contention is removed.

---

### Post by sami8519 on 2011-01-10
I had the exact same problem and I thought I am the only one because I  might have messed with the system. Had to eventually reinstall mythbuntu  from scratch. Now it is gone but seeing it is occuring for many people  here I might just get ready for it any time soon:(

---

### Post by MonsterMaxx on 2011-01-10
> **wjohnsaunders said:**
> Try going to Setup/General and select the "Scan for audio devices" button at the top. Scroll through the audio output devices and select "ALSA: pulse", set audio options below to suit your speaker setup. Then on the next page set your Mixer device to "software".

My theory is that mythtv and pulseaudio have a contention issue with direct access to the audio hardware, via ALSA. By configuring mythtv to direct audio via pulseaudio the contention is removed.
done that, no help

---

### Post by newbuntu81 on 2011-03-30
> **MonsterMaxx said:**
> done that, no help

I am having the same problems on both frontends.  One is Fedora 14, a new install, the second is Mythbuntu 10.10, also a new install.

I've tried changing the Playback settings from CPU+ to Normal, which seems to get rid of the blue line at the top and the video plays better.  However, when I try to stop the playback and go back to the previous screen with ESC, the screen freezes.  Any ideas?

**_In mythfrontend:_**
Setup
TV Settings
Playback
change Current Video Playback (pg 3) from CPU+ to Normal

---

### Post by newbuntu81 on 2011-04-01
> **newbuntu81 said:**
> I am having the same problems on both frontends.  One is Fedora 14, a new install, the second is Mythbuntu 10.10, also a new install.

I've tried changing the Playback settings from CPU+ to Normal, which seems to get rid of the blue line at the top and the video plays better.  However, when I try to stop the playback and go back to the previous screen with ESC, the screen freezes.  Any ideas?

**_In mythfrontend:_**
Setup
TV Settings
Playback
change Current Video Playback (pg 3) from CPU+ to Normal


Ok I got it.  I changed my Playback settings to CPU++, set it to use both of my CPU's, and changed the setting to Linear instead of Bob2x.  This got rid of the lines and has a smooth playback.  When I hit i for info, the blue bar looked good and I could read the information clearly.

---

### Post by gator on 2011-04-02
I have been getting the same thing. Running 10.10 with VDPAU - GT220 with HDMI audio. The screen turns black when i exit live TV or movies and you cant do anything. It doesn't happen all the time, maybe 1 every couple of days ). I can log in with ssh and notice the frontend process not dead or using high cpu. When i kill it i return to the desktop but restarting the frontend i lose sound. The only fix is to reboot. This seemed to start after getting HDMI Audio working. Telling VDPAU to use a single core in the playback process has helped a little. Any other idea's?
P.S i'll post the log next time, i think it had buffer under run or something like that. My box has a huge 9 day uptime at the moment!!

---

### Post by pils92 on 2011-05-17
I was having the same problem as original poster, after modifying settings in cpu++. After much experimenting I narrowed it down to problems with openGL vertical sync. ESC will crash on exiting recording or live tv if openGL vertical sync is checked enabled, but works fine if disabled. Hope this helps someone out. :popcorn:

intel core 2 duo 2.4 GHZ ATIHD3650 4-GHZ DDR2 @ 800mhz

Note: using openGL and openGL2 in cpu++ Settings

---

### Post by natuk on 2011-05-24
Same problem on a Mac Mini. Solved by rescanning audio devices and choosing Pulse audio instead of Alsa.

---

