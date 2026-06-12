---
title: "Unable to get Nvidia settings to persist after reboot"
date: 2009-12-29
forum: Multimedia Software
---

### Post by AgingKeeper on 2009-12-29
I recently installed Ubuntu (9.10) on an old Dell Dimension 4800 with a Nvidia GeForce FX 5200 video card.  Everything appears to be be working properly with one exception. I can't get my Nvidia settings to persist after I reboot.  

I have found numerous posts indicating that others have experie3nced these problems as well but none of the solutions I have implemented has worked so far.

Being new to Linux I am not certain if it is pilot error (more than likely)  or if there is something else going on that I simply haven't noticed.

I have created an xorg.conf file (/etc/X11/xorg.conf)
I created a .nvidia-settings-rc file (~/,nvidia-settings-rc)
I created a .xinitrc file (~/.xinitrc)
I have symobolic link between the .xinitrc file and .xsession (also tried .xsessionrc)
(~/home/.xsession->.xinitrc)

With the video settings reverting to 720x450 every time I reboot I don't believe the nvida-settings command in my .xinitrc (or .xsession) file are actually being executed or there is an error of some sort. Though I can't find the error in my .xsession-errors file.
I am including copies of these files as well.

Help would be much appreciated-my forehead is getting flat from the pounding on my desk ( ](*,) )!

----------------- xorg.conf --------------------
Section "Screen"
    Identifier    "Configured Screen Device"
    DefaultDepth    24
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
EndSection
----------------- xorg.conf --------------------

------------------------.nvidia-settings-rc-------------
#
# /home/chip/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Tue Dec 29 14:37:58 2009
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000

# Attributes:

0/CursorShadow=0
0/CursorShadowAlpha=64
0/CursorShadowRed=0
0/CursorShadowGreen=0
0/CursorShadowBlue=0
0/CursorShadowXOffset=4
0/CursorShadowYOffset=2
0/SyncToVBlank=0
0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/GammaCorrectedAALines=0
0/AllowFlipping=1
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
0/RedBrightness=0.000000
0/GreenBrightness=0.000000
0/BlueBrightness=0.000000
0/RedContrast=0.000000
0/GreenContrast=0.000000
0/BlueContrast=0.000000
0/RedGamma=1.000000
0/GreenGamma=1.000000
0/BlueGamma=1.000000
0/DigitalVibrance[DFP-0]=0
0/ImageSharpening[DFP-0]=0
0/GPUScaling[DFP-0]=65537
0/XVideoTextureSyncToVBlank=1
0/XVideoBlitterSyncToVBlank=0
0/XVideoSyncToDisplay=65536
------------------------.nvidia-settings-rc-------------

---------------------.xinitrc------------------
#!/usr/bin/env bash
echo "$0: Running .xinitrc" &
/usr/bin nvidia-settings --load-config-only &
gnome-terminal &
exec gnome-session &
---------------------.xinitrc------------------

------------------.xsession-errors-------------
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

GNOME_KEYRING_SOCKET=/tmp/keyring-ctHgCh/socket
SSH_AUTH_SOCK=/tmp/keyring-ctHgCh/socket.ssh

(gnome-settings-daemon:1601): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Unable to find a synaptics device.
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (720x450) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 

(nautilus:1697): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (gnome-panel:1696): DEBUG: Adding applet 0.
** (gnome-panel:1696): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:1696): DEBUG: Adding applet 1.
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3

(polkit-gnome-authentication-agent-1:1717): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1717): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** (gnome-panel:1696): DEBUG: Adding applet 2.
** (gnome-panel:1696): DEBUG: Adding applet 3.
** (gnome-panel:1696): DEBUG: Adding applet 4.
Initializing nautilus-gdu extension

