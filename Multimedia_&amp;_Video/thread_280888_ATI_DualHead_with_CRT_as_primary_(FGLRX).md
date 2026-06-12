---
title: "ATI DualHead with CRT as primary? (FGLRX)"
date: 2006-10-20
forum: Multimedia &amp; Video
---

### Post by T-One on 2006-10-20
I'm using Edgy, xorg 7.1, and ATI's 8.29.6 binary, HP laptop with ATI X300 M22 (5460). I have dual head and DRI working, except I have one small problem that I need help resolving:

My external CRT is to the right of my laptop's LCD. I do get gnome sessions on both, but I want the CRT to be the primary display. Right now, the Laptop's LCD is the primary, and whenever I plug in USB devices or CD's, the icons load on that screen. I usually keep a full screen app running there, and I use the CRT for the desktop and other work. I've tried googling and extensive searching here, and have found no workaround yet.

Here's my current xorg.conf...

 ```
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen" 0 0
Screen "aticonfig-Screen1" RightOf "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "Files"

# path to defoma fonts
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "Laptop LCD"
HorizSync 28.0 - 50.0
VertRefresh 43.0 - 75.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor1"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "ATI Radeon X300 M22 (5460)"
Driver "fglrx"
Option "UseFBDev" "true"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "aticonfig-Device1"
Driver "fglrx"
BusID "PCI:1:0:0"
Screen 1
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Radeon X300 M22 (5460)"
Monitor "Laptop LCD"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

Section "Screen"
Identifier "aticonfig-Screen1"
Device "aticonfig-Device1"
Monitor "aticonfig-Monitor1"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection
```

---

### Post by jsandys on 2006-10-21
I think the first screen in the serverlayout should be the "aticonfig-Screen1" instead of "Default Screen"

---

### Post by tronica on 2006-10-21
heres what i do to get dual monitors with a dual head ati card to work. 

first make sure you have the ati driver installed and setup correctly. Making sure you change the driver part in the xorg.conf to fglrx. Then run this:


> aticonfig --initial=dual-head


then edit your xorg.conf and add this to your serverlayout section:
> 
Option "Xinerama" "on"
Option "Clone" "off"

Just restart X and you should be good to go. at least i've never had anyprobs with it.

---

### Post by T-One on 2006-10-23
Please at least READ MY ORIGINAL post...I DO have dual-head and DRI working...all is as it should be for the default dual-head layout, using two screens with separate Gnome sessions. NOT Xinerama, I'm not stretching one session across two screens. I'm actually using two separate Gnome sessions, one on each screen, the default way when you use 

```
aticonfig --initial=dual-head --screen-layout=rightof  --dtop=horizontal,reverse
```My problem is that the default layout puts the main (Default) screen on my LCD and the external (CRT) as the secondary.

What I'm looking for is forcing the CRT to be the primary screen, and the LCD as the secondary. I haven't seen any way of doing that yet.

Any ideas?

---

### Post by teemow on 2006-11-01
Did you try using the MonitorLayout Option? You have to put it in your first device section. Something like this:

```
Section "Device"
    Identifier "aticonfig-Device[0]"
    Driver     "fglrx"
    BusID      "PCI:1:0:0"
    Option     "MonitorLayout" "CRT, LVDS"
EndSection
```

---

