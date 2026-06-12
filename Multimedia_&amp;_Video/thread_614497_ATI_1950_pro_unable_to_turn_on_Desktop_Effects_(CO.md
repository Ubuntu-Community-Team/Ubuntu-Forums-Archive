---
title: "ATI 1950 pro unable to turn on Desktop Effects (COMPIZ) on 7.10"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by SKiFF on 2007-11-16
Hello,

It took me some time to enable 3d acceleration drivers (restricted), it seems the only way that works somewhat is when I use the drivers from the ATI site and manually install them.
If I simply click on install restricted drivers from clean install, it after the login window, it just goes black...so I had to use the alternative way using the drivers from ATI sit, which allows me to use dual monitors and proper resolution.

But now when I try to use COMPIZ (using visual effects settings) I get the following error:
"The Composite extension is not available."

if in my xorg.conf I do
Section "Extensions"
Option "Composite" "1"
EndSection

instead of Composite 0
I get the error saying:
"Desktop Effects could not be enabled"

and if I do sudo apt-get install xserver-xgl (as recommended in some posts and has worked for some) it after login screen, i simple see the mouse on the screen and thats it.


Any ideas on what to do? Im doing this from a clean install, so if anyone was successful with enabling desktop effects on ATI (especially x1950), do post here

Thanks in advance,

Skiff.

EDIT:
$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6958 Release


XORG.CONF:
Section "ServerLayout"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
Identifier "Default Layout"
screen "Default Screen" 0 0
Inputdevice "Generic Keyboard"
Inputdevice "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
Load "glx"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "DELL2407WFPH"
Option "DPMS"
EndSection

Section "Device"
Identifier "Generic Video Card"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Busid "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "DELL2407WFPH"
Defaultdepth 24
SubSection "Display"
Modes "1920x1200" "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "Extensions"
Option "Composite" "1"
EndSection
___________

---

### Post by Yellow Pasque on 2007-11-17
You are using the latest drivers (8.42.3) from ATI, correct?
Also, you have to add fglrx to the WHILETLISTED driver string in the /usr/bin/compiz-manager file.

---

### Post by SKiFF on 2007-11-18
> **Temüjin said:**
> You are using the latest drivers (8.42.3) from ATI, correct?
Also, you have to add fglrx to the WHILETLISTED driver string in the /usr/bin/compiz-manager file.

ok Ive done that, the error message went away, but it still doesnt work, when i set visual settings, everything disappears except the background and then it returns to normal, no eye candy mode.
Any ideas?

glxinfo | grep direct
direct rendering: Yes

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6958 Release
s

---

