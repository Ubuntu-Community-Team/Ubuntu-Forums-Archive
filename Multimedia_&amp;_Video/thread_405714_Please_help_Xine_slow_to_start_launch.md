---
title: "Please help Xine slow to start launch"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by Wielenga on 2007-04-10
I installed Xubuntu on a real low spec machine and it works! Opera is great and I am happy with the perfomance of the Xserver.

I use gxine for playing back wmv content and that works as well but launching xine takes forever. To be honest there are of codecs in the codec folder and pruning them may help but even when I rename the codecsfolder, just starting gxine takes forever. 

Other players are around but all seem to use the xine engine. Real media player in contrast launches ok (well for such a low spec machine..

Spec:

Sony Vaio PCG-C1XD
PII
64 Megs
12 G HD

Any suggestions?

---

### Post by heimo on 2007-04-10
> **Wielenga said:**
> Any suggestions?


Yeah. Try VLC for media player and check if DSL would be more appropriate distribution.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by Wielenga on 2007-04-10
Would love to try DSL eh, no CD rom drive .... have to figure out an install from HD partition or Network :-) No time for that at the moment.

Hey this is ubuntu forum why are pushing people me towards DSL :-) (not the first time...)

Will try VLC.

To be honest I am quite impressed with Xubuntu (compared to gatesware)

---

### Post by Tylerdirden on 2007-08-03
Hi,

I'm trying to get Ubuntu / Xubuntu working on my C1XD as well, but am having no luck with the video resolution as it always defaults to 1024x728 even though I've had a play around in the Xorg.conf file ..
Did you manage to get it working okay ? If so, please share how ! :)

Thx in advance

---

### Post by Wielenga on 2007-08-04
a bit careful with cut and paste but here you go.
-------------------------------------- cut from below
Section "Module"
#load    "glx"
load 	"dbe"
 
    Subsection "extmod"
    Option "omit xfree86-dga"
    EndSubSection    

EndSection

Section "Files"
    RgbPath	"/usr/X11R6/lib/X11/rgb"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/URW/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"
EndSection

Section "ServerFlags"
#    NoTrapSignals
#    DontZap
#    DontZoom
#    DisableVidModeExtension
#    AllowNonLocalXvidtune
#    DisableModInDev
#    AllowNonLocalModInDev
 
#    Option "blank time"    "2"
    Option "standby time"  "2"
    Option "suspend time"  "4"
    Option "off time"      "5"

EndSection

Section "Keyboard"
    Protocol	"Standard"
    AutoRepeat	500 5
    XkbKeymap   "xfree86(es)"
EndSection

Section "Pointer"
    Protocol    "PS/2"
    Device      "/dev/psaux"
    Emulate3Buttons
    Emulate3Timeout    50
EndSection

Section "Monitor"
    Option      "DPMS"
    Identifier  "Generic Multisync"
    VendorName  "Unknown"
    ModelName   "Unknown"
    HorizSync   30-64
    VertRefresh 50-100
    
# 1024x480
Modeline "1024x480"    65    1024 1032 1176 1344   480  491  493  525 -hsync -vsync

EndSection

Section "Device"
    Identifier	"NeoMagic"
    Driver      "neomagic"
    VideoRam	2560
    Option "override_validate_mode"
EndSection

Section "Screen"
    Driver      "svga"
    Device      "NeoMagic"
    Monitor     "Generic Multisync"
    DefaultColorDepth 16
    Subsection "Display"
        Depth       8
        Modes       "1024x480"
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1024x480"
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1024x480"
    EndSubsection
EndSection
To here --------------------------------------------------------------------------------------------


Tested with Unbuntu, xubutu edgy and feisty. If you mail me to nospam at wielenga dot plus dot net I will mail ti to you :-)

---

