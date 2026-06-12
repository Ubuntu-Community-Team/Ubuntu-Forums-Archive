---
title: "DVI-D Dimension wrong"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by flando on 2007-04-28
Hi guys

My PC runs Dapper.
I use nvidia GeForce6150 which has a DVI-D output and normal VGA.
"Monitor" is a 46 inch LCD (Sharp 46xd1e Full HD) using a DVI-D to HDMI cable or VGA.

I want to use DVI-D to HDMI (digital) rather than vga (analog). 

I face the problem that via DVI-D to HDMI the desktop does not fit to the screen.
The desktop appears bigger than the LCD screen, means I cannot see the top menu or the bottom taskbar at all. Additionally I don't have audio, thought via DVI-D there should also be audio transfered?
Via analog VGA all looks fine.
If I connect to the LCD via analog VGA all graphic issues work fine.

xdpyinfo gives me the following information (xdpyinfo | grep "dimens|resolu"):

via DVI-D:
dimension: 1920x1080 pixels (1016x571 milimeters)
resolution: 48x48 dpi

via VGA:
dimension: 1280x1024 pixels (677x541 milimeters)
resolution: 48x48 dpi

physically the Sharp LCD screen has:
length: 1020 mm
width: 577mm

Anyone any idea what could help?
I added some more information below (xorg.conf, x-log)
Many thanks, Fritz
----------------------------------------------

xserverrc holds the following command:
exec /usr/bin/X11/X -nolisten tcp

Here some output from X.0.log:
[COLOR="SeaGreen"]X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 x86_64
Current Operating System: Linux ubuntu1 2.6.15-28-amd64-generic #1 SMP PREEMPT Tue Mar 13 20:51:52 UTC 2007 x86_64
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 28 19:31:02 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "LCD Sharp"
(**) |   |-->Device "nvidia geforce 6150"

(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9746
        Module class: X.Org Video Driver

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEdidDpi" "false"
(**) NVIDIA(0): Option "DPI" "48 x 48"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.33.07
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     SHARP HDMI (DFP-0)
(--) NVIDIA(0): SHARP HDMI (DFP-0): 310.0 MHz maximum pixel clock
(--) NVIDIA(0): SHARP HDMI (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1920x1200"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1920x1080"
(II) NVIDIA(0):     "1680x1050"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(**) NVIDIA(0): DPI set to (48, 48); computed from "DPI" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

(II) NVIDIA(0): Setting mode "1920x1080"
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
(II) Setting vga for screen 0.[/COLOR]



Here my xorg.conf:
[COLOR="Navy"]
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
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
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "nvidia geforce 6150"
        Driver          "nvidia"
        BusID           "PCI:0:5:0"
        VideoRam        131072
        Option          "UseFBDev"              "true"
        Option          "UseEdidDpi"            "false"
        Option          "Dpi"                   "48 x 48"
EndSection

Section "Monitor"
        Identifier      "LCD Sharp"
        Option          "DPMS"
        HorizSync       28-96
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nvidia geforce 6150"
        Monitor         "LCD Sharp"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1200" "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1200" "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1920x1200" "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1200" "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1200" "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1200" "1920x1080" "1680x1050" "1280x1024" "1024x768" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
[/COLOR]

---

### Post by herrerads on 2007-05-02
The only real help I can give you here is to let you know that DVI-D is Video only.  HDMI is both Audio/video but the source would have to be HDMI as well.  The resolution you posted sounds like it's for a 1080p.  Try using 1280x720 for a 720p resolution.

---

