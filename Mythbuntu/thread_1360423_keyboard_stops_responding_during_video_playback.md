---
title: "keyboard stops responding during video playback"
date: 2009-12-20
forum: Mythbuntu
---

### Post by leeko on 2009-12-20
Hi,

I'm running mythbuntu 9.10 on a zotac ionitx motherboard with integrated geforce 9400M video. The CPU is a dual core atom 330, and the system is fully updated. 

Mythbuntu is running, but whenever I watch TV or play a recording, the keyboard (a logitech mk300 wireless) partially stops responding for a couple of minutes. I say partially, because myth doesn't respond to keypresses but I'm able to alt-tab out of myth ok. It keeps playing in the background, and the video runs smoothly. 

When I'm in another application (with video running), the keypresses are only variably picked up, and occasionally repeat multiple times. It almost seems like the CPU load is maxed out, but top shows it running only at ~30%. When video isn't running, the keyboard works fine.

I've also noticed this happens when playing flash video (e.g. youtube) in a browser, so it's not limited to myth. I've read that the dual-core atom (and this mobo in particular) is more than capable of HD-video, and I'm only trying to play SD-video at present. 

I tried updating the gfx drivers (nvidia 185.x to 190.x), but the problem persists. Can anyone help me troubleshoot this? 

Thanks,

Lee

---

### Post by movieman on 2009-12-20
I get that too; most recently I started playing a DVD and after a few minutes MythTV stopped responding to the keyboard so I couldn't even get out of the DVD playback. Eventually I had to ssh into the machine and kill the frontend.

So far I'm afraid that 0.22 is turning out to be vastly less robust than 0.21.

---

### Post by radnor on 2009-12-21
Do you have a desktop lockup too?  There are times I do not have the FE running and the desktop is NOT responsive at all.  I Can SSH in and mess with the BE fine.

---

### Post by newlinux on 2009-12-21
A couple of things to look into:

1. Make sure you have Option "Use Events" "on" in xorg.conf if you are using a nvidia card.

