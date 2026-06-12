---
title: "ATI fglrx issues with 3d acceleration"
date: 2005-10-15
forum: Multimedia &amp; Video
---

### Post by Yuri on 2005-10-15
[FONT="Times New Roman"]Hi.. I'm new to Ubuntu and Linux in general. I have been attempting to set up the fglrx drivers for my ATI 9600 Pro (AGP, 128mb) with no success. I have followed the instructions at the wiki ([https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28fglrx%29](https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28fglrx%29)) to spec, including shutting down X and reinstalling. When i run "fglrxinfo" i get the following values:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Clearly this is not what I need. I used cedega's automatic configurator and the "3d acceleration" is the only thing that fails. I have also tried uninstalling and reinstalling, as well as attempting to install linux drivers from the ATI website... to no avail ( I couldn't get the installer to work). In any case, I need some help. I assume that xorg.0.log is the file in question. I will include only the errors in the log file - I assume that is all I need. Correct me If I am wrong.[/FONT]

[FONT="Verdana"](WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

(WW) Open APM failed (/dev/apm_bios) (No such file or directory)

(WW) Ignoring request to load module GLcore

(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found

(WW) fglrx(0): Bad V_BIOS checksum

(WW) fglrx(0): Specified desktop setup not supported: 8

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

(WW) fglrx(0): Option "UseFBDev" is not used[/FONT]

[FONT="Times New Roman"]I hope this is all that is required for someone knowledgable to fix my problem. I will post the entire xorg.0.log file if necessary. Ubuntu me! Thanks.[/FONT]

---

### Post by mlomker on 2005-10-15
Try **sudo dpkg-reconfigure xserver-xorg** to create your xorg.conf file.  The results are different than fglrxconfig, and some people have had luck with one and not the other.

---

### Post by Yuri on 2005-10-15
I have used xserver-xorg reconfigure several times. it wont budge

---

### Post by mlomker on 2005-10-15
Are you one of the people whose cards come up as 'unidentified'?  There is a bug report filed on that.  Most of the posters seem to have 9550-series cards.

```

mlomker@mlomkernote:/$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```

---

### Post by Yuri on 2005-10-15
I think it comes up identified... in the xorg.conf it says radeon 9600 in the section devide identifier

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option 		"UseInternalAGPGART" "no"
EndSection

I'm also not sure about your code... I dont know what it is or how to use it

---

### Post by Yuri on 2005-10-15
oh wait.. its for mobility radeon nvm...

---

### Post by Golgoth on 2005-10-17
[QUOTE=mlomker]Are you one of the people whose cards come up as 'unidentified'?  There is a bug report filed on that.  Most of the posters seem to have 9550-series cards.

```

mlomker@mlomkernote:/$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```[/QUOTE]

I have the same card as yours:
```

golgoth@ubuntu-laptop:~$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```

and I experience big freezes which make me reboot my laptop when I surf the internet.
Games and other software are OK.
Why? I don't know.
I try firefox, epiphany, opera, it's the same.
I try without java and flash, it's the same.
I try the "fglrx made in ubuntu" and I install the latest one.

I can't restart X, I have to type: ALT+Syst+B to reboot.

```

golgoth@ubuntu-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.6)

```

Here is my xorg.conf:

```

# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

    RgbPath	"/usr/X11R6/lib/X11/rgb"


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

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

#    Option "NoTrapSignals"

#    Option "DontZap"

#    Option "Dont Zoom"

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
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc105"
    Option "XkbLayout"	"fr"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ExplorerPS/2"
    Option "Device"     "/dev/input/mice"
    Option "Buttons"	"7"
    Option "ZAxisMapping"	"6 7"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
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
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"

#    Chipset     "generic"

    Driver      "vga"

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "(null)" 
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x06419064"
    Option "GammaCorrectionII"          "0x06419064"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e50
    Screen 0
EndSection

Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

    Screen "Screen0"

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

```

I erase some comments...

Could you see if there is something wrong inside comparing to yours or give me yours so that I can do it.

Thx!

---

### Post by Golgoth on 2005-10-17
my e-mail if you want to send me your xorg.conf:

[email]gauthier.tellier@gmail.com[/email]

---

### Post by Golgoth on 2005-10-18
help!

---

### Post by mlomker on 2005-10-18
If you need to reach me then you can click on my name in one of the posts and send a PM.  I always check them but I won't read the threads here if I'm really busy.  Helping out on here is something that I do whenever I have free time.  ;) 

I'm attaching my current xorg.conf but I'd have to guess that your problem is elsewhere.  I'm not sure what to suggest, though.  You can't Ctrl-Alt-F2 to another terminal when X freezes?  That's almost always a hardware problem and not a driver issue.

---

### Post by Golgoth on 2005-10-18
I can't Ctrl-Alt-F2 or Ctrl-Alt-Backspace...

I don't know what to do...

I read all I can here and on the french forum and nothing...

:(

---

### Post by Golgoth on 2005-10-18
how could I know where to search?

is there somewhere a log file for my crash?

thanks BTW!

---

### Post by mlomker on 2005-10-18
All of the log files are in /var/log.  I'm not sure where you'd start searching.  The main log files are: messages, kern.log, and syslog.

---

### Post by Golgoth on 2005-10-18
I wanted to add that I think it's a driver problem because I had no problem with the "ati" driver... No freeze!

---

### Post by Adapted.Cat on 2005-10-18
[QUOTE=Golgoth]I wanted to add that I think it's a driver problem because I had no problem with the "ati" driver... No freeze![/QUOTE]

I'll second this! I have exactly the same problem, and have had it in various different configurations. The two common factors are Xorg and the fglrx driver.

My card is a Radeon 9100(QM) with 128Mb memory.

A while back I had fglrx working well for me, under XFree86 in MEPIS with a custom kernel.
I then switched to Xorg, where my troubles began. With a newer custom kernel, I tried the both the standard ati driver (no accel) and the latest r200. When I eventually got the r200 module to work, I had pretty slow FPS (slower than before) and corrupted images/text in most games.

Switching to the latest kernel, I tried installing the fglrx newer fglrx module. This worked in that it gave me the right driver string (as you also have) and glxinfo/fglrxinfo were convinced that everything was fine. However, glxgears gave me a couple of hundred FPS at most, and fgl_glxgears gave me 150 FPS with corrupted textures. And then there were the lock ups...

Last night, I switched to Ubuntu 5.10, and I now have the standard k7 kernel, and the standard restricted modules and fglrx packages. Running Xorg with the ati driver shows me as having direct rendering and acceleration through Mesa. While this is nice, it doesn't give me the sort of performance I'd like, and was previously able to get using XFree86.

Running with fglrx, I get various problems. Again, fgl_glxgears gives me 150 FPS. Again, the textures are corrupt (in the same way) - the rotating cube is there, but it's black or blue, with other colours fading in and the occasional shimmer of what look like gears coming out of the screen towards me. After the first couple of logins where it locked up as soon as I launched FireFox, now it locks up as soon as I try to start a terminal window.

I have tried switching on/off each of the fglrx options in xorg.conf that seem like they would do anything, and restarting gdm, but to no avail. When I turned on "no_accel" or "no_dri" the screen was corrupted, so I didn't investigate those further. Each time it locks up, I am unable to get any response from any of button (even the power button) other than reset. In /var/log/messages I just get a message saying I restarted. In /var/log/Xorg.0.log, I get NO error (EE) messages, and everything looks fine.

Now I'm fairly certain that this isn't a hardware (e.g. IRQ) problem. The same card in the same configuration has worked before under fglrx and XFree86. It also works in non-accelerated mode with the ati or radeon driver under xorg, and (to some extent) in accelerated mode using the r200 drm module.

I think it's some as yet un-worked-out incompatability between fglrx and the Xorg packages shipped with either Ubuntu or Debian-unstable.

This problem is very persistent, and reproducible across different kernels and different distros, and different versions of fglrx (8.18.6 and 8.16.??).

If anyone has any light to shed on this topic, I'd be glad to hear from you!

---

### Post by zox on 2005-10-18
Hi.
I don't have any new light to shed on the problem as I have the same behaviour like the rest of the gang.
I am running ATI 8500 with AMD64 but 32 bit breezy.
FGLRX installed and if I use "fglrx" in xorg.conf, system freezes in various stages, usually as soon as I lunch any application.
If I use "ati" in xorg.conf, all is well but no 3d :(

I wish someone has the answer for us.

I also want to point out to users that after freeze, you don't have to do hard reboot as it might screw up something else.
There is an old rule when system freezes, you can get it rebooted nicely with combination of tasters.

If you press left ALT+SysRq (key with Print Screen on my keyboard) + R, than wait couple of seconds, than repeat with ALT+SysRq+S, than repeat with same combo only changing last laetter to E, I, U, B

It is easy to remember it like this (**R**aising **S**kinny **E**lephants **I**s **U**terly **B**oring).

This way system will reboot nicely from freeze, even if it doesn't appear there is any reaction while you are pressing tasters.

---

### Post by Golgoth on 2005-10-19
try [that]("http://ubuntuforums.org/showpost.php?p=413031&postcount=10") for your ATI 8500

---

### Post by Golgoth on 2005-10-19
each time I go to this blog: [http://placelibre.ath.cx/keyes/](http://placelibre.ath.cx/keyes/)

(don't worry it's french! ;) )

and try to read the comments, I freeze! Why? I don't know!!!

on other websites, I have the same problems...

I have no problem with games and other software...
Why only with firefox???????

It's a shame because I love this ubuntu!

---

### Post by Adapted.Cat on 2005-10-19
[QUOTE=Golgoth]try [that]("http://ubuntuforums.org/showpost.php?p=413031&postcount=10") for your ATI 8500[/QUOTE]

Golgoth,

  The 'radeon' driver is the same as the default 'ati' driver - if you pick the wrong one for your card it automatically switches to the right one, so there's no difference between them. For older cards, support is better and in any case it's the best that you can do - fglrx doesn't support anything lower than the 8500. However, for those semi-new cards, it does support some acceleration but the performance is nowhere near what you'd expect - nowhere near what I've previously had with the fglrx drivers on the same card.

  I ran glxgears and fgl_glxgears last night with LIBGL_DEBUG=verbose, and got this output:
```
libGL: XF86DRIGetClientDriverName: 8.16.20 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
libGL: XF86DRIGetClientDriverName: 8.16.20 atiogl_a (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0

```

That libGL version error looks significant. I am picking up the libGL.so.1.2 from the fglrx-driver-xorg package - it's the only libGL I have. Likewise, atiogl_a_dri.so comes from this package. This is what ldd tells me about it:
```
	linux-gate.so.1 =>  (0xffffe000)
	libGL.so.1 => /usr/lib/libGL.so.1 (0xb7f02000)
	libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7e8c000)
	libglut.so.3 => /usr/lib/libglut.so.3 (0xb7e63000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e41000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d13000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c52000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c45000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c33000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c30000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7b4a000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7b3f000)
	/lib/ld-linux.so.2 (0xb7faf000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b3b000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7b37000)

```
MD5s for the relevant files are:
5bcd7d903cd866c2bfcf9fdc57a4fc89  /usr/X11R6/lib/libGL.so.1.2
9412f446ed729c5d354d1a80032b559b  /usr/X11R6/lib/modules/dri/atiogl_a_dri.so
70d5833acabf8ce85a78ce0ed5506cdb  /usr/X11R6/lib/modules/dri/fglrx_dri.so

I have managed to reduce the crashes a little. Uncommenting this improves it:
Option "KernelModuleParm" "agplock=0"
Also, going into my /lib/modules/<k_version>/kernel/drivers/char/agp and renaming the agp_*.ko to _ko_bak means that while the agpgart module is loaded none of the motherboard-specific modules are loaded. With this change, the "UseInternalAGPGART" "yes" option actually makes a difference. And it (for me) improves stability. However, I still get random lockups :(

And I've now tried the "no_accel" and "no_dri" options. Unsurprisingly, "no_dri" stops the crashes. You still have accelerated 2D graphics, but all 3D OpenGL apps will crawl. The "no_accel" doesn't make any stability improvement on that.

Many thanks to zox for the Raising Skinny Elephants trick - I'll try that! :)

---

### Post by Golgoth on 2005-10-19
[QUOTE=Adapted.Cat]
I have managed to reduce the crashes a little. Uncommenting this improves it:
Option "KernelModuleParm" "agplock=0"
[/QUOTE]

how?

[QUOTE=Adapted.Cat]
Also, going into my /lib/modules/<k_version>/kernel/drivers/char/drm and renaming the agp_*.ko to _ko_bak means that while the agpgart module is loaded none of the motherboard-specific modules are loaded. With this change, the "UseInternalAGPGART" "yes" option actually makes a difference. And it (for me) improves stability. However, I still get random lockups :(
[/QUOTE]

what did you exactly do? I have no agp_*.ko files... just:
drm.ko, fglrx.ko, i810.ko, i830.ko, i915.ko, mga.ko, r128.ko, radeon.ko, sis.ko, tdfx.ko

---

### Post by Adapted.Cat on 2005-10-19
[QUOTE=Golgoth]how?[/QUOTE]
I think that change allowed me to get as far as running glxinfo without a crash. It was still pretty flaky.

[QUOTE=Golgoth]what did you exactly do? I have no agp_*.ko files... just:
drm.ko, fglrx.ko, i810.ko, i830.ko, i915.ko, mga.ko, r128.ko, radeon.ko, sis.ko, tdfx.ko[/QUOTE]

Sorry - I gave you the wrong path - it should have said:
/lib/modules/<k_version>/kernel/drivers/char/agp
Leave agpgart.ko alone. There'll be one agp_*.ko for your motherboard type (try "lsmod | grep agp" to find out which, or rename them all) and you just move it out of the way so that it isn't automatically loaded when agpgart is. Then the fglrx module is free to do its stuff.

Since my last post, I've downloaded the RPMs from ATI, unpacked them, and tried to use the files from those (still keeping a copy of the fglrx-driver-xorg files). 8.18.6 gives the same error as 8.16.20, and 8.14.13 and earlier don't compile, due to a deprecated API - when I tried to patch it I ended up getting a black screen of death.

I don't see why it would be complaining of a version mis-match between atiogl_a_drv.so and libGL.so.1.2 - I'm going to look for version strings in each and see if I can find anything. There must be something else going on here.

---

### Post by mlomker on 2005-10-19
> Then the fglrx module is free to do its stuff.


I don't have this problem but I was curious and tested the renaming process to see what would happen.  Renaming the motherboard-specific piece doesn't seem to hurt anything (3D still works) but **dmesg | grep fglrx** clearly shows that the kernel's gart is still being used.  I'm pretty certain that the only way to disable the internal gart is to recompile the kernel without the option.

I tried renaming the agpgart.ko as well and it just disables 3D altogether due to missing symbols.

Your fix may be unique to your machine.

---

### Post by Adapted.Cat on 2005-10-19
[QUOTE=mlomker]**dmesg | grep fglrx** clearly shows that the kernel's gart is still being used. [/QUOTE]

Yes, that's fine. agpgart is just a wrapper. The real meat is in agp_via, agp_ati, agp_sis or whatever. The fglrx module contains code to interface directly to agpgart, or to agpgart via agp_<type>. If agp_<type> is loaded before fglrx, you can't use the UseInternalAGPGART option for fglrx.

At least, that's my guess at what's going on - I'm no expert on kernel modules. In any case, it improves stability for me. Not much, mind. I still can't run FireFox without it locking up on me :(

So, when you run **LIBGL_DEBUG=verbose glxgears**, do you get any messages about a version mismatch? Could you post the output you get, if any, and also the output from **ldd /usr/bin/glxgears**? Thanks.

I found the place where that error message is generated, and tweaked it to ignore the version mismatch. It happily did so, without complaining about glapi falling back, but there was no improvement in performance or stability. Back to square one, I suppose :(

---

### Post by Golgoth on 2005-10-19
golgoth@ubuntu-laptop:~$ LIBGL_DEBUG=verbose glxgears
libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
Can't open configuration file /etc/drirc: No such file or directory.
Can't open configuration file /home/golgoth/.drirc: No such file or directory.
12589 frames in 5.0 seconds = 2517.632 FPS

golgoth@ubuntu-laptop:~$ ldd /usr/bin/glxgears
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7f1d000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7ea7000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0xb7e7d000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e5b000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d2d000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c6d000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c60000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c4e000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c4a000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7b64000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7b59000)
        /lib/ld-linux.so.2 (0xb7fcb000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b56000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7b52000)


I don't understand the problem with agp...

Should I put agpgart and intel-agp in /etc/modules and use "UseInternalAGPGART" "no" or put only fglrx in /etc/module and use "UseInternalAGPGART" "yes" ??

Is it something else?

My main question is: why only with firefox and not with games???
Games are supposed to use more 3D than firefox??

---

### Post by Golgoth on 2005-10-19
[QUOTE=Adapted.Cat]Yes, that's fine. agpgart is just a wrapper. The real meat is in agp_via, agp_ati, agp_sis or whatever. The fglrx module contains code to interface directly to agpgart, or to agpgart via agp_<type>. If agp_<type> is loaded before fglrx, you can't use the UseInternalAGPGART option for fglrx.
[/QUOTE]

I tried and it doesn't change anything... :(

---

### Post by Golgoth on 2005-10-19
It has changed something anyway when removing /lib/modules/<k_version>/kernel/drivers/char/agp/intel-agp.ko

I saw the changes in my var/log/kern.log :

```

Oct 19 18:42:41 localhost kernel: [4298978.560000] [fglrx] module loaded - fglrx 8.18.6 [Oct 11 2005] on minor 0
Oct 19 18:43:01 localhost kernel: [4298998.427000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Oct 19 18:43:01 localhost kernel: [4298998.427000] [fglrx] Have to use kernel AGP support to avoid conflicts.
Oct 19 18:43:01 localhost kernel: [4298998.427000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
Oct 19 18:43:01 localhost kernel: [4298998.427000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
Oct 19 18:43:01 localhost kernel: [4298998.428000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct 19 18:43:01 localhost kernel: [4298998.428000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct 19 18:43:01 localhost kernel: [4298998.428000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Oct 19 18:43:01 localhost kernel: [4298998.428000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
Oct 19 18:43:01 localhost kernel: [4298998.438000] [fglrx] free  AGP = 256126976
Oct 19 18:43:01 localhost kernel: [4298998.438000] [fglrx] max   AGP = 256126976
Oct 19 18:43:01 localhost kernel: [4298998.438000] [fglrx] free  LFB = 122679296
Oct 19 18:43:01 localhost kernel: [4298998.438000] [fglrx] max   LFB = 122679296
Oct 19 18:43:01 localhost kernel: [4298998.438000] [fglrx] free  Inv = 0
Oct 19 18:43:01 localhost kernel: [4298998.438000] [fglrx] max   Inv = 0
Oct 19 18:43:01 localhost kernel: [4298998.438000] [fglrx] total Inv = 0
Oct 19 18:43:01 localhost kernel: [4298998.438000] [fglrx] total TIM = 0
Oct 19 18:43:01 localhost kernel: [4298998.438000] [fglrx] total FB  = 0
Oct 19 18:43:01 localhost kernel: [4298998.438000] [fglrx] total AGP = 65536


Oct 19 19:24:00 localhost kernel: [4294721.312000] Fire GL built-in AGP-support
Oct 19 19:24:00 localhost kernel: [4294721.312000] Based on agpgart interface v0.99 (c) Jeff Hartmann
Oct 19 19:24:00 localhost kernel: [4294721.312000] agpgart: Maximum main memory to use for agp memory: 439M
Oct 19 19:24:00 localhost kernel: [4294721.312000] agpgart: Detected an Intel 845G Chipset, no integrated grapics found.
Oct 19 19:24:00 localhost kernel: [4294721.312000] agpgart: Detected Intel i845 G/GL/GV/GE/PE chipset
Oct 19 19:24:00 localhost kernel: [4294721.315000] agpgart: AGP aperture is 256M @ 0xc0000000
Oct 19 19:24:00 localhost kernel: [4294721.315000] Power management callback for AGP chipset installed
Oct 19 19:24:00 localhost kernel: [4294721.315000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
Oct 19 19:24:00 localhost kernel: [4294721.316000] AGP: Found 2 AGPv2 devices
Oct 19 19:24:00 localhost kernel: [4294721.316000] AGP: Doing enable for AGPv2
Oct 19 19:24:00 localhost kernel: [4294721.316000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
Oct 19 19:24:00 localhost kernel: [4294721.325000] [fglrx] free  AGP = 256126976
Oct 19 19:24:00 localhost kernel: [4294721.325000] [fglrx] max   AGP = 256126976
Oct 19 19:24:00 localhost kernel: [4294721.325000] [fglrx] free  LFB = 122679296
Oct 19 19:24:00 localhost kernel: [4294721.325000] [fglrx] max   LFB = 122679296
Oct 19 19:24:00 localhost kernel: [4294721.325000] [fglrx] free  Inv = 0
Oct 19 19:24:00 localhost kernel: [4294721.325000] [fglrx] max   Inv = 0
Oct 19 19:24:00 localhost kernel: [4294721.325000] [fglrx] total Inv = 0
Oct 19 19:24:00 localhost kernel: [4294721.325000] [fglrx] total TIM = 0
Oct 19 19:24:00 localhost kernel: [4294721.325000] [fglrx] total FB  = 0
Oct 19 19:24:00 localhost kernel: [4294721.325000] [fglrx] total AGP = 65536

```

BTW I have some warnings in my Xorg.0.log:

(WW) The directory "/usr/share/X11/fonts/local/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Speedo/" does not exist.
	Entry deleted from font path.
.
.
.
.
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
.
.
.
.
(WW) fglrx(0): board is an unknown third party board, chipset is supported

---

### Post by Adapted.Cat on 2005-10-19
[QUOTE=Golgoth]It has changed something anyway when removing /lib/modules/<k_version>/kernel/drivers/char/agp/intel-agp.ko

I saw the changes in my var/log/kern.log :

```

Oct 19 18:42:41 localhost kernel: [4298978.560000] [fglrx] module loaded - fglrx 8.18.6 [Oct 11 2005] on minor 0
Oct 19 18:43:01 localhost kernel: [4298998.427000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Oct 19 18:43:01 localhost kernel: [4298998.427000] [fglrx] Have to use kernel AGP support to avoid conflicts.
Oct 19 18:43:01 localhost kernel: [4298998.427000] [fglrx] Kernel AGP support doesn't provide agplock functionality.

```
[/QUOTE]
Okay, that's what I'd expect. Now if you set "UseInternalAGPGART" "yes" and fire up Xorg, you'll be using the all-ATI driver. Whether that improves things for any particular machine seems to be somewhat of a lottery. I haven't seen a consistent message either way when searching forums.

[QUOTE=Golgoth]
BTW I have some warnings in my Xorg.0.log:

(WW) The directory "/usr/share/X11/fonts/local/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Speedo/" does not exist.
	Entry deleted from font path.
.
.
.
.
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
.
.
.
.
(WW) fglrx(0): board is an unknown third party board, chipset is supported[/QUOTE]

Okay, the first of those are just fonts you probably don't have installed. If you don't like the messages, you can always comment out those FontPath lines in xorg.conf

The second is likewise harmless. There are 2 competing power management modules - APM and ACPI. You either have one or the other loaded, and I think ACPI is more common nowadays and overrides APM, but I'm not sure. X just likes to see if it needs to send specific calls to blank the screen when you're away for a long time.

The third - I get that too. I don't know if it's talking about the motherboard or the AGP card, but it seems to recognise the graphics card well enough...:???:

Thanks for posting your glxgears output. I'll try switching to 8.18.6 again and compare my output to yours. Your FPS is way higher than mine, though, so as long as you can fix the stability problems you should be fine.

---

### Post by mlomker on 2005-10-19
> So, when you run **LIBGL_DEBUG=verbose glxgears**, do you get any messages about a version mismatch? Could you post the output you get, if any, and also the output from **ldd /usr/bin/glxgears**?

```

mlomker@mlomkernote:/$ LIBGL_DEBUG=verbose glxgears
libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
Can't open configuration file /etc/drirc: No such file or directory.
Can't open configuration file /home/mlomker/.drirc: No such file or directory.
10689 frames in 5.0 seconds = 2137.758 FPS
11790 frames in 5.0 seconds = 2357.868 FPS

```

and 

```

mlomker@mlomkernote:/$ ldd /usr/bin/glxgears
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0x4c36e000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0x4c4ac000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0x4ae32000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x4acfb000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x4abc6000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x4ad4e000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x4ae16000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x4ad35000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x4acf6000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x4aea8000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x4ae25000)
        /lib/ld-linux.so.2 (0x4abae000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x4ad49000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x4ae10000)

```

I have the 8.18.6 driver using [these instructions]("http://ubuntuforums.org/showthread.php?p=423589#post423589").

---

### Post by Adapted.Cat on 2005-10-19
[QUOTE=mlomker]```

I have the 8.18.6 driver using [these instructions]("http://ubuntuforums.org/showthread.php?p=423589#post423589").[/QUOTE]

Alright - thanks for that! I followed those instructions to the letter, and it has helped. It's much more stable than before. I can now login to ubuntuforums and post without the machine locking up on me :KS

Here is the current output from glxgears:
[CODE]libGL: XF86DRIGetClientDriverName: 8.18.6 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
libGL: XF86DRIGetClientDriverName: 8.18.6 atiogl_a (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
6454 frames in 5.0 seconds = 1290.648 FPS
6420 frames in 5.0 seconds = 1283.991 FPS
6421 frames in 5.0 seconds = 1284.197 FPS
6417 frames in 5.0 seconds = 1283.231 FPS
1485 frames in 5.0 seconds = 296.328 FPS (maximized window)
386 frames in 5.0 seconds = 77.061 FPS
386 frames in 5.0 seconds = 77.056 FPS
313 frames in 5.4 seconds = 57.448 FPS (maximized, with terminal in front)
291 frames in 5.0 seconds = 58.162 FPS
267 frames in 5.0 seconds = 53.363 FPS
267 frames in 5.0 seconds = 53.361 FPS
267 frames in 5.0 seconds = 53.357 FPS

```
I thought with DRI the FPS from glxgears wasn't supposed to drop so much when you maximized the window...

Strangely, the output from fgl_glxgears hasn't changed a bit:
```
Using GLX_SGIX_pbuffer
libGL: XF86DRIGetClientDriverName: 8.18.6 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
libGL: XF86DRIGetClientDriverName: 8.18.6 atiogl_a (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
753 frames in 5.0 seconds = 150.600 FPS
824 frames in 5.0 seconds = 164.800 FPS
901 frames in 5.0 seconds = 180.200 FPS
918 frames in 5.0 seconds = 183.600 FPS
407 frames in 5.0 seconds = 81.400 FPS  (maximized window)
245 frames in 5.0 seconds = 49.000 FPS
244 frames in 5.0 seconds = 48.800 FPS

```
I'm still getting some strange corruption in the rotating cube, as I described earlier. Perhaps it is specific to my machine - I haven't seen any descriptions elsewhere that match it.

Well, I'm going to go try a few games, and see how they are, and then come back and edit this post with the results.

Well, I've tried a bunch of games, and I've been webbrowsing, even to that Keyes site Golgoth mentioned, and I haven't had a single crash :)
Most things seem to be running at a fairly good pace. The ones that aren't...I'm hoping it's just the computational load of updating lots of particles on a 1600x1200 screen. Unless it starts dying on me again, I think I'm done here.

Thanks for the detailed instructions mlomker!

---

### Post by Golgoth on 2005-10-19
I'm alone!

... cries ... :(

---

### Post by allupinya on 2005-10-19
Just like to mention..this thread got me 2 machines up and running the new ati driver in 10 minutes

[http://ubuntuforums.org/showthread.php?t=75428](http://ubuntuforums.org/showthread.php?t=75428)

Just follow them and all is good

At the bottom where he mentions changing from ati to fglrx:  That is the first screen in fglrxconfig. Change that from ati down the list to fglrx, and install..I used frame buffering is "yes" loaded all the display options and simple monitor setup 21"  for both ati loaded machines.
After playing around for days trying to get it to work, i was almost emmbarassed at how easy it was..

So easy in fact i did it 3 times on each machine to make sure.."LOL"

---

### Post by Golgoth on 2005-10-19
[QUOTE=allupinya]Just like to mention..this thread got me 2 machines up and running the new ati driver in 10 minutes

[http://ubuntuforums.org/showthread.php?t=75428](http://ubuntuforums.org/showthread.php?t=75428)

Just follow them and all is good

At the bottom where he mentions changing from ati to fglrx:  That is the first screen in fglrxconfig. Change that from ati down the list to fglrx, and install..I used frame buffering is "yes" loaded all the display options and simple monitor setup 21"  for both ati loaded machines.
After playing around for days trying to get it to work, i was almost emmbarassed at how easy it was..

So easy in fact i did it 3 times on each machine to make sure.."LOL"[/QUOTE]

I reinstall my system and fglrx...
The installation is ok but it's still freezing on some websites...

I watched tonight one episode of the second season of "the 4400" in english (we don't have it yet in France on TV) and one person in the show said "brain freeze".
I thought I'll get crazy and throw my laptop away out of the window!

I think I become mad! :confused:

---

### Post by allupinya on 2005-10-20
i understand your pain...
Even with the easy-install of the ATI drivers
Last nite late i was playing a game called "mafia"...Was in a really good part of the game and doing well...My keyboard and mouse just dropped out of site, completely:eek: ..
So i am also leaning to the fact that there may be some things to work out with the version of fgrlx that ubuntu is using from the latest deb.
I also run mandriva on another drive,and i use it for reference for this install..
The Mandriva uses 6.9 unstable version as of yet and am working on the 3-d drivers for that to work..No luck as of yet:rolleyes: ..I think as time goes on we will see improvment about 3 weeks or so down the road as more folks play with  them..
guess we will wait and see.

---

### Post by Golgoth on 2005-10-20
I had the same freezes with hoary and breezy with the "made in ubuntu" fglrx but not that often with hoary...

I just hope it's a problem with the driver and not my laptop...

---

### Post by alanrr_sr on 2005-12-12
My ubuntu box was freezing, than I just removed VideoRam parameter from xorg.conf and it worked perfectly now....

---

### Post by sonicpling on 2005-12-17
this is going to be pretty incoherent, but I'm still working on the problem, and am too lazy to try and make it cohesive.

I've been struggling with getting the fglrx drivers up and running on dapper.

when I would run ```
fglrxinfo
``` it would still say that mesa was providing the acceleration (or lack thereof), even though my xorg logs didn't report any errors loading fglrx and neither did the kern log.

running ```
LIBGL_DEBUG=verbose glxgears
``` tells me that it's looking for /usr/X11R6/lib/modules/dri/atiogl_a_dri.so (which doesn't exist...)

so:
```
sudo mkdir /usr/X11R6/lib/modules/dri/
ln -s /usr/lib/dri/atiogl_a_dri.so /usr/X11R6/lib/modules/dri/atiogl_a_dri.so
``` 

now it's working, but I still get this message:

```
libGL: XF86DRIGetClientDriverName: 8.20.8 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
libGL: XF86DRIGetClientDriverName: 8.20.8 atiogl_a (screen 0)
```

if it make anymore progress I'll be back...

Keywords: fglrx mesa dapper ati 9250 dri glx

---

