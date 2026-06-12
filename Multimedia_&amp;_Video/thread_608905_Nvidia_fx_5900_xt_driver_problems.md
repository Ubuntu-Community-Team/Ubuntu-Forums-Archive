---
title: "Nvidia fx 5900 xt driver problems"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by moses036 on 2007-11-10
Hey guys,

I've been trying to install the nvidia drivers for my nvidia fx 5900 xt card for the last few weeks on gutsy, but no matter what method I try I get the same result. I've used envy, the restricted drivers manager, and install the driver manually but no matter what method, every time after I install it, I reboot and all i get is a black screen. The only way i can get back into my gui is by rebooting in safe mode and restoring my old x.org.conf file or by changing the graphics driver from "nvidia" back to "nv"

So i was hoping that somebody else out here has an nvidia fx 5900 xt video card and has successfully installed the nvidia drivers. If so, could you please tell me what method worked for you and also provide me with a copy of your x.org.conf so I can see if I need to add any sort of special commands to mine.

---

### Post by carlinuxlearner on 2007-11-10
Have you ever installed the driver with "envy" and then just restarted X, to see if it worked?

C@RL

---

### Post by moses036 on 2007-11-10
yes, x fails and im taken straight to the text interface. Here is a copy of my xorg.conf with the nvidia driver installed using envy: 

[PHP]# Uncomment if you have a wacom tablet
# InputDevice     "stylus" "SendCoreEvents"
# InputDevice     "cursor" "SendCoreEvents"
# InputDevice     "eraser" "SendCoreEvents"
   Identifier     "Default Layout"
   Screen         "Default Screen" 0 0
   InputDevice    "Generic Keyboard"
   InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
   Load           "glx"
EndSection

Section "InputDevice"
   Identifier     "Generic Keyboard"
   Driver         "kbd"
   Option         "CoreKeyboard"
   Option         "XkbRules" "xorg"
   Option         "XkbModel" "pc105"
   Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
   Identifier     "Configured Mouse"
   Driver         "mouse"
   Option         "CorePointer"
   Option         "Device" "/dev/input/mice"
   Option         "Protocol" "ImPS/2"
   Option         "ZAxisMapping" "4 5"
   Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
   Identifier     "stylus"
   Driver         "wacom"
   Option         "Device" "/dev/input/wacom"
   Option         "Type" "stylus"
   Option         "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
   Identifier     "eraser"
   Driver         "wacom"
   Option         "Device" "/dev/input/wacom"
   Option         "Type" "eraser"
   Option         "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
   Identifier     "cursor"
   Driver         "wacom"
   Option         "Device" "/dev/input/wacom"
   Option         "Type" "cursor"
   Option         "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
   Identifier     "Generic Monitor"
   HorizSync       30.0 - 70.0
   VertRefresh     50.0 - 160.0
   Option         "DPMS"
EndSection

Section "Device"
   Identifier     "nVidia Corporation NV35 [GeForce FX 5900XT]"
   Driver         "nvidia"
EndSection

Section "Screen"
   Identifier     "Default Screen"
   Device         "nVidia Corporation NV35 [GeForce FX 5900XT]"
   Monitor        "Generic Monitor"
   DefaultDepth    24
   Option         "AddARGBGLXVisuals" "True"
   SubSection     "Display"
       Depth       24
       Modes      "nvidia-auto-select"
   EndSubSection
EndSection

Section "Extensions"
   Option         "Composite" "Enable"
EndSection
[/PHP]

---

### Post by carlinuxlearner on 2007-11-10
I believe I know what your problem is. You DON'T have a BusID in the "Device" section of your "xorg.conf".

Here's what mine looks like
"Section "Device"
    Identifier     "Nvidia Geforce4 MX 420"
    Driver         "nvidia"
    BoardName      "nv"
    **BusID          "PCI:1:11:0"**
    Screen          0