[http://ubuntuforums.org/showthread.php?t=885337](http://ubuntuforums.org/showthread.php?t=885337)

2. One sometimes the sync method you use can cause it. I think RTC is generally the worst. On one of my frontends, using openGL vertical sync fixed this issue for me. But you have to make sure it is actually working, not just using the option (check the logs).

BTW I'm still on .21 and that had these problems too... For me I had some problems when I switched video drivers or cards. 

Other than that, post your frontend logs from the times when this happens.

---

### Post by leeko on 2009-12-23
Hi, 

Thanks for the replies. I changed mythtv's settings to use openGL sync, and added the "UseEvents" option to xorg.conf. I also made mythtv bring up the program guide whenever I start Live TV, and played around with some of the settings in Nvidia x-server config. I changed it to "high performance" instead of "quality", and enabled openGL sync to vblank. 

The end-result is that it's slightly better, but still a problem. I can navigate the program guide, but not all keypresses are registered. If I bring up a terminal and try to type "this is a test", it produces "tiiiiiiis isa ttttttet" - some keypresses repeat, others are missed. The mouse is also poorly responsive during this time. The video doesn't skip, and the problems go away when video is not playing (although it does show up when viewing certain webpages as well, such as gmail). 

I've included my mythfrontend log (opened mythfrontend, started live TV, changed channels, exited live TV, exited mythfrontend) and xorg log below. Hope this makes sense to someone! 

```

2009-12-23 10:05:19.256 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-12-23 10:05:19.257 Using runtime prefix = /usr
2009-12-23 10:05:19.257 Using configuration directory = /home/lee/.mythtv
2009-12-23 10:05:20.842 Empty LocalHostName.
2009-12-23 10:05:20.842 Using localhost value of LeekoMythFE
2009-12-23 10:05:20.843 Testing network connectivity to '192.168.1.100'
2009-12-23 10:05:20.872 New DB connection, total: 1
2009-12-23 10:05:20.888 Connected to database 'mythconverg' at host: 192.168.1.100
2009-12-23 10:05:20.890 Closing DB connection named 'DBManager0'
2009-12-23 10:05:20.910 ScreenSaverX11Private: Gnome screen saver support enabled
2009-12-23 10:05:20.913 DPMS is active.
2009-12-23 10:05:20.916 Primary screen: 0.
2009-12-23 10:05:20.928 Connected to database 'mythconverg' at host: 192.168.1.100
2009-12-23 10:05:20.936 Using screen 0, 1366x768 at 0,0
2009-12-23 10:05:21.032 MythUI Image Cache size set to 20971520 bytes
2009-12-23 10:05:21.033 Enabled verbose msgs:  important general
2009-12-23 10:05:21.116 Primary screen: 0.
2009-12-23 10:05:21.122 Using screen 0, 1366x768 at 0,0
2009-12-23 10:05:21.124 Using theme base resolution of 1280x720
2009-12-23 10:05:21.241 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
			eno: No such file or directory (2)
2009-12-23 10:05:21.241 JoystickMenuThread Error: Joystick disabled - Failed to read /home/lee/.mythtv/joystickmenurc
2009-12-23 10:05:21.978 Using the Qt painter
2009-12-23 10:05:22.417 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-12-23 10:05:22.632 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-12-23 10:05:22.853 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-12-23 10:05:22.853 Unable to load window 'backgroundwindow' from base
2009-12-23 10:05:22.905 Current MythTV Schema Version (DBSchemaVer): 1244
2009-12-23 10:05:24.311 Desktop video mode: 1366x768 62.2937 Hz
2009-12-23 10:05:26.567 Registering Internal as a media playback plugin.
2009-12-23 10:05:27.148 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-12-23 10:05:27.153 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-12-23 10:05:27.186 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-12-23 10:05:27.187 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-12-23 10:05:27.258 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-12-23 10:05:27.750 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-12-23 10:05:27.892 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-12-23 10:05:28.533 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-12-23 10:05:28.672 Loading menu theme from /usr/share/mythtv/themes/mediacentermenu//mainmenu.xml
2009-12-23 10:05:28.683 Found mainmenu.xml for theme 'Mythbuntu'
2009-12-23 10:05:29.435 MythContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2009-12-23 10:05:29.441 Using protocol version 50
2009-12-23 10:05:34.584 New DB connection, total: 2
2009-12-23 10:05:34.598 Connected to database 'mythconverg' at host: 192.168.1.100
2009-12-23 10:05:35.029 TV: Attempting to change from None to Watching WatchingLiveTV
2009-12-23 10:05:35.043 MythContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2009-12-23 10:05:35.050 Using protocol version 50
2009-12-23 10:05:35.089 Spawning LiveTV Recorder -- begin
2009-12-23 10:05:35.869 Spawning LiveTV Recorder -- end
2009-12-23 10:05:36.008 We have a playbackURL(myth://192.168.1.100:6543/1339_20091223100535.nuv) & cardtype(V4L)
2009-12-23 10:05:36.148 We have a RingBuffer
2009-12-23 10:05:36.203 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2009-12-23 10:05:36.505 Opening audio device 'default'. ch 2(2) sr 44100
2009-12-23 10:05:36.505 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-12-23 10:05:36.643 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2009-12-23 10:05:36.976 New DB connection, total: 3
2009-12-23 10:05:37.020 Connected to database 'mythconverg' at host: 192.168.1.100
2009-12-23 10:05:37.451 FilterManager: Failed to load filter 'colorspace', no such filter exists
2009-12-23 10:05:37.462 OSD Theme Dimensions W: 1280 H: 720
2009-12-23 10:05:38.539 New DB connection, total: 4
2009-12-23 10:05:38.539 New DB connection, total: 5
2009-12-23 10:05:38.564 Connected to database 'mythconverg' at host: 192.168.1.100
2009-12-23 10:05:38.564 Connected to database 'mythconverg' at host: 192.168.1.100
2009-12-23 10:05:38.619 The realtime priority setting is not enabled.
2009-12-23 10:05:38.638 OpenGLVideoSync()
2009-12-23 10:05:38.710 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end ok
2009-12-23 10:05:38.710 TV: Changing from None to Watching WatchingLiveTV
2009-12-23 10:05:38.710 TV: State is LiveTV & mctx == ctx
2009-12-23 10:05:38.735 TV: UpdateOSDInput done
2009-12-23 10:05:38.735 TV: UpdateLCD done
2009-12-23 10:05:38.735 TV: ITVRestart done
2009-12-23 10:05:38.757 Video timing method: SGI OpenGL
2009-12-23 10:05:38.762 ScreenSaverX11Private: DPMS Deactivated 1
2009-12-23 10:05:38.874 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/schedule-ui.xml
2009-12-23 10:06:10.641 FilterManager: Failed to load filter 'colorspace', no such filter exists
2009-12-23 10:06:10.944 WriteAudio: buffer underrun
2009-12-23 10:06:28.655 ScreenSaverX11Private: DPMS Reactivated 1
2009-12-23 10:06:29.656 TV: Attempting to change from Watching WatchingLiveTV to None
2009-12-23 10:06:29.690 ~OpenGLVideoSync() -- closing opengl vsync
2009-12-23 10:06:30.101 TV: Changing from Watching WatchingLiveTV to None
2009-12-23 10:06:33.474 Deleting UPnP client...

```

```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux LeekoMythFE 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=3fee537f-6dd0-41a3-a4a7-b8770f78f7ae ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 23 09:49:24 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:3:0:0) 10de:087d:19da:a108 nVidia Corporation ION VGA rev 177, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  190.53  Tue Dec  8 20:47:42 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  190.53  Tue Dec  8 19:16:02 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEvents" "True"
(**) Dec 23 09:49:28 NVIDIA(0): Enabling RENDER acceleration
(II) Dec 23 09:49:28 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Dec 23 09:49:28 NVIDIA(0):     enabled.
(II) Dec 23 09:49:30 NVIDIA(0): NVIDIA GPU ION (C79) at PCI:3:0:0 (GPU-0)
(--) Dec 23 09:49:30 NVIDIA(0): Memory: 524288 kBytes
(--) Dec 23 09:49:30 NVIDIA(0): VideoBIOS: 62.79.65.00.00
(--) Dec 23 09:49:30 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Dec 23 09:49:30 NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0:
(--) Dec 23 09:49:30 NVIDIA(0):     PLX PHD5039NUS (DFP-0)
(--) Dec 23 09:49:30 NVIDIA(0): PLX PHD5039NUS (DFP-0): 330.0 MHz maximum pixel clock
(--) Dec 23 09:49:30 NVIDIA(0): PLX PHD5039NUS (DFP-0): Internal Dual Link TMDS
(II) Dec 23 09:49:30 NVIDIA(0): Assigned Display Device: DFP-0
(==) Dec 23 09:49:30 NVIDIA(0): 
(==) Dec 23 09:49:30 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Dec 23 09:49:30 NVIDIA(0):     will be used as the requested mode.
(==) Dec 23 09:49:30 NVIDIA(0): 
(II) Dec 23 09:49:30 NVIDIA(0): Validated modes:
(II) Dec 23 09:49:30 NVIDIA(0):     "nvidia-auto-select"
(II) Dec 23 09:49:30 NVIDIA(0): Virtual screen size determined to be 1366 x 768
(--) Dec 23 09:49:30 NVIDIA(0): DPI set to (31, 34); computed from "UseEdidDpi" X config
(--) Dec 23 09:49:30 NVIDIA(0):     option
(==) Dec 23 09:49:30 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Dec 23 09:49:30 NVIDIA(0): Initialized GPU GART.
(II) Dec 23 09:49:30 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Dec 23 09:49:30 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Dec 23 09:49:30 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Logitech USB Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 12 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.

```

Thanks again, 

Lee

---

