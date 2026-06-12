---
title: "radeon 9200 + fglrx 8.28.8_amd64"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by je1117 on 2007-01-18
OK, so I'm trying my best here, but I need to help of you fine people once again. I say again, but I haven't even got my video running yet. SO, a recap:

I am running a Radeon 9200 on an AMD 64 bit system. I feel like I have tried every possible combination of video drivers and acclerators and open sources and etc. and my video will still not run. The only thing that works are the vesa drivers. I came to the conclusion that this guide was seemingly the best "looking." Mind you, i'm extremely new at this. But I feel like I finally understand basically what each of the important parts of getting this to run, ACTUALLY DO!

So with that in mind, here's my xorg.conf after following the guide (using the 8.28.8 drivers, which are the newest that still "support" my radeon.) ALSO in addition to the way this guide installs the three debs, I also tried using the GUI interface and to the same effect, I boot to the black screen before the login, and that is where I remain until I reboot.

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
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
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
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
Identifier "Q95-2"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. RV280 [Radeon 9200]"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. RV280 [Radeon 9200]"
Monitor "Q95-2"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]"
Device "aticonfig-Device[0]"
Monitor "aticonfig-Monitor[0]"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection


PLEASE DON'T MAKE ME WAIT UNTIL I HAVE ENOUGH $$ FOR A NEW CARD.

---

### Post by Fitzy_oz on 2007-01-18
> **je1117 said:**
> OK, so I'm trying my best here, but I need to help of you fine people once again. I say again, but I haven't even got my video running yet. SO, a recap:

I am running a Radeon 9200 on an AMD 64 bit system. I feel like I have tried every possible combination of video drivers and acclerators and open sources and etc. and my video will still not run. The only thing that works are the vesa drivers. I came to the conclusion that this guide was seemingly the best "looking." Mind you, i'm extremely new at this. But I feel like I finally understand basically what each of the important parts of getting this to run, ACTUALLY DO!

So with that in mind, here's my xorg.conf after following the guide (using the 8.28.8 drivers, which are the newest that still "support" my radeon.) ALSO in addition to the way this guide installs the three debs, I also tried using the GUI interface and to the same effect, I boot to the black screen before the login, and that is where I remain until I reboot.

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
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
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
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
Identifier "Q95-2"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. RV280 [Radeon 9200]"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. RV280 [Radeon 9200]"
Monitor "Q95-2"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]"
Device "aticonfig-Device[0]"
Monitor "aticonfig-Monitor[0]"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection


PLEASE DON'T MAKE ME WAIT UNTIL I HAVE ENOUGH $$ FOR A NEW CARD.


[Twitching] The word direct rendering and any Radeon card make twitch uncontrollably but I will tell you what I did to get my 9600 working (Which nearly resulted in me sledgehammering the computer in the process).

Try the following: 
Edit you xorg.conf file and remove the following or quote (#) the following lines;

Section "Device"
Identifier "ATI Technologies, Inc. RV280 [Radeon 9200]"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection

Next:
run sudo modprobe fglrx, if it posts an error message, post it here but it'll be a fair bet that the kernel module has failed to load...

Next:
edit you /etc/modules and find the disabled modules line and add fglrx and agpgart and even nvagpgart to it if there not there already.

Next:
edit your /etc/default/linux-restricted-modules-common
add this line to it:

DISABLED_MODULES="fglrx"

Next:
sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)

Next: 
ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper

If you've still got the debs handy use them and skip this part.

Next: Install them again
sudo dpkg -i xorg-driver-fglrx_8.29.6-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.29.6-1_i386.deb
sudo dpkg -i fglrx-control_8.29.6-1_i386.deb

Next: 
sudo rm /usr/src/fglrx-kernel*.deb

This is where it finally started working for me was building the new source

Next:
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

Next:
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv


Now just reboot it and give it a try - These were the instructions of the Linux ATI Driver wiki - They worked for me but it took a couple of goes and adding the kernel modules manually and disabling the others manually.  Good luck.

:)

---

### Post by je1117 on 2007-01-19
> **Fitzy_oz said:**
> adding the kernel modules manually and disabling the others manually.

How did you go about doing that?

---

### Post by je1117 on 2007-01-19
YES! I have finally made it past the black screen, and have successfully logged into Dapper using the fglrx drivers. All I had to do was add Option "BusType" "PCI" in the fglrx device section.

Except my OpenGL isn't working right. 
This is what I get when I enter glxgears, glxinfo, etc.

glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory.

SO that's my new problem, any suggestions?

---

### Post by Fitzy_oz on 2007-01-19
> **je1117 said:**
> YES! I have finally made it past the black screen, and have successfully logged into Dapper using the fglrx drivers. All I had to do was add Option "BusType" "PCI" in the fglrx device section.

Except my OpenGL isn't working right. 
This is what I get when I enter glxgears, glxinfo, etc.

glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory.

SO that's my new problem, any suggestions?

yes, reinstall mesa3d libraries - That should fix that problem...

---

