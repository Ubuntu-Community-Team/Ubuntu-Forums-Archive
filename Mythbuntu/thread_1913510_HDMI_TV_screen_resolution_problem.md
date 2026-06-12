---
title: "HDMI TV screen resolution problem"
date: 2012-01-22
forum: Mythbuntu
---

### Post by Paulgirardin on 2012-01-22
I'm running mythbuntu into a HDMI input on a TV with a 1024 x 768 screen size.

The maximum resolution option available on the myth box is 1280 x 720 and the tv reports that the signal is only 720p.
I get 1080i on other inputs with other devices. How can I get better resolution?
graphics card is Nvidia GT430
xorg.conf :
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Extensions"
	Option	"Composite"	"Disable"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"TVOutFormat"	"COMPONENT"
	Option	"TVStandard"	"HD1080p"
	Option	"DPI"	"100x100"
	Option	"NoLogo"	"1"
	Option	"ConnectedMonitor"	"TV"
EndSection

```
Output of xrandr:
```
myth@myth:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1280 x 720, maximum 1280 x 720
default connected 1280x720+0+0 0mm x 0mm
   1280x720       50.0*    51.0     52.0  
   960x720        53.0     54.0  
   960x600        55.0  
   960x540        56.0  
   928x696        57.0     58.0  
   896x672        59.0     60.0  
   840x525        61.0     62.0     63.0     64.0     65.0  
   832x624        66.0  
   800x600        67.0     68.0     69.0     70.0     71.0     72.0     73.0     74.0     75.0     76.0  
   800x512        77.0  
   720x576        78.0     79.0  
   720x480        80.0     81.0  
   720x450        82.0  
   720x400        83.0  
   700x525        84.0     85.0     86.0     87.0  
   680x384        88.0     89.0  
   640x512        90.0     91.0     92.0  
   640x480        93.0     94.0     95.0     96.0     97.0     98.0     99.0  
   640x400       100.0  
   640x350       101.0  
   576x432       102.0    103.0    104.0    105.0    106.0    107.0    108.0  
   512x384       109.0    110.0    111.0    112.0    113.0  
   416x312       114.0  
   400x300       115.0    116.0    117.0    118.0    119.0  
   360x200       120.0  
   320x240       121.0    122.0    123.0    124.0  
   320x200       125.0  
   320x175       126.0  

```

output of xwininfo:
```
xwininfo: Window id: 0x1200003 "Desktop"

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1280
  Height: 720
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1280x720+0+0

