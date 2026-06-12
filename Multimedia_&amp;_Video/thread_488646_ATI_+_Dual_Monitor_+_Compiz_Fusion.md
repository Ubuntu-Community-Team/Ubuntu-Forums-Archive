---
title: "ATI + Dual Monitor + Compiz Fusion"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by jeffmills on 2007-06-30
Hi All,

I have a question which may seem to be a very common question, but I have no idea where to begin.
This topic looked interesting, but it didn't seem specific enough for my situation: [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

**My computer:**
- ATI Radeon X850XT
- 19" TFT (DVI) - 1280x1024 - max60Hz
- 17" CRT (D-Sub) - 1280x1024 - max85Hz
- TV-out - 1024x768 - max60Hz
- Ubuntu 7.04

**Desired setup:**
- Dual Monitor
- The windows can be dragged from one screen to the other 
- Compiz Fusion
- I am willing to disconnect 1 monitor to activate TV-out (ATI card doesn't support 2 monitors + TV at the same time) but this should be as easy as possible.

What I would like to ask you is wether it would be possible to using my to make setup like that, and how should I handle this? Should I use Binary drivers, because I want TV-out? Should I use Open Source drivers because this works better with Xinerama? Is it possible to have TV out on a different resolution when still having one screen on 1280x1024?

Like I said .. taking *ALL* this into account, I don't know which solution to choose.

---

### Post by jeffmills on 2007-07-02
Not possible?

---

### Post by MikeEx on 2007-07-05
Before you get lost in what I'm about to tell you, Keep in mind Linux is *not* my primary OS. I don't know much about Linux but I do take a stab at learning about it. I **stumbled** upon a way to do this just the other day while taking another shot at this awesome OS.
If any one wants to; Feel free to re-post a cleaned up version.

[COLOR="Red"]**The following is for Ubuntu 7.04 Feisty + Gnome + Ati (Fglrx drivers) + Xgl**[/COLOR]
**Coming off a fresh install of Ubuntu 7.04** - This is exactly how I did it


**First I followed this How-to for installing 8.38.6 drivers manually:**
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Pre-Installation_Checks](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Pre-Installation_Checks)
Note: I did not disable the composite extention but I did put the following at the end of my xorg.conf file
```
Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```
[B][COLOR="Red"]When you get to "Configure the Driver" section. Do not do the "aticonfig --initial" step! It nuked my xorg.conf[/COLOR]
(8.38.6 only. luckily there was a backup in the "/etc/X11" folder)[/B]
The alternative to the aticonfig --initial command is to edit /etc/X11/xorg.conf and replace the string "ati" with "fglrx" in the "Device" section.

**After rebooting from installing the Fglrx drivers I followed this how-to:**
[http://ubuntuforums.org/showthread.php?p=1773544](http://ubuntuforums.org/showthread.php?p=1773544)

Then I went to System>Preferences>Screen Resolution
Then I chose 2048x768 **(Note: This will be different for you.)**
This gave me proper dual screen in regular X. (I was shocked at this point as it was a first for me)

The "Device" section of my xorg.conf file looked like this after I was done:
```
Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "0x0+0x0,1024x768+1024x768"
	Option	    "EnableMonitor" "crt1,crt2"
	Option	    "ForceMonitors" "crt1,crt2"
	BusID       "PCI:1:0:0"
EndSection
```
I then swapped VideoOverlay and OpenGLOverlay values:
```
Option	    "VideoOverlay" "off"
Option	    "OpenGLOverlay" "on"
```
**Then I followed the Compiz Fusion installation guide from:**
[http://www.compiz.org/Compiz_and_Compiz_Fusion_GIT_Ubuntu_Repository](http://www.compiz.org/Compiz_and_Compiz_Fusion_GIT_Ubuntu_Repository)

**And finally did the following to complete the installation (because I forgot to get Xgl :oops:)**
```
sudo apt-get install xserver-xgl
```
Then made the startxgl script.
```
sudo gedit /usr/local/bin/startxgl.sh
```
Copied the following into the file
```
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```
Saved it and made it executable:
```
sudo chmod a+x /usr/local/bin/startxgl.sh
```
Made the Session file:
```
sudo gedit /usr/share/xsessions/xgl.desktop
```
Copied the following into it:
```
[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```
Saved it and made it executable:
```
sudo chmod a+x /usr/share/xsessions/xgl.desktop
```
Then got the Emerald Theme Manager because like Xgl, I FORGOT ](*,)
```
sudo apt-get install emerald emerald-themes
```

The last step I did was go to System>Preferences>Sessions

hit "New"
Name: Compiz
Command: compiz --replace
hit "Ok"

hit "New"
Name: Emerald
Command: emerald --replace
hit "OK"

Hit Ctrl+Alt+Backspace to kill and restart Gnome/X
Chose "GNOME and Xgl" from the sessions list.
And logged in.

I am sorry if this does not work for you. I wasn't even expecting Dual Screen Compositing when I went to install Compiz Fusion. Just a pleasant surprise.

The only problems I have:
Mplayer does not display video while in Xgl Session. Use "Totem Movie Player" that comes with Ubuntu.
Avoid having any video-playing programs entering Full Screen mode.
Blur effect does not work

---

### Post by ZeroThree on 2008-02-15
Hello,

I'm have the dual monitor on an ATI X1400 working fairly well, but there are a few bugs..

If I maximize any window, or a window starts up maximized (only with Compiz is the window manager), I get booted to the login screen. Other than that everything works very very well. I'm curious to see if anyone has had a similar problem and if a solution in fact exists.

Thanks in advance!

Anthony

---

### Post by patrickvdgrift on 2008-02-25
> **ZeroThree said:**
> Hello,

I'm have the dual monitor on an ATI X1400 working fairly well, but there are a few bugs..

If I maximize any window, or a window starts up maximized (only with Compiz is the window manager), I get booted to the login screen. Other than that everything works very very well. I'm curious to see if anyone has had a similar problem and if a solution in fact exists.

Thanks in advance!

Anthony

Hi Anthony, i have been trying to get my x1400 working with dual screen for a few weeks now and dit not succeed yet. Could you please send me your xorg.conf?

thank you very much!

---

### Post by ZeroThree on 2008-02-25
For sure.. but mind you its a total hack. Applications start maximized all the time, and with XFCE you sometimes have to start a new session (Session Manager Applet) and manually start Compiz. On top of that I'm running it on a laptop, so in order for me to switch back to a single screen I can't use XFCE, only Gnome will work with Compiz and this particular xorg.conf..

You have to update your ATI drivers: [http://ubuntuforums.org/showthread.php?t=301941&page=26](http://ubuntuforums.org/showthread.php?t=301941&page=26)

And here is the xorg.conf:

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
#
#   ********************************
#   ** BIG DESKTOP CONFIGURATION  **
#   ********************************
#
#  redwheelbarrow 03-10-07

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "EnablePrivateBackZ" "yes"
	Option	    "HSync2" "83"
	Option	    "VRefresh2" "75"
	Option "DesktopSetup" "LVDS,AUTO"
	Option 	    "Mode2" "1440x900" #Resolution for second monitor
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual 1440 1050
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```

Hope it works for you.. good luck!

---

