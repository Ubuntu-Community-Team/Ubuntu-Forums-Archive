---
title: "New NVIDIA driver issues- 169.12"
date: 2008-05-25
forum: Multimedia Software
---

### Post by Jvaldezjr on 2008-05-25
I need help with NVIDIA video driver 169.12.  I'm running Kubuntu 8.04 amd64 and I've installed the nvidia-glx package.  My problem is that when I start X, I get a black screen.  I used to have problems with imy monitor being detected, but I've been able to force my digital flat panel on DVI to be recognized, however now I don't get a display.  here are the excerpts from my Xorg.log file and my Xorg.config file:

Xorg.0.log:
```

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP"
(**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT,TV"
(**) NVIDIA(0): Option "HorizSync" "DFP-0:28-64"
(**) NVIDIA(0): Option "VertRefresh" "DFP-0:43-60"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "True"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP-0"
(**) NVIDIA(0): Option "DPI" "95 x 96"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): ConnectedMonitor string: "DFP"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-0
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 (NV43) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.46.01
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 at PCI:1:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 155.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1280x960"; removing.
(WW) NVIDIA(0): No valid modes for "1280x800"; removing.
(WW) NVIDIA(0): No valid modes for "1280x768"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(**) NVIDIA(0): DPI set to (95, 96); computed from "DPI" X config option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
```

and my xorg.conf (Device, Monitor, and Screen sections):
```
Section "Device"
        Identifier      "NVIDIA Corporation NV43 [Geforce 6600 GT]"
        BusID           "PCI:1:0:0"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
        Option          "AllowGLXWithComposite" "True"
#       Option          "ConnectedMonitor" "DFP"
        Option          "UseDisplayDevice" "DFP-0"
        Option          "IgnoreDisplayDevices" "CRT,TV"
EndSection

Section "Monitor"
        Identifier              "Sony SDM-HS75P"
        Option                  "DPMS"
        HorizSync               28-64
        VertRefresh     43-60
        DisplaySize             342 271
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Sony SDM-HS75P"
        Option                  "DPMS"
        HorizSync               28-64
        VertRefresh     43-60
        DisplaySize             342 271
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Sony SDM-HS75P"
        Device          "NVIDIA Corporation NV43 [Geforce 6600 GT]"
        Option          "HorizSync"     "DFP-0:28-64"
        Option          "VertRefresh"   "DFP-0:43-60"
        Option          "DPI"   "95 x 96"
        Option          "MetaModes"             "DFP-0: 1280x1024"
        Defaultdepth    24
EndSection

```

I'm not sure what the problem is, and I've tried installing the driver many different ways, but I have no idea where to start trying to troubleshoot this.

---

### Post by Jvaldezjr on 2008-05-28
Bump...hopeing someone can help...

---

### Post by presston on 2008-05-28
> Driver          "nvidia"

try here

> Driver          **"nv"**

---

### Post by reiki on 2008-05-28
install read-edid and use it. See if it can read the EDID from your monitor.

( sudo apt-get install read-edid ) 

and then sudo get-edid

Look at the output from get-edid and see if it's failing to read the EDID data from your monitor.  I have a feeling the nvidia drivers are not working correctly. This is a widespread issue.

---

### Post by Jvaldezjr on 2008-05-28
Thanks for the help- I don't remember the command I used to get the DPI settings on my monitor in Feisty to try to force them with the newer drivers, but I"ll try this command also.  Now if only I can get the NVIDIA people to get my account activated so I can post this on their boards.  It sounds like a NVIDIA issue.

Does anyone know how to fix the logout issue I have?  I'll post that in another thread.

---

### Post by Jvaldezjr on 2008-05-28
I've even tried the newest NVIDIA drivers 173.14.05 I think, and still problems- as Xorg log file says I have no screens that are detected.  The autogenerated xorg file from the nvidia installer has my monitor correctly detected there, along with several screen displays, etc.  However, X seems to crash now.

---

### Post by ~David on 2008-05-28
I had the same problem. On the black screen, press Ctrl + Alt + F2 and follow these steps:

1. 'sudo nano /etc/modules'. Add the 'nvidia' module to the list. (Control + O and Return to save then Control + X to exit)

