---
title: "Applications crash X with Nvidia drivers"
date: 2011-02-15
forum: Multimedia Software
---

### Post by audeojude on 2011-02-15
I have never had so many problems getting a Nvidia card working correctly.

I have a ION PCIe1X card that I am running two monitors in twin view with. Ubuntu runs fine. However if I start skype or virtualbox it will crash X. I have disable twinview and used xinerama.. same thing. I have set the monitors to be on separate screens, same thing. If I use the onboard video card.. it works fine but I can't run both monitors.

If I install the Xorg server from Lucid it will work fine with the Nvidia ION card. However it is a major pain using the xserver from lucid on a current version of Ubuntu. I have used both the proprietary drivers provided through Ubuntu and used the Nvidia drivers from Nvidia's website. same results.

Also any video I stream off of youtube or any of the tv channels website in full screen is choppy. It didn't used to be that way before upgrading. I am running an intel 2.66ghz quad core system with 8 gigs of ram and running the OS from a 100gig PCIe4x nand flash card that has about 600megs a second read and write IO, so system speed isn't an issue.

I am at my wits end. I have read days worth of posts on what looks like this issue but nothing seems to fix it other than rolling my Xserver back to a version from lucid.

I would appreciate any help I can get if someone has seen this and found a fix.

thanks
Scott

---

### Post by lidex on 2011-02-15
Is this on maverick?

---

### Post by audeojude on 2011-02-16
Yes it's on maverick 10.10.. fully updated as of yesterday.
Since this problem started I have moved up two versions of the kernel through normal updates and used about 5 different versions of the proprietary nvidia drivers. both the ones packaged through ubuntu and about 3 different ones from the nvidia website. Symptoms are as described above for all of them. The only thing that changes the behaviour is rolling the xorg server back to an old version from Lucid.

