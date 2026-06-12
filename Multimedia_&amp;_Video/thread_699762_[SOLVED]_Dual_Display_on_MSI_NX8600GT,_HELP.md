---
title: "[SOLVED] Dual Display on MSI NX8600GT, HELP"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by BassKozz on 2008-02-17
I am trying to get a Dual Display setup working on my rig (See Signature), with a MSI NX8600GT Vid Card with the two monitors being:
Hanns-G HG216D connected to port #1 on the video card with a [DVI to HDMI cable]("http://www.monoprice.com/products/product.asp?c_id=102&cp_id=10231&cs_id=1023104&p_id=2405&seq=1&format=2")
Dell 1905FP connected to port #2 on the video card with a [DVI to VGA connector]("http://www.monoprice.com/products/product.asp?c_id=104&cp_id=10419&cs_id=1041903&p_id=2396&seq=1&format=2") and a VGA cable going to the monitor
...
I just recently installed Ubuntu and when I was using the LiveCD and immediately after installation both screens would display the same desktop at the native resolution for the HannsG monitor (1680x1050) obviously that didn't look good on the Dell Monitor thou...
Then after I installed the Proprietary drivers "NVIDIA accelerated graphics driver", the Dell monitor now no longer works, it doesn't display anything and the screen is blank (as if it's not even connected).

How can I get both of these monitors to work?
Thanks for any/all help,
-BassKozz

---

### Post by overdrank on 2008-02-17
> **B/-\ssKozz said:**
> I am trying to get a Dual Display setup working on my rig (See Signature), with a MSI NX8600GT Vid Card with the two monitors being:
Hanns-G HG216D connected to port #1 on the video card with a [DVI to HDMI cable]("http://www.monoprice.com/products/product.asp?c_id=102&cp_id=10231&cs_id=1023104&p_id=2405&seq=1&format=2")
Dell 1905FP connected to port #2 on the video card with a [DVI to VGA connector]("http://www.monoprice.com/products/product.asp?c_id=104&cp_id=10419&cs_id=1041903&p_id=2396&seq=1&format=2") and a VGA cable going to the monitor
...
I just recently installed Ubuntu and when I was using the LiveCD and immediately after installation both screens would display the same desktop at the native resolution for the HannsG monitor (1680x1050) obviously that didn't look good on the Dell Monitor thou...
Then after I installed the Proprietary drivers "NVIDIA accelerated graphics driver", the Dell monitor now no longer works, it doesn't display anything and the screen is blank (as if it's not even connected).

How can I get both of these monitors to work?
Thanks for any/all help,
-BassKozz

HI and you can use the nvidia settings to setup your extra display
```
gksudo nvidia-settings
``` It will be located under xserver display configuration

---

### Post by BassKozz on 2008-02-17
> **overdrank said:**
> HI and you can use the nvidia settings to setup your extra display
```
gksudo nvidia-settings
``` It will be located under xserver display configuration
Thanks overdrank :D
I was able to setup my dual display, and I setup my Dell screen as a "separate X screen" which is the way I wanted it...
But I have run into another problem now:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/NVIDIAXServerSettings.jpg[/IMG]
Notice my Dell Monitor is showing up as a CRT and it's auto set the resolution to 800x600 which isn't pretty...
I'd like to setup this monitor to it's native (1280 x 1024) resolution, but it seems that the nvidia-settings won't allow me to change it from 800x600 :confused:

---

### Post by overdrank on 2008-02-17
HI and I had a similar issue with my son's system and I was unable to solve it, but I did revert to a older driver that fix his issues on Feisty.

---

### Post by BassKozz on 2008-02-18
It gets worse, the HannsG doesn't go into power saving mode :(
Only the dell goes into power saving mode even thou I've setup the monitors to turn off after 20minutes:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/powersaving-monitor.jpg[/IMG]
> **overdrank said:**
> HI and I had a similar issue with my son's system and I was unable to solve it, but I did revert to a older driver that fix his issues on Feisty.
Where might I be able to locate a driver that might work with my setup?

---

### Post by overdrank on 2008-02-18
Hi and I used Envy to install the older driver manually 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by BassKozz on 2008-02-18
Now I've really gone and done it... I installed Envy and I've been playing with different settings and installing different versions of the NVidia drivers and now my monitors won't display a resolution greater then 640x480 :(
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/ScreenResolutionPreferences.jpg[/IMG]

