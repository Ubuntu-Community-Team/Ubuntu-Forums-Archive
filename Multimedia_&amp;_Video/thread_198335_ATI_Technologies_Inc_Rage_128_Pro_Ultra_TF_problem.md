---
title: "ATI Technologies Inc Rage 128 Pro Ultra TF problem"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by weijie90 on 2006-06-17
Hi,
this problem has been with me since breezy. games like chromium run slowly, and google earth says "rage 128 timed out".

i suspect that i dont have 3d aceleration.

please help, thanks!

---

### Post by x64Jimbo on 2006-06-17
Have you tried installing the drivers? There's a good tutorial in the wiki about getting ATI drivers installed.
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29](https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29)

---

### Post by weijie90 on 2006-06-17
> Prerequisites

Make sure the following things are true about your video card:

    *

      It is a 'Radeon' card
    *

      The model of the card is in the 9xxx series, 9500 or higher, or it is in the X series (e.g. X300), or it has TV-Out capability. The 'fglrx' driver does not support cards earlier than the 8500.



it is not a radeon card, nor is it a 95xx series card. :(

---

### Post by patrick295767 on 2006-06-17
[QUOTE=weijie90]Hi,
this problem has been with me since breezy. games like chromium run slowly, and google earth says "rage 128 timed out".

i suspect that i dont have 3d aceleration.

please help, thanks![/QUOTE]

what's ur model ??
 
type : lspci | grep ati
  
mine gives: 
```
$ lspci | grep ati
0000:00:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
0000:00:06.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP
```

---

### Post by weijie90 on 2006-06-17
```
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:08.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:02:08.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:02:08.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:02:08.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
di@di-desktop:~$

```

---

### Post by raduc on 2006-06-19
[QUOTE=weijie90]Hi,
this problem has been with me since breezy. games like chromium run slowly, and google earth says "rage 128 timed out".

i suspect that i dont have 3d aceleration.

please help, thanks![/QUOTE]

I have the same problem with an ATI Rage Fury Pro (128).

---

### Post by weijie90 on 2006-06-19
Yup.

---

### Post by patrick295767 on 2006-06-20
if ```
glxgears 
```is slow
the ati video is not installed correctly.
  
fglrxinfo
I have troubles with a bi proc ati card too, that is not very common & was damn damn expensive !

:-(

---

### Post by weijie90 on 2006-06-20
[QUOTE=patrick295767]if ```
glxgears 
```is slow
the ati video is not installed correctly.
  
fglrxinfo
I have troubles with a bi proc ati card too, that is not very common & was damn damn expensive !

:-([/QUOTE]

glxgearsdi@di-desktop:~$ glxgears

glxgears runs OK. 

di@di-desktop:~$ fglrxinfo
bash: fglrxinfo: command not found
di@di-desktop:~$

does the problem lie in the agp mode that agpgart sets?

---

### Post by patrick295767 on 2006-06-21
[QUOTE=weijie90]glxgearsdi@di-desktop:~$ glxgears

glxgears runs OK. 

di@di-desktop:~$ fglrxinfo
bash: fglrxinfo: command not found
di@di-desktop:~$

does the problem lie in the agp mode that agpgart sets?[/QUOTE]
  
[http://www.ubuntuforums.org/showthread.php?t=200760&highlight=ati](http://www.ubuntuforums.org/showthread.php?t=200760&highlight=ati)
You get Mesa too ?
  
_These links can help you:_
         [http://ubuntuforums.org/showthread.php?t=143283&highlight=fixing+mesa+issue](http://ubuntuforums.org/showthread.php?t=143283&highlight=fixing+mesa+issue)
  
           Tutorial: [http://ubuntuforums.org/showthread.php?t=143283&highlight=fixing+mesa+issue](http://ubuntuforums.org/showthread.php?t=143283&highlight=fixing+mesa+issue) 
  
              [http://doc.ubuntu-fr.org/materiel/ati](http://doc.ubuntu-fr.org/materiel/ati)
              [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by weijie90 on 2006-06-22
```
di@di-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


```

Using "fglrx" in xorg.conf after using [http://ubuntuforums.org/showthread.php?t=143283&highlight=fixing+mesa+issue]("http://ubuntuforums.org/showthread.php?t=143283&highlight=fixing+mesa+issue")

does not work- X wont start.

thanks

---

### Post by patrick295767 on 2006-06-23
Good news: 
  
there is some improvements with our great ati not recognized by breezy / dapper for fglrx !
  
Soo, chekc the /etc/modules  so that when u boot / reboot ur machines, these modules are present:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
fglrx
r128
agppart

```
  
Then, do : 
```
dpkg-reconfigure xserver-xorg
```
select the ati one
    
then, 
vi /etc/X11/xorg.conf
and instead the ati driver, I choosed : 
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"r128"
#	Driver		"fglrx"
	BusID		"PCI:1:0:0"
[COLOR="Red"][B]	Option "UseInternalAGPGART" "yes"
        Option "VideoOverlay" "off"
        Option "OpenGLOverlay" "off"[/B][/COLOR]
EndSection
```
(in red above corresponds to the lines that I added & giving better results )

fglrxinfo gives still MESA 
  
**but glrxgears works visibly better :KS**
the glxgears gives 5 seconds of super fast then 5sec of slow glxgear_turning, then 5sec fast, ... and so on
there is improvements !!! :-)
before it was slow all the time
  
[B]IS there someone that can tell us why it is beettter ? 
and how we can get this fglrx working finally under dapper or breezy ?[/B]
  
Thank you !
  
==
no X with fglrx in driver
error libgl 0 ... sthg
====
or we could  try to install  xorg-aiglx + compiz (packages)  [http://ubuntuforums.org/showthread.php?t=145068](http://ubuntuforums.org/showthread.php?t=145068)   , no ??

---

### Post by weijie90 on 2006-06-23
Hi,
cat /etc/modules shows: 

lp
psmouse


what should i do?

---

### Post by patrick295767 on 2006-06-24
[QUOTE=weijie90]Hi,
cat /etc/modules shows: 

lp
psmouse


what should i do?[/QUOTE]
  
I tried this :
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
agppart
fglrx
r128

```
  
agppart should be before 
fglrx makes no senses 'cos not working for old ati video cards
 
for ati old video cards, the only way is to enable : 
glx rendering
visible by yes or no : 
 went typing : 
```
glxinfo 
```
(because fglrx wont work for us)
  
References: [http://doc.ubuntu-fr.org/materiel/ati](http://doc.ubuntu-fr.org/materiel/ati)

---

### Post by weijie90 on 2006-07-13
sorry, it still doesnt work :(

is it because dmesg says:

```
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode

```
?](*,)

---

### Post by patrick295767 on 2006-07-13
> **weijie90 said:**
> sorry, it still doesnt work :(

is it because dmesg says:

```
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode

```
?](*,)

would you think we should warn the programing team to check make the following release of Ubuntu with better rage ati support ?
 
In this forum, in bugs maybe ... :-k :-k µ

what would u think ?

---

### Post by weijie90 on 2006-07-15
hmm... even debian faces this problem... no hardware acceleration.

---

### Post by patrick295767 on 2006-07-16
> **weijie90 said:**
> hmm... even debian faces this problem... no hardware acceleration.

fglrx will not work
  
the glxinfo should be work out ... :-k :-k ](*,) 
Pitty because they were not too bad video cards

---

### Post by patrick295767 on 2006-07-18
> **weijie90 said:**
> hmm... even debian faces this problem... no hardware acceleration.

> **weijie90 said:**
> hmm... even debian faces this problem... no hardware acceleration.

  
I read in fedora core 5 , that there is too the problem
 
but one single person made it work !!! :-) So, that's interesting

With Fedora Core 3, it's working our video card !
  
Xorg sucks for our ati card
Xfree works for our ati cards !! 

 What would  you think to do ? ;)
  Downgrading to xfree?

---

### Post by weijie90 on 2006-07-21
how to downgrade?

---

### Post by patrick295767 on 2006-07-21
> **weijie90 said:**
> how to downgrade?

there is for xfree ways previous ubuntu version
or fedora core 3

or maybe ubuntu dapper if we find way to get xfree instead of xorg working

dont know yet... I have to go now... 
Let's keep in contact weijie90 !

Greetings to you !

---

### Post by weijie90 on 2006-07-21
actually, im on debian now, changed over recently. 
I'll research on this :)

---

### Post by patrick295767 on 2006-07-22
> **weijie90 said:**
> actually, im on debian now, changed over recently. 
I'll research on this :)

Ahh debian ! :-)
  
I recently installed fedora core 5.
I didnt keep it long.
  
In fedora core 5, I experienced damn not enough in their repositories. Life is so great with Ubuntu.
  
And ur impressions of debian ?
  
(i read, lastly, with fc3, one guy had the tuner, & even the tv out with our card !!  :-)  )
 Warty = Xfree 4.3.0
Hoary = xorg 6.8.1

---

### Post by patrick295767 on 2006-07-22
Oh oh :-) 
[http://www.xfree86.org/4.3.0/r128.html](http://www.xfree86.org/4.3.0/r128.html)

---

### Post by patrick295767 on 2006-07-22
Soo, I am posting now from XFree86 instead of xorg 

lets see if its better for our video card

==
the version I installed is:
```
:/usr/X11R6/bin# ./XFree86 -version

XFree86 Version 4.6.0
Release Date: 10 May 2006
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.4.24 i686 [ELF]
Current Operating System: Linux tower05 2.6.12-10-386 #1 Tue Jul 18 22:08:27 UTC 2006 i686
Build Date: 8 May 2006
Changelog Date: 10 May 2006
        Before reporting problems, check http://www.XFree86.Org/
        to make sure that you have the latest version.
Module Loader present
Command line: ./XFree86 -version

```

---

### Post by patrick295767 on 2006-07-22
it s working fine for the moment with xfree86 instead of xorg, for our old card 

[http://lists.debian.org/debian-user/2001/04/msg00090.html](http://lists.debian.org/debian-user/2001/04/msg00090.html)
how to conf the XFfree86 ...

---

### Post by patrick295767 on 2006-07-22
[B]
Whaoo !! Everythg works !!

glxgears works !!
ppracer works !!

  [/B]
Please find below my /etc/X11/XF86Config:
(a bit messy (I have to make it clean & ordered)) 
```
# File generated by xf86config.

#
# Copyright (c) 1999 by The XFree86 Project, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE XFREE86 PROJECT BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of the XFree86 Project shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from the
# XFree86 Project.
#

# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "speedo"
    Load        "freetype"
#    Load        "xtt"

# This loads the GLX module
    Load       "glx"
# This loads the DRI module
    Load       "dri"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/TrueType/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/freefont/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"
        ModulePath      "/usr/X11R6/lib/modules-dri"
        ModulePath      "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><Fn> VT switch sequence
# (where n is 1 through 12).  This allows clients to receive these key
# events.

#    Option "DontVTSwitch"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

   Identifier	"Keyboard1"
    Driver	"Keyboard"
#	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"

# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option     "Protocol"      "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option	"Xleds"      "1 2 3"

   Option "LeftAlt"     "Meta"
#    Option "RightAlt"    "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"    "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"    "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"   "de"
# or:
#    Option "XkbLayout"   "de"
#    Option "XkbVariant"  "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions"  "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"    "xfree86"
#    Option "XkbModel"    "pc101"
#    Option "XkbLayout"   "us"
#    Option "XkbVariant"  ""
#    Option "XkbOptions"  ""

#    Option "XkbDisable"

#     Option "XkbRules"	"xfree86"
#     Option "XkbModel"	"pc101"
#     Option "XkbLayout"	"fr"
#     Option "XkbVariant"	"fr"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver	"mouse"
    Option "Protocol"    "IMPS/2"
    Option "Device"      "/dev/mouse"

	Option		"CorePointer"
	#Option		"Device"		"/dev/input/mice"
	#Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"

# Mouse-speed setting for PS/2 mouse.

#    Option "Resolution"	"256"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"	"Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"	"9600"
#    Option "SampleRate"	"150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the XF86Config man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"        "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"        "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"        "/dev/ttyS0"
#    Option     "MinX"          "1412"
#    Option     "MaxX"          "15184"
#    Option     "MinY"          "15372"
#    Option     "MaxY"          "1230"
#    Option     "ScreenNumber"  "0"
#    Option     "ReportingMode" "Scaled"
#    Option     "ButtonNumber"  "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"        "/dev/ttyS0"
#    Option     "MinX"          "231"
#    Option     "MaxX"          "3868"
#    Option     "MinY"          "3858"
#    Option     "MaxY"          "272"
#    Option     "ScreenNumber"  "0"
#    Option     "ReportingMode" "Scaled"
#    Option     "ButtonThreshold"       "17"
#    Option     "ButtonNumber"  "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"

    Identifier  "ati rage"

# HorizSync is in kHz unless units are specified.
# HorizSync may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    HorizSync   31.5 - 48.5

#    HorizSync	30-64         # multisync
#    HorizSync	31.5, 35.2    # multiple fixed sync frequencies
#    HorizSync	15-25, 30-50  # multiple ranges of sync frequencies

# VertRefresh is in Hz unless units are specified.
# VertRefresh may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    VertRefresh 50-70

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier	"Standard VGA"
    VendorName	"Unknown"
    BoardName	"Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset	"generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver     "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# intalled.

#    BusID      "PCI:0:10:0"

#    VideoRam	256

#    Clocks	25.2 28.3

EndSection

# Device configured by xf86config:

Section "Device"
    Identifier  "ati rage"
    Driver      "r128"
    #VideoRam    32768
    # Insert Clocks lines here if appropriate
EndSection


# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen 1"
    Device      "ati rage"
    Monitor     "ati rage"
    DefaultDepth 16

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Simple Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.  In this example, screen 2 is located to the
# right of screen 1.

    Screen "Screen 1"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

Section "DRI"
   Mode 0666
EndSection


```

---

### Post by weijie90 on 2006-07-22
its frustrating, and i'm feeling like giving up now.
i think i'll wait till i buy a laptop with a good graphics card instead...

anyway, should i uninstall xorg with apt and follow the instructions on the xfree website to install xfree 4.6?

---

### Post by patrick295767 on 2006-07-23
> **weijie90 said:**
> its frustrating, and i'm feeling like giving up now.
i think i'll wait till i buy a laptop with a good graphics card instead...

anyway, should i uninstall xorg with apt and follow the instructions on the xfree website to install xfree 4.6?

you shouldnt uninstall the xserver-xorg

I am really very happy that this video card works now with ubuntu;
to make it, it's not too complicate

download from the ftp of xfree86 the version you need (glib 23 for me)
run 

run the script Xinstall.sh
(default values replies gave best results)
  
 
I did then:
cp xorg.conf XFree86config-4
(brutal way ;)  )
(after good results too with xf86setup)
  
rebooted, and that's it
 
(I dont know if it's the best way to install it, but it worked)
(I messed up a bit wiht my keyboard, ... i still have this to fix)
(keyboard working in twm but not in fvwm or maybe due to gdm ...)
  
(the procedure is a bit risky if you try strange things; risk of reinstallation)
  
I can enjoy now gaming with this PC !! Very Great !!

  
Greetings

---

### Post by weijie90 on 2006-07-24
amazing! does the keyboard work in uh, gdm/fluxbox? :D

---

### Post by patrick295767 on 2006-07-24
> **weijie90 said:**
> amazing! does the keyboard work in uh, gdm/fluxbox? :D

yes yes, If I didnt play around, It would be flawlessly working !!
  
That's great !
Have you install it, xfree86, also ? glxgears works.

HOWTO
> you shouldnt uninstall the xserver-xorg

I am really very happy that this video card works now with ubuntu;
to make it, it's not too complicate

download from the ftp of xfree86 the version you need (glib 23 for me)
run 

run the script Xinstall.sh
(default values replies gave best results)


I did then:
cp xorg.conf XFree86config-4
(brutal way  )
(after good results too with xf86setup)

rebooted, and that's it

(I dont know if it's the best way to install it, but it worked)
(I messed up a bit wiht my keyboard, ... i still have this to fix)
(keyboard working in twm but not in fvwm or maybe due to gdm ...)

(the procedure is a bit risky if you try strange things; risk of reinstallation)

I can enjoy now gaming with this PC !! Very Great !!

---

### Post by weijie90 on 2006-07-26
oh oh...
1. MS fonts are gone
2. Still no hardware acceleration

trying Xfree86 -configure

---

### Post by weijie90 on 2006-07-26
success! hardware acceleration!

sadly, the fonts are still dumb.

---

### Post by weijie90 on 2006-07-29
managed to break the system installing fonts to xfree.
how do i do so correctly? thanks!

---

### Post by patrick295767 on 2006-08-01
> **weijie90 said:**
> managed to break the system installing fonts to xfree.
how do i do so correctly? thanks!

I reinstalled the xfree & the xorg
then, fixed  my keyboard idea I had, now it works
  
I also have fonts problems. I can run ppracer no prob now.
How much you get with glxgears?

Greetings !

---

### Post by patrick295767 on 2006-08-09
> **weijie90 said:**
> managed to break the system installing fonts to xfree.
how do i do so correctly? thanks!

and this ? [http://ubuntuforums.org/showthread.php?t=7200&highlight=ati+rage](http://ubuntuforums.org/showthread.php?t=7200&highlight=ati+rage)

[http://dri.freedesktop.org/](http://dri.freedesktop.org/)

 rage128-20060309-lin..> 09-Mar-2006 08:22  2.1M  
 rage128-20060310-lin..> 10-Mar-2006 08:22  2.1M  
 rage128-20060311-lin..> 11-Mar-2006 08:22  2.1M  
 rage128-20060313-lin..> 13-Mar-2006 08:24  2.1M  
 rage128-20060315-lin..> 15-Mar-2006 11:10  2.1M  
 rage128-20060316-lin..> 16-Mar-2006 08:24  2.1M  
 rage128-20060317-lin..> 17-Mar-2006 08:25  2.1M  
 rage128-20060318-lin..> 18-Mar-2006 08:24  2.1M  
 rage128-20060319-lin..> 19-Mar-2006 08:24  2.1M  
 rage128-20060320-lin..> 20-Mar-2006 08:24  2.1M  
 rage128-20060321-lin..> 21-Mar-2006 08:25  2.1M  
 rage128-20060322-lin..> 22-Mar-2006 08:30  2.1M  
 rage128-20060323-lin..> 23-Mar-2006 08:31  2.1M  
 rage128-20060324-lin..> 24-Mar-2006 08:32  2.1M  
 rage128-20060325-lin..> 25-Mar-2006 08:31  2.1M  
 rage128-20060328-lin..> 28-Mar-2006 08:25  2.1M  
 rage128-20060329-lin..> 29-Mar-2006 08:25  2.1M  
 rage128-20060330-lin..> 30-Mar-2006

---

### Post by patrick295767 on 2006-08-14
And this ??
  
xserver-xorg-driver-ati (1:6.6.0-0ubuntu1) [Download]
[http://ubuntu.compiz.net/pool/aiglx/x/xserver-xorg-driver-ati/xserver-xorg-driver-ati_6.6.0-0ubuntu1_i386.deb](http://ubuntu.compiz.net/pool/aiglx/x/xserver-xorg-driver-ati/xserver-xorg-driver-ati_6.6.0-0ubuntu1_i386.deb)
X.Org X server -- ATI display driver
This driver for the X.Org X server (see xserver-xorg for a further description)
provides support for the ATI Mach, Rage, Radeon, and FireGL series. It
provides the 'atimisc', 'r128' and 'radeon' sub-drivers.
.
Note that this is not the same as the ATI-provided, binary-only, 'fglrx'
driver, which provides additional 3D functionality for some newer Radeon
cards, but is not supported.
.
This driver provides support for Mach, Rage, Rage128, Radeon, and most
FireGL series ATI cards.
.
More information about X.Org can be found at:
[http://xorg.freedesktop.org](http://xorg.freedesktop.org)
[http://lists.freedesktop.org/mailman/listinfo/xorg](http://lists.freedesktop.org/mailman/listinfo/xorg)
.
This module can be found as the module 'driver/xf86-video-ati' at
:pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg

---

### Post by patrick295767 on 2006-08-16
I needed composite & this wasnt possible with xfree


I switched to xorg. 
I did first : cp -a /usr/X11R6   /usr/X11R6.backup
then reinstalled xorg
I have now glxgears & xcompmgr composite working with xorg.
  
This is my xorg.conf:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"r128"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection



Section "Extensions"
	Option "Composite" "Enable"
EndSection



```
  
Sometimes, I have some frame buffer prb ;  glxgears & ppracer works fine.

---

### Post by weijie90 on 2006-08-25
Thanks, i'll try them soon ;)

---

### Post by weijie90 on 2006-08-30
are you sure that reinstalling xserver-xorg after installing xfree will work in solving the fonts problems?
thanks!

---

### Post by helpdeskdan on 2006-11-25
Anybody dared this with Edgy?  Would it improve mplayer performance?  (I'm guessing not - just opengl)

---

### Post by burek on 2006-11-26
> **helpdeskdan said:**
> Anybody dared this with Edgy?  Would it improve mplayer performance?  (I'm guessing not - just opengl)

Working  with EDGY  !!

rage 128 all in wonder
glxgears works great as in dapper but but not in breezy neither hoary

please find my config xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 RF/SG AGP"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 RF/SG AGP"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