Every thing else works... I have full 3d acceleration with smooth multiple monitor support using the nvidia utility to adjust settings. But if I try running skype X crashes about 2 seconds after starting. The exact same thing happens if I start Virtualbox. :( X crashes and then restarts leaving me at the login. I can then go back into a desktop environment no issues until I try and start skype or virtualbox again. I am sure there are other apps that would cause it but I'm not sure what those two programs have in common that is affecting X.
scott

---

### Post by audeojude on 2011-02-16
Just a update. I have run virtualbox in headless mode and attached to it with a terminal services client to access my Virtualized system. This is working fine so the issue isn't in the core virtualbox application it is in the graphical management interface application for Virtual box and how it interacts with X. 

So as far as I can tell something changed in X between the versions used in Lucid and the current versions that is causing this behaviour.

---

### Post by lidex on 2011-02-16
Please then do file a bug report. Why do we think it has to do with nvidia driver though? Have you tried noveau driver? Check your log files, dmesg, etc. after x crashes to get some idea of the cause.

---

### Post by audeojude on 2011-02-18
There were no log enteries during this time period in dmesg
/var/log/messages log entries after I cause it to crash by opening skype
It basically is just seeing X restarting and detecting the hdmi monitor.

```
Feb 18 07:49:28 ORCA kernel: [230946.842802] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
Feb 18 07:49:28 ORCA kernel: [230947.056317] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=0
Feb 18 07:49:28 ORCA kernel: [230947.233975] HDMI hot plug event: Pin=5 Presence_Detect=1 ELD_Valid=1
Feb 18 07:49:30 ORCA kernel: [230949.222515] HDMI: detected monitor VK246
Feb 18 07:49:30 ORCA kernel: [230949.222517]        at connection type HDMI
Feb 18 07:49:30 ORCA kernel: [230949.222521] HDMI: available speakers: FL/FR
Feb 18 07:49:30 ORCA kernel: [230949.222527] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 
Feb 18 07:49:32 ORCA kernel: [230951.160025] HDMI: detected monitor VK246
Feb 18 07:49:32 ORCA kernel: [230951.160028]        at connection type HDMI
Feb 18 07:49:32 ORCA kernel: [230951.160032] HDMI: available speakers: FL/FR
Feb 18 07:49:32 ORCA kernel: [230951.160038] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 
Feb 18 07:49:35 ORCA pulseaudio[25192]: pid.c: Stale PID file, overwriting.
```



here is the Xorg log but I don't see anything showing it crashing.. just it coming back up.. I crashed it twice in this time period.


```
[230946.139] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[230946.139] X Protocol Version 11, Revision 0
[230946.139] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[230946.139] Current Operating System: Linux ORCA 2.6.35-27-generic #47-Ubuntu SMP Fri Feb 11 22:52:49 UTC 2011 x86_64
[230946.139] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-27-generic root=UUID=51ccc5bb-4016-4a2e-a901-8043c3337dfd ro quiet splash
[230946.139] Build Date: 09 January 2011  12:14:27PM
[230946.139] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[230946.139] Current version of pixman: 0.18.4
[230946.139] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[230946.139] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[230946.139] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 18 07:49:27 2011
[230946.139] (==) Using config file: "/etc/X11/xorg.conf"
[230946.139] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[230946.139] (==) ServerLayout "Layout0"
[230946.139] (**) |-->Screen "Screen0" (0)
[230946.139] (**) |   |-->Monitor "Monitor0"
[230946.139] (**) |   |-->Device "Device0"
[230946.139] (**) |-->Input Device "Keyboard0"
[230946.139] (**) |-->Input Device "Mouse0"
[230946.139] (**) Option "Xinerama" "0"
[230946.139] (==) Automatically adding devices
[230946.139] (==) Automatically enabling devices
[230946.139] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[230946.139] 	Entry deleted from font path.
[230946.139] (**) FontPath set to:
	unix/:7100,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[230946.139] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[230946.139] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[230946.139] (WW) Disabling Keyboard0
[230946.139] (WW) Disabling Mouse0
[230946.140] (II) Loader magic: 0x7d17a0
[230946.140] (II) Module ABI versions:
[230946.140] 	X.Org ANSI C Emulation: 0.4
[230946.140] 	X.Org Video Driver: 8.0
[230946.140] 	X.Org XInput driver : 11.0
[230946.140] 	X.Org Server Extension : 4.0
[230946.141] (--) PCI: (0:3:0:0) 14f1:8880:0070:7801 rev 15, Mem @ 0xfce00000/2097152
[230946.141] (--) PCI:*(0:4:0:0) 10de:0a64:19da:2117 rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
[230946.141] (II) Open ACPI successful (/var/run/acpid.socket)
[230946.141] (II) LoadModule: "extmod"
[230946.141] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[230946.141] (II) Module extmod: vendor="X.Org Foundation"
[230946.141] 	compiled for 1.9.0, module version = 1.0.0
[230946.141] 	Module class: X.Org Server Extension
[230946.141] 	ABI class: X.Org Server Extension, version 4.0
[230946.141] (II) Loading extension MIT-SCREEN-SAVER
[230946.141] (II) Loading extension XFree86-VidModeExtension
[230946.141] (II) Loading extension XFree86-DGA
[230946.141] (II) Loading extension DPMS
[230946.141] (II) Loading extension XVideo
[230946.141] (II) Loading extension XVideo-MotionCompensation
[230946.141] (II) Loading extension X-Resource
[230946.141] (II) LoadModule: "dbe"
[230946.141] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[230946.141] (II) Module dbe: vendor="X.Org Foundation"
[230946.141] 	compiled for 1.9.0, module version = 1.0.0
[230946.141] 	Module class: X.Org Server Extension
[230946.141] 	ABI class: X.Org Server Extension, version 4.0
[230946.141] (II) Loading extension DOUBLE-BUFFER
[230946.141] (II) LoadModule: "glx"
[230946.141] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[230946.151] (II) Module glx: vendor="NVIDIA Corporation"
[230946.151] 	compiled for 4.0.2, module version = 1.0.0
[230946.151] 	Module class: X.Org Server Extension
[230946.151] (II) NVIDIA GLX Module  270.18  Tue Jan 18 22:03:05 PST 2011
[230946.151] (II) Loading extension GLX
[230946.151] (II) LoadModule: "record"
[230946.152] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[230946.152] (II) Module record: vendor="X.Org Foundation"
[230946.152] 	compiled for 1.9.0, module version = 1.13.0
[230946.152] 	Module class: X.Org Server Extension
[230946.152] 	ABI class: X.Org Server Extension, version 4.0
[230946.152] (II) Loading extension RECORD
[230946.152] (II) LoadModule: "dri"
[230946.152] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[230946.152] (II) Module dri: vendor="X.Org Foundation"
[230946.152] 	compiled for 1.9.0, module version = 1.0.0
[230946.152] 	ABI class: X.Org Server Extension, version 4.0
[230946.152] (II) Loading extension XFree86-DRI
[230946.152] (II) LoadModule: "dri2"
[230946.152] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[230946.152] (II) Module dri2: vendor="X.Org Foundation"
[230946.152] 	compiled for 1.9.0, module version = 1.2.0
[230946.152] 	ABI class: X.Org Server Extension, version 4.0
[230946.152] (II) Loading extension DRI2
[230946.152] (II) LoadModule: "nvidia"
[230946.152] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[230946.153] (II) Module nvidia: vendor="NVIDIA Corporation"
[230946.153] 	compiled for 4.0.2, module version = 1.0.0
[230946.153] 	Module class: X.Org Video Driver
[230946.153] (II) NVIDIA dlloader X Driver  270.18  Tue Jan 18 21:47:56 PST 2011
[230946.153] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[230946.153] (--) using VT number 7

[230946.176] (II) Loading sub module "fb"
[230946.176] (II) LoadModule: "fb"
[230946.176] (II) Loading /usr/lib/xorg/modules/libfb.so
[230946.176] (II) Module fb: vendor="X.Org Foundation"
[230946.176] 	compiled for 1.9.0, module version = 1.0.0
[230946.176] 	ABI class: X.Org ANSI C Emulation, version 0.4
[230946.176] (II) Loading sub module "wfb"
[230946.176] (II) LoadModule: "wfb"
[230946.176] (II) Loading /usr/lib/xorg/modules/libwfb.so
[230946.176] (II) Module wfb: vendor="X.Org Foundation"
[230946.176] 	compiled for 1.9.0, module version = 1.0.0
[230946.176] 	ABI class: X.Org ANSI C Emulation, version 0.4
[230946.176] (II) Loading sub module "ramdac"
[230946.176] (II) LoadModule: "ramdac"
[230946.176] (II) Module "ramdac" already built-in
[230946.176] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[230946.176] (==) NVIDIA(0): RGB weight 888
[230946.176] (==) NVIDIA(0): Default visual is TrueColor
[230946.176] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[230946.176] (**) NVIDIA(0): Option "TwinView" "1"
[230946.176] (**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: nvidia-auto-select +0+0"
[230946.176] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-1"
[230946.176] (**) NVIDIA(0): Enabling RENDER acceleration
[230946.176] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[230946.176] (II) NVIDIA(0):     enabled.
[230946.809] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[230946.809] (II) NVIDIA(GPU-0):     3D Vision stereo.
[230946.842] (II) NVIDIA(GPU-0): Display (Ancor Communications Inc VK246 (DFP-1)) does not
[230946.842] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[230946.844] (II) NVIDIA(0): NVIDIA GPU ION (GT218) at PCI:4:0:0 (GPU-0)
[230946.844] (--) NVIDIA(0): Memory: 524288 kBytes
[230946.844] (--) NVIDIA(0): VideoBIOS: 70.18.2e.00.00
[230946.844] (II) NVIDIA(0): Detected PCI Express Link width: 1X
[230946.844] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[230946.844] (--) NVIDIA(0): Connected display device(s) on ION at PCI:4:0:0
[230946.844] (--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
[230946.845] (--) NVIDIA(0):     Ancor Communications Inc VK246 (DFP-1)
[230946.845] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[230946.845] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[230946.845] (--) NVIDIA(0): Ancor Communications Inc VK246 (DFP-1): 165.0 MHz maximum
[230946.845] (--) NVIDIA(0):     pixel clock
[230946.845] (--) NVIDIA(0): Ancor Communications Inc VK246 (DFP-1): Internal Single Link
[230946.845] (--) NVIDIA(0):     TMDS
[230946.847] (**) NVIDIA(0): TwinView enabled
[230946.847] (II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-1
[230946.928] (WW) NVIDIA(0): The EDID for Ancor Communications Inc VK246 (DFP-1)
[230946.928] (WW) NVIDIA(0):     contradicts itself: mode "720x576" is specified in the
[230946.928] (WW) NVIDIA(0):     EDID; however, the EDID's valid VertRefresh range
[230946.928] (WW) NVIDIA(0):     (56.000-76.000 Hz) would exclude this mode's VertRefresh
[230946.928] (WW) NVIDIA(0):     (50.0 Hz); ignoring VertRefresh check for mode "720x576".
[230946.928] (WW) NVIDIA(0): The EDID for Ancor Communications Inc VK246 (DFP-1)
[230946.928] (WW) NVIDIA(0):     contradicts itself: mode "720x576" is specified in the
[230946.928] (WW) NVIDIA(0):     EDID; however, the EDID's valid VertRefresh range
[230946.928] (WW) NVIDIA(0):     (56.000-76.000 Hz) would exclude this mode's VertRefresh
[230946.928] (WW) NVIDIA(0):     (50.0 Hz); ignoring VertRefresh check for mode "720x576".
[230946.928] (WW) NVIDIA(0): The EDID for Ancor Communications Inc VK246 (DFP-1)
[230946.928] (WW) NVIDIA(0):     contradicts itself: mode "1280x720" is specified in the
[230946.928] (WW) NVIDIA(0):     EDID; however, the EDID's valid VertRefresh range
[230946.928] (WW) NVIDIA(0):     (56.000-76.000 Hz) would exclude this mode's VertRefresh
[230946.928] (WW) NVIDIA(0):     (50.0 Hz); ignoring VertRefresh check for mode
[230946.928] (WW) NVIDIA(0):     "1280x720".
[230946.928] (WW) NVIDIA(0): The EDID for Ancor Communications Inc VK246 (DFP-1)
[230946.928] (WW) NVIDIA(0):     contradicts itself: mode "1920x1080" is specified in the
[230946.928] (WW) NVIDIA(0):     EDID; however, the EDID's valid HorizSync range
[230946.928] (WW) NVIDIA(0):     (31.000-83.000 kHz) would exclude this mode's HorizSync
[230946.928] (WW) NVIDIA(0):     (28.1 kHz); ignoring HorizSync check for mode
[230946.928] (WW) NVIDIA(0):     "1920x1080".
[230946.928] (WW) NVIDIA(0): The EDID for Ancor Communications Inc VK246 (DFP-1)
[230946.928] (WW) NVIDIA(0):     contradicts itself: mode "1920x1080" is specified in the
[230946.928] (WW) NVIDIA(0):     EDID; however, the EDID's valid VertRefresh range
[230946.928] (WW) NVIDIA(0):     (56.000-76.000 Hz) would exclude this mode's VertRefresh
[230946.928] (WW) NVIDIA(0):     (50.0 Hz); ignoring VertRefresh check for mode
[230946.928] (WW) NVIDIA(0):     "1920x1080".
[230946.928] (WW) NVIDIA(0): The EDID for Ancor Communications Inc VK246 (DFP-1)
[230946.928] (WW) NVIDIA(0):     contradicts itself: mode "1920x1080" is specified in the
[230946.928] (WW) NVIDIA(0):     EDID; however, the EDID's valid VertRefresh range
[230946.928] (WW) NVIDIA(0):     (56.000-76.000 Hz) would exclude this mode's VertRefresh
[230946.928] (WW) NVIDIA(0):     (50.0 Hz); ignoring VertRefresh check for mode
[230946.928] (WW) NVIDIA(0):     "1920x1080".
[230946.934] (WW) NVIDIA(0): The EDID for Ancor Communications Inc VK246 (DFP-1)
[230946.934] (WW) NVIDIA(0):     contradicts itself: mode "720x576" is specified in the
[230946.934] (WW) NVIDIA(0):     EDID; however, the EDID's valid VertRefresh range
[230946.934] (WW) NVIDIA(0):     (56.000-76.000 Hz) would exclude this mode's VertRefresh
[230946.934] (WW) NVIDIA(0):     (50.0 Hz); ignoring VertRefresh check for mode "720x576".
[230946.935] (WW) NVIDIA(0): The EDID for Ancor Communications Inc VK246 (DFP-1)
[230946.935] (WW) NVIDIA(0):     contradicts itself: mode "720x576" is specified in the
[230946.935] (WW) NVIDIA(0):     EDID; however, the EDID's valid VertRefresh range
[230946.935] (WW) NVIDIA(0):     (56.000-76.000 Hz) would exclude this mode's VertRefresh
[230946.935] (WW) NVIDIA(0):     (50.0 Hz); ignoring VertRefresh check for mode "720x576".
[230946.936] (WW) NVIDIA(0): The EDID for Ancor Communications Inc VK246 (DFP-1)
[230946.936] (WW) NVIDIA(0):     contradicts itself: mode "1280x720" is specified in the
[230946.936] (WW) NVIDIA(0):     EDID; however, the EDID's valid VertRefresh range
[230946.936] (WW) NVIDIA(0):     (56.000-76.000 Hz) would exclude this mode's VertRefresh
[230946.936] (WW) NVIDIA(0):     (50.0 Hz); ignoring VertRefresh check for mode
[230946.936] (WW) NVIDIA(0):     "1280x720".
[230946.937] (WW) NVIDIA(0): The EDID for Ancor Communications Inc VK246 (DFP-1)
[230946.937] (WW) NVIDIA(0):     contradicts itself: mode "1920x1080" is specified in the
[230946.937] (WW) NVIDIA(0):     EDID; however, the EDID's valid HorizSync range
[230946.937] (WW) NVIDIA(0):     (31.000-83.000 kHz) would exclude this mode's HorizSync
[230946.937] (WW) NVIDIA(0):     (28.1 kHz); ignoring HorizSync check for mode
[230946.937] (WW) NVIDIA(0):     "1920x1080".
[230946.937] (WW) NVIDIA(0): The EDID for Ancor Communications Inc VK246 (DFP-1)
[230946.937] (WW) NVIDIA(0):     contradicts itself: mode "1920x1080" is specified in the
[230946.937] (WW) NVIDIA(0):     EDID; however, the EDID's valid VertRefresh range
[230946.937] (WW) NVIDIA(0):     (56.000-76.000 Hz) would exclude this mode's VertRefresh
[230946.937] (WW) NVIDIA(0):     (50.0 Hz); ignoring VertRefresh check for mode
[230946.937] (WW) NVIDIA(0):     "1920x1080".
[230946.937] (WW) NVIDIA(0): The EDID for Ancor Communications Inc VK246 (DFP-1)
[230946.937] (WW) NVIDIA(0):     contradicts itself: mode "1920x1080" is specified in the
[230946.937] (WW) NVIDIA(0):     EDID; however, the EDID's valid VertRefresh range
[230946.937] (WW) NVIDIA(0):     (56.000-76.000 Hz) would exclude this mode's VertRefresh
[230946.937] (WW) NVIDIA(0):     (50.0 Hz); ignoring VertRefresh check for mode
[230946.937] (WW) NVIDIA(0):     "1920x1080".
[230947.024] (II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
[230947.024] (II) NVIDIA(0): Validated modes:
[230947.024] (II) NVIDIA(0):    
[230947.024] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1920+0,DFP-1:nvidia-auto-select+0+0"
[230947.024] (II) NVIDIA(0): Virtual screen size determined to be 3600 x 1080
[230947.046] (--) NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
[230947.046] (--) NVIDIA(0):     option
[230947.046] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[230947.046] (--) Depth 24 pixmap format is 32 bpp
[230947.046] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[230947.047] (II) NVIDIA(0): Initialized GPU GART.
[230947.055] (II) NVIDIA(0): Setting mode
[230947.056] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1920+0,DFP-1:nvidia-auto-select+0+0"
[230947.269] (II) Loading extension NV-GLX
[230947.422] (II) NVIDIA(0): Initialized OpenGL Acceleration
[230947.422] (==) NVIDIA(0): Disabling shared memory pixmaps
[230947.422] (II) NVIDIA(0): Initialized X Rendering Acceleration
[230947.422] (==) NVIDIA(0): Backing store disabled
[230947.422] (==) NVIDIA(0): Silken mouse enabled
[230947.423] (**) NVIDIA(0): DPMS enabled
[230947.423] (II) Loading extension NV-CONTROL
[230947.423] (II) Loading extension XINERAMA
[230947.423] (II) Loading sub module "dri2"
[230947.423] (II) LoadModule: "dri2"
[230947.423] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[230947.423] (II) NVIDIA(0): [DRI2] Setup complete
[230947.423] (==) RandR enabled
[230947.423] (II) Initializing built-in extension Generic Event Extension
[230947.423] (II) Initializing built-in extension SHAPE
[230947.423] (II) Initializing built-in extension MIT-SHM
[230947.423] (II) Initializing built-in extension XInputExtension
[230947.423] (II) Initializing built-in extension XTEST
[230947.423] (II) Initializing built-in extension BIG-REQUESTS
[230947.423] (II) Initializing built-in extension SYNC
[230947.423] (II) Initializing built-in extension XKEYBOARD
[230947.423] (II) Initializing built-in extension XC-MISC
[230947.423] (II) Initializing built-in extension SECURITY
[230947.423] (II) Initializing built-in extension XINERAMA
[230947.423] (II) Initializing built-in extension XFIXES
[230947.423] (II) Initializing built-in extension RENDER
[230947.423] (II) Initializing built-in extension RANDR
[230947.423] (II) Initializing built-in extension COMPOSITE
[230947.423] (II) Initializing built-in extension DAMAGE
[230947.423] (II) Initializing built-in extension GESTURE
[230947.425] (II) Initializing extension GLX
[230947.448] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[230947.457] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[230947.457] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[230947.457] (II) LoadModule: "evdev"
[230947.457] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[230947.457] (II) Module evdev: vendor="X.Org Foundation"
[230947.457] 	compiled for 1.9.0, module version = 2.3.2
[230947.457] 	Module class: X.Org XInput Driver
[230947.457] 	ABI class: X.Org XInput driver, version 11.0
[230947.457] (**) Power Button: always reports core events
[230947.457] (**) Power Button: Device: "/dev/input/event1"
[230947.522] (II) Power Button: Found keys
[230947.522] (II) Power Button: Configuring as keyboard
[230947.522] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[230947.522] (**) Option "xkb_rules" "evdev"
[230947.522] (**) Option "xkb_model" "pc105"
[230947.522] (**) Option "xkb_layout" "us"
[230947.524] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[230947.524] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[230947.524] (**) Power Button: always reports core events
[230947.524] (**) Power Button: Device: "/dev/input/event0"
[230947.603] (II) Power Button: Found keys
[230947.603] (II) Power Button: Configuring as keyboard
[230947.603] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[230947.603] (**) Option "xkb_rules" "evdev"
[230947.603] (**) Option "xkb_model" "pc105"
[230947.603] (**) Option "xkb_layout" "us"
[230947.607] (II) config/udev: Adding input device Mitsumi Electric Mitsumi USB Keyboard (/dev/input/event2)
[230947.607] (**) Mitsumi Electric Mitsumi USB Keyboard: Applying InputClass "evdev keyboard catchall"
[230947.607] (**) Mitsumi Electric Mitsumi USB Keyboard: always reports core events
[230947.607] (**) Mitsumi Electric Mitsumi USB Keyboard: Device: "/dev/input/event2"
[230947.683] (II) Mitsumi Electric Mitsumi USB Keyboard: Found keys
[230947.683] (II) Mitsumi Electric Mitsumi USB Keyboard: Configuring as keyboard
[230947.683] (II) XINPUT: Adding extended input device "Mitsumi Electric Mitsumi USB Keyboard" (type: KEYBOARD)
[230947.683] (**) Option "xkb_rules" "evdev"
[230947.683] (**) Option "xkb_model" "pc105"
[230947.683] (**) Option "xkb_layout" "us"
[230947.691] (II) config/udev: Adding input device BTC USB Multimedia Cordless Kit (/dev/input/event3)
[230947.691] (**) BTC USB Multimedia Cordless Kit: Applying InputClass "evdev keyboard catchall"
[230947.691] (**) BTC USB Multimedia Cordless Kit: always reports core events
[230947.691] (**) BTC USB Multimedia Cordless Kit: Device: "/dev/input/event3"
[230947.763] (II) BTC USB Multimedia Cordless Kit: Found keys
[230947.763] (II) BTC USB Multimedia Cordless Kit: Configuring as keyboard
[230947.763] (II) XINPUT: Adding extended input device "BTC USB Multimedia Cordless Kit" (type: KEYBOARD)
[230947.763] (**) Option "xkb_rules" "evdev"
[230947.763] (**) Option "xkb_model" "pc105"
[230947.763] (**) Option "xkb_layout" "us"
[230947.764] (II) config/udev: Adding input device BTC USB Multimedia Cordless Kit (/dev/input/event4)
[230947.764] (**) BTC USB Multimedia Cordless Kit: Applying InputClass "evdev pointer catchall"
[230947.764] (**) BTC USB Multimedia Cordless Kit: Applying InputClass "evdev keyboard catchall"
[230947.764] (**) BTC USB Multimedia Cordless Kit: always reports core events
[230947.764] (**) BTC USB Multimedia Cordless Kit: Device: "/dev/input/event4"
[230947.842] (II) BTC USB Multimedia Cordless Kit: Found 3 mouse buttons
[230947.842] (II) BTC USB Multimedia Cordless Kit: Found scroll wheel(s)
[230947.842] (II) BTC USB Multimedia Cordless Kit: Found relative axes
[230947.842] (II) BTC USB Multimedia Cordless Kit: Found x and y relative axes
[230947.842] (II) BTC USB Multimedia Cordless Kit: Found keys
[230947.842] (II) BTC USB Multimedia Cordless Kit: Configuring as mouse
[230947.842] (II) BTC USB Multimedia Cordless Kit: Configuring as keyboard
[230947.842] (**) BTC USB Multimedia Cordless Kit: YAxisMapping: buttons 4 and 5
[230947.842] (**) BTC USB Multimedia Cordless Kit: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[230947.842] (II) XINPUT: Adding extended input device "BTC USB Multimedia Cordless Kit" (type: KEYBOARD)
[230947.842] (**) Option "xkb_rules" "evdev"
[230947.842] (**) Option "xkb_model" "pc105"
[230947.842] (**) Option "xkb_layout" "us"
[230947.842] (II) BTC USB Multimedia Cordless Kit: initialized for relative axes.
[230947.843] (II) config/udev: Adding input device BTC USB Multimedia Cordless Kit (/dev/input/mouse0)
[230947.843] (II) No input driver/identifier specified (ignoring)
[230947.844] (II) config/udev: Adding input device Guest Barcode Reader (/dev/input/event5)
[230947.844] (**) Guest Barcode Reader: Applying InputClass "evdev keyboard catchall"
[230947.844] (**) Guest Barcode Reader: always reports core events
[230947.844] (**) Guest Barcode Reader: Device: "/dev/input/event5"
[230947.922] (II) Guest Barcode Reader: Found keys
[230947.922] (II) Guest Barcode Reader: Configuring as keyboard
[230947.922] (II) XINPUT: Adding extended input device "Guest Barcode Reader" (type: KEYBOARD)
[230947.922] (**) Option "xkb_rules" "evdev"
[230947.922] (**) Option "xkb_model" "pc105"
[230947.922] (**) Option "xkb_layout" "us"
[230947.923] (II) config/udev: Adding input device ASUS USB2.0 Webcam (/dev/input/event6)
[230947.923] (**) ASUS USB2.0 Webcam: Applying InputClass "evdev keyboard catchall"
[230947.923] (**) ASUS USB2.0 Webcam: always reports core events
[230947.923] (**) ASUS USB2.0 Webcam: Device: "/dev/input/event6"
[230948.002] (II) ASUS USB2.0 Webcam: Found keys
[230948.002] (II) ASUS USB2.0 Webcam: Configuring as keyboard
[230948.002] (II) XINPUT: Adding extended input device "ASUS USB2.0 Webcam" (type: KEYBOARD)
[230948.002] (**) Option "xkb_rules" "evdev"
[230948.002] (**) Option "xkb_model" "pc105"
[230948.002] (**) Option "xkb_layout" "us"
[230948.011] (II) config/udev: Adding input device Media Center Ed. eHome Infrared Remote Transceiver (147a:e018) (/dev/input/event7)
[230948.011] (**) Media Center Ed. eHome Infrared Remote Transceiver (147a:e018): Applying InputClass "evdev keyboard catchall"
[230948.011] (**) Media Center Ed. eHome Infrared Remote Transceiver (147a:e018): always reports core events
[230948.011] (**) Media Center Ed. eHome Infrared Remote Transceiver (147a:e018): Device: "/dev/input/event7"
[230948.082] (II) Media Center Ed. eHome Infrared Remote Transceiver (147a:e018): Found keys
[230948.082] (II) Media Center Ed. eHome Infrared Remote Transceiver (147a:e018): Configuring as keyboard
[230948.082] (II) XINPUT: Adding extended input device "Media Center Ed. eHome Infrared Remote Transceiver (147a:e018)" (type: KEYBOARD)
[230948.082] (**) Option "xkb_rules" "evdev"
[230948.082] (**) Option "xkb_model" "pc105"
[230948.082] (**) Option "xkb_layout" "us"
```

---

### Post by jim.hitch on 2011-03-09
Hi

Did you have any luck with this in the end?

I think I've got the same problem. Here's my setup:

I have a separate frontend running through HDMI to my LCD TV, this is the setup:
 Mythbuntu 10.10
 Processor (CPU) - Intel® Atom&#8482; DualCore Processor D525 (1.8GHz) 667MHz FSB/1MB Cache
 Motherboard - ASUS® AT5IONT-I: NVIDIA® ION&#8482;, HDMI 1080P, USB 3.0

As you say, it's happening in chrome, skype, virtualbox and for me firefox and synaptic package manager, but strangely not so much when actually running mythtv. It's driving me completely nuts.

---

### Post by audeojude on 2011-03-10
No,
I haven't found a resolution. Right now I have minimal functionality that lets me get by and am just waiting till an update comes out that fixes this. It is a pain in the butt, but what are you going to do.. Xorg and or Nvidia need to get their **** together on this one... there are a lot of people having this specific issue.

---

### Post by jim.hitch on 2011-03-10
Hi

I found this from a couple of years ago and wonder if it might be a similar thing. [HERE]("https://bbs.archlinux.org/viewtopic.php?id=43792")


When I get time, I might try installing the nvidia driver from nvidia itself, using the tips in that link and see how it goes. What do you think?

I'm not genius with linux, but can follow instructions.

If that doesn't work, I'm going back to lucid, as you suggest.

---

### Post by audeojude on 2011-03-10
All the GLX and stuff is working fine for me so I think that is a different issue. I am using the latest NVidia drivers from the NVidia website so that didn't fix the issue. I have tried all the Ubuntu supported drivers as well as the one's from Nvidia itself. :(

The only way I have resolved the issue is to roll back the Xorg server to 3 or 4 versions ago in the Lucid repository... It is a bit of a pain in the butt to do and it messes with the installed software and dependencies. I don't recommend it for the faint of heart. 

I had it all working with the above rollback but then updated some stuff in the dependencies it updated Xorg server back to the newer version which broke it again. In trying to roll the drivers back again I now had some dependencies that wouldn't allow me to do it again... 

I have spent way to much time beating my head against this. My computer isn't here for me to spend hundreds of hours just trying to get it to work. It's here for me to spend hundreds of hours working and doing stuff I need to do online. 

I'm a big Ubuntu fan and in general it "just runs" which I like. I get really frustrated when I hit an issue like this though. Especially when it lasts for months without a fix.

---

### Post by jim.hitch on 2011-03-10
> **audeojude said:**
> My computer isn't here for me to spend hundreds of hours just trying to get it to work. It's here for me to spend hundreds of hours working and doing stuff I need to do

Exactly. I've been using kubuntu on a laptop for work for the last three years. KDE can do things that macs and ms can't that make my work sing. So I branched out but after 18 months have been unimpressed by the usability of the popcorn hour as a media centre. So I've invested in a server and frontend to run mythtv on, using mythbuntu, hence the trouble now.

Mythtv looks great and seems to work well, though of course I've ended up at the bleeding edge, having promised myself I wouldn't (I needed to play remote iso's...)... and now this.

If I start again on the frontend with 10.04.2, will that have the correct xorg to stop this happening?

btw, thanks for the info and saving me the timewaste with the nvidia drivers etc etc.

---

### Post by jim.hitch on 2011-03-10
To answer my own question, the answer will be no, as I've just checked that 10.04.2 has the latest version of the x-server.

What version of the x server is working for you?

---

### Post by audeojude on 2011-03-10
It's been a bit since I rolled back the Xorg to the lucid version and I'm not sure of which version it is now.. Probably the first one that came out with lucid. In synaptic in  one of the file menu options it allows you to show all versions of a application such as Xorg and specify which one you want to install. So if in Lucid repositories it will show you all the versions within lucid or if in Maverick it will show you all the versions in maverick.. It won't show you lucid versions if your running Maverick. to do that you have to manually change your apt sources/repositories back to the lucid repositories and then refresh the apt sources and it will show up then. However that is fraught with secondary issues when you start installing stuff out of other repositories. You can get into some weird dependency issues.

---

### Post by jim.hitch on 2011-03-13
I did a clean install of lucid 10.04 and realised that if I unchecked lucid-updates, but kept lucid-security there would be no updating of the xserver.

If I had kept it checked, the only relevant package that would have been upgraded was 

xserver-org-core

which would have been upgraded from

2:1.7.6-2ubuntu7

to

2:1.7.6-2ubuntu7.5

So the problem lies somewhere between the two, with 2:1.7.6-2ubuntu7 not causing any problems.

I've been running this all day now without a single crash of x.

Needing this for a mythtv frontend, by needs are not too demanding, so I should be able to get away with this. Lucky for me.

I'll post again if I run into trouble.

NB I should mention that I reinstalled with 32bit rather than 64bit for an unrelated reason.

---

### Post by mabloom on 2011-04-04
> **lidex said:**
> Please then do file a bug report. Why do we think it has to do with nvidia driver though? Have you tried noveau driver? Check your log files, dmesg, etc. after x crashes to get some idea of the cause.

I have the same problem on a laptop with a geforce 8600m Gt chip.

When my laptop died several weeks ago,  I moved the hard disk over to an older machine using a Geforce 4 chip, which needed the older "nvidia-96" driver.  The crash did not occur with that driver.

I moved the disk back to my newer laptop once it was repaired,  and the crash again occurs with the nvidia-current driver. 

A couple of observations: 
1) the last line in the log is: "ddxSigGiveUp: Closing log".  It's preceded by a bunch of UnloadModule messages,  but no explicit hint as to what caused the signal (assuming that is what ddxSig... implies)

2) There are posts elewhere on the net saying that the problem can be worked around by disabling Xinerama,  yet when I tried that it did not help.  Not only that, but even when I have tried disabling xinerama while using this driver, xdpyinfo reports the presence of XINERAMA. Twice!  

After changing xorg.conf failed to disable Xinerama,  I tried using -xinerama on the command line (by replacing X with a shell script that invokes ``X.real "$@" -xinerama``).  That still did not disable it.  Something screwy is going on here, and I do not understand what.

3) On the assumption that there might be a driver mismatch,  I tried using the server and driver from Ubuntu-X-Swat's PPA, but again had no luck. 