2. 'sudo nano /etc/default/linux-restricted-modules-common'. Make sure the file looks like: 'DISABLED_MODULES="nv" (Again, Control + O and Return to save then Control + X to exit)

3. Enter the following:
sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-173.14.05-pkg1.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start

Courtesy of this guy: [http://ubuntuforums.org/showpost.php?p=4479190&postcount=15](http://ubuntuforums.org/showpost.php?p=4479190&postcount=15)

---

### Post by Jvaldezjr on 2008-05-28
@reiki
I tried your advice, and Hardy won't let me even install the package.

@~David
I followed your steps using the 173.14.05 driver, and no dice, it still doesn't detect my display properly.  I even edited my xorg.conf file to force the detection, and that doesn't help.

Still no luck with this massive breakage...Oh, my new xorg.conf, and log files are below.

Thanks for the help so far!

xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Mon May 19 00:29:52 PDT 2008

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
#	Load	"dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "altwin:meta_win"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Sony SDM-HS75P"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
	BusID		   "PCI:1:0:0"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "NoLogo" "true"
    Option         "ConnectedDevice" "DFP"
	Option		   "UseDisplayDevice" "DFP-0"
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Sony SDM-HS75P"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

and my log file (/var/log/Xorg.0.log):
```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux extra64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64
Build Date: 15 April 2008  05:41:18PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May 28 22:22:41 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Sony SDM-HS75P"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 1695,100c rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1695,100c rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1695,100c rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1695,100c rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1695,100c rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1695,100c rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:05:0: chip 10de,00df card 1695,100c rev a2 class 06,80,00 hdr 00
(II) PCI: 00:06:0: chip 10de,00ea card 1695,100b rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card f695,100c rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,00f2 card 0000,0000 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe2ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0206 (VGA_EN is cleared)
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600] rev 162, Mem @ 0xe0000000/24, 0xd0000000/28, 0xe1000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xc0000000 to 0xbfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe3002000 - 0xe3002fff (0x1000) MX[B]
	[1] -1	0	0xe3001000 - 0xe3001fff (0x1000) MX[B]
	[2] -1	0	0xe3000000 - 0xe30000ff (0x100) MX[B]
	[3] -1	0	0xe3005000 - 0xe3005fff (0x1000) MX[B]
	[4] -1	0	0xe3004000 - 0xe3004fff (0x1000) MX[B]
	[5] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[6] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[10] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[13] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[14] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe3002000 - 0xe3002fff (0x1000) MX[B]
	[1] -1	0	0xe3001000 - 0xe3001fff (0x1000) MX[B]
	[2] -1	0	0xe3000000 - 0xe30000ff (0x100) MX[B]
	[3] -1	0	0xe3005000 - 0xe3005fff (0x1000) MX[B]
	[4] -1	0	0xe3004000 - 0xe3004fff (0x1000) MX[B]
	[5] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[6] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[10] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[13] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[14] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
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
	[4] -1	0	0xe3002000 - 0xe3002fff (0x1000) MX[B]
	[5] -1	0	0xe3001000 - 0xe3001fff (0x1000) MX[B]
	[6] -1	0	0xe3000000 - 0xe30000ff (0x100) MX[B]
	[7] -1	0	0xe3005000 - 0xe3005fff (0x1000) MX[B]
	[8] -1	0	0xe3004000 - 0xe3004fff (0x1000) MX[B]
	[9] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[10] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[20] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.05  Mon May 19 00:27:33 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  173.14.05  Mon May 19 00:09:56 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3002000 - 0xe3002fff (0x1000) MX[B]
	[5] -1	0	0xe3001000 - 0xe3001fff (0x1000) MX[B]
	[6] -1	0	0xe3000000 - 0xe30000ff (0x100) MX[B]
	[7] -1	0	0xe3005000 - 0xe3005fff (0x1000) MX[B]
	[8] -1	0	0xe3004000 - 0xe3004fff (0x1000) MX[B]
	[9] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[10] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[20] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3002000 - 0xe3002fff (0x1000) MX[B]
	[5] -1	0	0xe3001000 - 0xe3001fff (0x1000) MX[B]
	[6] -1	0	0xe3000000 - 0xe30000ff (0x100) MX[B]
	[7] -1	0	0xe3005000 - 0xe3005fff (0x1000) MX[B]
	[8] -1	0	0xe3004000 - 0xe3004fff (0x1000) MX[B]
	[9] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[10] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[23] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP-0"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): No display devices connected; falling back to: CRT-0
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 (NV43) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.46.01
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(WW) NVIDIA(0): Unable to find any of the requested display device "DFP-0" in
(WW) NVIDIA(0):     the list of available display devices "CRT-0".
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x854"; removing.
(WW) NVIDIA(0): No valid modes for "1200x800"; removing.
(WW) NVIDIA(0): No valid modes for "1152x864"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1280x960"
(II) NVIDIA(0):     "1280x800"
(II) NVIDIA(0):     "1280x768"
(II) NVIDIA(0):     "1152x768"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3002000 - 0xe3002fff (0x1000) MX[B]
	[5] -1	0	0xe3001000 - 0xe3001fff (0x1000) MX[B]
	[6] -1	0	0xe3000000 - 0xe30000ff (0x100) MX[B]
	[7] -1	0	0xe3005000 - 0xe3005fff (0x1000) MX[B]
	[8] -1	0	0xe3004000 - 0xe3004fff (0x1000) MX[B]
	[9] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[10] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[23] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "ConnectedDevice" is not used
(==) RandR enabled
(II) Setting vga for screen 0.
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
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "altwin:meta_win"
(**) Generic Keyboard: XkbOptions: "altwin:meta_win"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
```

---

### Post by salvador_luna on 2008-05-29
Hi:

I had the same issue with gutsy and hardy: Get a blank screen with the live cd or an hd install.

I've updated my bios and it worked, so maybe you can try that.

By the way, i updated the bios using windows because i hadn't other choice (installing from a bootable cd didn't work) so maybe you could try using a VM.

