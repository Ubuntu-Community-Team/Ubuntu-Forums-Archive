---
title: "fglrx, s-video and PAL-I"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by aidans on 2007-10-21
Probably something really simple and obvious here, but I'm incapable of seeing it. I've got an ATI X1650 with the fglrx driver installed and I'm getting black and white output from the s-video connection. I've set TVFormat and TVStandard to PAL-I and VIDEO respectively (I'm in the UK, these values worked with the nvidia card in the old machine), and i've cycled through all the combinations thereof with no success.

Haylp! as Penelope Pitstop would say. (Please)

- Aidan

xorg.conf:

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "gb"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    28.0 - 64.0
        VertRefresh  43.0 - 60.0
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        Option      "TVFormat" "PAL-I"
        Option      "TVStandard" "VIDEO"
        BusID       "PCI:3:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480" "640x400"
        EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

---

