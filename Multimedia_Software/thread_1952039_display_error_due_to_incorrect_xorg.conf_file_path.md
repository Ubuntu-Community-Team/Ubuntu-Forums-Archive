---
title: "display error due to incorrect xorg.conf file path settings?"
date: 2012-04-03
forum: Multimedia Software
---

### Post by openick on 2012-04-03
Hello

On 11.10,  I have trouble getting desktop display on boot after making some changes to /etc/x11/xorg.conf

My usr/share/X11/xorg.conf.d directory has the following files

10-evdev.conf             50-synaptics.conf  50-wacom.conf
11-evdev-quirks.conf      50-tslib.conf      51-synaptics-quirks.conf
11-evdev-trackpoint.conf  50-vmmouse.conf

The /etc/X11/xorg.conf file has the following instructions, a combination of an earlier xorg.conf file that worked + a set of instructions from an evdev configuration instructions. Definitely there are some errors. Please help.

( This happened possible because I missed some instructions on the thread at [https://answers.launchpad.net/ubuntu/+source/xorg/+question/191949](https://answers.launchpad.net/ubuntu/+source/xorg/+question/191949) )

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice "touchscreen" "CorePointer"
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
    Load  "extmod"
    Load  "dbe"
    Load  "record"
    Load  "glx"
    Load  "dri2"
    Load  "dri"
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
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event1"
    Option "DeviceName" "touchscreen"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card1"
    Driver      "fbdev"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card2"
    Driver      "vesa"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
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

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
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

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
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

---

### Post by Favux on 2012-04-04
Hi openick,

Wow you are blowing my mind.  What the heck are you trying to do?

You have a Hanvon drawing tablet you are trying to configure.  Is that the basics?

Please put the xorg.conf etc. in code tags, thats the hashmark (#), upper right in your post window, so idents are preserved.  It is very difficult to read your xorg.conf because there are no idents.

What is this suppose to be?
```
Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
Identifier "touchscreen"
Driver "evtouch"
Option "Device" "/dev/input/event1"
Option "DeviceName" "touchscreen"
Option "MinX" "98"
Option "MinY" "43"
Option "MaxX" "940"
Option "MaxY" "925"
Option "ReportingMode" "Raw"
Option "Emulate3Buttons"
Option "Emulate3Timeout" "50"
Option "SendCoreEvents" "On"
Identifier "dummy"
Driver "void"
Option "Device" "/dev/input/mice"
EndSection
```
Is that on purpose or did you copy paste the mouse and "touchscreen" together?  If the later is there any reason to have the mouse in the xorg.conf?  If at all possible you should remove the keyboard and mouse since they should be automatically handled and it would cut down the clutter.

Plus core pointer has been assumed since X Server 1.7.

So at least delete:
```
Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
EndSection

```
And change to:
```
Section "ServerLayout"
    Identifier "X.org Configured"
    Screen 0 "Screen0" 0 0
    Screen 1 "Screen1" RightOf "Screen0"
    Screen 2 "Screen2" RightOf "Screen1"
    InputDevice "Mouse0"
    InputDevice "touchscreen"
EndSection
```

---

### Post by openick on 2012-04-04
Dear Fauvx

Thank you for the help.  

All this happened in the process of making the touch screen work. The name of the touch screen is hanvon, as shown in the hwinfo at ubuntu [pastebin]("http://paste.ubuntu.com/907781/")

I deleted the keyboard section and made the other changes in the xorg.conf file,  which now looks as follows

```
 
//contents of the xorg.conf file in /etc/X11
// this configuration is a sum of xorg.conf.new in /home directory + [touch configuration]("http://www.conan.de/touchscreen/evtouch.html#config%22")

Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
Screen 1 "Screen1" RightOf "Screen0"
Screen 2 "Screen2" RightOf "Screen1"
InputDevice "Mouse0" 
InputDevice "touchscreen"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
EndSection

Section "Module"
Load "extmod"
Load "dbe"
Load "record"
Load "glx"
Load "dri2"
Load "dri"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
Option "Device" "/dev/input/mice"
EndSection

Section "InputDevice"
Identifier "touchscreen"
Driver "evtouch"
Option "Device" "/dev/input/event1"
Option "DeviceName" "touchscreen"
Option "MinX" "98"
Option "MinY" "43"
Option "MaxX" "940"
Option "MaxY" "925"
Option "ReportingMode" "Raw"
Option "Emulate3Buttons"
Option "Emulate3Timeout" "50"
Option "SendCoreEvents" "On"
EndSection

Section "InputDevice"
Identifier "dummy"
Driver "void"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
EndSection

Section "Monitor"
Identifier "Monitor1"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
EndSection

Section "Monitor"
Identifier "Monitor2"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
### <percent>: "<f>%"
### [arg]: arg optional
#Option "DRI" # [<bool>]
#Option "ColorKey" # <i>
#Option "VideoKey" # <i>
#Option "FallbackDebug" # [<bool>]
#Option "Tiling" # [<bool>]
#Option "LinearFramebuffer" # [<bool>]
#Option "Shadow" # [<bool>]
#Option "SwapbuffersWait" # [<bool>]
#Option "TripleBuffer" # [<bool>]
#Option "XvMC" # [<bool>]
#Option "XvPreferOverlay" # [<bool>]
#Option "DebugFlushBatches" # [<bool>]
#Option "DebugFlushCaches" # [<bool>]
#Option "DebugWait" # [<bool>]
#Option "HotPlug" # [<bool>]
#Option "RelaxedFencing" # [<bool>]
Identifier "Card0"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
### <percent>: "<f>%"
### [arg]: arg optional
#Option "ShadowFB" # [<bool>]
#Option "Rotate" # <str>
#Option "fbdev" # <str>
#Option "debug" # [<bool>]
Identifier "Card1"
Driver "fbdev"
BusID "PCI:0:2:0"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
### <percent>: "<f>%"
### [arg]: arg optional
#Option "ShadowFB" # [<bool>]
#Option "DefaultRefresh" # [<bool>]
#Option "ModeSetClearScreen" # [<bool>]
Identifier "Card2"
Driver "vesa"
BusID "PCI:0:2:0"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
SubSection "Display"
Viewport 0 0
Depth 1
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 4
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 8
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 15
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 16
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection 
```On reboot, the computer did not get past the grub menu, the desktop did not load.  As you have observed there is too much clutter in the xorg.conf file, if there is any thing more to be deleted, please tell me.

This is possibly because there is another xorg file,  xorg.conf.new either in the home directory or in /usr/share  which was the one that was picked up until the xorg.conf file was created in /etc/X11   I am not sure if the xorg.conf.new file with some other contents is in conflict with etc x11 xorg.conf.

```
 // contents of the xorg.conf.new file which may be in conflict
//this was the configuration that was working before the xorg.conf was created in /etc/X11, 
// was working with some touch screen problems such as slow response and a visible mouse cursor.

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
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
    Load  "extmod"
    Load  "dbe"
    Load  "record"
    Load  "glx"
    Load  "dri2"
    Load  "dri"
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
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card1"
    Driver      "fbdev"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card2"
    Driver      "vesa"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
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

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
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

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
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


```

---

### Post by Favux on 2012-04-04
Alright.

Looking at the new xorg.conf I don't know if C++ comments // work.  Change those to ##.

For the mouse it now appears the only reason to have it in the xorg.conf now is to apply the option:
```
Option "ZAxisMapping" "4 5 6 7"
```
What does that do?  Do you need it?

Regarding the Hanvon touchscreen, which is what you really care about, the driver you are using:
```
Driver "evtouch"
```
is deprecated in Oneiric.  I think it was deprecated earlier in fact.  Were you able to build the evtouch driver in Oneiric?  If you could that would surprise me.  Instead of evtouch the generic driver evdev would probably be a better choice.  It now does a better job of supporting drawing tablets.

That said I think the Hanvon's have their own driver, or at least some of them do:  [http://forschung.wi.uni-passau.de/~ond/myweb/hw/hanvon/index.cgi](http://forschung.wi.uni-passau.de/~ond/myweb/hw/hanvon/index.cgi)  Is your model one of the ones indicated?  You might want to run *lsusb* in a terminal to determine the Vendor and Product ID.  I don't know much about this driver but my guess it includes a usb kernel driver and an X driver, because I don't recall a hanvon driver in the kernel's HID section (drivers/hid).

Another thing I noticed in your usr/share/X11/xorg.conf.d directory there appear to be custom .conf files.  Technically user custom .conf files should be in /etc/X11/xorg.conf.d.

---

### Post by openick on 2012-04-05
Hello Favux,

Thank you.

1.MOVED  the xorg.conf.d  to /etc/X11

2. ZAxisMapping probably has something to do with touch screen, DELETED

3. CHANGED driver to evdev.
.

```
locate evdev
/usr/lib/pulse-1.0/modules/module-mmkbd-evdev.so
/usr/lib/xorg/modules/input/evdev_drv.so
/usr/share/X11/xkb/keycodes/evdev
/usr/share/X11/xkb/rules/evdev
/usr/share/X11/xkb/rules/evdev.extras.xml
/usr/share/X11/xkb/rules/evdev.lst
/usr/share/X11/xkb/rules/evdev.xml
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf
/usr/share/apport/package-hooks/source_xserver-xorg-input-evdev.py
/usr/share/bug/xserver-xorg-input-evdev
/usr/share/bug/xserver-xorg-input-evdev/script
/usr/share/doc/xserver-xorg-input-evdev
/usr/share/doc/xserver-xorg-input-evdev/changelog.Debian.gz
/usr/share/doc/xserver-xorg-input-evdev/copyright
/usr/share/man/man4/evdev.4.gz
/usr/src/linux-headers-3.0.0-16-generic/include/config/input/evdev.h
/usr/src/linux-headers-3.0.0-16-generic/include/config/usb/pwc/input/evdev.h
/usr/src/linux-headers-3.0.0-16-generic/include/config/usb/video/class/input/evdev.h
/usr/src/linux-headers-3.0.0-17-generic/include/config/input/evdev.h
/usr/src/linux-headers-3.0.0-17-generic/include/config/usb/pwc/input/evdev.h
/usr/src/linux-headers-3.0.0-17-generic/include/config/usb/video/class/input/evdev.h
/usr/src/linux-headers-3.0.0-7-generic/include/config/input/evdev.h
/usr/src/linux-headers-3.0.0-7-generic/include/config/usb/pwc/input/evdev.h
/usr/src/linux-headers-3.0.0-7-generic/include/config/usb/video/class/input/evdev.h
/var/lib/dpkg/info/xserver-xorg-input-evdev.list
/var/lib/dpkg/info/xserver-xorg-input-evdev.md5sums
/var/lib/dpkg.backup/dpkg/info/xserver-xorg-input-evdev.list
/var/lib/dpkg.backup/dpkg/info/xserver-xorg-input-evdev.md5sums
/var/lib/dpkg.backup/info/xserver-xorg-input-evdev.list
/var/lib/dpkg.backup/info/xserver-xorg-input-evdev.md5sums

```I found in the hardware info 22ed:1010 to be the device/product id. A search for this product id led to the page [http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html) which shows an OK status for a driver named hid-multitouch, so I could follow the instruction at page [http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html) and it might work.

The following is PART of the info I found on hanvon in [hwinfo]("http://paste.ubuntu.com/907781/")

```
 29: udi = '/org/freedesktop/Hal/devices/usb_device_22ed_1010_noserial_if0_logicaldev_input'   linux.hotplug_type = 2 (0x2)   linux.subsystem = 'input'   input.device = '/dev/input/event4'   input.product = 'Hanvon      10.1'   input.originating_device = '/org/freedesktop/Hal/devices/usb_device_22ed_1010_noserial_if0'   info.product = 'Hanvon      10.1'   linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input4/event4'   info.parent = '/org/freedesktop/Hal/devices/usb_device_22ed_1010_noserial_if0'   info.udi = '/org/freedesktop/Hal/devices/usb_device_22ed_1010_noserial_if0_logicaldev_input'   info.category = 'input'   info.capabilities = { 'input', 'input.tablet' }   linux.device_file = '/dev/input/event4'   info.subsystem = 'input'
``````
 I: Bus=0003 Vendor=22ed Product=1010 Version=0111   N: Name="Hanvon      10.1 "   P: Phys=usb-0000:00:1d.2-1/input0   S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input4   U: Uniq=   H: Handlers=mouse0 event4    B: PROP=0   B: EV=1b   B: KEY=403 0 3 0 0 0 0 0 0 0 0   B: ABS=700 f   B: MSC=10
```

Changed /etc/X11/xorg.conf file


```
Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
Screen 1 "Screen1" RightOf "Screen0"
Screen 2 "Screen2" RightOf "Screen1"
InputDevice "Mouse0" 
InputDevice "touchscreen"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
EndSection

Section "Module"
Load "extmod"
Load "dbe"
Load "record"
Load "glx"
Load "dri2"
Load "dri"
EndSection

Section "InputDevice"
Identifier "touchscreen"
Driver "evdev"
Option "Device" "/dev/input/event1"
Option "DeviceName" "touchscreen"
Option "MinX" "98"
Option "MinY" "43"
Option "MaxX" "940"
Option "MaxY" "925"
Option "ReportingMode" "Raw"
Option "Emulate3Buttons"
Option "Emulate3Timeout" "50"
Option "SendCoreEvents" "On"
EndSection

Section "InputDevice"
Identifier "dummy"
Driver "void"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
EndSection

Section "Monitor"
Identifier "Monitor1"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
EndSection

Section "Monitor"
Identifier "Monitor2"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
### <percent>: "<f>%"
### [arg]: arg optional
#Option "DRI" # [<bool>]
#Option "ColorKey" # <i>
#Option "VideoKey" # <i>
#Option "FallbackDebug" # [<bool>]
#Option "Tiling" # [<bool>]
#Option "LinearFramebuffer" # [<bool>]
#Option "Shadow" # [<bool>]
#Option "SwapbuffersWait" # [<bool>]
#Option "TripleBuffer" # [<bool>]
#Option "XvMC" # [<bool>]
#Option "XvPreferOverlay" # [<bool>]
#Option "DebugFlushBatches" # [<bool>]
#Option "DebugFlushCaches" # [<bool>]
#Option "DebugWait" # [<bool>]
#Option "HotPlug" # [<bool>]
#Option "RelaxedFencing" # [<bool>]
Identifier "Card0"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
### <percent>: "<f>%"
### [arg]: arg optional
#Option "ShadowFB" # [<bool>]
#Option "Rotate" # <str>
#Option "fbdev" # <str>
#Option "debug" # [<bool>]
Identifier "Card1"
Driver "fbdev"
BusID "PCI:0:2:0"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
### <percent>: "<f>%"
### [arg]: arg optional
#Option "ShadowFB" # [<bool>]
#Option "DefaultRefresh" # [<bool>]
#Option "ModeSetClearScreen" # [<bool>]
Identifier "Card2"
Driver "vesa"
BusID "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
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

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
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

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
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
```

In the original xorg.conf.new file, based on which I made the /etc/X11/xorg.conf file, there were three sections on screen, screen 0, 1 and 2,   earlier I deleted screen 1 and 2, now I have added back screen 1 and 2,.

Will try rebooting now.

---

### Post by Favux on 2012-04-05
Remember to update the "ServerLayout" if you add or remove a Section that involves it.  So it now should be:
```
Section "ServerLayout"
  Identifier "X.org Configured"
  Screen 0 "Screen0" 0 0
  Screen 1 "Screen1" RightOf "Screen0"
  Screen 2 "Screen2" RightOf "Screen1"
  InputDevice "touchscreen"
EndSection
```
since you removed the mouse.  Does the xorg.conf work yet?

Good now we have:
Vendor ID = 22ed = Hanvon
Product ID = 1010 = Artmaster?

If it is an Artmaster tablet there is likely an addition model designation like Artmaster II or something.

Since you have a drawing or graphics tablet I doubt any of the information from the Enac site is useful.  That's strictly for touchscreens, i.e. you actually use your fingers on them, not a stylus.  I think there is a little definition confusion.  Your tablet uses a stylus for drawing correct?

---

### Post by openick on 2012-04-05
Before seeing your instructions #6  I tried to start, the computer did not get past the loading screen after grub.  Back on CD, now will make the changes you have suggested.

In the 'load' section, do I have to add anything ?  Such as evdev driver ?

Thank you

---

### Post by Favux on 2012-04-05
No, the Driver line set to evdev is enough.

If it is on the evdev driver and it is correctly configured by the kernel then the evdev tablet snippet should be the one grabbing the Hanvon.

---

### Post by openick on 2012-04-05
There could be a problem with the line

```
Option "Device" "/dev/input/event1"
```

This is one of the lines of code I added following the [instructions for linux touchscreen ]("http://www.conan.de/touchscreen/evtouch.html#config%22")

There was a note of caution about specifying /dev/input/event1.  The author said 

[COLOR="Red"]Beware that some distributions use other names for the device. Some use "/dev/input/evdevX" and others use "/dev/input/eventX". [/COLOR]

I tried to look for /dev/input, there is no input directory under /dev

I have 

```

 /usr/bin/xinput

/usr/lib/ts0/input.so
/usr/lib/xorg/modules/input
/usr/lib/xorg/modules/input/evdev_drv.so
/usr/lib/xorg/modules/input/mouse_drv.so
/usr/lib/xorg/modules/input/synaptics_drv.so
/usr/lib/xorg/modules/input/vmmouse_drv.so
/usr/lib/xorg/modules/input/wacom_drv.so


/usr/share/bug/xserver-xorg-input-mouse
/usr/share/bug/xserver-xorg-input-synaptics
/usr/share/bug/xserver-xorg-input-vmmouse
/usr/share/bug/xserver-xorg-input-evdev/script
/usr/share/bug/xserver-xorg-input-mouse/script
/usr/share/bug/xserver-xorg-input-synaptics/script
/usr/share/bug/xserver-xorg-input-vmmouse/script
```


Assuming that this may not be a problem, will now try restarting.

( Tried to restart. The same problem. Did not get to the Desktop )

---

### Post by Favux on 2012-04-05
> There could be a problem with the line *Option "Device" "/dev/input/event1"*

Yes.  The event number can change especially if you are using a usb device.  However you can't do plug and play in the xorg.conf, it has to be plugged in before boot and stay that way.  That's what the .conf files in xorg.conf.d are for, they permit plug and play.

Usually you use the by-id.
> I tried to look for /dev/input, there is no input directory under /dev

You must have missed it some how.  With usb devices there will be a /dev directory and in /dev/input there will be the events and two folders: by-id and by-path.

Usually to figure out what event a device is on you can do something like the following:
```
dmesg | grep Hanvon
```
and
```
ls -l /dev/input/by-path
```
See the LinuxWacom HOW TO appendix 4 for an example.  The Xorg.0.log in /var/log only gives you the event #.

Well remember the options are for evtouch not evdev so they may break things.  Comment them out.  Once xorg.conf boots you can add options in if needed.  See *man evdev* in a terminal.  So right now just concentrate on the path to the tablet.
```
Section "InputDevice"
  Identifier "touchscreen"
  Driver "evdev"
  Option "Device" "/dev/input/event1"
#  Option "DeviceName" "touchscreen"
#  Option "MinX" "98"
#  Option "MinY" "43"
#  Option "MaxX" "940"
#  Option "MaxY" "925"
#  Option "ReportingMode" "Raw"
#  Option "Emulate3Buttons"
#  Option "Emulate3Timeout" "50"
#  Option "SendCoreEvents" "On"
EndSection
```

---

### Post by openick on 2012-04-06
> **Favux said:**
> 
Usually to figure out what event a device is on you can do something like the following:
dmesg | grep Hanvonand
ls -l /dev/input/by-pathSee the LinuxWacom HOW TO appendix 4 for an example.  The Xorg.0.log in /var/log only gives you the event #. 

```
ubuntu@ubuntu:~$ dmesg | grep Hanvon
[   17.283828] generic-usb 0003:22ED:1010.0001: hiddev96,hidraw0: USB HID v1.11 Device [Hanvon      10.1 ] on usb-0000:00:1d.2-1/input0
```and 


```
ubuntu@ubuntu:/media/7d5aeac6-2bb6-4950-a160-5538a90a661b$ ls /dev/input
by-id  by-path  event0  event1  event2  event3  event4  event5  event6  event7  mice  mouse0  mouse1
ubuntu@ubuntu:/media/7d5aeac6-2bb6-4950-a160-5538a90a661b$ ls /dev/input/by-id
usb-04f3_0103-event-if01  usb-Logitech_USB_Optical_Mouse-event-mouse
usb-04f3_0103-event-kbd   usb-Logitech_USB_Optical_Mouse-mouse
ubuntu@ubuntu:/media/7d5aeac6-2bb6-4950-a160-5538a90a661b$ ls /dev/input/by-path
pci-0000:00:1d.7-usb-0:2.2:1.0-event-kbd  pci-0000:00:1d.7-usb-0:2.4:1.0-event-mouse  platform-i8042-serio-0-event-kbd
pci-0000:00:1d.7-usb-0:2.2:1.1-event      pci-0000:00:1d.7-usb-0:2.4:1.0-mouse

```> **Favux said:**
> Well remember the options are for evtouch not evdev so they may break things.  Comment them out.  Once xorg.conf boots you can add options in if needed.  See *man evdev* in a terminal.  So right now just concentrate on the path to the tablet.

Commented them out. Rebooting.

The following output is what made me say that there is no input directory.  Giving them here in case you are curious. (I am curious as to why this occurs)

```
[COLOR=Gray]ubuntu@ubuntu:/media/7d5aeac6-2bb6-4950-a160-5538a90a661b/dev$ ls
agpgart   console  fd     loop2  mapper  midi03  mixer2      ptmx   ram11  ram2  ram8    rmidi3     smpte3   tty0  tty6
audio     core     full   loop3  mem     midi1   mixer3      pts    ram12  ram3  ram9    sequencer  sndstat  tty1  tty7
audio1    dsp      fuse   loop4  midi0   midi2   mpu401data  ram    ram13  ram4  random  shm        stderr   tty2  tty8
audio2    dsp1     kmem   loop5  midi00  midi3   mpu401stat  ram0   ram14  ram5  rmidi0  smpte0     stdin    tty3  tty9
audio3    dsp2     loop0  loop6  midi01  mixer   null        ram1   ram15  ram6  rmidi1  smpte1     stdout   tty4  urandom
audioctl  dsp3     loop1  loop7  midi02  mixer1  port        ram10  ram16  ram7  rmidi2  smpte2     tty      tty5  zero[/COLOR]



```# There is no directory by name input seen in the output of the command above, but 'input' showed up when I tried;

```
ubuntu@ubuntu:/media/7d5aeac6-2bb6-4950-a160-5538a90a661b$ ls /dev/
agpgart          ecryptfs  loop3               ppp    ram6    sda7        tty10  tty25  tty4   tty54  ttyS2    vcs6
audio            fb0       loop4               psaux  ram7    sequencer   tty11  tty26  tty40  tty55  ttyS3    vcs7
block            fd        loop5               ptmx   ram8    sequencer2  tty12  tty27  tty41  tty56  urandom  vcsa
bsg              full      loop6               pts    ram9    sg0         tty13  tty28  tty42  tty57  usb      vcsa1
bus              fuse      loop7               ram0   random  sg1         tty14  tty29  tty43  tty58  usbmon0  vcsa2
cdrom            hidraw0   mapper              ram1   rfkill  shm         tty15  tty3   tty44  tty59  usbmon1  vcsa3
cdrw             hidraw1   mcelog              ram10  rtc     snapshot    tty16  tty30  tty45  tty6   usbmon2  vcsa4
char             hidraw2   mem                 ram11  rtc0    snd         tty17  tty31  tty46  tty60  usbmon3  vcsa5
console          hidraw3   mixer               ram12  scd0    sndstat     tty18  tty32  tty47  tty61  usbmon4  vcsa6
core             hpet      net                 ram13  sda     sr0         tty19  tty33  tty48  tty62  usbmon5  vcsa7
cpu_dma_latency  input     network_latency     ram14  sda1    stderr      tty2   tty34  tty49  tty63  vcs      vga_arbiter
disk             kmsg      network_throughput  ram15  sda2    stdin       tty20  tty35  tty5   tty7   vcs1     zero
dri              log       null                ram2   sda3    stdout      tty21  tty36  tty50  tty8   vcs2
dsp              loop0     oldmem              ram3   sda4    tty         tty22  tty37  tty51  tty9   vcs3
dvd              loop1     pktcdvd             ram4   sda5    tty0        tty23  tty38  tty52  ttyS0  vcs4
dvdrw            loop2     port                ram5   sda6    tty1        tty24  tty39  tty53  ttyS1  vcs5

```and  not all events were listed on the following command.

```
[COLOR=Gray]ubuntu@ubuntu:/media/7d5aeac6-2bb6-4950-a160-5538a90a661b$ ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root 9 2012-04-07 00:23 pci-0000:00:1d.7-usb-0:2.2:1.0-event-kbd -> ../event4
lrwxrwxrwx 1 root root 9 2012-04-07 00:23 pci-0000:00:1d.7-usb-0:2.2:1.1-event -> ../event5
lrwxrwxrwx 1 root root 9 2012-04-07 00:23 pci-0000:00:1d.7-usb-0:2.4:1.0-event-mouse -> ../event6
lrwxrwxrwx 1 root root 9 2012-04-07 00:23 pci-0000:00:1d.7-usb-0:2.4:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2012-04-07 00:23 platform-i8042-serio-0-event-kbd -> ../event3[/COLOR]

```# There are only five events starting with event4 in the output of the command above.

That is rather strange.

Commented out the unnecessary entries in xorg.conf as you have suggested. Now trying to reboot. Perhaps some more changes are required based on the dmesg and the by path and by id commands.

Thank you again.

Didn't work.  

And, unlike the outputs of commands as in the example from page [http://ubuntuforums.org/showthread.php?t=1952039&page=2](http://ubuntuforums.org/showthread.php?t=1952039&page=2),   I don't see a match between the output of the grep and ls -l by dev id commands.  Does that mean that the evdev driver is not properly installed?

Also, how should I change the line ```
Option "Device" "/dev/input/event1"
 
```

---

### Post by Favux on 2012-04-06
We don't know the event # to use.  From the dmesg input0 it should be event0 but that isn't present, implying the device node is not being created.  I would comment out:
```
#Option "Device" "/dev/input/event1"
```
and restart and see if dmesg is the same and you now see something in the ls by-path.

Otherwise we should give up on the putting the tablet in the xorg.conf and try commenting out its section and "SeverLayout" line and see if the xorg.conf finally boots with your video stuff.  At least get a working baseline xorg.conf.  We probably should switch to setting up a .conf file in xorg.conf.d.

---

### Post by openick on 2012-04-06
Commented out the line and on reboot id did not work

Output of the dmesg and ls commands after commenting out the event1 line in xorg.conf

```
 ubuntu@ubuntu:~$ cd /media/7d5aeac6-2bb6-4950-a160-5538a90a661b/
ubuntu@ubuntu:/media/7d5aeac6-2bb6-4950-a160-5538a90a661b$ dmesg grep | Hanvon
Hanvon: command not found
ubuntu@ubuntu:/media/7d5aeac6-2bb6-4950-a160-5538a90a661b$ dmesg | grep Hanvon
[   17.287659] generic-usb 0003:22ED:1010.0001: hiddev96,hidraw0: USB HID v1.11 Device [Hanvon      10.1 ] on usb-0000:00:1d.2-1/input0
ubuntu@ubuntu:/media/7d5aeac6-2bb6-4950-a160-5538a90a661b$ ls /dev/input
by-id    event0  event2  event4  event6  mice    mouse1
by-path  event1  event3  event5  event7  mouse0
ubuntu@ubuntu:/media/7d5aeac6-2bb6-4950-a160-5538a90a661b$ ls /dev/input/by-id
usb-04f3_0103-event-if01  usb-Logitech_USB_Optical_Mouse-event-mouse
usb-04f3_0103-event-kbd   usb-Logitech_USB_Optical_Mouse-mouse
ubuntu@ubuntu:/media/7d5aeac6-2bb6-4950-a160-5538a90a661b$ ls /dev/input/by-pathpci-0000:00:1d.7-usb-0:2.2:1.0-event-kbd
pci-0000:00:1d.7-usb-0:2.2:1.1-event
pci-0000:00:1d.7-usb-0:2.4:1.0-event-mouse
pci-0000:00:1d.7-usb-0:2.4:1.0-mouse
platform-i8042-serio-0-event-kbd

```Also looked into the /etc/X11/xorg.conf.d directory

The following are the contents:

10-evdev.conf 

```
#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection
```11-evdev-quirks.conf

```
Section "InputClass"
    Identifier "Avago Technologies mouse quirks (LP: #746639)"
    MatchIsPointer "on"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
    MatchUSBID "192f:0416"
    Option "Emulate3Buttons" "True"
    Option "Emulate3Timeout" "50"
EndSection

# X/Y axis not working due to device reporting absolute axes
# https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/325581
# https://bugs.freedesktop.org/show_bug.cgi?id=32882
Section "InputClass"
    Identifier    "Benq m310"
    MatchProduct    "HID 0d62:1000"
    Driver        "evdev"
    Option        "IgnoreAbsoluteAxes"    "true"
EndSection
```11-evdev-trackpoint.conf

```
# trackpoint users want wheel emulation

Section "InputClass"
    Identifier    "trackpoint catchall"
    MatchIsPointer    "true"
    MatchProduct    "TrackPoint|DualPoint Stick"
    MatchDevicePath    "/dev/input/event*"
    Option    "Emulate3Buttons"    "true"
    Option    "EmulateWheel"    "true"
    Option    "EmulateWheelButton"    "2"
    Option    "XAxisMapping"    "6 7"
    Option    "YAxisMapping"    "4 5"
EndSection
```All these files show event as event*

Interestingly evdev-trackpoint.conf   shows some instructions for XAxisMapping and YAxisMapping which probably answers one of your earlier questions related to references to these in the xorg.conf file.

Now trying with event* .   Also in ServerLayout there was an entry saying Mouse0 , deleted it.  Rebooting now to see if it works, if there is a failure, will report back after a few hours.

Thank you

---

### Post by openick on 2012-04-06
It works, could get to the Desktop, touch screen worked with the same problems of inaccuracy, no pop up keyboard, and curson on touch.


The xorg.conf that works at the moment is as below:

```

Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
Screen 1 "Screen1" RightOf "Screen0"
Screen 2 "Screen2" RightOf "Screen1"
InputDevice "touchscreen"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
EndSection

Section "Module"
Load "extmod"
Load "dbe"
Load "record"
Load "glx"
Load "dri2"
Load "dri"
EndSection

Section "InputDevice"
Identifier "touchscreen"
Driver "evdev"
#Option "Device" "/dev/input/event*"
Option "DeviceName" "touchscreen"
#Option "MinX" "98"
#Option "MinY" "43"
#Option "MaxX" "940"
#Option "MaxY" "925"
#Option "ReportingMode" "Raw"
#Option "Emulate3Buttons"
#Option "Emulate3Timeout" "50"
#Option "SendCoreEvents" "On"
EndSection

Section "InputDevice"
Identifier "dummy"
Driver "void"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
EndSection

Section "Monitor"
Identifier "Monitor1"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
EndSection

Section "Monitor"
Identifier "Monitor2"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
### <percent>: "<f>%"
### [arg]: arg optional
#Option "DRI" # [<bool>]
#Option "ColorKey" # <i>
#Option "VideoKey" # <i>
#Option "FallbackDebug" # [<bool>]
#Option "Tiling" # [<bool>]
#Option "LinearFramebuffer" # [<bool>]
#Option "Shadow" # [<bool>]
#Option "SwapbuffersWait" # [<bool>]
#Option "TripleBuffer" # [<bool>]
#Option "XvMC" # [<bool>]
#Option "XvPreferOverlay" # [<bool>]
#Option "DebugFlushBatches" # [<bool>]
#Option "DebugFlushCaches" # [<bool>]
#Option "DebugWait" # [<bool>]
#Option "HotPlug" # [<bool>]
#Option "RelaxedFencing" # [<bool>]
Identifier "Card0"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
### <percent>: "<f>%"
### [arg]: arg optional
#Option "ShadowFB" # [<bool>]
#Option "Rotate" # <str>
#Option "fbdev" # <str>
#Option "debug" # [<bool>]
Identifier "Card1"
Driver "fbdev"
BusID "PCI:0:2:0"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
### <percent>: "<f>%"
### [arg]: arg optional
#Option "ShadowFB" # [<bool>]
#Option "DefaultRefresh" # [<bool>]
#Option "ModeSetClearScreen" # [<bool>]
Identifier "Card2"
Driver "vesa"
BusID "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
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

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
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

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
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

```Installed Calibrate Touchscreen, ran calibration, and it generated an output to be copied to /etc/X11/xorg.conf.d/99-calibrate.conf

```
Section "InputClass"
    Identifier    "calibration"
    MatchProduct    "Hanvon      10.1 "
    Option    "Calibration"    "4995 10526 8590 18418"
EndSection
```Now touch is even more chaotic. Will try recalibrating.

---

### Post by Favux on 2012-04-06
Great!

So to get it straight with the Hanvon stuff out of the xorg.conf it is now working and X is starting.  Please finish commenting out the Hanvon stuff.
```
Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
Screen 1 "Screen1" RightOf "Screen0"
Screen 2 "Screen2" RightOf "Screen1"
#InputDevice "touchscreen"
EndSection
```
and
```
#Section "InputDevice"
#Identifier "touchscreen"
#Driver "evdev"
#Option "Device" "/dev/input/event*"
#Option "DeviceName" "touchscreen"
#Option "MinX" "98"
#Option "MinY" "43"
#Option "MaxX" "940"
#Option "MaxY" "925"
#Option "ReportingMode" "Raw"
#Option "Emulate3Buttons"
#Option "Emulate3Timeout" "50"
#Option "SendCoreEvents" "On"
#EndSection

```
That is not the way to calibrate your tablet.  Please remove your /etc/X11/xorg.conf.d/99-calibrate.conf and after a reboot post the output of:
```
xinput list
```
Also let's verify what X Server you have by posting the output of:
```
Xorg -version
```

---

### Post by openick on 2012-04-07
> **Favux said:**
> Great!

So to get it straight with the Hanvon stuff out of the xorg.conf it is now working and X is starting.  Please finish commenting out the Hanvon stuff.

...

...

That is not the way to calibrate your tablet.  Please remove your /etc/X11/xorg.conf.d/99-calibrate.conf 

Have done that.

> **Favux said:**
> and after a reboot post the output of xinput list and Xorg -version :

Here is the code:

```
# output of xinput list 
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Hanvon      10.1                        	id=9	[slave  pointer  (2)]
&#9116;   &#8627; HID 04f3:0103                           	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; HID 04f3:0103                           	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]

```



> **Favux said:**
> Also let's verify what X Server you have by posting the output of:


Here is the Xorg version output

```
#output of xorg version
X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux turiyatv0 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=7d5aeac6-2bb6-4950-a160-5538a90a661b ro quiet splash vt.handoff=7
Build Date: 19 October 2011  05:09:41AM
xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.22.2
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
```

Thank you.

---

### Post by Favux on 2012-04-07
Good.

So from *xinput list* your <device name> is "Hanvon      10.1".  You only need to use the <device name> in xinput and with say xinput_calibrator.  I assume xinput_calibrator is how you are getting your calibration.

Now the evdev.conf should be in /etc/X11/xorg.conf.d since it is a system file.  This is the snippet that should be picking up your Hanvon tablet:
```
Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection
```
Provided the USB HID descriptor in the kernel is "correct" so the MatchIsTablet applies.

To verify that run this command and post the output:
```
xinput list-props "Hanvon      10.1"
or
xinput list-props 9
```
For the <device name> not sure if you need trailing white spaces or not.  The ID # can change so you have to verify it with *xinput list* each time.

The Identifier line provides the human readable description "evdev tablet catchall".  That's what will let you know the snippet has applied to the device in say Xorg.0.log in /var/log.


For coordinates and other options we want to create a custom .conf and snippet in /etc/X11/xorg.conf.d.  With xorg.conf.d you don't need the whole <device name>.  Instead a keyword will do and "Hanvon" is the obvious choice.  Also with X Server 1.10 we have the availability of a new match parameter called *MatchDriver*.

---

### Post by openick on 2012-04-07
> **Favux said:**
> Good.

So from *xinput list* your <device name> is "Hanvon      10.1".

Yes, it is xinput-calibrator 0.7.5-0ubuntu1, this is what I used.  

> **Favux said:**
>  You only need to use the <device name> in xinput and with say xinput_calibrator.  I assume xinput_calibrator is how you are getting your calibration.

This part is not clear. 'use the <device name> in xinput and say xinput_calibrator'  -  Where and How?  Is this while calibrating touch screen or in one of the conf files?  What do I need to say exactly?



> **Favux said:**
>  [COLOR=Gray]Now the evdev.conf should be in /etc/X11/xorg.conf.d since it is a system file.  This is the snippet that should be picking up your Hanvon tablet:
Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection


Provided the USB HID descriptor in the kernel is "correct" so the MatchIsTablet applies[/COLOR]. 


Don't know how to verify the USB HID descriptor in the kernel

/etc/X11/xorg.conf.d/10-evdev.conf has this contents and here is the full output of evdev.conf

```
#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection
```> **Favux said:**
> 
To verify that run this command and post the output:
xinput list-props "Hanvon      10.1"
or
xinput list-props 9 For the <device name> not sure if you need trailing white spaces or not.  The ID # can change so you have to verify it with *xinput list* each time.

Here is the output:

```
tv0user@ttv0:~$ xinput list-props "Hanvon      10.1"
unable to find device Hanvon      10.1

tv0user@ttv0:~$ xinput list-props Hanvon      10.1
unable to find device Hanvon
unable to find device 10.1

tv0user@ttv0:~$ xinput list-props 9
Device 'Hanvon      10.1 ':
    Device Enabled (135):    1
    Coordinate Transformation Matrix (137):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (260):    0
    Device Accel Constant Deceleration (261):    1.000000
    Device Accel Adaptive Deceleration (262):    1.000000
    Device Accel Velocity Scaling (263):    10.000000
    Evdev Axis Inversion (264):    0, 0
    Evdev Axis Calibration (265):    <no items>
    Evdev Axes Swap (266):    0
    Axis Labels (267):    "Abs X" (255), "Abs Y" (256), "Abs Z" (257), "Abs Rotary X" (258), "Abs Misc" (259), "Abs Misc" (259), "Abs Misc" (259)
    Button Labels (268):    "Button 0" (253), "Button 1" (254), "Button Unknown" (252), "Button Wheel Up" (141), "Button Wheel Down" (142)
    Evdev Middle Button Emulation (269):    0
    Evdev Middle Button Timeout (270):    50
    Evdev Wheel Emulation (271):    0
    Evdev Wheel Emulation Axes (272):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (273):    10
    Evdev Wheel Emulation Timeout (274):    200
    Evdev Wheel Emulation Button (275):    4
    Evdev Drag Lock Buttons (276):    0

```> **Favux said:**
> The Identifier line provides the human readable description "evdev tablet catchall".  That's what will let you know the snippet has applied to the device in say Xorg.0.log in /var/log.

For coordinates and other options we want to create a custom .conf and snippet in /etc/X11/xorg.conf.d.  With xorg.conf.d you don't need the whole <device name>.  Instead a keyword will do and "Hanvon" is the obvious choice.  Also with X Server 1.10 we have the availability of a new match parameter called *MatchDriver*.


Is there anything that you want me to do on the configuration files based on the instructions in the above two paragraphs?

And, updated to version Build Operating System:

```
 Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux ttv0 3.0.0-19-generic #32-Ubuntu SMP Thu Apr 5 18:21:13 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-19-generic root=UUID=7d5aeac6-2bb6-4950-a160-5538a90a661b ro quiet splash vt.handoff=7
Build Date: 19 October 2011  05:09:41AM
xorg-server 2:1.10.4-1ubuntu4.2 

#X-org version remains the same as 

X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0 
```Thank you.

---

### Post by Favux on 2012-04-07
Great, some progress!

Clearly there is one trailing space in the <device name>
```
"Hanvon      10.1 "
```
Now what would be good to know is what snippet it is on.  You'd have to check the Xorg.0.log.  The main reason is it doesn't appear to be on the tablet snippet and the list-props doesn't tell us what Mode it is in.  You want "Absolute".  If it isn't in "Absolute" that might mess up the coordinates, maybe.  The coordinates you have from calibration look a little funky.  Believable but funky.

So the HID descriptor is not labelling your model Hanvon (by the way did you say what it was?) a tablet which is presumably why the MatchIsTablet is not picking it up.  Looks like evdev thinks it is a mouse?

Anyway the snippet you want in /etc/X11/xorg.conf.d would be:
```
Section "InputClass"
    Identifier   "Hanvon tablet options"
    MatchDriver  "evdev"
    MatchProduct "Hanvon"
#    Option   "Mode"          "Absolute"
    Option   "Calibration"   "4995 10526 8590 18418"
EndSection
```
I left Mode commented out because we don't know if you need it yet.  So this will match to the evdev driver and devices on it and matching to Hanvon will make it a unique match.

Now what runs last controls and /etc/X11/xorg.conf.d runs after /usr/share/X11/xorg.conf.d.  Even so its a good idea to use a later number too.  Evdev is 10 but other tablet .conf's are at 50 like Wacom.  So rather than use 11 or 12 or something let's use 52.  So let's call it 52-hanvon-on-evdev.conf.
```
gksudo gedit /etc/X11/xorg.conf.d/52-hanvon-on-evdev.conf.
```

---

### Post by openick on 2012-04-07
> **Favux said:**
> [COLOR=Gray]Now what would be good to know is what snippet it is on.  You'd have to check the Xorg.0.log.  The main reason is it doesn't appear to be on the tablet snippet and the list-props doesn't tell us what Mode it is in.  You want "Absolute".  If it isn't in "Absolute" that might mess up the coordinates, maybe.  The coordinates you have from calibration look a little funky.  Believable but funky.[/COLOR][COLOR=Gray]

[COLOR=DarkSlateGray]
**Xorg.0.log is at page [http://paste.ubuntu.com/918542/](http://paste.ubuntu.com/918542/)**[/COLOR]



[/COLOR]> **Favux said:**
> [COLOR=Gray]So the HID descriptor is not labelling your model Hanvon (by the way did you say what it was?) a tablet which is presumably why the MatchIsTablet is not picking it up.  Looks like evdev thinks it is a mouse?[/COLOR] [COLOR=Gray]
[COLOR=DarkSlateGray]
It is a fic tycoon tvb0 touch tablet. 

I think Yes, probably evdev thinks it is a mouse :) There was some instruction about "middle button" that I saw somewhere.[/COLOR]

[/COLOR]> **Favux said:**
> [COLOR=Gray]Anyway the snippet you want in /etc/X11/xorg.conf.d would be:[/COLOR] [COLOR=Gray]

Section "InputClass"
    Identifier   "Hanvon tablet options"
    MatchDriver  "evdev"
    MatchProduct "Hanvon"
#    Option   "Mode"          "Absolute"
    Option   "Calibration"   "4995 10526 8590 18418"
EndSection

I left Mode commented out because we don't know if you need it yet.  So this will match to the evdev driver and devices on it and matching to Hanvon will make it a unique match.

Now what runs last controls and /etc/X11/xorg.conf.d runs after /usr/share/X11/xorg.conf.d.  Even so its a good idea to use a later number too.  Evdev is 10 but other tablet .conf's are at 50 like Wacom.  So rather than use 11 or 12 or something let's use 52.  So let's call it 52-hanvon-on-evdev.conf.[/COLOR] [COLOR=Gray]
gksudo gedit /etc/X11/xorg.conf.d/52-hanvon-on-evdev.conf.[/COLOR][COLOR=Gray]

[COLOR=DarkSlateGray]Should I create 52-hanvon-on-evdev.conf and paste the snippet that you have given above?

Thank you.
[/COLOR][/COLOR]

---

### Post by Favux on 2012-04-07
So a Fic Tycoon tvb0 touch tablet = "Hanvon 10.1 ".

Yes please apply the snippet.  From your Xorg.0.log it appears we can leave the Mode commented out:
```
[    30.077] (II) config/udev: Adding input device Hanvon      10.1  (/dev/input/event4)
[    30.077] (**) Hanvon      10.1 : Applying InputClass "evdev tablet catchall"
[    30.077] (II) Using input driver 'evdev' for 'Hanvon      10.1 '
[    30.077] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.077] (**) Hanvon      10.1 : always reports core events
[    30.077] (**) Hanvon      10.1 : Device: "/dev/input/event4"
[    30.078] (--) Hanvon      10.1 : Found 2 mouse buttons
[    30.078] (--) Hanvon      10.1 : Found absolute axes
[    30.078] (II) evdev-grail: failed to open grail, no gesture support
[    30.078] (--) Hanvon      10.1 : Found x and y absolute axes
[    30.078] (--) Hanvon      10.1 : Found absolute tablet.
[    30.078] (II) Hanvon      10.1 : Configuring as tablet
[    30.078] (**) Hanvon      10.1 : YAxisMapping: buttons 4 and 5
[    30.078] (**) Hanvon      10.1 : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    30.078] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input4/event4"
[    30.078] (II) XINPUT: Adding extended input device "Hanvon      10.1 " (type: TABLET)
[    30.079] (II) Hanvon      10.1 : initialized for absolute axes.
[    30.079] (**) Hanvon      10.1 : (accel) keeping acceleration scheme 1
[    30.079] (**) Hanvon      10.1 : (accel) acceleration profile 0
[    30.079] (**) Hanvon      10.1 : (accel) acceleration factor: 2.000
[    30.079] (**) Hanvon      10.1 : (accel) acceleration threshold: 4
[    30.081] (II) config/udev: Adding input device Hanvon      10.1  (/dev/input/mouse0)
[    30.081] (II) No input driver/identifier specified (ignoring)
```
because:
```
[    30.079] (II) Hanvon      10.1 : initialized for absolute axes.
```
And it is using Absolute because the right snippet has it after all:
```
[    30.077] (**) Hanvon      10.1 : Applying InputClass "evdev tablet catchall"
```

---

### Post by openick on 2012-04-07
Dear Favux,

Thank you. I have your snippet from #19 pasted in the file I created as /etc/X11/xorg.conf.d/52-hanvon-on-evdev.conf
[FONT=monospace]
Restarted lightdm, have the mouse cursor on the top menu bar, touch on an icon on the left menu bar does not create any response on the menu item, but causes the cursor to move along the top menu bar, (occurs when an external mouse is attached or otherwise)

1. Touch works, but seems calibrated about 600 pixels away
2. Cursor is a persistent problem.

The only solution I have seen online to the problem of mouse cursor is from [http://www.conan.de/touchscreen/evtouch.html#config%22](http://www.conan.de/touchscreen/evtouch.html#config%22)

[/FONT]> Since Xorg 7.2 there is always a  default-mouse-pointer which will run simultaneously with evtouch if you  do not prevent it from loading. It is extremely important that you add  the following to your configuration. Otherwise you will get double click  events and all kind of strange things.
  
[LIST=1]
[*] Add the following new input-device to your xorg.conf:
  ```
Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection
[*] Add the following line your your "ServerLayout"-section:
 InputDevice "dummy"
```
[/LIST]
   Calibration is also supported since V0.6.0. You can also reuse your settings from the old driver for the 2.6 driver. Actually you only have to exchange the driver name in the "Inputdevice"-section from "lbtouch" to "evtouch" and change the "Device".And is this something that could lead to a solution to the strange calibration problem?  Is it something to do with the Y Axis?

>  

# from the conan.de page as above

[LIST=1]
[*]Add the line below to the file "/etc/X11/XF86Config-4" or "/etc/X11/xorg.conf" to the section "ServerLayout".
InputDevice "touchscreen" "CorePointer"
[*] If your Y-axis is interchanged you might have used the wrong event-device. Maybe you should try the next few event-devices (/dev/event[1-9]).
[/LIST]
# Didn't make any changes based on these instructions.




 Tried running the Calibration, the results generated on the terminal are Option    "Calibration"    "7383 7489 8800 8853"  which doesn't look accurate

Tried changing the snippet with the new calibration settings, it is still not right, a touch somewhere opened 34 instances of the trash folder. 

      3.  Touch does not work inside a browser or open office.

There is some conflict somewhere, possibly between any of these files in xorg.conf.d ?

```
10-evdev.conf             50-tslib.conf             52-hanvon-on-evdev.conf
11-evdev-quirks.conf      50-vmmouse.conf           52-hanvon-on-evdev.conf~
11-evdev-trackpoint.conf  50-wacom.conf
50-synaptics.conf         51-synaptics-quirks.conf

```

---

### Post by Favux on 2012-04-07
I think this is obsolete advice:
```
Section "InputDevice"
Identifier "dummy"
Driver "void"
EndSection
```
Evdev seems smart enough to tell there isn't a mouse device node, which is why you see:
```
[    30.081] (II) config/udev: Adding input device Hanvon      10.1  (/dev/input/mouse0)
[    30.081] (II) No input driver/identifier specified (ignoring)
```
So I believe you can and should comment that section out or remove it from your xorg.conf.

Now that I know what your tablet is called is this it?
[http://www.fic.com.tw/product/tvb00.aspx](http://www.fic.com.tw/product/tvb00.aspx)
[http://www.engadget.com/2010/11/12/fic-launches-10-1-inch-windows-7-tycoon-tablet-prices-it-at-66/](http://www.engadget.com/2010/11/12/fic-launches-10-1-inch-windows-7-tycoon-tablet-prices-it-at-66/)

If it is, it in fact is not a Hanvon drawing tablet with a stylus/pen.  It is a multi-touch atom tablet that runs Win7 with a capacitive multi-touch screen made by Hanvon.  And since it is new it does not seem to have a driver and this explains your interest in the Enac site.  Head slap.

I assume your current touch is single finger, correct?  You can calibrate manually, let's look at your xinput list-props again with the 52-hanvond-on-evdev.conf in place and see if now there are coordinates in:
```
Evdev Axis Calibration (265):    <no items>
```
Normally the x and y minimums are somewhere near 0,0.  The top left corner of the screen is the origin (0,0).

---

### Post by openick on 2012-04-08
> **Favux said:**
> 
So I believe you can and should comment that section out or remove it from your xorg.conf.

Commented it out


> **Favux said:**
>  I assume your current touch is single finger, correct?   

It is in fact a capacitive multitouch screen, tested it with Windows 8 and android, worked well.

> **Favux said:**
>  You can calibrate manually, let's look at your xinput list-props again with the 52-hanvond-on-evdev.conf in place and see if now there are coordinates in:
Evdev Axis Calibration (265):    <no items>
Normally the x and y minimums are somewhere near 0,0.  The top left corner of the screen is the origin (0,0). 

Would be very helpful if you tell me where to specify x and y minimums, how, with the exact syntax.

Thanks.

---

### Post by Favux on 2012-04-08
> It is in fact a capacitive multitouch screen, tested it with Windows 8 and android, worked well.
Yes but it is not clear to me that the generic kernel driver is enabling multi-touch.  If it is then you should be able to use ginn along with the evdev X driver to enable multi-touch.
> Would be very helpful if you tell me where to specify x and y minimums, how, with the exact syntax.
You already have the static option/command in the 52-hanvon-on-evdev.conf:
```
Option   "Calibration"   "0 10526 0 18418"
```
What I was hoping to discover is if you can use a run-time command through xinput.  Something like:
```
xinput set-prop "Hanvon      10.1 " "Evdev Axis Calibration" "0 10526 0 18418"
```
By seeing if the list-props now shows coordinates for "Evdev Axis Calibration" because of the 52-hanvon-on-evdev.conf coordinate option.  If you can use xinput to affect the evdev driver's coordinates calibrating will go much faster.  Because all you have to do is run the changed coordinates in a terminal and they would apply immediately.  No need to restart.

---

### Post by openick on 2012-04-09
> **Favux said:**
>  Option   "Calibration"   "0 10526 0 18418"

Have made this change in 52-evdev...conf


> **Favux said:**
>  What I was hoping to discover is if you can use a run-time command through xinput.  Something like:
xinput set-prop "Hanvon      10.1 " "Evdev Axis Calibration" "0 10526 0 18418"  Because all you have to do is run the changed coordinates in a terminal and they would apply immediately.  No need to restart.

Errors on the xinput set-prop Hanvon... command on the terminal:

X Error of failed request:  Badmatch (invalid parameter attributes)
Major opcode of failed request 140 (XinputExtension)
Minor opcode of failed request 57 ()
Serial Number of failed request: 19
Current Serial number in output stream: 20

---

### Post by Favux on 2012-04-09
That's unfortunate.  It means manual calibration will be slower since you can not use xinput.

What happened with the 0 and 0 static option coordinates?

---

### Post by openick on 2012-04-11
Dear Favux,

> **Favux said:**
> What happened with the 0 and 0 static option coordinates?

I changed in the 52-Hanvon... file as 

Option   "Calibration"   "0 10526 0 18418"

Did you mean "0,0" in place of "0 10526 0 18418" ?

( I have another problem, misplaced the power adapter, so I need to wait till I get an alternate adapter deliverd :(  )

Thank you

---

### Post by Favux on 2012-04-11
Hi openick,

> Option "Calibration" "0 10526 0 18418"
Should be correct.  From *man evdev*:
```
       Option "Calibration" "min-x max-x min-y max-y"
              Calibrates  the X and Y axes for devices that need to scale to a different
              coordinate system than reported to the X server. This feature is  required
              for devices that need to scale to a different coordinate system than orig&#8208;
              inally reported by the kernel (e.g. touchscreens). The scaling to the cus&#8208;
              tom coordinate system is done in-driver and the X server is unaware of the
              transformation. Property: "Evdev Axis Calibration".

```
The order of the coordinates is driver specific and some drivers do want the two minimums first followed by the maximums, but not evdev.

---

### Post by openick on 2012-04-11
> **Favux said:**
> Hi openick,


Should be correct.  

I have the same settings in 52-hanvon-on-evdev.conf, but it is still chaotic.

I ran calibrator again, used a mouse to click the pointers for calibration for accuracy, it generated an output very close to the figures you have given, but the instructions tell me to copy it to 99-calibration.conf.

```
--> Making the calibration permanent <--
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf'
Section "InputClass"
	Identifier	"calibration"
	MatchProduct	"Hanvon      10.1 "
	Option	"Calibration"	"12 10524 0 18417"
EndSection 
```

Somewhere in some file, is evdev looking for 99-calibration.conf or any file with the name 'calibration.conf' ?

Thank you.

---

### Post by Favux on 2012-04-11
> Somewhere in some file, is evdev looking for 99-calibration.conf or any file with the name 'calibration.conf' ?
No.  I haven't used that version of xinput_calibrator, it must have been updated.  It is suggesting you use 99 because 99 will make it the last .conf file run and it is trying to make sure the calibration file is the last one run so it controls.  But we already know using 52 does the same thing for you.  Plus our match makes sure we're setting the coordinates for the Hanvon on the evdev driver.  Don't use both.
> I have the same settings in 52-hanvon-on-evdev.conf, but it is still chaotic.
How do you mean chaotic?  Could you describe it in more detail?  Is it still 600 pixels off?

Have you run the xinput list-props command again?  What does the output look like?  Does it now show the coordinates in "Evdev Axis Calibration"?

Have you tried removing the comment (#) from the Mode "Absolute" option line in 52-hanvon-on-evdev.conf?  Does that make a difference?

---

### Post by openick on 2012-04-12
> **Favux said:**
>  Don't use both.

            How do you mean chaotic?  Could you describe it in more detail?  Is it still 600 pixels off?

             Have you run the xinput list-props command again?  What does the output look like?  Does it now show the coordinates in "Evdev Axis Calibration"?

Have you tried removing the comment (#) from the Mode "Absolute" option line in 52-hanvon-on-evdev.conf?  Does that make a difference?

Deleted 99 configuration
Removed the comment on the mode Absolute
Touch is still 200 - 300 pixels off on the taskbar 

Output of xinput-list

```
xinput list-props 12
Device 'Hanvon      10.1 ':
	Device Enabled (135):	1
	Coordinate Transformation Matrix (137):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (258):	0
	Device Accel Constant Deceleration (259):	1.000000
	Device Accel Adaptive Deceleration (260):	1.000000
	Device Accel Velocity Scaling (261):	10.000000
	Evdev Axis Inversion (262):	0, 0
	Evdev Axis Calibration (263):	0, 10526, 0, 18418
	Evdev Axes Swap (264):	0
	Axis Labels (265):	"Abs X" (277), "Abs Y" (278), "Abs Z" (279), "Abs Rotary X" (280), "Abs Misc" (281), "Abs Misc" (281), "Abs Misc" (281)
	Button Labels (266):	"Button 0" (275), "Button 1" (276), "Button Unknown" (252), "Button Wheel Up" (141), "Button Wheel Down" (142)
	Evdev Middle Button Emulation (267):	0
	Evdev Middle Button Timeout (268):	50
	Evdev Wheel Emulation (269):	0
	Evdev Wheel Emulation Axes (270):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (271):	10
	Evdev Wheel Emulation Timeout (272):	200
	Evdev Wheel Emulation Button (273):	4
	Evdev Drag Lock Buttons (274):	0

```

It does show the coordinates. Something else is the problem.

Thank you.

---

### Post by Favux on 2012-04-12
```
	Evdev Axis Calibration (263):	0, 10526, 0, 18418
```
Good.  With that property active I was hoping evdev could handle a xinput command for coordinates:
```
xinput set-prop "device name" "Evdev Axis Calibration" min-x max-x min-y max-y
```
Since that would speed things up.  You can use the ID # from *xinput list* in place of the "device name".
> Removed the comment on the mode Absolute
Touch is still 200 - 300 pixels off on the taskbar 
But did activating the Mode Absolute option do anything?  Or no change as far as you can tell?

Is the taskbar on the left or the top?  Does the pointer arrow fall short?  If so be aware for at least the Wacom X driver you can use a negative number for a coordinate.  Let's see if that is true of the evdev driver too.  Left would be x and the top would be y.

Let's say you are falling short at both the left and top.  But going off the right and bottom edge.  Try a shift of say at least 200, maybe even 400.
```
	Option	"Calibration"	"-198 8524 -200 16417"
```
You don't have to do it as a shift.  You can treat each coordinate as independent.

---

### Post by openick on 2012-04-14
> **Favux said:**
> ```
	Evdev Axis Calibration (263):	0, 10526, 0, 18418
```

But did activating the Mode Absolute option do anything?  Or no change as far as you can tell?

Is the taskbar on the left or the top?  Does the pointer arrow fall short?  If so be aware for at least the Wacom X driver you can use a negative number for a coordinate.  Let's see if that is true of the evdev driver too.  Left would be x and the top would be y.

Let's say you are falling short at both the left and top.  But going off the right and bottom edge.  Try a shift of say at least 200, maybe even 400.
```
	Option	"Calibration"	"-198 8524 -200 16417"
```
You don't have to do it as a shift.  You can treat each coordinate as independent.

Tried reducing the coordinates by 200 and 400 by changing the first value alone, and then by changing all four values, (actually in your code immediately above you have changed it by -200 -2000 -200 -2000 I corrected the error when I changed settings) in all instances, I tried the second icon from bottom (the task bar is on the left) but the mouse cursor moves always to the Desktop area to select an icon about 200 pixels above and 200 pixels to the right of the icon and the icon, in this case, a file folder, stays selected and multiple instances of this folder is opened, 30 or more instances.

The mouse cursor is the problem. Should find a way to make it disappear.

Another possible cause is that I see both wacom and evdev in xorg.conf.d, quite possibly I followed the instructions to install wacom drivers / wacom touch some time before installing evdev. Should I uninstall wacom and try? Could this be a reason for a conflict?

No change after activating mode absolute.

Thanks

---

### Post by openick on 2012-05-08
Dear Favux,

With all this help from you the issue could be not be resolved in the partition where I had 11.10 and something that I did in the past to set up touch interfered with the settings, so the problems were persistent.

On another partition I had 12.04 beta and touch started working after upgrading to 12.04 stable. Touch works as one finger touch, without calibration problems. That is a good start :)

Thank you.

---

### Post by Favux on 2012-05-08
Hi openick,

> touch started working after upgrading to 12.04 stable. Touch works as one finger touch, without calibration problems. That is a good start.
Great!

So the questiong becomes whether or not to install the ENAC HID multi-touch kernel driver or not.  Clearly the 3.2 kernel has some support.  Is it what ENAC had or do they have more?  Neeed to look at that.

You might want to install [Mtview]("https://wiki.ubuntu.com/Multitouch/Testing/UsingMtview") from [Testing]("https://wiki.ubuntu.com/Multitouch/Testing") on the Ubuntu [Multitouch]("https://wiki.ubuntu.com/Multitouch/") wiki.  That will give you a visual look at how many fingers are being detected and if it is worth your time to get Ginn set up or not yet.

---

### Post by openick on 2012-05-09
> **Favux said:**
> Hi openick,


Great!

So the questiong becomes whether or not to install the ENAC HID multi-touch kernel driver or not.  Clearly the 3.2 kernel has some support.  Is it what ENAC had or do they have more?  Neeed to look at that.

You might want to install [Mtview]("https://wiki.ubuntu.com/Multitouch/Testing/UsingMtview") from [Testing]("https://wiki.ubuntu.com/Multitouch/Testing") on the Ubuntu [Multitouch]("https://wiki.ubuntu.com/Multitouch/") wiki.  That will give you a visual look at how many fingers are being detected and if it is worth your time to get Ginn set up or not yet.

Thank you for continued help on this problem. 

```

$ lsinput

/dev/input/event3
   bustype : BUS_USB
   vendor  : 0x22ed
   product : 0x1010
   version : 273
   name    : "Hanvon      10.1 "
   phys    : "usb-0000:00:1d.2-1/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS

/dev/input/event4
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x6
   version : 0
   name    : "Video Bus"
   phys    : "LNXVIDEO/video/input0"
   bits ev : EV_SYN EV_KEY

$ sudo ./bin/mtview /dev/input/event3
sudo: ./bin/mtview: command not found

$ sudo mtdev-test /dev/input/event3
supported mt events:
   ABS_MT_SLOT
   ABS_MT_POSITION_X
   ABS_MT_POSITION_Y
   ABS_MT_TRACKING_ID


```sudo ./bin/mtview /dev/input/event3  command does not work. What should I do?

Thank you.

---

### Post by Favux on 2012-05-09
Do you know which /bin directroy it is suppose to be in?  For example /home/username/bin or where?  Check the /bin directory and see if the mtview executable is in there.  If you installed it, it should be somewhere.  Perhaps /usr/bin?  Did you compile it or was it in the repository?

Or open a terminal and cd to root i.e. '/'.  Then 'locate mtview'.

---

### Post by openick on 2012-05-10
Dear Favux,

> **Favux said:**
> 

Or open a terminal and cd to root i.e. '/'.  Then 'locate mtview'.

Thank you. It was in /usr/bin.  I installed the binary.

```
 $ sudo ./usr/bin/mtview /dev/input/event6
map: 0.000000 -0.000015 0.000000 0.000000 1024.000000 600.000000
map: 0.000000 0.000000 0.000000 0.000000 1024.000000 600.000000
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 11 requests (11 known processed) with 0 events remaining.
tvuser@tvb00:/$ sudo ./usr/bin/mtview /dev/input/event6
map: 0.000000 -0.000015 0.000000 0.000000 1024.000000 600.000000
map: 0.000000 0.000000 0.000000 0.000000 1024.000000 600.000000

^Ctvuser@tvb00:/$ sudo ./usr/bin/mtview /dev/input/event6
map: 0.000000 -0.000015 0.000000 0.000000 1024.000000 600.000000
map: 0.000000 0.000000 0.000000 0.000000 1024.000000 600.000000
 
```

1.  On the screen I tried something similar to the examples on page [http://bitmath.org/code/mtview/collection.php](http://bitmath.org/code/mtview/collection.php)  The mtview pop up screen responded with impressions 600-800 pixels to the right of my finger and about the same distance to the south of the touch. Strangely this calibration problem does not exist on the desktop while triggering icons or working on the address bar of the browser.

2.  mtview took inputs from two fingers simultaneously. As two finger touch, it responded well subject to the problems above.

Thank you. :)

---

### Post by Favux on 2012-05-10
Alright so at least mtview can find 2FGT on your touchscreen.  Does that gibe with your understanding of what it is suppose to have?  I wouldn't worry too much about calibration with mtview since it is suppose to demo the device's multitouch.

So why are you only seeing 1FGT?  If the 2FGT was supported by whatever kernel driver has it, presumably in the HID section, evdev should support that.

What's the output of 'xinput list'?  When you look in /var/log/Xorg.0.log which evdev snippet identifier is claiming the touchscreen?  The evdev thouchscreen?

---

### Post by openick on 2012-05-10
> **Favux said:**
> Alright so at least mtview can find 2FGT on your touchscreen.  Does that gibe with your understanding of what it is suppose to have?  I wouldn't worry too much about calibration with mtview since it is suppose to demo the device's multitouch.

So why are you only seeing 1FGT?  If the 2FGT was supported by whatever kernel driver has it, presumably in the HID section, evdev should support that.

What's the output of 'xinput list'?  When you look in /var/log/Xorg.0.log which evdev snippet identifier is claiming the touchscreen?  The evdev thouchscreen?

```
 $ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Hanvon      10.1                            id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse                  id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627;   USB Keyboard                              id=11    [slave  keyboard (3)]
    &#8627;   USB Keyboard                              id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
 
```
Xorg.0.log is at [http://paste.ubuntu.com/979757/](http://paste.ubuntu.com/979757/)



Thank you.

---

### Post by Favux on 2012-05-10
Xorg.0.log shows us:
```
[    26.401] (II) config/udev: Adding input device Hanvon      10.1  (/dev/input/event6)
[    26.401] (**) Hanvon      10.1 : Applying InputClass "evdev touchscreen catchall"
[    26.401] (II) Using input driver 'evdev' for 'Hanvon      10.1 '
[    26.401] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.401] (**) Hanvon      10.1 : always reports core events
[    26.401] (**) evdev: Hanvon      10.1 : Device: "/dev/input/event6"
[    26.402] (--) evdev: Hanvon      10.1 : Vendor 0x22ed Product 0x1010
[    26.402] (--) evdev: Hanvon      10.1 : Found absolute axes
[    26.402] (--) evdev: Hanvon      10.1 : Found absolute multitouch axes
[    26.402] (--) evdev: Hanvon      10.1 : Found x and y absolute axes
[    26.402] (--) evdev: Hanvon      10.1 : Found absolute touchscreen
[    26.402] (II) evdev: Hanvon      10.1 : Configuring as touchscreen
[    26.402] (**) evdev: Hanvon      10.1 : YAxisMapping: buttons 4 and 5
[    26.402] (**) evdev: Hanvon      10.1 : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.402] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input6/event6"
[    26.402] (II) XINPUT: Adding extended input device "Hanvon      10.1 " (type: TOUCHSCREEN, id 9)
[    26.402] (II) evdev: Hanvon      10.1 : initialized for absolute axes.
[    26.403] (**) Hanvon      10.1 : (accel) keeping acceleration scheme 1
[    26.403] (**) Hanvon      10.1 : (accel) acceleration profile 0
[    26.403] (**) Hanvon      10.1 : (accel) acceleration factor: 2.000
[    26.403] (**) Hanvon      10.1 : (accel) acceleration threshold: 4
[    26.404] (II) config/udev: Adding input device Hanvon      10.1  (/dev/input/mouse1)
[    26.404] (II) No input driver specified, ignoring this device.
[    26.405] (II) This device may have been added with another device file.
.....
< and down a little further >
.....
[  2950.822] [dix] Hanvon      10.1 : unable to find touch point 0

```
Let's verify it is actually on evdev given we're seeing:
> [    26.404] (II) No input driver specified, ignoring this device.
[    26.405] (II) This device may have been added with another device file.
for the "mouse1" device.  Run the following command and post the output:
```
xinput list-props 9
```
We should also get some udevadm info in case we need to make a udev rule:
```
udevadm info -a -p $(udevadm info -q path -n /dev/input/event6)
```
But realize ID # and event# can change if you restart and/or hotplug.

---

### Post by openick on 2012-05-10
> **Favux said:**
> Xorg.0.log shows us:
Let's verify it is actually on evdev given we're seeing:

for the "mouse1" device.  Run the following command and post the output:
```
xinput list-props 9
```

```
 $ xinput list-props 9
Device 'Hanvon      10.1 ':
    Device Enabled (135):    1
    Coordinate Transformation Matrix (137):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (260):    0
    Device Accel Constant Deceleration (261):    1.000000
    Device Accel Adaptive Deceleration (262):    1.000000
    Device Accel Velocity Scaling (263):    10.000000
    Device Product ID (252):    8941, 4112
    Device Node (253):    "/dev/input/event6"
    Evdev Axis Inversion (264):    0, 0
    Evdev Axis Calibration (265):    <no items>
    Evdev Axes Swap (266):    0
    Axis Labels (267):    "Abs MT Position X" (258), "Abs MT Position Y" (259)
    Button Labels (268):    "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Wheel Up" (141), "Button Wheel Down" (142)
    Evdev Middle Button Emulation (269):    0
    Evdev Middle Button Timeout (270):    50
    Evdev Third Button Emulation (271):    0
    Evdev Third Button Emulation Timeout (272):    1000
    Evdev Third Button Emulation Button (273):    3
    Evdev Third Button Emulation Threshold (274):    20
    Evdev Wheel Emulation (275):    0
    Evdev Wheel Emulation Axes (276):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (277):    10
    Evdev Wheel Emulation Timeout (278):    200
    Evdev Wheel Emulation Button (279):    4
    Evdev Drag Lock Buttons (280):    0
 
```> **Favux said:**
>  We should also get some udevadm info in case we need to make a udev rule:
```
udevadm info -a -p $(udevadm info -q path -n  /dev/input/event6)
```But realize ID # and event# can change if you  restart and/or hotplug.

i am not sure if I did this part right

```
 $ udevadm info -a -p $(udevadm info -q path -n /dev/input/event6
> ^C
tvuser@tvb00:/$ udevadm info -a -p
info: option requires an argument -- 'p'
tvuser@tvb00:/$ udevadm info -q path -n /dev/input/event6
/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input6/event6 
```Thank you.

---

### Post by Favux on 2012-05-10
OK, it is on evdev and I guess the touch screen snippet.  Hopefully mouse1 is noise.  So we need to see what's going on in the kernel.

It looks like for the udevadm into you forgot the ) after event6 and that's why it got confused.  Copy Paste error in other words.

---

### Post by openick on 2012-05-11
> **Favux said:**
> OK, it is on evdev and I guess the touch screen snippet.  Hopefully mouse1 is noise.  So we need to see what's going on in the kernel.

It looks like for the udevadm into you forgot the ) after event6 and that's why it got confused.  Copy Paste error in other words.


Thanks.  Here is the output.

```
 udevadm info -a -p $(udevadm info -q path -n  /dev/input/event6) 
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input6/event6':
    KERNEL=="event6"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input6':
    KERNELS=="input6"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="Hanvon      10.1 "
    ATTRS{phys}=="usb-0000:00:1d.2-1/input0"
    ATTRS{uniq}==""
    ATTRS{properties}=="2"

  looking at parent device '/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0':
    KERNELS=="4-1:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usbhid"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="03"
    ATTRS{bInterfaceSubClass}=="00"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{supports_autosuspend}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.2/usb4/4-1':
    KERNELS=="4-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="17"
    ATTRS{idVendor}=="22ed"
    ATTRS{idProduct}=="1010"
    ATTRS{bcdDevice}=="0101"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="32"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="2"
    ATTRS{devpath}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Hanvon     "
    ATTRS{product}=="10.1 "

  looking at parent device '/devices/pci0000:00/0000:00:1d.2/usb4':
    KERNELS=="usb4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="35"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0302"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.2.0-24-generic uhci_hcd"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.2"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.2':
    KERNELS=="0000:00:1d.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x27ca"
    ATTRS{subsystem_vendor}=="0x1509"
    ATTRS{subsystem_device}=="0x5024"
    ATTRS{class}=="0x0c0300"
    ATTRS{irq}=="18"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
 
```

---

### Post by Favux on 2012-05-11
Hi openick,

I found a minute to look at the kernel and ENAC stuff.  Progress has been made because you have single finger touch (probably due to improvements made to the evdev driver) but to get multitouch you either have to wait for the 3.4 kernel in 12.10 Quanta whatever or compile the ENAC stuff.  Remember from the ENAC [supported devices table]("http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html") that your Vendor and Product ID's are 22ed:1010.

We're interested in the /drivers/hid directory of the kernel source code.  In Precise's 3.2 kernel in /drivers/hid/hid-ids.c your Hanvon model isn't there:
```
#define USB_VENDOR_ID_HANVON		0x20b3
#define USB_DEVICE_ID_HANVON_MULTITOUCH	0x0a18
```
In the 3.4 kernel (and supposedly the 3.3 kernel, but I haven't looked) and the ENAC stuff you see:
```
#define USB_VENDOR_ID_HANVON		0x20b3
#define USB_DEVICE_ID_HANVON_MULTITOUCH	0x0a18

#define USB_VENDOR_ID_HANVON_ALT	0x22ed
#define USB_DEVICE_ID_HANVON_ALT_MULTITOUCH	0x1010
```
As you see your model has been added.  And then when you look at /drivers/hid/hid-multitouch.c in the 3.2 kernel:
```
	/* PixCir-based panels */
	{ .driver_data = MT_CLS_DUAL_INRANGE_CONTACTID,
		HID_USB_DEVICE(USB_VENDOR_ID_HANVON,
			USB_DEVICE_ID_HANVON_MULTITOUCH) },
```
it becomes in 3.4:
```
	/* Hanvon panels */
	{ .driver_data = MT_CLS_DUAL_INRANGE_CONTACTID,
		HID_USB_DEVICE(USB_VENDOR_ID_HANVON_ALT,
			USB_DEVICE_ID_HANVON_ALT_MULTITOUCH) },
```
The general ENAC compile instructions are here:  [http://lii-enac.fr/en/architecture/linux-input/multitouch-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-howto.html)
Ubuntu specific instructions:  [http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html)
Although the Ubuntu instructions only go up to 11.10 it probably wouldn't be too hard to figure out 12.04.  With luck.


Edit:  I take that back.  When I cloned it:
```
git clone git://git.lii-enac.fr/linux-input/ubuntu-multitouch

cd ubuntu-multitouch
```
and listed available branches.
```
/ubuntu-multitouch$ git branch -r
  origin/hid-multitouch-ubuntu-10.10
  origin/hid-multitouch-ubuntu-11.04
  origin/hid-multitouch-ubuntu-11.10
  origin/hid-multitouch-ubuntu-12.04
```
So it looks like they just haven't updated the instructions to include:
```
git checkout hid-multitouch-ubuntu-12.04
```

---

### Post by openick on 2012-05-16
> **Favux said:**
> Hi openick,

I found a minute to look at the kernel and ENAC stuff.  Progress has been made because you have single finger touch (probably due to improvements made to the evdev driver) but to get multitouch you either have to wait for the 3.4 kernel in 12.10 Quanta whatever or compile the ENAC stuff.  Remember from the ENAC [supported devices table]("http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html") that your Vendor and Product ID's are 22ed:1010.

We're interested in the /drivers/hid directory of the kernel source code.  In Precise's 3.2 kernel in /drivers/hid/hid-ids.c your Hanvon model isn't there:
```
#define USB_VENDOR_ID_HANVON        0x20b3
#define USB_DEVICE_ID_HANVON_MULTITOUCH    0x0a18
```In the 3.4 kernel (and supposedly the 3.3 kernel, but I haven't looked) and the ENAC stuff you see:
```
#define USB_VENDOR_ID_HANVON        0x20b3
#define USB_DEVICE_ID_HANVON_MULTITOUCH    0x0a18

#define USB_VENDOR_ID_HANVON_ALT    0x22ed
#define USB_DEVICE_ID_HANVON_ALT_MULTITOUCH    0x1010
```As you see your model has been added.  And then when you look at /drivers/hid/hid-multitouch.c in the 3.2 kernel:
```
    /* PixCir-based panels */
    { .driver_data = MT_CLS_DUAL_INRANGE_CONTACTID,
        HID_USB_DEVICE(USB_VENDOR_ID_HANVON,
            USB_DEVICE_ID_HANVON_MULTITOUCH) },
```it becomes in 3.4:
```
    /* Hanvon panels */
    { .driver_data = MT_CLS_DUAL_INRANGE_CONTACTID,
        HID_USB_DEVICE(USB_VENDOR_ID_HANVON_ALT,
            USB_DEVICE_ID_HANVON_ALT_MULTITOUCH) },
```The general ENAC compile instructions are here:  [http://lii-enac.fr/en/architecture/linux-input/multitouch-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-howto.html)
Ubuntu specific instructions:  [http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html)
Although the Ubuntu instructions only go up to 11.10 it probably wouldn't be too hard to figure out 12.04.  With luck.


Edit:  I take that back.  When I cloned it:
```
git clone git://git.lii-enac.fr/linux-input/ubuntu-multitouch

cd ubuntu-multitouch
```and listed available branches.
```
/ubuntu-multitouch$ git branch -r
  origin/hid-multitouch-ubuntu-10.10
  origin/hid-multitouch-ubuntu-11.04
  origin/hid-multitouch-ubuntu-11.10
  origin/hid-multitouch-ubuntu-12.04
```So it looks like they just haven't updated the instructions to include:
```
git checkout hid-multitouch-ubuntu-12.04
```


Dear Favux

Sorry for the delay in response. Thank you for the solution. I have carried out the git instructions you have given.

```
it clone git://git.lii-enac.fr/linux-input/ubuntu-multitouch
Cloning into 'ubuntu-multitouch'...
remote: Counting objects: 827, done.
remote: Compressing objects: 100% (561/561), done.
remote: Total 827 (delta 451), reused 421 (delta 194)
Receiving objects: 100% (827/827), 355.43 KiB | 15 KiB/s, done.
Resolving deltas: 100% (451/451), done.
warning: remote HEAD refers to nonexistent ref, unable to checkout.

tvuser@tvb00:~$ cd ubuntu-multitouch
tvuser@tvb00:~/ubuntu-multitouch$ git branch -r
  origin/hid-multitouch-ubuntu-10.10
  origin/hid-multitouch-ubuntu-11.04
  origin/hid-multitouch-ubuntu-11.10
  origin/hid-multitouch-ubuntu-12.04
tvuser@tvb00:~/ubuntu-multitouch$ git checkout hid-multitouch-ubuntu-12.04
Branch hid-multitouch-ubuntu-12.04 set up to track remote branch hid-multitouch-ubuntu-12.04 from origin.
Switched to a new branch 'hid-multitouch-ubuntu-12.04'
tvuser@tvb00:~/ubuntu-multitouch$ 

```What should I do next?  In the first part you have talked about compiling ENAC drivers and then you said "I take it back" and went on to suggest the git clone process. I have done that. Should I also compile ENAC and make changes to hid.ids.c file ?

Thank you.

---

### Post by openick on 2012-05-16
In addition to the steps carried out as described in #47, I compiled multi-touch

```
cd ubuntu-multitouch
tvuser@tvb00:~/ubuntu-multitouch$ git checkout hid-multitouch-ubuntu-12.04
Already on 'hid-multitouch-ubuntu-12.04'
tvuser@tvb00:~/ubuntu-multitouch$ make
make -C /lib/modules/3.2.0-24-generic/build SUBDIRS=/home/tvuser/ubuntu-multitouch modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
  CC [M]  /home/tvuser/ubuntu-multitouch/drivers/hid/hid-debug.o
  CC [M]  /home/tvuser/ubuntu-multitouch/drivers/hid/hid-core.o
  CC [M]  /home/tvuser/ubuntu-multitouch/drivers/hid/hid-input.o
  CC [M]  /home/tvuser/ubuntu-multitouch/drivers/hid/hidraw.o
  LD [M]  /home/tvuser/ubuntu-multitouch/drivers/hid/hid.o
  CC [M]  /home/tvuser/ubuntu-multitouch/drivers/hid/hid-multitouch.o
/home/tvuser/ubuntu-multitouch/drivers/hid/hid-multitouch.c: In function ‘mt_input_mapping’:
/usr/src/linux-headers-3.2.0-24-generic/arch/x86/include/asm/bitops.h:312:8: warning: array subscript is above array bounds [-Warray-bounds]
/usr/src/linux-headers-3.2.0-24-generic/arch/x86/include/asm/bitops.h:312:8: warning: array subscript is above array bounds [-Warray-bounds]
  Building modules, stage 2.
  MODPOST 2 modules
  CC      /home/tvuser/ubuntu-multitouch/drivers/hid/hid-multitouch.mod.o
  LD [M]  /home/tvuser/ubuntu-multitouch/drivers/hid/hid-multitouch.ko
  CC      /home/tvuser/ubuntu-multitouch/drivers/hid/hid.mod.o
  LD [M]  /home/tvuser/ubuntu-multitouch/drivers/hid/hid.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
tvuser@tvb00:~/ubuntu-multitouch$ sudo make install
[sudo] password for tvuser: 
make -C /lib/modules/3.2.0-24-generic/build SUBDIRS=/home/tvuser/ubuntu-multitouch modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
  INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid-multitouch.ko
  INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid.ko
  DEPMOD  3.2.0-24-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
depmod
tvuser@tvb00:~/ubuntu-multitouch$ 

```

Now what else needs to be done ?

Thanks.

---

### Post by Favux on 2012-05-16
Correct, you are cloning the ENAC git repository for Ubuntu and then compiling it once you've switched to the 12.04 branch.

Since the 'make' went OK it looks like the only thing left to do is the 'sudo make install'.  The Makefile they include should do the install automatically for you and from the output of make do a 'sudo depmod -a',  i.e. rebuild all module dependencies.  You can see that towards the end of the make output:
>   INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid-multitouch.ko
  INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid.ko
  DEPMOD  3.2.0-24-generic
That tells you it wants to install the modules hid-multitouch.ko and hid.ko and where it wants them installed to.  But it shouldn't hurt to run:
```
sudo depmod -a
```
after 'sudo make install'.  Then reboot and cross your fingers.  :)

---

### Post by openick on 2012-05-17
> **Favux said:**
> Correct, you are cloning the ENAC git repository for Ubuntu and then compiling it once you've switched to the 12.04 branch.

Since the 'make' went OK it looks like the only thing left to do is the 'sudo make install'.  The Makefile they include should do the install automatically for you and from the output of make do a 'sudo depmod -a',  i.e. rebuild all module dependencies.  You can see that towards the end of the make output:

That tells you it wants to install the modules hid-multitouch.ko and hid.ko and where it wants them installed to.  But it shouldn't hurt to run:
```
sudo depmod -a
```after 'sudo make install'.  Then reboot and cross your fingers.  :)





sudo make install command is not working. Am I in the wrong path?

```
cd ubuntu-multitouch
tvuser@tvb00:~/ubuntu-multitouch$ sudo make install
[sudo] password for tvuser: 
make -C /lib/modules/3.2.0-24-generic/build SUBDIRS=/home/tvuser/ubuntu-multitouch modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
  INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid-multitouch.ko
  INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid.ko
  DEPMOD  3.2.0-24-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
depmod
tvuser@tvb00:~/ubuntu-multitouch$ sudo depmod -a
tvuser@tvb00:~/ubuntu-multitouch$ sudo make install
make -C /lib/modules/3.2.0-24-generic/build SUBDIRS=/home/tvuser/ubuntu-multitouch modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
  INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid-multitouch.ko
  INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid.ko
  DEPMOD  3.2.0-24-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
depmod

```I then tried this:

```
 tvuser@tvb00:~$ cd /usr/src/linux-headers-3.2.0-24-generic
tvuser@tvb00:/usr/src/linux-headers-3.2.0-24-generic$ make install
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:433:1: fatal error: opening dependency file scripts/basic/.fixdep.d: Permission denied
compilation terminated.
make[2]: *** [scripts/basic/fixdep] Error 1
make[1]: *** [scripts_basic] Error 2
sh /usr/src/linux-headers-3.2.0-24-generic/arch/x86/boot/install.sh 3.2.0-24-generic arch/x86/boot/bzImage \
        System.map "/boot"

 *** Missing file: arch/x86/boot/bzImage
 *** You need to run "make" before "make install".

make[1]: *** [install] Error 1
make: *** [install] Error 2
tvuser@tvb00:/usr/src/linux-headers-3.2.0-24-generic$ sudo make install
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf --silentoldconfig Kconfig
sh /usr/src/linux-headers-3.2.0-24-generic/arch/x86/boot/install.sh 3.2.0-24-generic arch/x86/boot/bzImage \
        System.map "/boot"

 *** Missing file: arch/x86/boot/bzImage
 *** You need to run "make" before "make install".

make[1]: *** [install] Error 1
make: *** [install] Error 2
tvuser@tvb00:/usr/src/linux-headers-3.2.0-24-generic$ sudo make
\  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  UPD     include/generated/utsrelease.h
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make: *** [prepare0] Error 2
tvuser@tvb00:/usr/src/linux-headers-3.2.0-24-generic$ sudo make
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make: *** [prepare0] Error 2
tvuser@tvb00:/usr/src/linux-headers-3.2.0-24-generic$ sudo make install
sh /usr/src/linux-headers-3.2.0-24-generic/arch/x86/boot/install.sh 3.2.16 arch/x86/boot/bzImage \
        System.map "/boot"

 *** Missing file: arch/x86/boot/bzImage
 *** You need to run "make" before "make install".

make[1]: *** [install] Error 1
make: *** [install] Error 2
tvuser@tvb00:/usr/src/linux-headers-3.2.0-24-generic$ sudo depmod -a
tvuser@tvb00:/usr/src/linux-headers-3.2.0-24-generic$ cd
tvuser@tvb00:~$ cd ubuntu-multitouch
tvuser@tvb00:~/ubuntu-multitouch$ sudo make
make -C /lib/modules/3.2.0-24-generic/build SUBDIRS=/home/tvuser/ubuntu-multitouch modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
  Building modules, stage 2.
  MODPOST 2 modules
  CC      /home/tvuser/ubuntu-multitouch/drivers/hid/hid-multitouch.mod.o
  LD [M]  /home/tvuser/ubuntu-multitouch/drivers/hid/hid-multitouch.ko
  CC      /home/tvuser/ubuntu-multitouch/drivers/hid/hid.mod.o
  LD [M]  /home/tvuser/ubuntu-multitouch/drivers/hid/hid.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
tvuser@tvb00:~/ubuntu-multitouch$ sudo make install
make -C /lib/modules/3.2.0-24-generic/build SUBDIRS=/home/tvuser/ubuntu-multitouch modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
  INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid-multitouch.ko
  INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid.ko
  DEPMOD  3.2.16
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
depmod
tvuser@tvb00:~/ubuntu-multitouch$ sudo make install hid-multitouch.ko
make -C /lib/modules/3.2.0-24-generic/build SUBDIRS=/home/tvuser/ubuntu-multitouch modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
  INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid-multitouch.ko
  INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid.ko
  DEPMOD  3.2.16
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
depmod
make: *** No rule to make target `hid-multitouch.ko'.  Stop.  
```Now it says DEPMOD 3.2.16

---

### Post by Favux on 2012-05-17
You appear to be in the correct directory when you did:
```
tvuser@tvb00:~/ubuntu-multitouch$ sudo make install
```
I missed that you already ran that in post #48 before.  Oops.  But it doesn't hurt to rerun it.

Why did you then change to this directory and run it again?
```
tvuser@tvb00:~$ cd /usr/src/linux-headers-3.2.0-24-generic
tvuser@tvb00:/usr/src/linux-headers-3.2.0-24-generic$ make install
```
Besides you don't appear to be root with just 'make install' in that directory, luckily.  The Makefile that directs the installation is in the ubuntu-multitouch folder in the 12.04 branch you have switched to.  The Makefile in /usr/src/linux-headers-3.2.0-24-generic would presumably be for the kernel itself, not a specific module.  Would have to look.

That output looks OK.  But it didn't work after a reboot?

In:
```
lsmod
```
do you see **hid** and **hid-multitouch**?  Did you do a?
```
sudo depmod -a
```

---

### Post by openick on 2012-05-17
```
tvuser@tvb00:~$ cd ubuntu-multitouch
tvuser@tvb00:~/ubuntu-multitouch$ sudo depmod -a
tvuser@tvb00:~/ubuntu-multitouch$ lsmod
Module                  Size  Used by
hidp                   22165  0 
btusb                  17912  2 
joydev                 17393  0 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
hid_multitouch         17212  0 
bnep                   17830  2 
ath3k                  12825  0 
rfcomm                 38139  12 
arc4                   12473  2 
bluetooth             158438  25 hidp,btusb,ath3k,bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath9k                 117425  0 
mac80211              436455  1 ath9k
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           13781  1 ath9k
ath9k_hw              391523  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
mac_hid                13077  0 
cfg80211              178679  3 ath9k,mac80211,ath
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  414637  2 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
soundcore              14635  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  1 hid_multitouch
hid                    77367  3 hidp,hid_multitouch,usbhid
tvuser@tvb00:~/ubuntu-multitouch$ 

```

I can see hid and hid_multitouch here, but it still doesn't work.   What am I missing while reading your instructions ?

Thank you.

---

### Post by cotj on 2012-05-17
I’d should verify with you here. Which isn't something I normally do! I enjoy studying a post that can make folks think. Also, thanks for allowing me to comment!

---

### Post by Favux on 2012-05-17
It looks like we've followed the ENAC instructions.  Did you reboot before the ***lsmod***?

Let's see what the outputs of the following tell us, if anything:
```
modinfo hid

modinfo hid-multitouch
```
Has ***xinput list*** changed?  Please post the Hanvon line(s) again.

Does mtview show multitouch?

And do you have **ginn** installed?

---

### Post by openick on 2012-05-18
> **Favux said:**
> It looks like we've followed the ENAC instructions.  Did you reboot before the ***lsmod***?

Let's see what the outputs of the following tell us, if anything:
```
modinfo hid

modinfo hid-multitouch
```Has ***xinput list*** changed?  Please post the Hanvon line(s) again.

Does mtview show multitouch?

And do you have **ginn** installed?

Yes I did reboot before lsmod

```
 modinfo hid
filename:       /lib/modules/3.2.0-24-generic/extra/drivers/hid/hid.ko
license:        GPL
author:         Jiri Kosina
author:         Vojtech Pavlik
author:         Andreas Gal
srcversion:     39839014124B816CEB21B74
depends:        
vermagic:       3.2.0-24-generic SMP mod_unload modversions 686 
parm:           debug:toggle HID debugging messages (int)
tvuser@tvb00:~$ modinfo hid-multitouch
filename:       /lib/modules/3.2.0-24-generic/extra/drivers/hid/hid-multitouch.ko
license:        GPL
description:    HID multitouch panels
author:         Benjamin Tissoires <benjamin.tissoires@gmail.com>
author:         Stephane Chatty <chatty@enac.fr>
srcversion:     C0B7EB790198EB06651001D
alias:          hid:b0003v00001477p00001025
alias:          hid:b0003v00001477p00001026
alias:          hid:b0003v00001477p00001024
alias:          hid:b0003v00001477p00001022
alias:          hid:b0003v00001477p00001023
alias:          hid:b0003v00001477p00001021
alias:          hid:b0003v00001477p0000100E
alias:          hid:b0003v00001477p00001007
alias:          hid:b0003v00001477p00001006
alias:          hid:b0003v00002505p00000220
alias:          hid:b0003v0000227Dp00000A19
alias:          hid:b0003v0000227Dp00000709
alias:          hid:b0003v00001E5Ep00000313
alias:          hid:b0003v00001784p00000016
alias:          hid:b0003v00001403p00005001
alias:          hid:b0003v00000483p00003261
alias:          hid:b0003v00001F87p00000002
alias:          hid:b0003v00000408p00003008
alias:          hid:b0003v00000408p00003001
alias:          hid:b0003v00000408p00003000
alias:          hid:b0003v00002087p00000703
alias:          hid:b0003v000020B3p00000A18
alias:          hid:b0003v0000093Ap00008003
alias:          hid:b0003v0000093Ap00008002
alias:          hid:b0003v0000093Ap00008001
alias:          hid:b0003v000014E1p00003500
alias:          hid:b0003v000004DAp0000104D
alias:          hid:b0003v000004DAp00001044
alias:          hid:b0003v0000062Ap00007100
alias:          hid:b0003v00000486p00000186
alias:          hid:b0003v00000486p00000185
alias:          hid:b0003v0000202Ep00000007
alias:          hid:b0003v0000202Ep00000006
alias:          hid:b0003v00001FD2p00000064
alias:          hid:b0003v00006615p00000070
alias:          hid:b0003v0000222Ap00000001
alias:          hid:b0003v00001CB6p00006651
alias:          hid:b0003v00001CB6p00006650
alias:          hid:b0003v000022EDp00001010
alias:          hid:b0003v00001AADp0000000F
alias:          hid:b0003v00000DFCp00000003
alias:          hid:b0003v000004E7p00000022
alias:          hid:b0003v00000EEFp0000A001
alias:          hid:b0003v00000EEFp00007349
alias:          hid:b0003v00000EEFp00007302
alias:          hid:b0003v00000EEFp000072FA
alias:          hid:b0003v00000EEFp000072AA
alias:          hid:b0003v00000EEFp000072A1
alias:          hid:b0003v00000EEFp00007262
alias:          hid:b0003v00000EEFp0000726B
alias:          hid:b0003v00000EEFp0000722A
alias:          hid:b0003v00000EEFp00007224
alias:          hid:b0003v00000EEFp0000725E
alias:          hid:b0003v00000EEFp00007207
alias:          hid:b0003v00000EEFp0000720C
alias:          hid:b0003v00000EEFp0000480E
alias:          hid:b0003v00000EEFp0000480D
alias:          hid:b0003v000004B4p0000C001
alias:          hid:b0003v00001FF7p00000013
alias:          hid:b0003v00002247p00000001
alias:          hid:b0003v00002087p00000F01
alias:          hid:b0003v00002087p00000B03
alias:          hid:b0003v00002087p00000A02
alias:          hid:b0003v00002087p00000A01
alias:          hid:b0003v000003EBp00002118
alias:          hid:b0003v000003EBp0000211C
alias:          hid:b0003v00002101p00001011
alias:          hid:b0003v00000596p00000506
alias:          hid:b0003v00000596p00000502
alias:          hid:b0003v00000596p00000500
depends:        hid,usbhid
vermagic:       3.2.0-24-generic SMP mod_unload modversions 686 
parm:           trace:Enable trace mode (bool)

```I have ginn installed


```
xinput list
  &#8627; Hanvon      10.1                            id=9    [slave  pointer  (2)]

```mtview window still takes inputs from only two fingers.

Thank you.

---

### Post by Favux on 2012-05-18
The ***modinfo hid*** is identical to what I get so not helpful.

Can you navigate to the two .ko's in nautilus and check them?
> INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid-multitouch.ko
INSTALL /home/tvuser/ubuntu-multitouch/drivers/hid/hid.ko
Right click on hid-multitouch.ko and hid.ko and see if in Properties they have the date you compiled them?  May 16 correct?

---

### Post by openick on 2012-05-18
> **Favux said:**
> The ***modinfo hid*** is identical to what I get so not helpful.

Can you navigate to the two .ko's in nautilus and check them?

Right click on hid-multitouch.ko and hid.ko and see if in Properties they have the date you compiled them?  May 16 correct?

Nautilus did not even so volume of these two files. man ls helped me figure out a useful terminal command

```


tvuser@tvb00:~/ubuntu-multitouch/drivers/hid$ ls --full-time

-rw-r--r-- 1 root   root   106835 2012-05-17 20:45:23.791871094 +0530 hid.ko
-rw-r--r-- 1 root   root    19027 2012-05-17 20:45:22.879866576 +0530 hid-multitouch.ko

```NOt sure if these are time accessed or time modified.

---

### Post by Favux on 2012-05-18
> NOt sure if these are time accessed or time modified. 
Me either.  Did you compile them on the 17th or the 16th.  Check their date in the ENAC folder if you are not sure.
> Nautilus did not even so volume of these two files. 
I'm not sure I understand.  It should.  Where did you look?

You can try entering:
```
locate hid.ko
and
locate hid-multitouch.ko
```
That should show you the path to navigate to the file.  For example that shows me:
> /lib/modules/3.2.0-24-generic/kernel/drivers/hid/hid.ko
among a bunch of others.  But you want to look at the one in your current kernel.

I would like to be sure you have the compiled modules in place before we go on to try the udev rule ENAC suggests.

---

### Post by openick on 2012-05-19
> **Favux said:**
> Me either.  Did you compile them on the 17th or the 16th.  Check their date in the ENAC folder if you are not sure.

I'm not sure I understand.  It should.  Where did you look?

 I was earlier looking at the file properties in nautilius on these two  files on the ubuntu-multitouch > drivers > hid path.

Can't find enac folder. locate ENAC and locate enac did not return any results.

> **Favux said:**
> You can try entering:
```
locate hid.ko
and
locate hid-multitouch.ko
```

On PATH ```
lib/modules/3.2.0-24-generic/extra/drivers/hid
```
 
 hid.ko last accessed AND last modified Thursday 17 May 2012 07:02:14 PM IST
 
 hid-multitoudch.ko  last accessed Friday 18 May 2012 08:31:47 PM IST
                                        last modified Thursday 17 May 2012 07:02:14 PM IST

---

### Post by Favux on 2012-05-19
Sorry, by the ENAC folder I meant the ubuntu-multitouch folder you cloned from ENAC.

> hid.ko last accessed AND last modified Thursday 17 May 2012 07:02:14 PM IST

hid-multitoudch.ko last accessed Friday 18 May 2012 08:31:47 PM IST
last modified Thursday 17 May 2012 07:02:14 PM IST 
Nice work!  That sure looks like the compiled modules copied into place.

Alright we're ready to try the udev rule because they say:
> The current release of hid-multitouch found on our site allows you to add any multitouch capable hardware from the user space. If your device seems to be recognized by the system (but either in single touch only or by doing strange stuffs) and after installing hid-multitouch it is not seen at all, that means that you can manually add it to our driver.
Give me a bit of time to go over it.

---

### Post by Favux on 2012-05-19
Could you check in /lib/udev/rules.d if you have a file called 41-hid-multitouch.rules?  If you do please post its contents.  And enclose them in code tags (the # in the right upper side) to preserve the formatting.

---

### Post by openick on 2012-05-19
Thank You :)


Will wait.

---

### Post by Favux on 2012-05-19
OK, here we go.  :)

Download the attached load_hid_multitouch.sh.txt onto your Desktop and rename it "load_hid_multitouch.sh" (without the quotes).

Copy it into place:
```
sudo cp ~/Desktop/load_hid_multitouch.sh /etc/udev/load_hid_multitouch.sh
```
Change its permissions:
```
sudo chmod 744 /etc/udev/load_hid_multitouch.sh
```
Now if you right click on it and check in Properties in the Permissions tab it should be executable.

Then using:
```
gksudo gedit /etc/udev/rules.d/41-hid-multitouch.rules
```
Copy and Paste the following line into the empty file.
```
SUBSYSTEM=="usb", ATTRS{idVendor}=="22ed", ATTRS{idProduct}=="1010, RUN+="/bin/sh /etc/udev/load_hid_multitouch.sh $env{ID_VENDOR_ID} $env{ID_MODEL_ID}"
```

Save and Close.  Reboot.  My fingers are crossed.

---

### Post by openick on 2012-05-19
> **Favux said:**
> OK, here we go.  :)

Download the attached load_hid_multitouch.sh.txt onto your Desktop and rename it "load_hid_multitouch.sh" (without the quotes).

Copy it into place:
```
sudo cp ~/Desktop/load_hid_multitouch.sh /etc/udev/load_hid_multitouch.sh
```Change its permissions:
```
sudo chmod 744 /etc/udev/load_hid_multitouch.sh
```Now if you right click on it and check in Properties in the Permissions tab it should be executable.

Then using:
```
gksudo gedit /etc/udev/rules.d/41-hid-multitouch.rules
```Copy and Paste the following line into the empty file.
```
SUBSYSTEM=="usb", ATTRS{idVendor}=="22ed", ATTRS{idProduct}=="1010, RUN+="/bin/sh /etc/udev/load_hid_multitouch.sh $env{ID_VENDOR_ID} $env{ID_MODEL_ID}"
```Save and Close.  Reboot.  My fingers are crossed.

First, I missed your question from #61.  In /lib/udev/rules.d there was no file called 41-hid-multitouch.rules

I followed the steps and created /etc/udev/rules.d/41-hid-multitouch.rules and copied and pasted the SUBSYSTEM... code.  Also, downloaded, moved and changed the file permission of the text file that you have attached.

After reboot, mtview still took input only from two fingers. 

What I have noticed is that you have asked me to create 41-hid-multitouch.rules in /etc/udev/rules.d where there are only  the following files 

```
41-hid-multitouch.rules   70-persistent-cd.rules   README
41-hid-multitouch.rules~  70-persistent-net.rules
```Did you mean to create the file in /lib/udev/rules.d ?   Or did I miss something else?

```
tvuser@tvb00:/usr/bin$ sudo ./mtview /dev/input/event6
map: 0.000000 -0.000015 0.000000 0.000000 1024.000000 600.000000
map: 0.000000 0.000000 0.000000 0.000000 1024.000000 600.000000
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 443 requests (11 known processed) with 0 events remaining.

```


Thank you

---

### Post by Favux on 2012-05-19
Unfortunately the forum slowdown is making this a pain.
> Did you mean to create the file in /lib/udev/rules.d ? Or did I miss something else?
No, you don't want to do that, /etc/udev/rules.d is where we want it.

I was looking for the udev rule template.  From the instructions it appeared it was suppose to be installed when you did the 'sudo make install'.  But when I looked at my clone of the ubuntu-multitouch git repository I didn't see it or how it would be installed.  Turned out there were copies of what we needed on the ENAC site.  I just had to find them.
> After reboot, mtview still took input only from two fingers. 
Well 2FGT is still considered multitouch.  Could you tell me again how many fingers is your Hanvon touchscreen suppose to support?  And site a source if you can.

If things were working you should be seeing 2FGT gestures in applications that support gestures or through ginn and its wishes.xml (located in /etc) in applicattions that don't.

---

### Post by openick on 2012-05-21
> **Favux said:**
> 

Well 2FGT is still considered multitouch.  Could you tell me again how many fingers is your Hanvon touchscreen suppose to support?  And site a source if you can.

If things were working you should be seeing 2FGT gestures in applications that support gestures or through ginn and its wishes.xml (located in /etc) in applicattions that don't.


I am sorry,  somewhere along the process I was told that all capacitive touch is at least 5 fingers, so didn't check with the manufacturer. I did that after I saw this question from you.

> [COLOR=#1f497d][FONT=&quot] (From the manufacturer)  2.      [/FONT][/COLOR][COLOR=#1f497d][FONT=&quot]No ~~ it supports 2 fingers only.  However, we’re verifying 4 fingers touch now and hope that we could implement it into mass production soon.[/FONT][/COLOR]I am not sure if the reply is based on a full understanding of the touch screen's capabilities or based on similar experiences that they had with the touch screen, due to driver issues. 

If it appears that this is a hardware limitation,  after so much of your time on this problem so far, it is time to recognize this limitation. 

It is a very long thread on a single issue, I am not as much worried about multi-touch not working as much about the time that you have spent on this problem not resulting in a solution that would have made you feel that the time was well spent:sad:

---

### Post by Favux on 2012-05-21
Hi openick,

No worries, this has been an interesting challenge.

Given that Hanvon says it is 2 FGT and you are seeing 2FGT on mtview it should be there.

So I think you are very close to having 2FG gestures.  We might be missing just a little piece of the puzzle now.  What I'm not sure.

Since you have 1FGT I suspect the problem is with ginn.  But I am not very familiar with it.  I do have some examples of it working and changing its wishes.xml file on the N-Trig HOW TO:  [http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492)  Maybe a quick skim of that would give you an idea.

---

### Post by openick on 2012-05-27
> **Favux said:**
> 

Since you have 1FGT I suspect the problem is with ginn.  But I am not very familiar with it.  I do have some examples of it working and changing its wishes.xml file on the N-Trig HOW TO:  [http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492)  Maybe a quick skim of that would give you an idea.

Dear Favux,

1252492 is a post with 160 pages, and even the first page looks difficult for me to follow. 

I installed utouch-gesturetest, downloaded ntrig.c from [http://ofb.net/~rafi/2010_05_04_hid-ntrig.c]("http://ofb.net/%7Erafi/2010_05_04_hid-ntrig.c") and again followed the instructions from >  ```
sudo apt-get build-dep linux-meta  sudo apt-get build-dep linux-image-$(uname -r)  cd Desktop  apt-get source linux-image-$(uname -r)  wget http://ofb.net/~rafi/2010_05_04_hid-ntrig.c  cp 2010_05_04_hid-ntrig.c linux-2.6.32/drivers/hid/hid-ntrig.c  cd linux-2.6.32/drivers/hid  sudo make -C /lib/modules/`uname -r`/build M=`pwd` modules  sudo cp hid-ntrig.ko /lib/modules/`uname -r`/kernel/drivers/hid/  sudo depmod -a
```and ran into the following difficulty:

```
2012-05-27 21:27:03 (39.5 KB/s) - `2010_05_04_hid-ntrig.c' saved [23406/23406]

tvuser@tvb00:~/Desktop$ cp 2010_05_04_hid-ntrig.c linux-2.6.32/drivers/hid/hid-ntrig.c
cp: cannot create regular file `linux-2.6.32/drivers/hid/hid-ntrig.c': No such file or directory
tvuser@tvb00:~/Desktop$ cp 2010_05_04_hid-ntrig.c linux-2.6.32-24/drivers/hid/hid-ntrig.c
cp: cannot create regular file `linux-2.6.32-24/drivers/hid/hid-ntrig.c': No such file or directory
tvuser@tvb00:~/Desktop$ cp 2010_05_04_hid-ntrig.c /usr/src/linux-headers-3.2.0-24-generic/include/config/hid
cp: cannot create regular file `/usr/src/linux-headers-3.2.0-24-generic/include/config/hid/2010_05_04_hid-ntrig.c': Permission denied
tvuser@tvb00:~/Desktop$ sudo cp 2010_05_04_hid-ntrig.c /usr/src/linux-headers-3.2.0-24-generic/include/config/hid
[sudo] password for tvuser: 
tvuser@tvb00:~/Desktop$ cd /usr/src/linux-headers-3.2.0-24-generic/include/config/hid
tvuser@tvb00:/usr/src/linux-headers-3.2.0-24-generic/include/config/hid$ sudo make -C /lib/modules/`uname -r`/build M=`pwd` modules
make: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
scripts/Makefile.build:44: /usr/src/linux-headers-3.2.0-24-generic/include/config/hid/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-3.2.0-24-generic/include/config/hid/Makefile'.  Stop.
make: *** [_module_/usr/src/linux-headers-3.2.0-24-generic/include/config/hid] Error 2
make: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
tvuser@tvb00:/usr/src/linux-headers-3.2.0-24-generic/include/config/hid$ ls nt*
ntrig.c  ntrig.h

```From the instructions in this post 160 pages long, I do not know what to do and what to skip.

---

### Post by Favux on 2012-05-27
Hi openick,

You do not need to compile the hid-ntrig.ko because you do not have a N-Trig digitizer.

I just wanted you to look at the ginn information.  On the HOW TO it is under:
> 1) Oneiric, Natty, & Maverick:

a) Win7 updated firmware (4.6.5.8.5 in the 2.239 software bundle) and multitouch ("N-Trig MultiTouch")
starting with:
> If you want to try out some multitouch gestures use ginn ("Gesture Injector: No-GEIS, No-Toolkits"). With Natty ginn should be installed by default, or if it isn't it's in the repository. Just install it using your preferred method, i.e. Synaptic Package Manager, Software Center, or apt-get.
going to:
> floyd0815 shares two videos of ginn in action "Ubuntu 10.10 with GINN (gestures) on an HP TX2" & "Ubuntu 10.10 HP TX2 ginn magick-rotation onboard". He also provides examples of the ginn scripts he is using in posts #1391, #1392, & #1404. smallblackanimal joins the fun in post #1402 as does wildschweini in post #1413. See also the original Maverick ginn post at post #1272 by Ayuthia.
Then you could follow the links to the various wishes.xml file scripts in the thread.

As I said I don't use ginn so I don't know much about it.  But I just wanted something to get you started.  You could then google up more information.  For example did things change for ginn again in Precise?  Maybe the wishes.xml syntax changed again?

---