My video card:  GeForce 7150M (rev a2) in a Compaq Presario V3617la.

---

### Post by Jvaldezjr on 2008-05-29
I've already upadted the BIOS on my motherboard a long time ago- and there are no more BIOS updates.

---

### Post by Chiaki on 2008-05-29
I am having the same problem. Question - should I update the xorg config manually, or let the nvidia script do it?

---

### Post by Jvaldezjr on 2008-05-29
I've done it both ways and it hasn't maade a difference with the errors.

---

### Post by Jonie on 2008-05-30
Try adding  Option       "ModeValidation" "NoDFPNativeResolutionCheck" in your xorg.conf. This error pops sometimes out of the blue for specific card/monitor combination with nvidia restricted driver. I had to add this with 100 series, 169 seem to work fine for me.

---

### Post by Jvaldezjr on 2008-05-30
I tried that and still no dice...I am noticing this warning message, which I suspect is what is causing me to get a black screen:

```

(**) NVIDIA(0): ConnectedMonitor string: "DFP"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-0
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 (NV43) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.46.01
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 at PCI:1:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 155.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Single Link TMDS
(II) NVIDIA(0): Mode Validation Overrides for DFP-0:
(II) NVIDIA(0):     NoDFPNativeResolutionCheck
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1280x960"; removing.
(WW) NVIDIA(0): No valid modes for "1280x854"; removing.
(WW) NVIDIA(0): No valid modes for "1280x800"; removing.
(WW) NVIDIA(0): No valid modes for "1280x768"; removing.
(WW) NVIDIA(0): No valid modes for "1200x800"; removing.
(WW) NVIDIA(0): No valid modes for "1152x864"; removing.
(WW) NVIDIA(0): No valid modes for "1152x768"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default

```

I'm still stumped.  I can use older versions of the drivers to get it to work, but then I have a problem of losing my logout screen when I do- everytime I logout to switch to another user, KDM doesn't come back up.  I posted about that [here.]("http://ubuntuforums.org/showthread.php?t=810794")

Thanks to everyone that has posted to help so far.

---

### Post by kforum on 2008-05-30
i simply use a program, 'envy', to dl teh drivers/config-set everything for me. works like a charm ;)

---

