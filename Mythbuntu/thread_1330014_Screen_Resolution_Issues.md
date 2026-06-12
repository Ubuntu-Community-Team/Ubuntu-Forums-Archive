---
title: "Screen Resolution Issues"
date: 2009-11-18
forum: Mythbuntu
---

### Post by gcasa on 2009-11-18
Good Evening All!  My screen resolution is not quite right.  Valid resolutions according to the documentation are:

[FONT=Courier New]Mode Resolution Refresh rate
VGA 640x480 60Hz
WVGA 848x480 60Hz
SVGA 800x600 60Hz
XGA 1024x768 60Hz
WXGA 1280x720 60Hz
WXGA 1280x768 60Hz
WXGA 1360x768 60Hz[/FONT]

If I set the Modes to "1024x768" "800x600" "640x480"

[FONT=Verdana]then I get a black screen.

If I set it as below, it works @ 1360x768 but extends well beyond the frame of the TV.  I turned on the TV's WXGA features.

My Xorg.0.log states:Unable to read EDID for display device CRT-0

Question: ***How do I get the desktop to fit on the monitor (TV)?***
[/FONT] 
Any help would be greatly appreciated!!!  :p

I have a fresh install of MythBuntu 9.10 with default settings.  My hardware is:
Toshiba 42HP66 (LCD TV)
nVidia GeForce4 MX 440 (video card on VGA output)
NVIDIA Driver Version 96.43.13

My xorg.conf is:
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

Section "Screen"
    Identifier      "Default Screen"
    Device          "nVidia Card"
    DefaultDepth     24
    Monitor         "Monitor0"
    SubSection      "Display"
        Depth        24
        Modes       "1360x768" "1280x768" "1280x720" "1024x768" "800x600"
"848x480" "640x480"
    EndSubSection
    Option          "AddARGBGLXVisuals" "True"
EndSection

Section "Module"
        Load        "glx"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Toshiba"
    ModelName      "42HP66"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier            "nVidia Card"
    Driver            "nvidia"
    Option          "NoLogo"        "True"
    VendorName      "NVIDIA Corporation"
EndSection

THANK YOU VERY MUCH!!!
glenn

---

### Post by SiHa on 2009-11-18
I think you'll find you've hit the issue of 'Overscan'. Most TV's, even LCD's scale the input image so that the edges are off-screen. It was originally so that the ragged edges of analogue signals, and the teletext data at the top of the screen didn't show up.

It looks like you're using VGA/DVI(or HDMI) to connect?
If so, there's not much that can be done to fit the whole desktop onto the screen, unless your TV has an option to turn it off (my Panasonic does).

What you can do though, is tell Myth to fit it's display within the visible portion of the screen.

There's a screen setup wizard where you drag a couple of markers to the visible corners of the screen. Personally I find this a bit flaky. I prefer to adjust it manually (TV Settings -> Appearance -> GUI Size IIRC). The offset will move the top-left corner, and then subtract twice the offset from the screen resolution to give you the new GUI size.

ie, 1360x768 resolution, offset of 30,10 would give a GUI size of 1300x748.

One thing the Wizard is useful for is finding out the offset to start of with.

---

### Post by utar on 2009-11-18
Looking at Toshiba's website I am confused about your TV as the panel size is stated as 1024*768, which is not 720p although the website says it is.  This could be why 1368*768 extends so far past the frame of your TV.

Notwithstanding the above I personally would recommend you connect via a DVI to HDMI adapter as these tend to minimise overscan issues.  In addition the picture quality is better.


Utar

---

### Post by SiHa on 2009-11-18
Just one point, I still get overscan on my Panasonic wether I connect via S-Video, DVI or HDMI. VGA, on the other hand doesn't.

---

### Post by gcasa on 2009-11-18
I am at work right now but will try the setup later tonight.  Thank you very much for your assistance!!!:D

glenn

---