** (nautilus:1697): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1697): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1697): WARNING **: No marshaller for signature of signal 'ShareCreateError'
** (gnome-panel:1696): DEBUG: Adding applet 5.
** (gnome-panel:1696): DEBUG: Adding applet 6.
** (gnome-panel:1696): DEBUG: Adding applet 7.
** (gnome-panel:1696): DEBUG: Adding applet 8.
** (gnome-panel:1696): DEBUG: Adding applet 9.
Starting gtk-window-decorator
** (gnome-panel:1696): DEBUG: Adding applet 10.
** (gnome-panel:1696): DEBUG: Adding applet 11.
** (gnome-panel:1696): DEBUG: Adding applet 12.

(gnome-panel:1696): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
I/O warning : failed to load external entity "/home/chip/.compiz/session/10751237eb7cbcac53126212281434884900000015340022"

(gnome-display-properties:1779): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:1779): Gtk-WARNING **: No object called: 
evolution-alarm-notify-Message: Setting timeout for 8353 1262131200 1262122847
evolution-alarm-notify-Message:  Tue Dec 29 17:00:00 2009

evolution-alarm-notify-Message:  Tue Dec 29 14:40:47 2009


(firefox:1843): GLib-WARNING **: g_set_prgname() called multiple times

---

### Post by joan_gvillaraco on 2009-12-30
Hey!, just to say you that your are not alone. I've gotten the same problem and I'm working on it.

I'll write everything if I get it solved.

Regards,

Joan.

---

### Post by atropa on 2009-12-30
Hi

Back up your xorg.conf and see what happens if you change the Screen Section to

----------------- xorg.conf --------------------
Section "Screen"
Identifier "Configured Screen Device"
Device "Configured Video Device"
Monitor "Monitor0"
DefaultDepth 24
    SubSection     "Display"
        Depth       24
        Modes    "1400x1050" "1280x1024" "1024x768" [supply your own]
    EndSubSection
EndSection

----------------- xorg.conf --------------------

Somewhere in your xorg.conf you should also have a section "Monitor" like:

Section "Monitor"
    Identifier  "Monitor0" #<-- This must match identifier in "Screen"
EndSection

---

### Post by Linuxforall on 2009-12-30
Have you tried gksudo nvidia-settings and then making your selections and hit the quit button. For resolution change to stick, just click on save to X.

---

### Post by joan_gvillaraco on 2009-12-30
Hi AgingKeeper,

I think we are falling in bug #384439 ([https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/384439](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/384439)), I have add me as a people affected and wrote some info as joankk user.

Regards,

Joan.[U]
[/U]

---

### Post by AgingKeeper on 2009-12-30
All - thanks for the replies!! 

**Linuxforall** - Yes I have tried using gksudo nvidia-settings and saving the settings and configruation numerous times with no luck.

**atropa** - I attempted what you suggested - but no luck. I did find that it is being read because I had accidentally left your bracketed comment in when I copied, pasted, tweaked your suggestion into the xorg.conf file and the system didn't like it so it booted into a non-graphical mode. Easy enough to remedy but the end result is the same. 

**Joan - **I suspect you may be on to something. I had looked for these error statements in the forums and found the bug you referenced. Being so new to Linux I wasn't quite sure what to make of the bug report but intend to look at it in more detail. In the .xsession-errors file I originally included the resolution called out 8 lines below it is 720x450 *(and nowhere in my settings is 720x450 called out!)*. So somewhere between the error and this description of resolution the error is occurring. In looking at these 8 lines I noticed the Xorg.0.log file being referenced so I have pasted it below.  The second to line is of interest because it calls out the 720x450 resolution. Not the 1600x1024 I included using the xorg.conf suggested by **atropa**. 

Does anyone know what is being executed and is spitting out the lines between the error statement ((gnome-settings-daemon:1601): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed) and the statement (Checking screen 1Comparing resolution (720x450) to maximum 3D texture size (4096): Passed)?? Is it the gnome-settings-daemon??  

