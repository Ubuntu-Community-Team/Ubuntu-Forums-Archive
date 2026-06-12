---
title: "Need help setting up Tv-Out (nvidia)"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by tHub on 2007-06-24
I have the latest nvidia driver installed (through Envy), it wont detect my TV.The nvidia Windows driver wont detect it as well, i have to use the "Force TV Detection" option, which isn't present in the linux version of the driver.

So i was trying to follow this tutorial ([https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition](https://help.ubuntu.com/community/NvidiaTVOutNewbieEdition)) but haven't been successful. 

Heres my edited xorg.conf:

[PHP]
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0 "Screen[0]"
    Screen 1 "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
    Identifier     "Monitor[0]"
    Option         "DPMS"
EndSection


Section "Monitor" 
        Identifier "Monitor[1]"
        HorizSync 30-50
        VertRefresh 60
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    screen 0
    BusID          "PCI:2:0:0"
EndSection

Section "Device" 
        Driver          "nvidia" 
        Identifier      "Device[1]" 
        Screen 1 
        Option          "TVOutFormat" "SVIDEO" 
        Option          "TVStandard" "PAL-M" 
        Option          "ConnectedMonitor" "Monitor[1]" 
        BusID           "PCI:2:0:0" 
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen" 
        Device "Device[1]" 
        Identifier "Screen[1]" 
        Monitor "Monitor[1]" 
        DefaultDepth 24 
        SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
        EndSubSection    
EndSection[/PHP]

Nothing happens at the TV nor at the nvidia-settings, only my monitor is found at the Server Display Configuration tab.

Any ideas? I can't live without tv-out :(

---

### Post by markkun on 2007-06-25
Post your Xorg log (/var/log/Xorg.0.log) and maybe there is an answer.

In my GeForce 3 Ti200, tv-out didn't work what ever I tried.

---

### Post by tHub on 2007-06-25
Here's the part that i think is important:
> (II) NVIDIA(0): Detected PCI Express Link width: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GT at PCI:2:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(0): Samsung SyncMaster (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[COLOR="Green"](**) NVIDIA(1): Option "ConnectedMonitor" "Monitor[1]"
(**) NVIDIA(1): Option "TVStandard" "PAL-M"
(**) NVIDIA(1): Option "TVOutFormat" "SVIDEO"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing SVIDEO output
(**) NVIDIA(1): TV Standard string: "PAL-M"[/COLOR]
(II) NVIDIA(1): NVIDIA GPU GeForce 7300 GT at PCI:2:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.73.22.51.01
(II) NVIDIA(1): Detected PCI Express Link width: 8X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 7300 GT at PCI:2:0:0:
(--) NVIDIA(1):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(1): Samsung SyncMaster (CRT-0): 400.0 MHz maximum pixel clock
[COLOR="Red"](EE) NVIDIA(1): Unable to find available Display Devices for screen 1.[/COLOR]

---

### Post by tHub on 2007-06-25
It's working!
I added these (part of a tutorial to get dual-view on slackware):

> #Option "TwinViewOrientation" "Device[0] LeftOf Device[1]"
#Option "TwinView" "true"
#Option "ConnectedMonitor" "lcd,tv"
#Option "MetaModes" "Device[0]: 1280x1024, Device[1]: 800x600"

at the Screen section (of Device[0], which would be the LCD monitor), restarted X and got image at the TV, but only at the tv.So i edited xorg.conf again and commented those lines i had added and got image at both LCD monitor and TV.

Pretty lucky i must say lol

[img]http://img45.imageshack.us/img45/8372/tvouths7.png[/img]

---

### Post by tHub on 2007-06-25
Man what a mess.
Ok** i got it to work** by copying and pasting that stuff, then i used that "Save to X Configuration File" option and it stopped working again as this option messes with the whole xorg.conf.So i had to check what exactly was the option that made it work.

Here's my working xorg.conf, ill highlight what's important:

(ONLY THE PARTS THAT AFFECT THE VIDEO CONFIGURATION)

> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
   [COLOR=Red] Screen      1  "Screen1" LeftOf "Screen0"[/COLOR] # [COLOR=Navy]TV on the left of my Monitor[/COLOR]
[COLOR=Gray]    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
[/COLOR]EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:2:0:0"
    Screen          0
[COLOR=Red]    Option         "UseDisplayDevice"   "crt-0, tv-0"[/COLOR] # [COLOR=Navy]it won't work without this, i think it forces the "creation" of the TV display.[/COLOR]
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:2:0:0"
    Screen          1
    Option         "TVOutFormat" "SVIDEO" 
    Option         "TVStandard" "PAL-M" 
   [COLOR=Red] Option         "UseDisplayDevice" "TV"[/COLOR] # [COLOR=Navy]This alone wouldnt work, i would get an error in the xorg log saying there was no TV available. (thats why i think the 'crt-0, tv-0' parameter forces the creation of the tv display.Maybe it will only work when the TV is detected by the driver, which was not my case.[COLOR=Red]BTW, "UseDisplayDevice" replaced  "ConnectedMonitor" that is still in most tutorials.[/COLOR][/COLOR]
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x1024 +0+0 TV: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen" 
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "TV: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSectionRemember: don't use that "Save to X Configuration File" option, or it will stop working as it wont use the "crt-0, tv-0" parameter and you'll get an error saying there was no display device for Screen1 or something.

You might still have to go to nvidia-settings to enable the TV and set the Tv-Out type (twinview/separated X view).

And finally, no friggin errors in the log:

> (**) NVIDIA(1): Option "TVStandard" "PAL-M"
(**) NVIDIA(1): Option "TVOutFormat" "SVIDEO"
(**) NVIDIA(1): Option "MetaModes" "TV: 800x600 +0+0"
(**) NVIDIA(1): Option "UseDisplayDevice" "TV"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing SVIDEO output
(**) NVIDIA(1): TV Standard string: "PAL-M"
(II) NVIDIA(1): NVIDIA GPU GeForce 7300 GT at PCI:2:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.73.22.51.01
(II) NVIDIA(1): Detected PCI Express Link width: 8X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
([COLOR=Green]--) NVIDIA(1): Connected display device(s) on GeForce 7300 GT at PCI:2:0:0:
(--) NVIDIA(1):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)[/COLOR]
(--) NVIDIA(1): Samsung SyncMaster (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
[COLOR=Green](II) NVIDIA(1): Option "UseDisplayDevice" "TV" converted to "TV-0".
(II) NVIDIA(1): Assigned Display Device: TV-0[/COLOR]
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "TV:800x600+0+0"
[COLOR=Green](II) NVIDIA(1): Virtual screen size determined to be 800 x 600[/COLOR]

I think the effect of these changes is the same of the "Force TV detection" option present in the Windows Driver.

---

### Post by gtr225 on 2007-06-26
Hi I'm having trouble getting the Tv-out on my geforce 6200 to work and any help would be greatly appreciated. I tried some of the suggestions listed here but it still doesn't work. Here's my xorg.conf```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:39:38 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen 0 "Screen[0]"
    Screen 1 "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor[0]" #Primary display
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor" 
    Identifier     "TV" #TV
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30-50
    VertRefresh     60
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    BusID	   "PCI:1:11:0"
    Screen 0
    Option         "UseDisplayDevice" "crt-0, tv-0"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Device" 
    Driver          "nvidia" 
    Identifier      "Device[1]" 
    Screen 1 
    Option          "TVOutFormat" "SVIDEO" 
    Option          "TVStandard" "NTSC-M" 
    Option          "UseDisplayDevice" "TV" 
    BusID           "PCI:1:11:0" 
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x1024 +0+0 TV: 800x600 +0+0"    
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen" 
     Device        "Device[1]" 
     Identifier    "Screen[1]" 
     Monitor       "TV" 
     DefaultDepth   24 
     Option        "metamodes" "TV: 800x600 +0+0"
     SubSection    "Display" 
         Depth      24 
         Modes     "1024x768" "800x600" "640x480"
     EndSubSection    
EndSection
```and here's what the log says
```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux gtr225-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 26 17:38:09 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen[0]" (0)
(**) |   |-->Monitor "Monitor[0]"
(**) |   |-->Device "Device[0]"
(**) |-->Screen "Screen[1]" (1)
(**) |   |-->Monitor "TV"
(**) |   |-->Device "Device[1]"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "0"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7124 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7125 card 0e11,b165 rev 03 class 03,00,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,2418 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2410 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2411 card 8086,2411 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2412 card 8086,2412 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2413 card 8086,2413 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:05:0: chip 125d,1988 card 0e11,b19d rev 12 class 04,01,00 hdr 00
(II) PCI: 01:08:0: chip 1317,0985 card 1317,0574 rev 11 class 02,00,00 hdr 00
(II) PCI: 01:0b:0: chip 10de,0221 card 1b13,0221 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[2] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[3] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x40000000 - 0x420fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x5fffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:1:0) Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] rev 3, Mem @ 0x44000000/26, 0x42100000/19
(--) PCI:*(1:11:0) nVidia Corporation NV44A [GeForce 6200] rev 161, Mem @ 0x40000000/24, 0x50000000/28, 0x41000000/24
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
(II) Active PCI resource ranges:
	[0] -1	0	0x42000000 - 0x420003ff (0x400) MX[B]
	[1] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[2] -1	0	0x50000000 - 0x5fffffff (0x10000000) MX[B](B)
	[3] -1	0	0x40000000 - 0x40ffffff (0x1000000) MX[B](B)
	[4] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[5] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[6] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[7] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[8] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0x42100000 - 0x4217ffff (0x80000) MX[B](B)
	[1] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x42000000 - 0x420003ff (0x400) MX[B]
	[1] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[2] -1	0	0x50000000 - 0x5fffffff (0x10000000) MX[B](B)
	[3] -1	0	0x40000000 - 0x40ffffff (0x1000000) MX[B](B)
	[4] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[5] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[6] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[7] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[8] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x42100000 - 0x4217ffff (0x80000) MX[B](B)
	[1] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
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
	[4] -1	0	0x42000000 - 0x420003ff (0x400) MX[B]
	[5] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[6] -1	0	0x50000000 - 0x5fffffff (0x10000000) MX[B](B)
	[7] -1	0	0x40000000 - 0x40ffffff (0x1000000) MX[B](B)
	[8] -1	0	0x42100000 - 0x4217ffff (0x80000) MX[B](B)
	[9] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[13] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[14] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[15] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[16] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
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
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:0b:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x42000000 - 0x420003ff (0x400) MX[B]
	[5] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[6] -1	0	0x50000000 - 0x5fffffff (0x10000000) MX[B](B)
	[7] -1	0	0x40000000 - 0x40ffffff (0x1000000) MX[B](B)
	[8] -1	0	0x42100000 - 0x4217ffff (0x80000) MX[B](B)
	[9] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[13] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[14] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[15] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[16] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x42000000 - 0x420003ff (0x400) MX[B]
	[5] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[6] -1	0	0x50000000 - 0x5fffffff (0x10000000) MX[B](B)
	[7] -1	0	0x40000000 - 0x40ffffff (0x1000000) MX[B](B)
	[8] -1	0	0x42100000 - 0x4217ffff (0x80000) MX[B](B)
	[9] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[18] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[19] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[20] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[21] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "MetaModes" "CRT: 1280x1024 +0+0 TV: 800x600 +0+0"
(**) NVIDIA(0): Option "UseDisplayDevice" "crt-0, tv-0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 at PCI:1:11:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.11.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:11:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(WW) NVIDIA(0): Requested display device "TV-0" not available; only the
(WW) NVIDIA(0):     display device "CRT-0" will be used.
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): Error while parsing offset information in mode description
(WW) NVIDIA(0):     "1280x1024+0+0TV:800x600+0+0"
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TVStandard" "NTSC-M"
(**) NVIDIA(1): Option "TVOutFormat" "SVIDEO"
(**) NVIDIA(1): Option "MetaModes" "TV: 800x600 +0+0"
(**) NVIDIA(1): Option "UseDisplayDevice" "TV"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing SVIDEO output
(**) NVIDIA(1): TV Standard string: "NTSC-M"
(II) NVIDIA(1): NVIDIA GPU GeForce 6200 at PCI:1:11:0 (GPU-0)
(--) NVIDIA(1): Memory: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.44.a2.11.00
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 6200 at PCI:1:11:0:
(--) NVIDIA(1):     CRT-0
(--) NVIDIA(1): CRT-0: 400.0 MHz maximum pixel clock
(WW) NVIDIA(1): Option "UseDisplayDevice" requested "TV", but no unused TVs
(WW) NVIDIA(1):     are available.
(II) NVIDIA(1): Option "UseDisplayDevice" "TV" converted to "".
(WW) NVIDIA(1): Unable to find any of the requested display device "" in the
(WW) NVIDIA(1):     list of available display devices "".
(EE) NVIDIA(1): Unable to find available Display Devices for screen 1.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x41000000 - 0x41ffffff (0x1000000) MX[B]
	[1] 0	0	0x50000000 - 0x5fffffff (0x10000000) MX[B]
	[2] 0	0	0x40000000 - 0x40ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0x42000000 - 0x420003ff (0x400) MX[B]
	[8] -1	0	0x41000000 - 0x41ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x50000000 - 0x5fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x40000000 - 0x40ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x42100000 - 0x4217ffff (0x80000) MX[B](B)
	[12] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[18] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[19] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