### Post by reiki on 2008-05-30
Try renaming your xorg.conf file and restarting your machine. Basically X will try to boot with no xorg.conf. It will complain that it can't find your monitor and give you an opportunity to choose one from a list. You should also be able to choose your graphics card on a tab in that same dialog. It shoul boot to X but may blink a bit an look like it's stuck while it tries to figure out the display. 

When X starts you may have a little screen. Type sudo nvidia-settings.
It may then tell you that you don't have the nvidia driver configured... so type:
sudo nvidia-xconfig.

Restart your machine.

When you get back to X run sudo nvidia-settings
Choose your monitor from the list. Choose the resolution you want. 
And finally tell nvidia-settings applet to write the configuration file.

You will probably have to restart to get everything to take effect.

FYI: use DFP ONLY for flat panels connected using DVI cable. You may already know that but I thought I'd toss it in here.

ALSO... if your monitor also has a regular VGA connector... try using that instead of the DVI. .... I know, I know... if you have DVI you should be able to USE DVI, but you also may not notice a difference and for whatever reason, using the VGA connector solves this problem for a lot of people. And if you connect using teh VGA cable make sure your xorg.conf doesn't have that DFP parameter in it. ANYTHING connected to the VGA connector is called "CRT" regardless of whether it's a CRT or flat panel.

---

### Post by Jvaldezjr on 2008-05-30
@reiki
I do know about the DFP paramter- but thanks for telling me.  Mine is connected via DVI.  It was one of the reasons I bought my monitor, and I can tell a difference.

I've tried using the autogenerated xorg.conf file created by nvidia-xorg, and my monitor cuts off.  I'll try it in the steps you provided tomorrow.  I'm tired now.  I thin I'm getting close...I have attached my new xorg.conf and log files:

xorg.conf:
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
#	Path to Defoma Fonts
	FontPath	"/var/lib/defoma/xttcidfont-conf.d/dirs/TrueType"
EndSection

Section	"Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"altwin:meta_win"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"   "/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"	"true"            
	Option		"RenderAccel"	"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"UseEdidFreqs"	"false"
	Option		"UseEdid"	"false"
	Option		"UseDisplayDevice"	"DFP-0"
	Option		"ConnectedMonitor"	"DFP"
	Option		"UseFBDev"		"true"
	Option		"UseEdidDpi"	"false"
	Option		"Dpi"	"95 x 96"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	48-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"NVIDIA Corporation NV43 [Geforce 6600 GT]"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "Extensions"
	Option	"Composite"	"Enable"
EndSection

