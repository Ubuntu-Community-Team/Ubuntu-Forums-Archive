---
title: "Projector display problems"
date: 2007-11-15
forum: Mythbuntu
---

### Post by Daminator on 2007-11-15
I had a real fight a few months ago to get a decent display from my BenQ W100 projector. I never did managed to get a wide screen image outputting but spent so long trying that I settled on a 1024x768 image with wide screen 'display size' settings.

This worked ok, and still displays ok, but I've had a problem since upgrading to Ubuntu 7.10. The main GUI of Ubuntu works fine, but when I press CONTROL + ALT + F1 to log in without the GUI the screen can not be displayed. I just get an out of range or invalid message from my monitor.

I don't need to do this much, but do need it.

I can see the boot up of the machine when the computer starts, so it's not like that mode can't be displayed at all, and I know this used to work fine. But now going to CONTROL + ALT + F1 is invalid.

Also, the display seems fine in Mythfrontend, but when I watch tv or play recordings, I need to set the display to 4x3 in order for them to look right. This seems weird to me. Any ideas?

Can any of you in the know check out my xorg.conf file and tell me where I'm going wrong?

If anyone can get wide screen resolutions going on my projector then I'll be in your debt forever!

Cheers
Damian


xorg.conf:

#Section "ServerFlags"
#       Option "AIGLX" "OFF"
#EndSection
#Section "Extensions"
#    Option         "Composite" "Enable"
#EndSection

Section "ServerLayout"
       Identifier      "Default Layout"
 screen "Default Screen" 0 0
       Inputdevice     "Generic Keyboard"
       Inputdevice     "Configured Mouse"
EndSection

Section "Files"

       # path to defoma fonts
       Fontpath        "/usr/share/fonts/X11/misc"
       Fontpath        "/usr/share/fonts/X11/cyrillic"
       Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
       Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
       Fontpath        "/usr/share/fonts/X11/Type1"
       Fontpath        "/usr/share/fonts/X11/100dpi"
       Fontpath        "/usr/share/fonts/X11/75dpi"
       Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
       Load            "i2c"
       Load            "bitmap"
       Load            "ddc"
       Load            "extmod"
       Load            "freetype"
       Load            "glx"
       Load            "int10"
       Load            "vbe"
       Load            "dbe"
       Load            "vnc"
EndSection

Section "InputDevice"
       Identifier      "Generic Keyboard"
       Driver          "kbd"
       Option          "CoreKeyboard"
       Option          "XkbRules"      "xorg"
       Option          "XkbModel"      "pc105"
       Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "CorePointer"
       Option          "Device"        "/dev/input/mice"
       Option          "Protocol"      "ImPS/2"
       Option          "ZAxisMapping"  "4 5"
       Option          "Emulate3Buttons"       "true"
EndSection

Section "Monitor"

       #     HorizSync    31-82
       #     VertRefresh  48-85
       #     HorizSync    31-69
       #     VertRefresh  59-85
       Identifier      "BenQ W100"
       Displaysize     347     195
       Option          "ModeValidation"        "NoDFPNativeResolutionCheck"
       #       Option  "ModeValidation"        "NoDFPNativeResolutionCheck, AllowNon60HzDFPModdes"
EndSection

Section "Device"
       Identifier      "nVidia Corporation NV34 [GeForce FX 5200]"
       Driver          "nvidia"
       Option          "AddARGBVisuals"        "True"
       Option          "AddARGBGLXVisuals"     "True"
       Option          "NoLogo"        "True"
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Device          "nVidia Corporation NV34 [GeForce FX 5200]"
       Monitor         "BenQ W100"
       Defaultdepth    24
       Option          "NoDDC"
       Option          "ModeValidation"        "NoDFPNativeResolutionCheck"
       Option          "AddARGBGLXVisuals"     "True"
       Option          "SecurityTypes" "VncAuth"
       Option          "UserPasswdVerifier"    "VncAuth"
       Option          "PasswordFile"  "/root/.vnc/passwd"
       SubSection "Display"

               #               Modes       "1280x720_60" "1280x720"
               ##              Modes       "1024x768_70" "1024x768_60" "1024x768" "800x600_70" "800x600_60" "800x600"
               ##              Modes       "1920x1080_60" "1280x720_60" "720x480_60"
               Depth   24
#               Modes           "1024x768_60"   "1024x768"      "800x600_60"    "800x600"
               Modes           "1024x768_60"   "1024x768"      "800x600_60"    "800x600" "640x480_60" "640x480" "640x400_60" "640x400" "320x240_60"    "320x240"

       EndSubSection
EndSection

#Section "Etensions"
#    Option         "Composite" "Enable"
#EndSection

---

