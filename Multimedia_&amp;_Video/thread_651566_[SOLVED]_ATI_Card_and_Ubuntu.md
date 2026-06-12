---
title: "[SOLVED] ATI Card and Ubuntu"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by rmores on 2007-12-27
I'm unable to run anything that's 3D accelerated EXCEPT Compiz with my current setup. I've gone over tons of forums and google searches and I'm finally giving up. 

My setup is a x64 dual core AMD running Gutsy with a ATI **X1650** PCIE card.

Tested applications that would not work are:
Google Earth;
any Windows game running on Wine;
glxgears;

Like I said, Compiz runs fine.

The error given :
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0"
```

running ```
DISPLAY=:0 glxgears
``` I can get glxgears working, but of course, no window borders, etc

Google Earth jumps to a splash screen but then freezes.

I'm using the fglrx drivers from the repository, but I've also tried generating .deb packages from the latest drivers, which are actually worse(Compiz runs sloow) and the problem persists.

This is in my xorg.conf file:
```
Section "Module"
	Load  "glx"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc ATI Default Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection


Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc ATI Default Card"
	Monitor    "L1720B"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

Output of glxinfo | grep direct:
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

Output of fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6473 (8.37.6)

```

---

### Post by moron on 2007-12-27
I'm not 100% sure but it looks like you are missing some modules there.  Here's a list of what could go in there:

[http://wiki.x.org/wiki/XorgConfModulesSection](http://wiki.x.org/wiki/XorgConfModulesSection)

I think at the least you should have:

Section "Module"
        Load  "dri" # this one is why you don't have full acceleration I expect
        Load  "glx"
EndSection

I run Gentoo at work so cannot compare your module section to the one I have at home but I know that I have way more stuff in that section on my Ubuntu box.

Cheers

---

### Post by rmores on 2007-12-27
I've had "dri" in and out many times, but not along with that pack there. I'll try and reboot, see what happens.

---

### Post by rmores on 2007-12-27
Didn't work either. And HAL failed to initialize. I've ran a sudo dpkg-reconfigure hal to fix it.
So back to only glx, but I'm keeping dri module too.

I dug into my syslogs and found these(if any help):

```
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
```

```
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)

(EE) AIGLX: reverting to software rendering
```

---

### Post by rmores on 2007-12-28
Anyone?

---

### Post by evetrins on 2007-12-28
I have similar problem:
In CS on Wine it is impossible to set "D3D" mode, only "Software" and "OpenGL" available :(

This check i find suggested on other thread:

$ glxinfo |head -3
name of** display: :1.0**
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

It indicates a problem.
On other hand:

stas@game-pc:/lib/modules/2.6.22-14-generic$ fglrxinfo
**display: :0.0**  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 2.1.7170 Release

After all, i see there is somewhat messy with  displays 1.0 vs  0.0

fglrxinfo -display :1.0
**display: :1.0**  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

$ glxinfo -display :0.0|head -3
name of **display: :0.0**
display: :0  screen: 0
direct rendering: Yes

Someone have an ideas how to fix it?

---

### Post by rmores on 2007-12-28
[SIZE=4][COLOR=red]**SOLVED:**[/COLOR][/SIZE]
 
I've backed up my /home folder, formatted the partition and did a fresh install on it, did all the updates, installed the restricted drivers, installed compiz, installed Xgl, and the error persisted.:mad:
 
so I purged the fglrx driver and installed the one from ATI's website.
 
Then after looking out there some more, I found that AIGLX runs different, no DRI to render, so I had to remove Xgl. Done.:)
 
Now I have 3D acceleration :popcorn: but compiz won't work :(.
Even after whitelisting fglrx and removing the blacklist "T" in the compiz config. file AND creating a file to bypass DRI check in compiz, it doesn't work at all.:(
 
 
To sum up, I either use:
A - Xgl to run compiz but no 3D acceleration or
B - No Xgl, whitelist my driver, giving 3D acceleration but no compiz.
 
I want to use both!!
 
so then i ran compiz from the console to get this message:
 
**$ compiz**
**.: 3: Can't open /etc/xdg/compiz/compiz-manager.ubuntu**
 
 
I was nearly biting my nails off when I figured ls /etc/xdg/compiz showed the same file but with a different name so I did this
```
sudo cp /etc/xdg/compiz/compiz-manager.ubuntu.dpkg-new /etc/xdg/compiz/compiz-manager.ubuntu
``` and it worked like a charm :guitar:

---

### Post by rmores on 2007-12-28
Since I solved this one I'm posting my xorg.conf file if anyone needs to have a look at it.

not many tweaks as you may see:
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "abnt2"
    Option        "XkbLayout" "br"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
    Option        "Device" "/dev/input/mice"
    Option        "Protocol" "ImPS/2"
    Option        "ZAxisMapping" "4 5"
    Option        "Buttons" "9"
    Option        "Emulate3Buttons" "false"
EndSection

Section "InputDevice"
    Identifier  "stylus"
    Driver      "wacom"
    Option        "Device" "/dev/input/wacom"
    Option        "Type" "stylus"
    Option        "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier  "eraser"
    Driver      "wacom"
    Option        "Device" "/dev/input/wacom"
    Option        "Type" "eraser"
    Option        "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier  "cursor"
    Driver      "wacom"
    Option        "Device" "/dev/input/wacom"
    Option        "Type" "cursor"
    Option        "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier   "L1720B"
    Option        "DPMS"
EndSection

Section "Device"
    Identifier  "ATI Technologies Inc ATI Default Card"
    Driver      "fglrx"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
    Option "XAANoOffscreenPixmaps" "true"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "ATI Technologies Inc ATI Default Card"
    Monitor    "L1720B"
    DefaultDepth     24
    SubSection "Display"
        Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

#Section "Extensions"
#    Option        "Composite" "0"
#EndSection

#Section "ServerFlags"
#    Option        "AIGLX" "On"
#EndSection

```