```

Xorg.0.log:
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux extra64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64
Build Date: 15 April 2008  05:41:18PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May 30 22:54:41 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/var/lib/defoma/xttcidfont-conf.d/dirs/TrueType" does not exist.
	Entry deleted from font path.
(WW) FontPath is completely invalid.  Using compiled-in default.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(==) |-->Input Device "Generic Keyboard"
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 1695,100c rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1695,100c rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1695,100c rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1695,100c rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1695,100c rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1695,100c rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:05:0: chip 10de,00df card 1695,100c rev a2 class 06,80,00 hdr 00
(II) PCI: 00:06:0: chip 10de,00ea card 1695,100b rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card f695,100c rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,00f2 card 0000,0000 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe2ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0206 (VGA_EN is cleared)
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600] rev 162, Mem @ 0xe0000000/24, 0xd0000000/28, 0xe1000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xc0000000 to 0xbfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe3002000 - 0xe3002fff (0x1000) MX[B]
	[1] -1	0	0xe3001000 - 0xe3001fff (0x1000) MX[B]
	[2] -1	0	0xe3000000 - 0xe30000ff (0x100) MX[B]
	[3] -1	0	0xe3005000 - 0xe3005fff (0x1000) MX[B]
	[4] -1	0	0xe3004000 - 0xe3004fff (0x1000) MX[B]
	[5] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[6] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[10] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[13] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[14] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe3002000 - 0xe3002fff (0x1000) MX[B]
	[1] -1	0	0xe3001000 - 0xe3001fff (0x1000) MX[B]
	[2] -1	0	0xe3000000 - 0xe30000ff (0x100) MX[B]
	[3] -1	0	0xe3005000 - 0xe3005fff (0x1000) MX[B]
	[4] -1	0	0xe3004000 - 0xe3004fff (0x1000) MX[B]
	[5] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[6] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[10] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[11] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[13] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[14] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
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
	[4] -1	0	0xe3002000 - 0xe3002fff (0x1000) MX[B]
	[5] -1	0	0xe3001000 - 0xe3001fff (0x1000) MX[B]
	[6] -1	0	0xe3000000 - 0xe30000ff (0x100) MX[B]
	[7] -1	0	0xe3005000 - 0xe3005fff (0x1000) MX[B]
	[8] -1	0	0xe3004000 - 0xe3004fff (0x1000) MX[B]
	[9] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[10] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[20] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.05  Mon May 19 00:27:33 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  173.14.05  Mon May 19 00:09:56 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3002000 - 0xe3002fff (0x1000) MX[B]
	[5] -1	0	0xe3001000 - 0xe3001fff (0x1000) MX[B]
	[6] -1	0	0xe3000000 - 0xe30000ff (0x100) MX[B]
	[7] -1	0	0xe3005000 - 0xe3005fff (0x1000) MX[B]
	[8] -1	0	0xe3004000 - 0xe3004fff (0x1000) MX[B]
	[9] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[10] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[20] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3002000 - 0xe3002fff (0x1000) MX[B]
	[5] -1	0	0xe3001000 - 0xe3001fff (0x1000) MX[B]
	[6] -1	0	0xe3000000 - 0xe30000ff (0x100) MX[B]
	[7] -1	0	0xe3005000 - 0xe3005fff (0x1000) MX[B]
	[8] -1	0	0xe3004000 - 0xe3004fff (0x1000) MX[B]
	[9] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[10] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[23] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "UseEDID" "false"
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "UseEdidFreqs" "false"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP-0"
(**) NVIDIA(0): Option "UseEdidDpi" "false"
(**) NVIDIA(0): Option "DPI" "95 x 96"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(**) NVIDIA(0): ConnectedMonitor string: "DFP"
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 (NV43) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.46.01
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 at PCI:1:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 155.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(**) NVIDIA(0): DPI set to (95, 96); computed from "DPI" X config option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3002000 - 0xe3002fff (0x1000) MX[B]
	[5] -1	0	0xe3001000 - 0xe3001fff (0x1000) MX[B]
	[6] -1	0	0xe3000000 - 0xe30000ff (0x100) MX[B]
	[7] -1	0	0xe3005000 - 0xe3005fff (0x1000) MX[B]
	[8] -1	0	0xe3004000 - 0xe3004fff (0x1000) MX[B]
	[9] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[10] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e47f (0x80) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[23] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "640x480"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "UseFBDev" is not used
(==) RandR enabled
(II) Setting vga for screen 0.
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
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "altwin:meta_win"
(**) Generic Keyboard: XkbOptions: "altwin:meta_win"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "altwin:meta_win"
(**) Generic Keyboard: XkbOptions: "altwin:meta_win"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[config/hal] couldn't initialise context: (null) ((null))

```

---

### Post by reiki on 2008-05-31
I understand what you're saying about DVI vs VGA. And I have no doubt that on some (maybe many) monitors you can see the difference. But also keep in mind that DVI has a "speed limit" of ... I think it's 165MHz ...and VGA doesn't have that limit. Connected using DVI your monitor probably has an optimum refresh rate of 60Hz. You may find that when connected using VGA you have much higher refresh rates available. 

I am not arguing that VGA is better. And I am also disappointed that DVI is not working as it should. However.... as an alternative until this gets fixed.... you may want to at least consider connecting VGA as a work-around.

---

### Post by Jvaldezjr on 2008-05-31
I've tried everything that everyone has suggested, and nothing has worked.  I can't get any of the NVIDIA forum admins to activate my account so i can't get help from them either.  I will probably have to use older drivers (96.43) and then try to solve my logout problem.  This has annoyed me to no end, and I've updated Kubuntu Hardy also, and still no fix.  I ahve this problem now with Feisty, and I can't use any NVIDIA driver past 96.43 with my Geforce 6600.

