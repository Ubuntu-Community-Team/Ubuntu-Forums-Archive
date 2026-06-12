---
title: "twinview: only 1 tft is working"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by sadrak on 2008-01-27
OK, i read now 1 weekend all i found about xorg.conf and nvidia ... now the most of my provblems are gone ...

the situation:

i hit the standby-button and after reboot (standby wont working properly) i get only 1 TFT with 640x480 ...

dont know, perhaps there was an update for the nvidia-glx-new?

i cant get it to work, changed many things back and tested ... the nv-driver are working ... without twinview, but with 1280x1024 ...

so i go deep into xorg and make startx -- -logverbose 6

and what is this? he dont accept another resoltuion then 640x480! he always sayed: not native resolution or something else ... dont know anymore.

so i changed some options for the nvidia driver and i get back to 1280x1024 ... twinview are running ... but ... the second monitor say: out of sync range: 91khz / 85hz

the monitors are the same! both are connected to DVI-I and and there is no analog thing between one connection (i hope so :-/ i dont use adapters and both are connected to a DVI-I connection).


What happend? i testes another options about Frequences, but nothing work :-/

Here are my current config:

```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
#       FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "glx"
        Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "int10"
#       Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
        Option          "XkbVariant"    "nodeadkeys"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV31 [GeForce FX 5600]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option "RenderAccel" "true"
        Option "TripleBuffer" "true"
        Option "NvAgp" "1"
        Option "AllowGLXWithComposite" "true"
        Option "NoLogo" "true"
        Option "TwinView" "True"
        Option "TwinViewOrientation" "LeftOf"
        Option "UseEdid" "true"
        Option "UseEdidFreqs" "true"
        Option "ModeValidation" "AllowNon60HzDFPModes, NoDFPNativeResolutionCheck, NoHorizSyncCheck, NoVertRefreshCheck"
        Option "UseDisplayDevice" "DFP-0, DFP-1"
        Option "ExactModeTimingsDVI" "true"
#       Option "HorizSync"      "DFP-0: 31.0-65.0; DFP-1: 31.0-65.0"
#       Option "VertRefresh"    "DFP-0: 56.0-76.0; DFP-1: 56.0-76.0"
        Option "HorizSync"      "DFP-0: 31.0-64.0; DFP-1: 31.0-100.0"
        Option "VertRefresh"    "DFP-0: 60.0-75.0; DFP-1: 60.0-95.0"
        Option "MetaModes" "DFP-0: 1280x1024, DFP-1: 1280x1024; DFP-0: 1024x768,DFP-1: 1024x768"
EndSection

Section "Monitor"
        Identifier      "S17-1"
        Option          "DPMS"
        Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV31 [GeForce FX 5600]"
        Option          "AddARGBGLXVisuals" "True"
        Monitor         "S17-1"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
EndSection

#Section "DRI"
#       Mode    0666
#EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection



```


btw. currently i have used ENVY to install nvidia driver ... is this the best way? i had the nvidia-glx-new before and that was working well i think (or the nvidia-glx, dont know)



P.S.: There are no warnings or errors in the logs :-/

---

### Post by sadrak on 2008-01-28
nobody? :-/

---

### Post by sadrak on 2008-01-29
Option "MetaModes" "DFP-0: 1280x1024, DFP-1: 1280x1024; DFP-0: 1024x768,DFP-1: 1024x768"

DAMN! there was the fault ... i forgot to say the refresh rate ...

1280x1024_60 and all is working fine :) after that i killed many options i dont need :)

---