---

### Post by pgn674 on 2007-12-29
What was that file you created to bypass the DRI check in compiz? I got the whitelist and blacklist figured out, but not that part.

I have a thread [here]("http://ubuntuforums.org/showthread.php?t=651578") with my problem of no direct rendering, and your fix worked for me. Thank you :) So now I just need to get compiz-fusion back. Here is my compiz-manager file```
# Ubuntu specifc compiz-manager configuration file
# goes into /etc/xdg/compiz/compiz-manager
# works with git://anongit.compiz-fusion.org/fusion/misc/compiz-manager
COMPIZ_BIN_PATH="/usr/bin/" 
PLUGIN_PATH="/usr/lib/compiz/" 
COMPIZ_NAME="compiz.real"

# from http://ubuntuforums.org/showthread.php?t=651566
WHITELIST="fglrx"

# maybe?
#SKIP_CHECKS=yes
```and what happens when I try to run compiz in the terminal right now.```
paul@paul-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4153 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity
```And here's my xorg.conf if that helps.```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"fglrx"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
    Option "XAANoOffscreenPixmaps" "true"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL1912"
	Option		"DPMS"
	Horizsync	24-80
	Vertrefresh	49-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"Acer AL1912"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Module"
#	Load		"glx"
EndSection

#Section "Extensions"
#	Option		"Composite"	"0"
#EndSection

#Section "ServerFlags"
#    Option "AIGLX" "off"
#EndSection
```

---

### Post by glantucan on 2007-12-30
> **rmores said:**
> [SIZE=4][COLOR=Red]**SOLVED:**[/COLOR][/SIZE]
...
so then i ran compiz from the console to get this message:

**$ compiz**
[B].: 3: Can't open /etc/xdg/compiz/compiz-manager.ubuntu

[/B]which is a cruel bug :lolflag:
I was nearly biting my nails off when I figured ls /etc/xdg/compiz showed the same file but with a different name so I did this
```
sudo cp /etc/xdg/compiz/compiz-manager.ubuntu.dpkg-new /etc/xdg/compiz/compiz-manager.ubuntu
``` and it worked like a charm :guitar:

Hi , I found the same ¿bug? :confused: and solved it like you. Strange... I suppose it has to do with the manual installation of the ati binary package.

**pgn674**: You just have to follow this instructions (that's what **rmores** meant)
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects)
to tell compiz to use your manually installed fglrx driver

And then you just:
```
sudo cp /etc/xdg/compiz/compiz-manager.ubuntu.dpkg-new /etc/xdg/compiz/compiz-manager.ubuntu
```
to create the (let's call it so) "launcher" that wasn't automatically created

Cheers

---

### Post by rmores on 2007-12-30
Don`t forget to empty the BLACKLIST value where it blocks certain IDs(with a variable $T), its right below the whitelist settings.
 
About the "bug", I'm sorry for naming it like that, but I just don't know what to call it otherwise, maybe a programmer's typo?
 
 
Anyhow, It's all working here, but I switch compiz off to play games or run google earth because those drivers still need improvement(screen flickers horizontally with compiz and 3D).
 
just type in 
metacity --replace
then compiz --replace to switch back
 
i'm trying to figure out a way to run an application with a shell script like that, but it's hardly efficient the way i'm putting it,but it looks like im getting close to it:
 
```
 
metacity --replace
sh /3d/app/here
compiz --replace

```

---

### Post by pgn674 on 2007-12-30
Ah, thanks **glantucan**, I had already followed that part and forgot about it. :oops:

I don't have the file /etc/xdg/compiz/compiz-manager.ubuntu.dpkg-new, but it seems to me that's not my problem anyways, looking at what happens when I try to run compiz. Guess I'll keep researching about texture_from_pixmap.

**Edit**:
Oh yea, and the compiz-manager file I had edited earlier was located at /etc/xdg/compiz/compiz-manager. I guess that was the wrong file to edit, according to the [guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects").

---

### Post by pgn674 on 2007-12-30
In case someone's curious, here's what happens if I run compiz with [checks]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects") being skipped:```
paul@paul-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4153 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```So that texture_from_pixmap is an error, not a warning.

---

### Post by pgn674 on 2007-12-30
I got compiz working using this thread [here]("http://forum.compiz-fusion.org/showthread.php?t=6354"). Yay!

---

