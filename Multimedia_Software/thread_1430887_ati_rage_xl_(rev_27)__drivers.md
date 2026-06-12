---
title: "ati rage xl (rev 27)  drivers"
date: 2010-03-15
forum: Multimedia Software
---

### Post by bignol on 2010-03-15
I'm running a Compaq proliant ML310, 2.0ghz processor and 512 ram, jaunty.

I'm currently dealing with the video lag, fullscreen, games, video,even screen savers (pipes is the only one which seems to work right) all windowed or not. . I've gotten performance a little better by turning the hardware acceleration off in flash player. but yet, frame rate is  still choppy and sporadic. I've searched extensively for drivers, but can only find radeon type drivers. Envy almost killed me trying to fix the problems it caused. Does any one know a way to fix the lag, either with the terminal, direct downland or anything?

---

### Post by bignol on 2010-03-16
Furthermore, i can't even find out if there is a difference between radeon and rage. 

grrr... display problems

---

### Post by Mark Phelps on 2010-03-16
There are no ATI restricted drivers for your card.  

ATI dropped Linux support for the older cards a long time ago.  The open source driver, which have installed or would not be seeing a desktop, is all that is available.

For better video, if you stuck with ATI, you would have to get one of the newer HD 3x/4x/5x cards.

---

### Post by ShadowTek on 2010-03-16
I bought an old nVidia MMX440 for about $10 on ebay, and nVidia's restricted drivers still support it.

ATI has dropped the ball.

I suggest voting with your wallet.

---

### Post by bignol on 2010-03-16
> **ShadowTek said:**
> 
ATI has dropped the ball.

I suggest voting with your wallet.


lol. i was hoping it wouldnt come to that :-({|=

---

### Post by jilindi on 2010-10-12
I have a Tyan S2723 system board which has the integrated ATI Rage XL 8MB video.

On a fresh install of Lucid Lynx my best screen resolution was the 800x600.

After much Googling and tinkering, I got the thing working with much better screen resolutions. Instead of 4 Resolution choices in System/Preferences/Monitors, I now have 30 choices including 1024x768, 1280x1024, and 1440x1050. Below is the Xorg.conf that I created that finally works. I think the key was identifying my monitor capabilities, because the Xorg detection identified the video adapter, the Mach64 driver just fine. My monitor was "Unknown" and I provided the relevant data from the monitor's documentation. 

=================================================
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "extmod"
    Load  "record"
    Load  "dri"
    Load  "dri2"
    Load  "dbe"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "SGI-GDM-5411"
    VendorName   "SGI"
    ModelName    "GDM-5411"
    DisplaySize  403 302       # In millimeters
    HorizSync    30-121
    VertRefresh  48-160
     Option       "DPMS" "true"

EndSection


Section "Device"
    Identifier  "ATI-Rage-XL"
    Driver      "mach64"
    VendorName  "ATI Technologies Inc"
    BoardName   "Rage XL"
    BusID       "PCI:1:2:0"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "probe_sparse"           # [<bool>]
        #Option     "accel"                  # [<bool>]
        #Option     "crt_display"            # [<bool>]
        #Option     "composite_sync"         # [<bool>]
        #Option     "hw_cursor"              # [<bool>]
        #Option     "force_pci_mode"         # [<bool>]
        #Option     "dma_mode"               # <str>
        #Option     "agp_mode"               # <i>
        #Option     "agp_size"               # <i>
        #Option     "local_textures"         # [<bool>]
        #Option     "buffer_size"            # <i>
        #Option     "tv_out"                 # [<bool>]
        #Option     "tv_standard"            # <str>
        #Option     "mmio_cache"             # [<bool>]
        #Option     "test_mmio_cache"        # [<bool>]
        #Option     "panel_display"          # [<bool>]
        #Option     "reference_clock"        # <freq>
        #Option     "shadow_fb"              # [<bool>]
        #Option     "sw_cursor"              # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "RenderAccel"            # [<bool>]
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "ATI-Rage-XL"
    Monitor    "SGI-GDM-5411"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
=================================================

---