I've since uninstalled and reinstalled the NVidia drivers w/ and w/out Envy, and I am stuck... now both screens are stuck at 640x480 and you can't even imagine how bad this looks on a widescreen monitor. :(

Now what can I do?

**_EDIT:_** ok I am now at 800x600, but still not back to where I was (1680x1050)...

**_EDIT2:_** I have since uninstalled Envy and completely removed it with Synaptic, I then enabled the "NVidia graphics driver" from the "Restricted Drivers Manager" and rebooted, upon reboot it said:
> **Ubuntu is running in low-graphics mode**
Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself
But when I configure it my self and boot into Ubuntu the highest resolution available is 800x600, and the restricted drivers aren't active, even thou I enabled them?
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/RestrictedDrivers.jpg[/IMG]

How come it was able to auto-detect on my initial install, but now it doesn't recognize my Video Card and Monitor?

[size=1](this is what I get for being greedy and trying to get dual-monitors to work, I should have stuck with what I had) :([/size]

**_EDIT3:_** Ok, I removed the HannsG monitor from the equation, re-installed Envy, installed the NVidia drivers (via Envy) and rebooted with just the Dell 1905FP connected... I was then able to get that to preform at it's native 1280 x 1024 resolution... I then shutdown the computer and connected the HannsG monitor and booted back up, now I have the HannsG monitor active at it's native resolution 1680x1050, but the Dell is now inactive, and when I activate the Dell from the NVidia settings and reboot it stays disabled:confused:
One thing I noticed that might be causing an issue is when I select "Save to X Configuration File" in the NVidia settings window I am presented with the following error message:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/nvidia-settings-err.jpg[/IMG]
So I manually removed w/:```
sudo rm xorg.conf.backup
```
and now it's telling me:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/nvidia-settings-err2.jpg[/IMG]
So it seems as if the "NVidia Settings" app is having a hard time saving to xorg.conf...
Could this be causing my problems? If so, how can I fix it?

---

### Post by BassKozz on 2008-02-19
Problem SOLVED :D
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/NVIDIAXServerSettings-workingdualmo.jpg[/IMG]

After reconfiguring the xserver by running
```
sudo dpkg-reconfigure xserver-xorg
```
with the Dell ONLY connected...
I then rebooted and ran
```
sudo nvidia-xconfig
```
I then copied the /etc/X11/xorg.conf file to a folder on my desktop
I then repeated the above with just the HannsG monitor connected.

I took the two copied xorg.conf files and used them to create a new xorg.conf file with the correct settings and there you have it... dual-monitor setup w/ both monitors working at their native resolutions :guitar:

---

### Post by HHelsinger on 2008-02-23
Can you post the your xorg.conf file for the Dell 1905FP?   I can't get mine to display using the Nvidia drivers on an Nvidia FX5200.  Thanks.

---

### Post by BassKozz on 2008-02-24
> **HHelsinger said:**
> Can you post the your xorg.conf file for the Dell 1905FP?   I can't get mine to display using the Nvidia drivers on an Nvidia FX5200.  Thanks.
Here she is: ```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Fri Jan 11 14:26:48 PST 2008

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Fri Jan 11 14:27:25 PST 2008
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
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "Screen0" 0 0
  screen 1 "Screen1" rightof "Screen0"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"0"
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
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	30.0	-	65.0
	Vertrefresh	50.0	-	75.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"HSD HG216"
	Horizsync	30.0	-	82.0
	Vertrefresh	50.0	-	75.0
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Horizsync	28.0	-	64.0
	Vertrefresh	43.0	-	60.0
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600 GT]"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce 8600 GT"
	Option		"AddARGBGLXVisuals"	"True"
	Busid		"PCI:1:0:0"
	Screen	0
EndSection

Section "Device"
	Identifier	"Videocard1"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce 8600 GT"
	Option		"AddARGBGLXVisuals"	"True"
	Busid		"PCI:1:0:0"
	Screen	1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"DFP: 1680x1050 +0+0"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes		"nvidia-auto-select"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Videocard1"
	Monitor		"Monitor1"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"DFP: 1280x1024 +0+0"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes		"nvidia-auto-select"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

The HannsG is "Monitor0" Dell is "Monitor1"

---