---

### Post by chibimushi on 2008-06-06
It is not an ubuntu specific problem. It is the drivers. I have tried multiple linux distros and I have the same issue. I am a Fedora user and with  the drivers after the 100 series they stopped working. I have sent bug reports to nvidia and asked on the forums and nvidia ignores it.
[http://www.nvnews.net/vbulletin/showthread.php?t=105410](http://www.nvnews.net/vbulletin/showthread.php?t=105410)

---

### Post by ChameleonDave on 2008-06-06
> **~David said:**
> 
3. Enter the following:
sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-173.14.05-pkg1.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start


Really, instead of typing "sudo" that many times, I'd recommend this:

```

sudo -s
apt-get install build-essential linux-headers-`uname -r`
apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
rm /etc/init.d/nvidia-*
/etc/init.d/gdm stop
sh NVIDIA-Linux-x86-173.14.05-pkg1.run
nvidia-xconfig --add-argb-glx-visuals
/etc/init.d/gdm start

```

---

### Post by Jvaldezjr on 2008-06-06
> **chibimushi said:**
> It is not an ubuntu specific problem. It is the drivers. I have tried multiple linux distros and I have the same issue. I am a Fedora user and with  the drivers after the 100 series they stopped working. I have sent bug reports to nvidia and asked on the forums and nvidia ignores it.
[http://www.nvnews.net/vbulletin/showthread.php?t=105410](http://www.nvnews.net/vbulletin/showthread.php?t=105410)

You're right.  I can't even get NVIDIA to activate my account so i can post questions on the board.  Nice to know they are listening, and care so I'm not too worried about getting my nvboard account activated now.  The 96 version drivers were the last ones that worked for me.  I'm using them now on Feisty, and I'll be using them when I finally switch to Hardy.

---

### Post by reiki on 2008-06-07
I'm using the nvidia 169.12 drivers installed by envyNG and prior to that used the nvidia-new drivers from ubuntu repos. I have my 22" wide screen connected using DVI only. The monitor is not detected, but I CAN get it to work. Some people seem to be having an issue with it getting no signal at all. I'm not finding that to be the case. I HAVE discovered that the EDID data does not seem to go across the DVI connection. With no detection via EDID, lots of displays aren't working correctly.... but they are still working. 

So am I hearing correctly that some of you are getting no signal at ALL on a DVI connected display on an nvidia card?

---

### Post by Jvaldezjr on 2008-06-07
> **reiki said:**
> I'm using the nvidia 169.12 drivers installed by envyNG and prior to that used the nvidia-new drivers from ubuntu repos. I have my 22" wide screen connected using DVI only. The monitor is not detected, but I CAN get it to work. Some people seem to be having an issue with it getting no signal at all. I'm not finding that to be the case. I HAVE discovered that the EDID data does not seem to go across the DVI connection. With no detection via EDID, lots of displays aren't working correctly.... but they are still working. 

So am I hearing correctly that some of you are getting no signal at ALL on a DVI connected display on an nvidia card?

Yep, pretty much.  I think with most people the EDID thing is killing their displays.  It's killed mine no matter what way I install the drivers (any version past 96.43).  I can't get an NV board account, and someone else posted that nvidia has not been helpful with the bug report.  My display is working with earlier dirvers, and EDID is detected when I use those drivers.  It is not when I try to use the newer ones, so there is something with the newer drivers that messes this up.  Something NVidia changed after 96.43 that causes my card and display to crap out.

---

### Post by chibimushi on 2008-06-08
The new drivers won't even detect the card has DVI output. It can't get the EDID data so its nothing to do with it. The problem seems to be very rare since I have only seen 3 or 4 us with this specific problem. I doubt Nvidia will fix this issue wince its so uncommon. If it does get fixed it will probably just be a side effect of something else they do.

---

### Post by Jvaldezjr on 2008-06-08
I doubt there is only 3-4 people with this problem.  I don't know how many bug reports have been filed or threads posted on the NV forums.  If the new drivers aren't detecting DVI output and EDID signals then I would imagine lots of people have similiar connectivity issues, and may have got their card "working" by forcing some parameters which may or may not work with every user.

Seeing that this problem has occured since the 100 version release, I don't see it as a bug.  I see it as a different way the software runs the card, which has significantly changed the way things are detected.  I know when Xorg 7 came out, NVidia cards started having problems and has tried to adress them.  Maybe it's an Xorg issue?  I have no clue, and I don't have the time at home to try to diagnose and resolve.

---

### Post by Anlace on 2008-07-15
Jvaldezjr,

Were you able to get your monitor to display correct resolution?  I too am having the same problem.  Brand new setup (Nvidia 9800GTS 512MB vid card) and can't get the Nvidia drivers to detect my monitor EDID correctly.

---

### Post by Jvaldezjr on 2008-07-15
@Anlace

No I have not.  I've tweaked just about every setting.  The only way for me to use hardy is to fall back to the 96.43 drivers.  Every driver after that gives me these problems.  I'm still using Feisty now and haven't upgraded because of this issue.

---

### Post by spyckotic on 2008-07-22
I too have suffered from this.  It feels like it's been at least 8 months I've been dealing with this.  Monitor goes to sleep and PC becomes unresponsive to any keyboard input on boot.  I am not exactly sure where the issue lies.  I have tried multiple distros and this happens with each one I try EXCEPT OpenSuse 10.3.  Opensuse is the only distro I have sucessfully gotten to work with my Geforce 8600 gts.  Took me maybe 5 minutes to have compiz-fusion running with rain, cube desktop, the whole nine yards with opensuse.  Can you that are having this blank screen issue give opensuse a try and post back the results.  This has been going on far to long now and there are so many threads about this very same thing, but never any solution.

---

### Post by duncane on 2008-07-22
Just chiming in to say I have exactly the same problem with my dual DVI output nvidia 8800GT.

I have tried Suse, Ubuntu, Envy and direct Nvidia driver install. Plus messing about in xorg.conf.

All results in the same issue... black screen on startup.

My card doesnt even have a VGA port so no way to fall back to that to test.

---

### Post by digitalbooyah on 2008-07-23
nevermind. :)

---

### Post by Jvaldezjr on 2008-07-23
I wasn't going to try another distro just to see if this is working.  I've accepted that I either need to use older drivers to work properly, or not update Kubuntu to a new release.  It's annoying, but not totally critical to my use.  I'm using Feisty now, everything works as well as I need it, so I'll keep using it until the next release improves on what I need Kubuntu to do now.  Asthetics aside, I only care about what's working underneath.  I'm not going to use a distro or release with newer drivers that won't work, when my current release is just as stable and works fine.

That said, I think it's more of an NVIDIA problem than it is with K/Ubuntu, and the fact that they STILL won't activate my message board account really pisses me off with them.  I've never had an NVboard account before, and I can't get any admins to email me back or activate my account.  Been like since I first posted this thread.

---

### Post by irlandes on 2008-07-30
I had this problem. I have done so much that I am lost as to where I got it. But, I hit a posting that said to go to System ==> Hardware drivers manager and enable the Nvidia driver.  When I did, it started an automatic download and install of the latest Nvidia driver.

When I rebooted, my resolution is perfect!  I did not get all the numbers off the driver but it did say 169.12.

It is late or I would try to find out what the exact release patch was.

---

### Post by Jvaldezjr on 2008-07-30
I'm pretty sure I tried that method and had the same problem.  It's been so long, I'm just gonna wait until 8.10 and move from there, I think.  Feisty support will be dead by then anyway.

---

### Post by linux_tech on 2008-07-30
You could try envy legacy (pre-8.04) or Envyng (8.04) if you want to automate 
the nvidia driver install.

---

### Post by Jvaldezjr on 2008-07-31
I'm not interested in autmating the process, I can install them manually just fine.  The problem is with the drivers themselves.

---

### Post by poekie on 2008-08-01
I had the same blank screen problems with the newest driver (173.14.12) but the trick was to add "nvidia_new" to the disabled modules as well, not just nv. (DISABLED_MODULES="nv nvidia_new") Also, nvidia-glx-new had to be removed. This combined with the steps of ~David resulted in a working X environment! Thanks :)

---