While I started this post just with the intention of providing data points to anyone who might be interested,  I'd be interested in following this to completion, so any suggestions would be appreciated.

It is many, many years since I have used gdb (to get an idea of the date,  I had distributed my own diffs for "stabs-in-coff-symbols" for gcc1,gcc2, gdb-3.5 and gas-1.38 since fsf didn't want them).   I would assume that debugging of X server code works best with a remote debugger.  Any pointers to a quick catch-up howto or primer on debugging the X server would be appreciated.

---

### Post by mabloom on 2011-04-04
oops.  This edit of my previous message somehow became a duplicate of it. I have therefore erased it's content. I'd delete it if I could.

---

### Post by mabloom on 2011-04-05
Su=ince the ppa did not help, I tried installing the latest driver (260.19.44)  from nvidia, and got the same crash, but there was more detail, including a report about a bad pointer to address nil, followed by a stack trace.  Unfortunately, when I reinstalled the ubuntu supplied driver, the xorg log was lost.  When I get the chance I will try again and save the log.

Notably, when the disk containing the OS is moved to a machine that needs the nvidia-96 driver,  and the system is reconfigured to use that driver, no crash occurs.

The problem is not unique to being triggered by virtualbox. I discovered today that emacs triggers it as well.

Not being able to use either virtuabox or emacs are major limitations, which I'm writing in a message to nvidia support.

---

### Post by audeojude on 2011-05-15
I upgraded to natty and this fixed itself... then it came back after a while. I believe it is now related to the compiz features.

under natty if you run "unity --reset" and reset all the settings back to default the issue goes away for me. I had enabled some of the advanced 3d stuff under compiz and started crashing x when running virtualbox, calibre etc.... 

not sure how this would work under maverick as it doesn't use unity.. but the reset feature seems to zero out any special settings of compiz to a default configuration and fix my issue.

could be im just seeing some conincidental stuff here but I'm now running everything fine.. I will not be enabling compiz's special effects anytime soon though.

---

### Post by audeojude on 2012-02-02
This is so frustrating. A couple days ago this started again. I'm on 11.10 right now with all the current updates.

---

### Post by hussam_nasir on 2012-04-22
After struggling with this bug for the past 1 year, i finally found a solution that is very simple and easy. This is on the assumption that all of you have used the nvidia-settings utility to generate your xorg.conf file.

Edit the /etc/X11/xorg.conf file and comment out or delete the below shown lines 

Section "Files"
    FontPath        "unix/:7100"
EndSection

Save the file and restart GDM or lightDM which ever is your login manager using

/etc/init.d/gdm restart

or /etc/init.d/lightdm restart


Now all of the QT applications like virtualbox and skype should not crash X

---

### Post by audeojude on 2012-05-31
This hasn't been happening to me for a few months but it's good to see someone figured out how to stop it. If it starts again I know what to do.
Scott

---

### Post by audeojude on 2012-08-29
I'm so frustrated with ubuntu right now I could scream. So I updated my third sytem to 12.04. This is my main work system. I waited till I had used 12.04 on two other systems for a while. All seemed good. It worked fine for a week and then then same issue with the nvidia/xsserver issue documented here happened again. I couldn't run skype, I couldn't run virtualbox, x kept crashing. 

however the solution above of commenting out the fonts in the xorg.conf file fixed it. What isn't fixed is that every time I boot up wether a cold boot or warm boot I get kicked into a low graphics mode recovery screen. However the recovery screen doesn't allow you to select any options to try and fix the issue. The only way I can get into x is to go to a console at F1 and run lightdm & 

This starts a normal xsession.

Has anyone seen this before and if so what is the solution?

---

