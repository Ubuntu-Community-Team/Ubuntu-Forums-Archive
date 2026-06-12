---
title: "Help Fixing overscan on HDTV"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by NJHokie on 2007-02-18
First of all, excellent site!

Well, I really didn't want to bug anyone for help but my efforts have been futile...

I'm a n00b in the linux world but i'm trying my hand out at building a MythTV box using ubuntu.  I love the operating system so far and have gotten pretty much everything to work right on my computer monitor, but when i connect to my Sony HDTV i have overscan issues.  I have tried the custom modeline generators out there, and advice from pretty much every post and google result about this topic to no avail.  The only way that it has worked correctly was by utilizing the nvidia-settings utility and checking the "centered" box under flat panel properties.  That did not stick however and everytime i restarted i had to run nvidia-settings again to make it scale correctly.  Trying to switch over to the MythTV end did not retain those settings either.  I want a permanent solution that a correct custom xorg.conf file should produce.

nvidia-settings reports my native resolution to be 1280x720 (which is what i'm using right now, without a modeline for it).  My HDTV is a SONY KP-46WT520, 1080i.  The BIOS splash screen and ubuntu load screens do not show at all on boot up.  TV displays only when the nvidia logo comes up and then the ubuntu login screen.  

here is my current xorg.conf:

Section "Monitor"
    Identifier     "SONY TV"
    HorizSync       15.0 - 46.0
    VertRefresh     59.0 - 61.0
    Option         "DPMS"
    Option	   "IgnoreEDID"
    #DisplaySize	   720 405
    #ModeLine "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine "1216x648@60" 74.48 1216 1272 1400 1664 684 685 688 746 -hsync +vsync
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
    Monitor        "SONY TV"
    Option         "FlatPanelProperties" "scaling = centered"
    DefaultDepth    24
    SubSection     "Display"
        Depth       16
        Modes      "1280x720" "1216x684" "1024x768" "800x600" "720x480" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x720" "1216x684" "1024x768" "800x600" "720x480" "640x480"
    EndSubSection
EndSection
 
Thanks so much for looking!

---

### Post by david_2001 on 2007-02-18
Quick point: In order to be recognised, custom modelines defined in the Monitor section of xorg.conf must be referenced from the Screen section ("man xorg.conf" for more information).  The highlighted changes should make the "1216x648@60" modeline available and the default at both defined Display colour depths:

```
Section "Monitor"
Identifier "SONY TV"
HorizSync 15.0 - 46.0
VertRefresh 59.0 - 61.0
Option "DPMS"
Option "IgnoreEDID"
#DisplaySize 720 405
#ModeLine "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
ModeLine "1216x648@60" 74.48 1216 1272 1400 1664 684 685 688 746 -hsync +vsync
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
Driver "nvidia"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
Monitor "SONY TV"
Option "FlatPanelProperties" "scaling = centered"
DefaultDepth 24
SubSection "Display"
Depth 16
Modes **"1216x648@60"**
EndSubSection
SubSection "Display"
Depth 24
Modes **"1216x648@60"**
EndSubSection
EndSection
```

(Add back any other desired alternative screen resolutions to the Display subsections after "1216x648@60".)

---

### Post by NJHokie on 2007-02-18
ahh, great.  thanks for pointing that out.  once i fixed that i was able to select that mode and it is a lot better but there is still overscan.  i'm trying to come up with another to shrink it down even more.  

i've been using this [thread]("http://www.ubuntuforums.org/showthread.php?t=304625&page=3") as guidance, using a modeline genrator to give me the correct entry for say 1160x652, but using the 1280x720 timings in that modeline.

e.g.
ModeLine "1280x720" 74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync
ModeLine "1216x648" 74.48  1216 1272 1400 1664  684 685 688 746 -hsync +vsync
ModeLine "1160x652" 74.48  1160 1208 1328 1664  652 653 656 746 -hsync +vsync
(keeping 74.48, 1664, and 746 the same for each)

---

### Post by david_2001 on 2007-02-18
Have you considered using xvidtune, which should be installed by default, to generate a usable modeline for your TV?  I'm not an expert on this program but I have used it successfully in the past to generate modelines when I needed them.  (Note, I find that xvidtune tends to crash after pressing the Show button but the modeline does get printed to the console before all the backtrace information.)

---

### Post by NJHokie on 2007-02-18
> **david_2001 said:**
> Have you considered using xvidtune, which should be installed by default, to generate a usable modeline for your TV?  I'm not an expert on this program but I have used it successfully in the past to generate modelines when I needed them.  (Note, I find that xvidtune tends to crash after pressing the Show button but the modeline does get printed to the console before all the backtrace information.)

I actually fiddled around with that program a bit but it would not apply any changes i tried to make to shrink the screen down.  It kept saying invalid modeline or something like that.  

No worries though.  Using that other thread and shrinking the res down to 1184x666 while keeping the 1280x720 timings worked like a charm.  The TV now displays correctly with just a slight overscan, but one I can live with!  I made that my default modeline/res putting it first and removing most of the others.  It now displays properly on the login screen, in gnome and in MythTV.  No display yet for BIOS though.  My remote is working in Myth too!  (just needs some button tweaking)

Now on to getting the firewire capture working with my 4200HD!   Thanks for your help all.  It just took me a real long time to find/understand modelines i guess.

---

### Post by goghgoner on 2007-03-21
I am a noob and have the same TV as NJhokie -- Sony wega 46WT520 connected via dvi/hdmi -- I tried to copy what I think his config is but I am not getting the modeline to stick and I have slight overscan with the one the Ubuntu gods give me. I am using Geforce 6150 graphics.  

The following errors are given at the bottom of my xorg log "xf86CheckModeForDriver: called with invalid scrnInfoRec". This error leads me to believe the modeline won't work on my setup but maybe I am missing something obvious. 

The modeline given by xvidtune (and automatically used on booting) has some overscan:
```
aborst@aborst-desktop:/var/log$ xvidtune
Vendor: , Model: 
Num hsync: 1, Num vsync: 1
hsync range 0:  15.00 -  46.00
vsync range 0:  59.00 -  61.00
"1216x684"     74.48   1216 1272 1400 1664    684  685  688  746 -hsync +vsync

```

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier "SONY TV"
	HorizSync 15.0 - 46.0
	VertRefresh 59.0 - 61.0
	Option "DPMS"
	#Option "IgnoreEDID"
	#DisplaySize 720 405
	#ModeLine "1280x720" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	ModeLine "1184x666" 74.48 1216 1272 1400 1664 684 685 688 746 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "SONY TV"
    Option 	   "FlatPanelProperties" "scaling = centered"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1184X666" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by NJHokie on 2007-03-22
hey man,
i'll try and help you out some.

i believe the current res i'm running at right now uses this modeline:
ModeLine "1160x652" 74.48 1160 1208 1328 1664 652 653 656 746 -hsync +vsync

try that one out by yourself first.  once i get home and have some time i'll copy my xorg.conf file how it is now and post it up for you.

---

### Post by williammanda on 2007-03-22
FWIW
I have found to get the native resolution for my monitor is to have it probed by nvidia. This setup works best so far across many debian setups I have tried. I have a westinghouse 42" lcd native 1366 x 768 and the best I can get is 1360 x 765. I will use the prior posted xorg.conf file as an example

Section "Monitor"
Identifier "SONY TV"
#HorizSync 15.0 - 46.0
#VertRefresh 59.0 - 61.0
#Option "DPMS"
#Option "IgnoreEDID"
Option "UseEDID" "True"
#DisplaySize 720 405
#ModeLine "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
#ModeLine "1216x648@60" 74.48 1216 1272 1400 1664 684 685 688 746 -hsync +vsync
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
Driver "nvidia"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
Monitor "SONY TV"
#Option "FlatPanelProperties" "scaling = centered"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "nvidia-auto-select"
EndSubSection
EndSection

Let me know how it works out.
Thanks

---

### Post by goghgoner on 2007-03-22
I tried Hokie's modeline and it worked -- I can see the time and what windows are open -- sweet.  The auto config line didn't work -- it gave me 720x480 or something weird like that. I am using the 8776 nvidia drivers so that may be the problem. I have to go into nvidia-settings and center the display each time (no biggie) since this version of the drivers do not respond to the FlatPanelOption. I read in a nvnews forum that this should be fixed in the new drivers so I'll wait until they are packaged...

Anyway, I'm on to bigger and badder things -- MythTV. OTA HD is my mission. 

Thanks for helping win this battle and :guitar: on.

---

### Post by NJHokie on 2007-04-01
Great glad it worked!  

I have myth up and running as well.  Good luck with it.  I don't have mythweb working yet though. =(  Next project to tackle...

---

### Post by hoggy on 2007-04-27
The 'Option "UseEDID" "True"' may not have worked for others, but worked perfectly for me today.  Thanks a ton!

---

### Post by zer0fill on 2007-06-27
Thanks for the help! This has been bugging me for the last year or so (when I was on Fedora..switched to Ubuntu today :-D). The screen is now almost perfect (have a small 2-4px black border)

FWIW I have a Panasonic TH-50PX60U and my conf settings are below

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA GeForce Ti4200"
	Driver		"nvidia"
	Busid		"PCI:2:0:0"
	Videoram	128000
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Option		"UseEDID" "True"
	Horizsync	15.0 - 68.0
	Vertrefresh	59.0 - 61.0
#	ModeLine	"1160x632"  74.25   1280 1392 1432 1648    720  725  730  750 +hsync +vsync
	ModeLine	"1232x672"  74.25   1232 1392 1432 1648    692  725  730  750 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce Ti4200"
	Monitor		"Generic Monitor"
	Option 		"FlatPanelProperties" "scaling = centered"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1232x672@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by NJHokie on 2007-06-28
zero,
make sure that these match letter for letter or else you won't be able to select that mode propertly in the display properties option.


> **zer0fill said:**
> Thanks for the help! This has been bugging me for the last year or so (when I was on Fedora..switched to Ubuntu today :-D). The screen is now almost perfect (have a small 2-4px black border)

FWIW I have a Panasonic TH-50PX60U and my conf settings are below

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Option		"UseEDID" "True"
	Horizsync	15.0 - 68.0
	Vertrefresh	59.0 - 61.0
#	ModeLine	"1160x632"  74.25   1280 1392 1432 1648    720  725  730  750 +hsync +vsync
	ModeLine	**"1232x672"**  74.25   1232 1392 1432 1648    692  725  730  750 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce Ti4200"
	Monitor		"Generic Monitor"
	Option 		"FlatPanelProperties" "scaling = centered"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		**"1232x672@60"**
	EndSubSection
EndSection

```

---

### Post by realvz on 2007-10-15
Just a quick question...do you guys have overscan option in nvidia-settings for your version of graphics card....

I know i had it in my HP DV 2000 with GeForce 7200 in Feisty...but now with GUTSY and GeForce 8600GT i dont seem to have any such option available.

I am using a normal TV via S-Video and my screen is heavily overscanned... i cant see any of the gnome panels and i have about 80 pixels missing from both right and left side.

---