EndSection
"
To get the correct BusID, boot up in "recovery mode" and put mine BusID in "PCI:1:11:0" (nano -w /etc/X11/xorg.conf) and try starting X (startx) it will give you an error message suggesting the correct BusID, so put it in! Then try starting X again, if it works then your good to go!

C@RL

---

### Post by moses036 on 2007-11-10
Thanks for the replies. unfortunately that failed to work as well. I added the BusID "PCI:1:0:0" and that didn't change anything. Also, I manually added the resolutions "1680x1050" "1024x768" "800x600" to the  screen section, but that didnt change anything either. When i went to restart x it does the same thing, screen acts like it is about to turn on and then in about 5 seconds it goes into standby mode.

---

### Post by moses036 on 2007-11-10
Also if it helps anyone, here is the result of my Xorg.0.log


[PHP]X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux john-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 10 16:44:38 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NV35 [GeForce FX 5900XT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 1043,813f rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1043,813f rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1043,813f rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1043,813f rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1043,813f rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1043,813f rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:05:0: chip 10de,00df card 1043,80a7 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:06:0: chip 10de,00ea card 1043,812a rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 1043,813f rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00e3 card 1043,813f rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0332 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfca00000 - 0xfeafffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xdc900000 - 0xec8fffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0003 (VGA_EN is cleared)
(--) PCI:*(1:0:0) nVidia Corporation NV35 [GeForce FX 5900XT] rev 161, Mem @ 0xfd000000/24, 0xe0000000/27, BIOS @ 0xfeae0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[1] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[2] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[3] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[4] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[10] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[11] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[12] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[13] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[14] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[15] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[19] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[20] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[21] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[1] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[2] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[3] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[4] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[10] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[11] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[12] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[13] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[14] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[15] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[19] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[20] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[21] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[7] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[8] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[17] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[18] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[19] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[20] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[25] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[26] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[27] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.23  Thu Oct  4 10:52:20 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  100.14.23  Thu Oct  4 10:18:31 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[7] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[8] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[17] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[18] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[19] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[20] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[25] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[26] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[27] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[5] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[7] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[8] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[28] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[29] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[30] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5900XT (NV35) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.35.20.27.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5900XT at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     BenQ FP202W (DFP-0)
(--) NVIDIA(0): BenQ FP202W (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): BenQ FP202W (DFP-0): External Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[7] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[9] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[10] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[22] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[23] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[24] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[25] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[30] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[31] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[32] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Unable to connect to the ACPI daemon; the ACPI daemon may not
(II) NVIDIA(0):     be running or the "AcpidSocketPath" X configuration option
(II) NVIDIA(0):     may not be set correctly.  When the ACPI daemon is
(II) NVIDIA(0):     available, the NVIDIA X driver can use it to receive ACPI
(II) NVIDIA(0):     events.  For details, please see the "ConnectToAcpid" and
(II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
(II) NVIDIA(0):     Config Options in the README.
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000000, 0x00000624)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x00000000, 0x00000624)
(II) NVIDIA(0): Setting mode "1680x1050"
(WW) NVIDIA(0): WAIT (2, 1, 0x8000, 0x00000000, 0x000006e8)
(WW) NVIDIA(0): WAIT (1, 1, 0x8000, 0x00000000, 0x000006e8)
(II) Loading extension NV-GLX
(WW) NVIDIA(0): WAIT (2, 11, 0x8000, 0x00000000, 0x00000d8c)
(WW) NVIDIA(0): WAIT (1, 11, 0x8000, 0x00000000, 0x00000d8c)
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000000, 0x00001424)
(WW) NVIDIA(0): WAIT (1, 6, 0x8000, 0x00000000, 0x00001424)
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded[/PHP]

---

### Post by carlinuxlearner on 2007-11-10
Do you mean that it doesn't ever give you error mesages and it just hangs???
Well I believe I have gone as far as I can with this (I have no more suggestions, or ideas), you could try doing a fresh install though, and then try installing the driver.


C@RL

---

