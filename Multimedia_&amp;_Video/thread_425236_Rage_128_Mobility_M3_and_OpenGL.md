---
title: "Rage 128 Mobility M3 and OpenGL?"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by drink on 2007-04-27
I'm trying to find information on using my Rage 128's 3D acceleration in Ubuntu Feisty. So far I have had no luck. All the guides I can find with google are about using nonstandard drivers with XFree, and say nothing about Xorg. Little help?

---

### Post by rooter666 on 2007-04-29
3D acceleration work only in 16bit desktop, in 24 bit NOT working

my xorg.conf on dell c600 with  ATI Technologies Inc Rage Mobility M3 AGP 2x
> Section "Device"
        Identifier      "ATI Technologies Inc Rage Mobility M3 AGP 2x"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        VendorName "Unknown"
        ModelName "Unknown"
        HorizSync 31.5-48.5
        VertRefresh 50-70
        # 1024x768 @ 60 Hz, 48.4 kHz hsync
        Modeline "1024x768" 65 1024 1032 1176 1344 768 771 777 806 -hsync -vsync

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Rage Mobility M3 AGP 2x"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection


marek@hellfire:~$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

marek@hellfire:~$ glxgears 
2482 frames in 5.0 seconds = 496.251 FPS
2467 frames in 5.0 seconds = 493.365 FPS
2469 frames in 5.0 seconds = 493.765 FPS

---

### Post by drink on 2007-04-30
I figured it out enough to get OpenGL working, now I'm trying to get Beryl or Compiz working... will be interesting.

I have an IBM Thinkpad A21p with a 1600x1200 monitor. The following is the info I used for modes.

```
Section "Monitor"
  HorizSync  31-77
  Identifier  "Monitor[0]"
  ModelName  "AutoDetected"
  VendorName  "AutoDetected"
  VertRefresh  50-77
  UseModes  "Modes[0]"
EndSection

Section "Modes"
  Identifier "Modes[0]"
  Modeline "640x480" 27.96 640 656 720 864 480 480 485 501
  Modeline "800x600" 43.68 800 816 928 1072 600 600 606 626
  Modeline "1024x768" 71.39 1024 1040 1216 1400 768 768 776 802
  Modeline "1152x864" 90.48 1152 1168 1384 1568 864 864 873 902
  Modeline "1280x960" 111.82 1280 1296 1552 1736 960 960 970 1003
  Modeline "1280x1024" 119.28 1280 1296 1552 1736 1024 1024 1035 1070
  Modeline "1600x1200" 160.16 1600 1616 1968 2208 1200 1200 1212 1253
  Modeline "1600x1200" 167.23 1600 1616 1968 2208 1200 1200 1212 1253
EndSection
```

And yes, I did discover that I could only do 16 bpp.

See also [http://tuxmobil.org/XF86Config_4_ibm_a21p.html](http://tuxmobil.org/XF86Config_4_ibm_a21p.html)

---

### Post by CalcProgrammer1 on 2007-05-17
I have an A21p as well, I have OpenGL games running and screensavers.  Has anyone gotten Xgl, Beryl, or Compiz working?

I ran the Desktop Effects (in 7.04) but it said Couldn't enable desktop effects.

Also, does anyone know how to turn on the TV-OUT from the Rage M3?  I'd like to use S-Video out on my A21p to display on the TV.  I'd also like to use the TV-in, but that's probably unsupported.

---

### Post by TheQuank on 2008-01-01
I found this on how to get the tv out to work.  I've had pritty good luck with it so far....

[http://radagast.bglug.ca/laptop/ubuntu_on_latitude_c600.html](http://radagast.bglug.ca/laptop/ubuntu_on_latitude_c600.html)

Only thing I didn't like was his xorg.conf didn't support vnc. Below is the one I use:

# xorg.conf for dell latitude c600 by A. Howlett and others
# vnc configuration added by Brendan Jensen

Section "ServerLayout"
        Identifier      "Default Server Layout"
        Screen          0 "Screen0"
        InputDevice     "Keyboard0" "CoreKeyboard"
        InputDevice     "Mouse0" "CorePointer"
        InputDevice     "Generic Mouse" "AlwaysCore"
EndSection

Section "Files"
    RgbPath     "/usr/X11R6/lib/X11/rgb"  
    FontPath    "/usr/share/fonts/local"
    FontPath    "/usr/share/fonts/misc"
    FontPath    "/usr/share/fonts/75dpi:unscaled"
    FontPath    "/usr/share/fonts/100dpi:unscaled"
    FontPath    "/usr/share/fonts/Type1"
    FontPath    "/usr/share/fonts/CID"
    FontPath    "/usr/share/fonts/Speedo"
    FontPath    "/usr/share/fonts/cyrillic"
    FontPath    "/usr/share/fonts/artwiz-aleczapka"
    FontPath    "/usr/share/fonts/TTF"
    FontPath    "/usr/share/fonts/util"
    FontPath    "/usr/local/share/fonts"
    FontPath    "/usr/share/fonts"
    FontPath    "/usr/share/fonts"
    FontPath    "/usr/share/fonts/aquafont"
    FontPath    "/usr/share/fonts/artwiz"
    FontPath    "/usr/share/fonts/artwiz-aleczapka-en"
    FontPath    "/usr/share/fonts/corefonts"
    FontPath    "/usr/share/fonts/freefont"
EndSection

Section "Module"
        Load  "GLcore"
        Load  "dbe"
        Load  "dri"
        Load  "extmod"
        Load  "glx"
        Load  "pex5"
        Load  "record"
        Load  "xie"
        Load  "v4l"
        Load  "freetype"
        Load  "vnc"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "keyboard"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout"       "us"
EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"            "PS/2"
        Option          "Emulate3Buttons"     "true"
        Option          "ZAxisMapping"                "4 5"
EndSection

Section "InputDevice"
        Identifier      "Generic Mouse"
        Driver          "mouse"
        Option          "SendCoreEvents"      "true"
        Option          "Device"              "/dev/input/mice"
        Option          "Protocol"            "ImPS/2"
        Option          "Emulate3Buttons"     "true"
        Option          "ZAxisMapping"                "4 5"
EndSection

Section "Monitor"
        Identifier "laptop LCD"
        VendorName "Dell"
        ModelName  "Latitude C600"
        HorizSync 31.5-48.5
        VertRefresh 40-70
EndSection

Section "Device"
        Identifier  "Video0"
        Driver      "r128"
        VideoRam     8192
        Option      "EnablePageFlip" "true"
        Option      "AGPFastWrite"  "true"
        Option      "AGPMode"     "2" 
        BusID       "PCI:01:00:0"
        Screen      0
        Option      "Display"  "FP"
        Option      "MonitorLayout"  "CRT, LFP"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device "Video0"
        Monitor "laptop LCD"
        DefaultDepth 24
        Option          "SecurityTypes" "VncAuth"
        Option          "UserPasswdVerifier"    "VncAuth"
        Option          "PasswordFile"  "/root/.vnc/passwd"
        Subsection "Display"
                Depth 32
                Modes "1024x768"
        EndSubSection
        Subsection "Display"
                Depth 24
                Modes "1024x768"
        EndSubSection
        Subsection "Display"
                Depth 16
                Modes "1024x768"
        EndSubSection
        Subsection "Display"
                Depth 8
                Modes "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection

---