```

---

### Post by nickrout on 2012-01-22
/var/log/Xorg.0.log should have relevant info.

What does the TV manual say ahould be available?

---

### Post by Paulgirardin on 2012-01-22
I've just realised that I can't tell the difference between 720p and 1080i on this TV so I might just leave it as is.
Thanks

This is Xorg.0.log:
```
[    26.927] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    26.927] X Protocol Version 11, Revision 0
[    26.927] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    26.927] Current Operating System: Linux myth 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
[    26.927] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=45f57286-d835-4a0a-8d0b-a27140753e14 ro quiet splash vt.handoff=7
[    26.927] Build Date: 29 September 2011  12:48:48AM
[    26.927] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    26.927] Current version of pixman: 0.22.2
[    26.927] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    26.927] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.927] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 23 16:34:19 2012
[    26.927] (==) Using config file: "/etc/X11/xorg.conf"
[    26.927] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.928] (==) No Layout section.  Using the first Screen section.
[    26.928] (**) |-->Screen "Default Screen" (0)
[    26.928] (**) |   |-->Monitor "<default monitor>"
[    26.928] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[    26.928] (**) |   |-->Device "Default Device"
[    26.928] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    26.928] (==) Automatically adding devices
[    26.928] (==) Automatically enabling devices
[    26.928] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.928] 	Entry deleted from font path.
[    26.928] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.928] 	Entry deleted from font path.
[    26.928] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.928] 	Entry deleted from font path.
[    26.928] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.928] 	Entry deleted from font path.
[    26.928] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.928] 	Entry deleted from font path.
[    26.942] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    26.942] 	Entry deleted from font path.
[    26.942] 	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    26.942] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    26.942] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.943] (**) Extension "Composite" is disabled
[    26.943] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.943] (II) Loader magic: 0x823ada0
[    26.943] (II) Module ABI versions:
[    26.943] 	X.Org ANSI C Emulation: 0.4
[    26.943] 	X.Org Video Driver: 10.0
[    26.943] 	X.Org XInput driver : 12.3
[    26.943] 	X.Org Server Extension : 5.0
[    26.943] (--) PCI:*(0:1:0:0) 10de:0de1:1458:3505 rev 161, Mem @ 0xfa000000/16777216, 0xe8000000/134217728, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    26.943] (II) Open ACPI successful (/var/run/acpid.socket)
[    26.943] (II) LoadModule: "extmod"
[    26.956] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    26.956] (II) Module extmod: vendor="X.Org Foundation"
[    26.956] 	compiled for 1.10.4, module version = 1.0.0
[    26.956] 	Module class: X.Org Server Extension
[    26.956] 	ABI class: X.Org Server Extension, version 5.0
[    26.956] (II) Loading extension MIT-SCREEN-SAVER
[    26.956] (II) Loading extension XFree86-VidModeExtension
[    26.956] (II) Loading extension XFree86-DGA
[    26.956] (II) Loading extension DPMS
[    26.956] (II) Loading extension XVideo
[    26.956] (II) Loading extension XVideo-MotionCompensation
[    26.957] (II) Loading extension X-Resource
[    26.957] (II) LoadModule: "dbe"
[    26.957] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    26.957] (II) Module dbe: vendor="X.Org Foundation"
[    26.957] 	compiled for 1.10.4, module version = 1.0.0
[    26.957] 	Module class: X.Org Server Extension
[    26.957] 	ABI class: X.Org Server Extension, version 5.0
[    26.957] (II) Loading extension DOUBLE-BUFFER
[    26.957] (II) LoadModule: "glx"
[    26.957] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    26.971] (II) Module glx: vendor="NVIDIA Corporation"
[    26.971] 	compiled for 4.0.2, module version = 1.0.0
[    26.971] 	Module class: X.Org Server Extension
[    26.971] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:14:51 PDT 2011
[    26.971] (II) Loading extension GLX
[    26.971] (II) LoadModule: "record"
[    26.971] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    26.971] (II) Module record: vendor="X.Org Foundation"
[    26.971] 	compiled for 1.10.4, module version = 1.13.0
[    26.971] 	Module class: X.Org Server Extension
[    26.971] 	ABI class: X.Org Server Extension, version 5.0
[    26.971] (II) Loading extension RECORD
[    26.971] (II) LoadModule: "dri"
[    26.972] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    26.972] (II) Module dri: vendor="X.Org Foundation"
[    26.972] 	compiled for 1.10.4, module version = 1.0.0
[    26.972] 	ABI class: X.Org Server Extension, version 5.0
[    26.972] (II) Loading extension XFree86-DRI
[    26.972] (II) LoadModule: "dri2"
[    26.972] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.972] (II) Module dri2: vendor="X.Org Foundation"
[    26.972] 	compiled for 1.10.4, module version = 1.2.0
[    26.972] 	ABI class: X.Org Server Extension, version 5.0
[    26.972] (II) Loading extension DRI2
[    26.972] (II) LoadModule: "nvidia"
[    26.972] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    26.972] (II) Module nvidia: vendor="NVIDIA Corporation"
[    26.972] 	compiled for 4.0.2, module version = 1.0.0
[    26.972] 	Module class: X.Org Video Driver
[    26.972] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:57:12 PDT 2011
[    26.972] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    26.972] (++) using VT number 7