```

---

### Post by tHub on 2007-06-26
This crap is still giving me a hard time, i get it to work, then i reboot and its gone, then i have to mess around with the xorg.conf again untill its back working.

I get that same friggin annoying error when it doesnt work:

(EE) NVIDIA(1): Unable to find available Display Devices for screen 1.

Here's my current xorg.conf

[PHP]# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "abnt2"
    Option         "XkbLayout" "br"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Resolution" "100"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:2:0:0"
    Screen          0
    Option         "UseDisplayDevice"   "CRT,TV"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:2:0:0"
    Screen          1
    Option         "TVOutFormat" "SVIDEO" 
    Option         "TVStandard" "PAL-M" 
    Option         "UseDisplayDevice" "TV"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x1024 +0+0 TV: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
#    Option "TwinView" "true"
    Option "ConnectedMonitor" "CRT,TV"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "TV: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

[/PHP]

---

### Post by gtr225 on 2007-06-26
> **tHub said:**
> This crap is still giving me a hard time, i get it to work, then i reboot and its gone, then i have to mess around with the xorg.conf again untill its back working.

I get that same friggin annoying error when it doesnt work:

(EE) NVIDIA(1): Unable to find available Display Devices for screen 1.

Here's my current xorg.conf

[PHP]# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "abnt2"
    Option         "XkbLayout" "br"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Resolution" "100"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:2:0:0"
    Screen          0
    Option         "UseDisplayDevice"   "CRT,TV"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:2:0:0"
    Screen          1
    Option         "TVOutFormat" "SVIDEO" 
    Option         "TVStandard" "PAL-M" 
    Option         "UseDisplayDevice" "TV"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1280x1024 +0+0 TV: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
#    Option "TwinView" "true"
    Option "ConnectedMonitor" "CRT,TV"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "TV: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

[/PHP]

I've been having the same exact problem :-/

---

### Post by castoroil97 on 2007-06-28
One possible problem is

"TVStandard" "PAL-M"  

The american tv standard is NTSC 

I do not know if it is NTSC-M,

But I think that may be the key

---

### Post by gtr225 on 2007-06-28
I got mine set to NTSC-M and it still doesn't work.

---

### Post by tHub on 2007-07-07
I'm from Brazil, our standard is PAL-M, my tv works with NTSC too.

Anyway, i got mine to work with that xorg.conf

---

### Post by gtr225 on 2007-07-08
Can someone please post a complete **working** xorg.conf for NTSC using S-video?

---

