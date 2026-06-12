---
title: "Dual display only after booting with lid open"
date: 2008-05-13
forum: Multimedia Software
---

### Post by mstreibe on 2008-05-13
I have an HP nc6400 (in a docking station) with an ATI Mobility X1300, and an external monitor connected. When I boot up with the laptop lid open, the text console will be shown on the internal LCD, and as soon as kdm starts, both screens become active.

I can close the lid, and the internal LCD will always switch on when opening the laptop again.

If I boot with the lid closed, the boot-up screen will be shown on the external CRT, and kdm will come up there as well.

BUT:

When I open the laptop then, the internal LCD will stay dark no matter what I do. "aticonfig --query-monitor" shows only crt1, no lvds, same thing with the ATI control center.

The only way to get the internal LCD working is to reboot with the laptop lid open.

Can anyone help? My xorg.conf is attached.

---

### Post by mstreibe on 2008-05-13
> My xorg.conf is attached.

Apparently not, so here it is inline:

Section "Screen"
        Identifier      "Internal"
        Device          "ATI Mobility Radeon X1300"
        Monitor         "Laptop LCD"
        SubSection "Display"
                Virtual 1600    1200
                Depth   24
                Modes           "1600x1200"     "1440x900"      "1024x768"      "800x600"       "640x480"
        EndSubSection
        Defaultdepth    24
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[1]"
        Device          "aticonfig-Device[1]"
        Monitor         "aticonfig-Monitor[1]"
        SubSection "Display"
                Viewport        0       0
                Virtual 1600    1200
                Depth   24
                Modes           "1600x1200"     "1440x900"      "1280x1024"     "1200x900"      "800x600"       "640x480"
        EndSubSection
        Defaultdepth    24
EndSection

Section "Device"
        Identifier      "ATI Mobility Radeon X1300"
        Driver          "fglrx"
        Option          "HSync2"        "27.0-107.0"
        Option          "VRefresh2"     "50.0-160.0"
        Option          "Mode2" "1600x1200,1280x1024,1200x900,1024x768,800x600"
        Option          "ForceMonitors" "crt1,lvds"
        Option          "EnableMonitor" "crt1,lvds"
        Option          "DesktopSetup"  "clone"
#       Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
#       Option          "XaaNoOffscreenPixmaps" "true"
#       Option          "DRI"                   "true"
        Option          "TexturedVideo"         "on"
#       Option          "UseFastTLS"            "0"
#       Option          "BlockSignalsOnLock"    "on"
#       Option          "KernelModuleParm"      "locked-userpages=0"
#       Option          "ForceGenericCPU"       "off"
        Busid           "PCI:1:0:0"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[1]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
        Screen  1
#       Option          "VideoOverlay"  "on"
#       Option          "OpenGLOverlay" "off"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
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

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Internal" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "Module"
        #       Load    "GLcore"
        Load            "bitmap"
        Load            "dbe"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        #       Load  "type1"
        Load            "vbe"
EndSection

Section "Monitor"
        Horizsync       27.0    -       107.0
        Vertrefresh     50.0    -       160.0
        Identifier      "Laptop LCD"
        Option          "DPMS"  "true"
EndSection

Section "Monitor"
        Identifier      "aticonfig-Monitor[1]"
        Horizsync       27.0    -       107.0
        Vertrefresh     50.0    -       160.0
        Option          "VendorName"    "ATI Proprietary Driver"
        Option          "ModelName"     "Generic Autodetecting Monitor"
        Option          "DPMS"  "true"
EndSection

#Section "ServerFlags"
#       Option          "AIGLX" "true"
#EndSection

Section "DRI"
        Mode    0666
EndSection

#Section "Extensions"
#       Option          "Composite"     "1"
#EndSection

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/CID"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

---

### Post by wkulecz on 2008-05-13
I believe this is a BIOS issue as I've seen the same behavior with other notebooks using Windows.

I think the assumption is if the lid is closed on boot up you *only* want to use the docking station monitor, mouse and keyboard.

I also see similar on some dual monitor video cards where if both monitors are not powered up at boot time, you only get the use of the one that was powered until you reboot.

--wally.

---

### Post by smurfik on 2011-01-26
Hi, I have the same issue:( Bios is not the reason. It works fine in  windows 7. I use ubuntu 10.10. Its very annoying to reboot always after I forgot to open the lid.

---

### Post by mstreibe on 2011-02-14
I tend to think the issue is with the fglrx driver. Are you using it? I tried it once with 10.10, and while the 3D performance is much better than with the radeon driver, dual screen never worked properly here. Now I'm back with the radeon driver, and the displays behave the way I want. 3D is slower again, but I don't need it that much. The desktop effects are fine, even with the radeon driver.

---

### Post by smurfik on 2011-03-05
Thx for your response. Yes I use the fglrx . OK i will try the radeon driver. I (probably) dont want to lose the 3D performance. Wil try and see:) thx again:)

---

