---
title: "Dual Monitors with Nvidia GeForce 4000 &amp; Intel i810 chipsets"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by waveslider on 2006-08-08
I have searched through the forums and have found plenty of threads about configuring Ubuntu to use dual monitors with Nvidia cards that have two monitor input ports, but mine only has one. I have my second monitor connected to the original monitor port, which is connected to my embedded Intel i810 Chipset that came with my computer.

Can anyone advise me how to get both of my monitors working by using these 2 different video cards?

Thanks in advance!!

---

### Post by tseliot on 2006-08-08
> **waveslider said:**
> I have searched through the forums and have found plenty of threads about configuring Ubuntu to use dual monitors with Nvidia cards that have two monitor input ports, but mine only has one. I have my second monitor connected to the original monitor port, which is connected to my embedded Intel i810 Chipset that came with my computer.

Can anyone advise me how to get both of my monitors working by using these 2 different video cards?

Thanks in advance!!

AFAIK you can use 2 cards but they must be using the same driver (e.g. nvidia). I'm not sure though.

You can ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by frankhdz on 2008-02-19
You know I have been for the same answer and no one seems to know... My conclusion is the it probabbly can't be done in Ubuntu. Fedora Core 8 has some better GUI tools but that OS does not seem to able to make the dual screens work with different chipsets. I have an onboard intel and anohter nVidia card in my PC aswell.

---

### Post by MrCoOkie on 2008-02-19
What kind of PC / Motherboard is that?
Is the Geforce AGP or PCI?

Usually, when you connect a card to the AGP slot, the onboard video gets disabled as it shares the AGP bus. 
If it's PCI it's only a matter of setting the right info in Xorg.conf.

You will need xinerama support in xorg.
I never tested it with compiz so you might encounter issues with the desktop effects.

Here's a sample xorg.conf```
Section "ServerLayout"
        Identifier     "Xinerama Layout"
        Screen         "Screen0"
        Screen         "Screen1" RightOf "Screen0"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerFlags"
    Option "Xinerama" "true"
EndSection

Section "Files"
    RgbPath    "/usr/X11R6/lib/X11/rgb"
    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath   "/usr/X11R6/lib/X11/fonts/CID/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/cyrillic/"
EndSection

Section "Module"
    Load        "dbe"   # Double buffer extension
    Load "extmod"
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection
    Load        "type1"
    Load        "freetype"
#    Load        "speedo"
    Load       "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "keyboard"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
        Option "Protocol"       "ExplorerPS/2"
        Option       "ZAxisMapping" "6 7"
        Option       "ButtonNumber" "7"
        Option       "Buttons" "7"
    Option "Device"      "/dev/mouse"
EndSection

Section "Monitor"
        Identifier   "LCD
        VendorName   "Acer LFP LCD"
        Identifier   "LCD
        VendorName   "Acer LFP LCD"
        ModelName    "LCD Panel 1024x768"
        DisplaySize  320        240
        HorizSync    31.5 - 48.5
        VertRefresh  40.0 - 70.0
        Option      "dpms"
EndSection

Section "Monitor"
       Identifier   "CRT"
      VendorName   "Dell"
       ModelName    "CRT Screen 1280x1024"
       DisplaySize  320        240
       HorizSync    31.5 - 48.5
       VertRefresh  40.0 - 70.0
       Option      "dpms"
EndSection


Section "Device"
        Identifier  "i855a"
        Driver      "i810"
        VendorName  "Videocard vendor"
        BoardName   "Intel 852"
        BusId       "0:2:0"
        Option      "Clone" "false"
        #Option     "DevicePresence" "false"
        #Option     "FlipPrimary" "true"
        Option      "DRI" "true"
        #Option      "CloneRefresh" "75"
        Option      "MonitorLayout" "CRT,LFP"
        Screen      0
EndSection

Section "Device"
       Identifier  "i855b"
       Driver      "i810"
       VendorName  "Videocard vendor"
       BoardName   "Intel 852"
       BusId       "0:2:0"
       Screen      1
EndSection


Section "Screen"
        Identifier "Screen0"
        Device     "i855a"
        Monitor    "LCD"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes    "800x600" "640x480"
        EndSubSection
        SubSection "Display"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
       Identifier "Screen1"
       Device     "i855b"
       Monitor    "CRT"
       DefaultDepth     24
       SubSection "Display"
               Viewport   0 0
               Depth     16
               Modes    "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Viewport   0 0
               Depth     24
               Modes    "1024x768" "800x600" "640x480"
       EndSubSection
EndSection

Section "DRI"
        Group        0
        Mode         0666
EndSection
```

---

