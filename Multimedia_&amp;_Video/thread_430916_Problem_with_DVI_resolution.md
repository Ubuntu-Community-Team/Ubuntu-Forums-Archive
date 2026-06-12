---
title: "Problem with DVI resolution"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by zivziv on 2007-05-02
I've installed Ubuntu 7.04 .
I have 32 Inch TV (Metz) that I use as a monitor.
Here are the technical details of the hardware:

CPU : Pentium 4HT 2800 Mhz
Motherboard: Asus P4S800-MX
Chipset: SIS 661FX

Video Adapter : NVIDIA GeForce FX 5200 (128 MB)


When I connect as CRT I can see as regular resolution&#1509;
However when I try to connect the DVI (which took my a while – after I use 
[This]("http://ubuntuforums.org/showthread.php?t=414857&highlight=DVI+viewsonic")

I get 640x480 resolution  and I can't change it.

What do I need to do to fix this and work with DVI in the correct mode ?????? 

Some Info

lspci : 

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)


/var/log/Xorg.log.0:



(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEdidDpi" "false"
(**) NVIDIA(0): Option "DPI" "48 x 48"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.87.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     KGC KLC 2718UG (DFP-0)
(--) NVIDIA(0): KGC KLC 2718UG (DFP-0): 135.0 MHz maximum pixel clock
(--) NVIDIA(0): KGC KLC 2718UG (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1920x1440"; removing.
(WW) NVIDIA(0): No valid modes for "1920x1200"; removing.
(WW) NVIDIA(0): No valid modes for "1856x1392"; removing.
(WW) NVIDIA(0): No valid modes for "1792x1344"; removing.
(WW) NVIDIA(0): No valid modes for "1680x1050"; removing.
(WW) NVIDIA(0): No valid modes for "1600x1200"; removing.
(WW) NVIDIA(0): No valid modes for "1440x900"; removing.
(WW) NVIDIA(0): No valid modes for "1400x1050"; removing.
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
(**) NVIDIA(0): DPI set to (48, 48); computed from "DPI" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

(II) NVIDIA(0): Built-in logo is bigger than the screen.
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

(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!



Xorg,conf:


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

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us he"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "NVIDIA GeForce 5200"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        VideoRam        131072
        Option          "UseFBDev" "true"
        Option          "UseEdidDpi" "false"
        Option          "Dpi" "48 x 48"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Metz"
        Option          "DPMS"
        HorizSync       28-96
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA GeForce 5200"
        Monitor         "Metz"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by GarlicFish on 2007-05-02
You could try setting the option

Option "IgnoreEDID" "true"

into the /etc/X11/xorg.conf
Section "Device"

This worked for me when my LCD would not run at native resolution over DVI.
Check the nvidia-settings utility, there is a field that shows what the nvidia driver has read as the "Native" resolution of the screen.  also, you can start X in debug level 6 then check the xorg.log.  There is a section in the log that shows the EDID data received from the screen.

My LCD reports different capabilities for VGA and DVI but once overrridden, works fine!

---

### Post by zivziv on 2007-05-03
I've tried to add 

Option "IgnoreEDID" "true"

into the /etc/X11/xorg.conf
Section "Device"

But still nothing.

Also when running nvidia-settings utility I see that I can't change the resolution and it stay 
640x480 which is the "Native" resolution .



I also tried to change the xorg.conf file but nothing works.

Any Idea  ?

---

### Post by vegarede on 2007-05-07
The option "IgnoreEDID" is deprecated.

Instead,  you must to use:                        

                               Option   "UseEDID"    "FALSE"         

See you.

---

### Post by karlhm76 on 2007-07-19
Hi there, I'm having the same problem but when I use the option UseEDID false it switches X into 640x480 when I use the VGA connector as well as when I use the DVI connector.

I have saved the EDID file from the monitor when it is connected with the VGA connector. Can I use this when I connect the monitor using the DVI connector?

if so where do I put the option?

Thanks

---