[    26.973] (II) Loading sub module "fb"
[    26.973] (II) LoadModule: "fb"
[    26.973] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.973] (II) Module fb: vendor="X.Org Foundation"
[    26.973] 	compiled for 1.10.4, module version = 1.0.0
[    26.973] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.973] (II) Loading sub module "wfb"
[    26.973] (II) LoadModule: "wfb"
[    26.973] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    26.973] (II) Module wfb: vendor="X.Org Foundation"
[    26.973] 	compiled for 1.10.4, module version = 1.0.0
[    26.973] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.973] (II) Loading sub module "ramdac"
[    26.973] (II) LoadModule: "ramdac"
[    26.973] (II) Module "ramdac" already built-in
[    26.973] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    26.973] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    26.973] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.973] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    26.973] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    26.973] (==) NVIDIA(0): RGB weight 888
[    26.973] (==) NVIDIA(0): Default visual is TrueColor
[    26.973] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    26.973] (**) NVIDIA(0): Option "NoLogo" "1"
[    26.973] (**) NVIDIA(0): Option "ConnectedMonitor" "TV"
[    26.973] (**) NVIDIA(0): Option "TVStandard" "HD1080p"
[    26.973] (**) NVIDIA(0): Option "TVOutFormat" "HDMI"
[    26.973] (**) NVIDIA(0): Option "DPI" "100x100"
[    26.974] (**) NVIDIA(0): Unknown TVOutFormat value.  Known values are"AUTOSELECT",
[    26.974] (**) NVIDIA(0):     "COMPOSITE", "SVIDEO", "COMPONENT", "SCART"
[    26.974] (**) NVIDIA(0): TV Standard string: "HD1080p"
[    26.974] (**) NVIDIA(0): ConnectedMonitor string: "TV"
[    27.580] (WW) NVIDIA(GPU-0): Invalid ConnectedMonitor request; request was for 'TV-0', but
[    27.580] (WW) NVIDIA(GPU-0):     the valid display devices are 'CRT-0, CRT-1, DFP-0,
[    27.580] (WW) NVIDIA(GPU-0):     DFP-1'.
[    27.649] (II) NVIDIA(GPU-0): Display (Panasonic-TV (DFP-1)) does not support NVIDIA 3D
[    27.649] (II) NVIDIA(GPU-0):     Vision stereo.
[    27.650] (II) NVIDIA(0): NVIDIA GPU GeForce GT 430 (GF108) at PCI:1:0:0 (GPU-0)
[    27.650] (--) NVIDIA(0): Memory: 1048576 kBytes
[    27.650] (--) NVIDIA(0): VideoBIOS: 70.08.29.00.01
[    27.650] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    27.650] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    27.650] (--) NVIDIA(0): Connected display device(s) on GeForce GT 430 at PCI:1:0:0
[    27.650] (--) NVIDIA(0):     Panasonic-TV (DFP-1)
[    27.650] (--) NVIDIA(0): Panasonic-TV (DFP-1): 165.0 MHz maximum pixel clock
[    27.650] (--) NVIDIA(0): Panasonic-TV (DFP-1): Internal Single Link TMDS
[    27.655] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[    27.655] (**) NVIDIA(0):     enabled on all display devices.
[    27.671] (II) NVIDIA(0): Assigned Display Device: DFP-1
[    27.672] (==) NVIDIA(0): 
[    27.672] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    27.672] (==) NVIDIA(0):     will be used as the requested mode.
[    27.672] (==) NVIDIA(0): 
[    27.672] (II) NVIDIA(0): Validated modes:
[    27.672] (II) NVIDIA(0):     "nvidia-auto-select"
[    27.672] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 720
[    27.716] (**) NVIDIA(0): DPI set to (100, 100); computed from "DPI" X config option
[    27.716] (--) Depth 24 pixmap format is 32 bpp
[    27.716] (II) NVIDIA: Using 1024.00 MB of virtual memory for indirect memory
[    27.716] (II) NVIDIA:     access.
[    27.719] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    27.743] (II) Loading extension NV-GLX
[    27.814] (==) NVIDIA(0): Disabling shared memory pixmaps
[    27.814] (==) NVIDIA(0): Backing store disabled
[    27.814] (==) NVIDIA(0): Silken mouse enabled
[    27.814] (==) NVIDIA(0): DPMS enabled
[    27.814] (II) Loading extension NV-CONTROL
[    27.815] (II) Loading extension XINERAMA
[    27.815] (II) Loading sub module "dri2"
[    27.815] (II) LoadModule: "dri2"
[    27.815] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.815] (II) Module dri2: vendor="X.Org Foundation"
[    27.815] 	compiled for 1.10.4, module version = 1.2.0
[    27.815] 	ABI class: X.Org Server Extension, version 5.0
[    27.815] (II) NVIDIA(0): [DRI2] Setup complete
[    27.815] (==) RandR enabled
[    27.815] (II) Initializing built-in extension Generic Event Extension
[    27.815] (II) Initializing built-in extension SHAPE
[    27.815] (II) Initializing built-in extension MIT-SHM
[    27.815] (II) Initializing built-in extension XInputExtension
[    27.815] (II) Initializing built-in extension XTEST
[    27.815] (II) Initializing built-in extension BIG-REQUESTS
[    27.815] (II) Initializing built-in extension SYNC
[    27.815] (II) Initializing built-in extension XKEYBOARD
[    27.815] (II) Initializing built-in extension XC-MISC
[    27.815] (II) Initializing built-in extension SECURITY
[    27.815] (II) Initializing built-in extension XINERAMA
[    27.815] (II) Initializing built-in extension XFIXES
[    27.815] (II) Initializing built-in extension RENDER
[    27.815] (II) Initializing built-in extension RANDR
[    27.815] (II) Initializing built-in extension COMPOSITE
[    27.815] (II) Initializing built-in extension DAMAGE
[    27.815] (II) Initializing built-in extension GESTURE
[    27.817] (II) Initializing extension GLX
[    27.831] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.837] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    27.837] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.837] (II) LoadModule: "evdev"
[    27.838] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.838] (II) Module evdev: vendor="X.Org Foundation"
[    27.838] 	compiled for 1.10.2, module version = 2.6.0
[    27.838] 	Module class: X.Org XInput Driver
[    27.838] 	ABI class: X.Org XInput driver, version 12.3
[    27.838] (II) Using input driver 'evdev' for 'Power Button'
[    27.838] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.838] (**) Power Button: always reports core events
[    27.838] (**) Power Button: Device: "/dev/input/event1"
[    27.838] (--) Power Button: Found keys
[    27.838] (II) Power Button: Configuring as keyboard
[    27.838] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    27.838] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    27.838] (**) Option "xkb_rules" "evdev"
[    27.838] (**) Option "xkb_model" "pc105"
[    27.838] (**) Option "xkb_layout" "us"
[    27.841] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    27.841] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.841] (II) Using input driver 'evdev' for 'Power Button'
[    27.841] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.841] (**) Power Button: always reports core events
[    27.841] (**) Power Button: Device: "/dev/input/event0"
[    27.841] (--) Power Button: Found keys
[    27.841] (II) Power Button: Configuring as keyboard
[    27.841] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    27.841] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    27.841] (**) Option "xkb_rules" "evdev"
[    27.841] (**) Option "xkb_model" "pc105"
[    27.841] (**) Option "xkb_layout" "us"
[    27.842] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event10)
[    27.842] (II) No input driver/identifier specified (ignoring)
[    27.842] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event7)
[    27.842] (II) No input driver/identifier specified (ignoring)
[    27.842] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event8)
[    27.842] (II) No input driver/identifier specified (ignoring)
[    27.843] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event9)
[    27.843] (II) No input driver/identifier specified (ignoring)
[    27.844] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/event2)
[    27.844] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev keyboard catchall"
[    27.844] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v8.0'
[    27.844] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.844] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: always reports core events
[    27.844] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Device: "/dev/input/event2"
[    27.844] (--) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found keys
[    27.844] (II) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Configuring as keyboard
[    27.844] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input2/event2"
[    27.844] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v8.0" (type: KEYBOARD)
[    27.844] (**) Option "xkb_rules" "evdev"
[    27.844] (**) Option "xkb_model" "pc105"
[    27.844] (**) Option "xkb_layout" "us"
[    27.844] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/event3)
[    27.844] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev pointer catchall"
[    27.844] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev keyboard catchall"
[    27.844] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v8.0'
[    27.844] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.844] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: always reports core events
[    27.844] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Device: "/dev/input/event3"
[    27.844] (--) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found 9 mouse buttons
[    27.844] (--) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found scroll wheel(s)
[    27.844] (--) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found relative axes
[    27.844] (--) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found x and y relative axes
[    27.844] (--) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found absolute axes
[    27.844] (II) evdev-grail: failed to open grail, no gesture support
[    27.844] (--) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found keys
[    27.844] (II) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Configuring as mouse
[    27.844] (II) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Configuring as keyboard
[    27.844] (II) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Adding scrollwheel support
[    27.844] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: YAxisMapping: buttons 4 and 5
[    27.844] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.845] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.1/input/input3/event3"
[    27.845] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v8.0" (type: KEYBOARD)
[    27.845] (**) Option "xkb_rules" "evdev"
[    27.845] (**) Option "xkb_model" "pc105"
[    27.845] (**) Option "xkb_layout" "us"
[    27.845] (II) Microsoft Microsoft® 2.4GHz Transceiver v8.0: initialized for relative axes.
[    27.845] (WW) Microsoft Microsoft® 2.4GHz Transceiver v8.0: ignoring absolute axes.
[    27.845] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) keeping acceleration scheme 1
[    27.845] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration profile 0
[    27.845] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration factor: 2.000
[    27.845] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration threshold: 4
[    27.845] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/mouse0)
[    27.845] (II) No input driver/identifier specified (ignoring)
[    27.845] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/event4)
[    27.845] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev keyboard catchall"
[    27.845] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v8.0'
[    27.845] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.846] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: always reports core events
[    27.846] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Device: "/dev/input/event4"
[    27.846] (--) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found 1 mouse buttons
[    27.846] (--) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found scroll wheel(s)
[    27.846] (--) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found relative axes
[    27.846] (--) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found absolute axes
[    27.846] (--) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found x and y absolute axes
[    27.846] (--) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found keys
[    27.846] (II) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Configuring as mouse
[    27.846] (II) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Configuring as keyboard
[    27.846] (II) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Adding scrollwheel support
[    27.846] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: YAxisMapping: buttons 4 and 5
[    27.846] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.846] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.2/input/input4/event4"
[    27.846] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v8.0" (type: KEYBOARD)
[    27.846] (**) Option "xkb_rules" "evdev"
[    27.846] (**) Option "xkb_model" "pc105"
[    27.846] (**) Option "xkb_layout" "us"
[    27.846] (EE) Microsoft Microsoft® 2.4GHz Transceiver v8.0: failed to initialize for relative axes.
[    27.848] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
[    27.848] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect
[    27.848] (II) Microsoft Microsoft® 2.4GHz Transceiver v8.0: initialized for absolute axes.
[    27.848] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) keeping acceleration scheme 1
[    27.848] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration profile 0
[    27.848] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration factor: 2.000
[    27.848] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration threshold: 4
[    27.848] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/js0)
[    27.848] (II) No input driver/identifier specified (ignoring)
[    27.849] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event5)
[    27.849] (II) No input driver/identifier specified (ignoring)
[    27.852] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event6)
[    27.852] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    27.852] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[    27.852] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.852] (**) Eee PC WMI hotkeys: always reports core events
[    27.852] (**) Eee PC WMI hotkeys: Device: "/dev/input/event6"
[    27.852] (--) Eee PC WMI hotkeys: Found keys
[    27.852] (II) Eee PC WMI hotkeys: Configuring as keyboard
[    27.852] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input6/event6"
[    27.852] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD)
[    27.852] (**) Option "xkb_rules" "evdev"
[    27.852] (**) Option "xkb_model" "pc105"
[    27.852] (**) Option "xkb_layout" "us"
```

---

### Post by newlinux on 2012-01-23
I'm assuming the 1024x768 you mentioned above is the native resolution of your TV (which if it is widescreen means it is probably using rectangular pixels). So then your TV is technically 768p. Whether you send it 1080i or 720p it will still use the native resolution of your set (the TV will scale the picture to it native resolution). So you not seeing much of a difference is not surprising. Most TV's are optimize to scale 720p and 1080i/p inputs to their respective native resolutions (Since that what all HD set top boxes, Blu-ray players, etc will send). You are probably fine sending either 1080i or 720p for video. The only thing that might be worth considering is sending it's native resolution, but for video that would mean the scaling is being done by your computer hardware - Your TV might be better at scaling and may not even support it's native resolution over HDMI.

---

