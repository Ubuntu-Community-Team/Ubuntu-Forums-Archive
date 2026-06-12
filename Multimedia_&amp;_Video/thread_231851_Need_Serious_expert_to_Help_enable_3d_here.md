---
title: "Need Serious expert to Help enable 3d here"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by sherpah on 2006-08-07
I know this has been covered before in other forums to some degree - but I have a specific problem with my laptop and my Intel 855GM onboard graphics card - and I think it must be related to my overall noobishness - though I have some broader experence with linux - (Red Hat pre Fedore, etc) I am shaking off the rust... here is my problem:

I have a fujitsu Lifebook P5010 subnotebook - and I am dualbooting Ubuntu. In order to install on a dualboot system with and keep my current bootloader intact (bootitng) I needed to install Ubuntu from the ALTERNATE INSTALL CD.

I Installed on expert mode to avoid putting GRUB on the MBR. I was successful, and after a base install of UBUNTU from the ALTERNATE CD, I then used SUDO APTITUDE command to install all the packages I thought I needed, including Xserver and GNOME. I then reboot, and Xserver and GNome works, I even used the little hack program to get widescreen enabled (1280x768 native on my P5010). But here is the main problem - I cannot run anything that requires 3d - specifically GLX. GLXGEARS and GLXINFO give me strange errors and wont work at all - see below.

Now I have read through hours of threads on the net and tried all kinds of stuff - including attempting to change kernels from a 386 to a 686 - but i don't think I need a 686 kernel. Also - when I boot in UBUNTU off the UBUNUT LIVE CD - GLX works perfectly - its just off of my install that it doesnt - so I know my hardware can support it on Ubuntu.

If I run GLXGEARS nothing happens, except this error message:

Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


If I run GLINFO I get this:

name of display: :0.0
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
0x21 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
0x22 24 dc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None

My Xorg.conf looks like this;
Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# path to defoma fonts
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
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Intel Corporation 82852/855GM Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82852/855GM Integrated Graphics Device"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection


--------------------------------
Uname -a:

Linux 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux





Any advice is appreciated. I think I am missing something basic, like maybe a simlink to a lib file - but the problem is just over my head.

Thanks in advance.

---

### Post by CameronCalver on 2006-08-08
is the onboard gfx nvidia?

---

### Post by sherpah on 2006-08-08
No,

the onboard graphics is intel 855gm. Its part of the centrino package on my laptop.

---

### Post by tseliot on 2006-08-08
See if you missed something when you installed ubuntu:
```
sudo apt-get install ubuntu-desktop
```


Then reboot

---

### Post by sherpah on 2006-08-08
I checked apt for ubuntu desktop and it showed me that there are no updates and nothing missing. I want to try to go down the road of installing intel drivers - such as the ones form intels website for the I855GM onboard chip in my laptop. I also notice that freedesktop.org has drivers for the Intel onborad series - but i cannot get any of them to install. Could you give me some advice on how to install these drivers? It appears that the drivers on Intels website include a 122mb download of Xfree86 - and I do not see even an RPM file let alone an install.sh file. I am baffled and confused - why is it so difficult just to uprade video drivers? I feel like if I do upgrade them it may solve my total lack of 3d problem.

Thanks

---

### Post by Paradoxdruid on 2006-08-08
I have a Koala Mini PC from system76.com, and I'm having the exact same problem--  but I didn't always.

Direct rendering (and thus, GLX) worked on my box originally, but a semi-recent (within the last month or so) upgrade killed it--  I don't know if it was a kernel or driver update, but I can't get direct rendering to work at all now.

lsmod | grep i8  shows that i810 and drm are loaded in the kernel, my xorg.conf is nearly identical to the above (my device section now has "VideoRam  65536", an early effort to fix the problem that didn't help), and I'm running in 16-bit depth.

/var/log/Xorg.0.log  says ```
I810(0): Direct Rendering: Failed
```

Any ideas?

---

### Post by tseliot on 2006-08-09
Try with:
```
sudo apt-get install --reinstall xserver-xorg-driver-i810
```

---

### Post by Paradoxdruid on 2006-08-09
> **tseliot said:**
> Try with:
```
sudo apt-get install --reinstall xserver-xorg-driver-i810
```

I've tried this, to no avail.  But a good suggestion, nonetheless.

---

### Post by Paradoxdruid on 2006-08-09
I solved the problem, at least in my case.

Apparently, at some point I accidently installed the package nvidia-glx , which is clearly wrong for an integrated graphics solution by intel.

so, I simply:```
sudo apt-get remove nvidia-glx
sudo apt-get --reinstall install libgl1-mesa-dri
sudo apt-get --reinstall install libgl1-mesa
``` and my rendering is working just fine! 

Thanks to anyone who was trying to help.

sherpah, you might want to try the same--  I only realized my mistake when looking through my /var/log/Xorg.0.log and I noticed an NVIDIA entry, which seemed odd.

---