----------------Xorg.0.log----------------

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux chip-Dell-Linux 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=592fa688-317d-497f-972b-c34fd2b382af ro vga=792 splash quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 30 10:24:14 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Configured Screen Device" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Configured Video Device"
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
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0322:10de:01b9 nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.20  Thu Jun 25 19:49:59 PDT 2009
(II) Loading extension GLX
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
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  173.14.20  Thu Jun 25 19:28:52 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
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
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 (NV34) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.22.bc
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     ViewSonic VX2235wm-3 (DFP-0)
(--) NVIDIA(0): ViewSonic VX2235wm-3 (DFP-0): 135.0 MHz maximum pixel clock
(--) NVIDIA(0): ViewSonic VX2235wm-3 (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1024"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1024
(--) NVIDIA(0): DPI set to (86, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "1600x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "terminate:ctrl_alt_bksp"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "terminate:ctrl_alt_bksp"
(II) config/hal: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event5"
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found 1 mouse buttons
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found scroll wheel(s)
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found x and y absolute axes
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as mouse
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "terminate:ctrl_alt_bksp"
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) set acceleration profile 0
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: initialized for absolute axes.
(II) config/hal: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event4"
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found 9 mouse buttons
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found x and y relative axes
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found scroll wheel(s)
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as mouse
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "terminate:ctrl_alt_bksp"
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) set acceleration profile 0
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: initialized for relative axes.
(II) config/hal: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
(**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event3"
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
(II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "terminate:ctrl_alt_bksp"
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
(II) NVIDIA(0): Setting mode "720x450"
(II) NVIDIA(0): Setting mode "1600x1024"
-----------------------Xorg.0.log-------------------------------

---

### Post by HappyFeet on 2009-12-30
Try:
```
sudo rm /etc/X11/xorg.conf
```
then restart nvidia-settings with:
```
gksudo nvidia-settings
```
then make all the changes you need, apply, then save configuration, and it will see you don't have a xorg.conf file. A new window will open. Hit the button lableled **show output**, and copy the file. Leave nvidia-settings open, and open a new terminal. Do:
```
sudo touch /etc/X11/xorg.conf && sudo gedit /etc/X11/xorg.conf
```
then paste what you copied from nvidia-settings. Save and reboot.

---

### Post by AgingKeeper on 2009-12-30
**HappyFeet**- Thanks I had seen your previous posts suggesting this and it had no effect - obviously my xorg.conf didn't reflect this because I changed back to an earlier version not being quite sure of what I should be using at the time.  I just repeated the process again & I do intend to leave it in this form.

I have read that I need to invoke nvidia-settings in my .xinitrc (symobolically linked to .xsession) but for some reason the high-res settings aren't being applied.

---

### Post by AgingKeeper on 2009-12-30
One other item I just noticed. After rebooting I went to System->Administration->Hardware Drivers and it stated that the nvida driver was active. When I go to System->Preferences->Display an information box appears asking "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" Not sure if this is important or not.

---

### Post by bchurchwell on 2009-12-31
From this page:

[http://linuxtipsandtricks.com/ubuntu/ubuntu-910-nvidia-monitor-settings-dont-save/]("http://linuxtipsandtricks.com/ubuntu/ubuntu-910-nvidia-monitor-settings-dont-save/")

Do:

```
sudo nvidia-xconfig
```

after that
```

gksudo nvidia-settings
```

Worked for me.

---

### Post by mc4man on 2009-12-31
> Do:

Code:

sudo nvidia-xconfig

after that
Code:

gksudo nvidia-settings



That has also always worked here ( the first command only needed to be done once.
That makes any settings that are saved to xorg remain persistent.

Settings that are only saved to .nvidia-settings-rc aren't persistent. (color corrections, gamma, ect.

While i'm sure there is a more 'proper' way to do so, ( suggestions are welcome) I simply made a small script and added to my start up.

```
#!/bin/bash
 nvidia-settings -l &
```

---

### Post by AgingKeeper on 2009-12-31
mc4man & bchurchwell

Thanks for the help but I've attempted this before as well.  After HappyFeet's suggestions I have built up a pretty good xorg.conf file that is in fact staying persistent.  The problem is that for some reason the settings are getting clobbered or adjusted on startup.  I think the error mentioned by Joan in the .xsession-errors file is where the settings are being changed.  Not sure how to prove that but I can't come up with anything else to do.

---

