---
title: "Manually Specify Resolution on nVIDIA laptop"
date: 2012-11-15
forum: Multimedia Software
---

### Post by frogotronic on 2012-11-15
Hello,

I'd like to manually specific a non-native resolution with the nVIDIA driver on a laptop.

The xorg.conf file is attached.  I'd like to specify 1280x800 for the LCD (laptop) as an option.  Currently, only the 1600x900 (native/auto) option is available.

How can I do this?

Thanks,
CH

---

### Post by cwsnyder on 2012-11-15
The use of a custom xorg.conf file has been deprecated since Ubuntu 9.10.  The suggested alternative for setting resolution is to install the x11-xserver-utils package, then use xrandr to set the resolution (included in the package).  In your case the following would be entered in a terminal to see if it sets properly:```
$ cvt 1280 800
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
[COLOR="Blue"]VGA-1[/COLOR] connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9   
$ xrandr --newmode 1280x800 83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
$ xrandr --addmode [COLOR="blue"]VGA-1[/COLOR] 1280x800
$ xrandr --output [COLOR="blue"]VGA-1[/COLOR] --mode 1280x800
```Use in place of VGA-1 whatever is displayed in the second line of the response to xrandr  on a line by itself.  The $ indicates a new line prompt.  If you get a response including 'xrandr: failed to get size of gamma for output default' and the replacement for VGA-1 is default, this procedure may not work, and I have a bug report on Launchpad #1078695.

---

### Post by frogotronic on 2012-11-15
> **cwsnyder said:**
> The use of a custom xorg.conf file has been deprecated since Ubuntu 9.10.  The suggested alternative for setting resolution is to install the x11-xserver-utils package, then use xrandr to set the resolution (included in the package).  In your case the following would be entered in a terminal to see if it sets properly:```
$ cvt 1280 800
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
[COLOR="Blue"]VGA-1[/COLOR] connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9   
$ xrandr --newmode 1280x800 83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
$ xrandr --addmode [COLOR="blue"]VGA-1[/COLOR] 1280x800
$ xrandr --output [COLOR="blue"]VGA-1[/COLOR] --mode 1280x800
```Use in place of VGA-1 whatever is displayed in the second line of the response to xrandr  on a line by itself.  The $ indicates a new line prompt.  If you get a response including 'xrandr: failed to get size of gamma for output default' and the replacement for VGA-1 is default, this procedure may not work, and I have a bug report on Launchpad #1078695.

You can have my xorg.conf file when you pry from my cold dead hands...


Actually I tried your suggestion before and it doesn't work right - but I'll give another go!

---

### Post by frogotronic on 2012-11-16
Ok, got an error:

```
$ cvt 1280 800
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
$ xrandr
Screen 0: minimum 8 x 8, current 1600 x 900, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected 1600x900+0+0 (normal left inverted right x axis y axis) 310mm x 174mm
   1600x900       60.1*+   40.3  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
$ xrandr --newmode 1280x800 83.50  1280 1352 1480 1680  800 803 809 831 -hsync
$ xrandr --addmode LVDS-0 1280x800
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  35
  Current serial number in output stream:  36
```

Is this the error in the bug report?

Thanks,
CH

---

### Post by cwsnyder on 2012-11-16
No, the error does not match that of my bug report.

I see why you need xorg.conf, to at the very least tell your computer what output to use!  My mistake.

In xorg.conf, see changes below:```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Unknown"
	ModelName "LGD"
	HorizSync 41.3 - 54.8
	VertRefresh 40.0 - 60.0
	Option "DPMS"
	[COLOR="Red"]ModeLine "1280x800_60" 83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync[/COLOR]
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	Option "RegistryDwords" "EnableBrightnessControl=1"
	Option "RandRRotation" "True"
	Option "Stereo" "0"
	Option "nvidiaXineramaInfoOrder" "DFP-0"
	Option "TwinViewXineramaInfoOrder" "DFP-0"
	Option "TwinView" "0"	
	Option "metamodes" "DFP: nvidia-auto-select +0+0"
	SubSection "Display"
		Depth 24
		[COLOR="red"]Modes "1280x800_60" 1600x900 1024x768[/COLOR]
	EndSubSection
EndSection

Section "InputDevice"
	Identifier "Mouse0"
	Driver "mouse"
	Option "Protocol" "auto"
	Option "Device" "/dev/psaux"
	Option "Emulate3Buttons" "no"
	Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier "mtev"
	Driver "evdev"
	Option "Device" "/dev/input/multitouch"
	Option "Protocol" "auto-dev"
EndSection

Section "InputDevice"
	Identifier "Keyboard0"
	Driver "kbd"
EndSection

Section "ServerLayout"
	Identifier "Layout0"
	Screen 0 "Screen0" 0 0
	InputDevice "Keyboard0" "CoreKeyboard"
	InputDevice "Mouse0" "CorePointer"
	Option "Xinerama" "0"
	InputDevice "mtev" "SendCoreEvents"
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "NVIDIA Corporation"
	BoardName "NVS 4200M"
	Option	"NoLogo"	"False"
EndSection
``` The modes in the Screen/Display subsection are suggestions only.  I have no idea what modes are pertinent to your monitor, but the new modeline mode should be referred to here as well.

---

### Post by frogotronic on 2012-11-17
Ok, I'll give this a go - I'm not in front of my dual head right now (laptop).

Thanks,
CH

---

### Post by frogotronic on 2012-11-30
Ok, that broke X completely.

- hmmmmm

---

### Post by MadMadness on 2012-11-30
I am in the same boat as you Cement.  I am using my LCD TV as my display and it doesnt have an EDID or something so it just shows as a generic monitor with very few resolution options.  The problem I am having specifically is overscan.  I cant see the edges of the screen.  In windows Nvidia has a utility that custom adjustsed the resolution to something like 1166x768 or something like that so I need to figure out how I can tell Ubuntu to set that resolution.  

All attempts at using xrandr have generated similiar errors as yours.  There seems to be so many different ways people have tried to fix this problem and each one has you doing backflips through rings of fire that still dont seem to work.

Anyways please do let me know if you manage to figure this out!  Thanks

---

### Post by cwsnyder on 2012-11-30
Okay guys, I may have a fix.  When I booted Linux Mint 14 Nadia Cinnamon desktop, I started getting similar problems with xrandr not working.  In this case, I simply changed from the nouveau driver to the nvidia-current driver, which then let me use xrandr to set my video mode.

---

### Post by jrussell88 on 2013-01-04
Has anyone made more progress with this? What were the resolutions you obtained?

         I'm running Ubuntu 12.04 x64, kernel 3.2.0-24-generic with an  NVidia GTX460 and an Achieva Shimian QH270-Lite 2560 x 1440 monitor  connected by a dual-link DVI cable. 

  I've installed the nvidia-current 313-09 drivers from xorg-edgers  (and tried the 310-19 from NVidia). Neither of these drivers read the  EDID information from my monitor (/var/log/Xorg.0.log) and default to  lower resolutions which my monitor will not display, resulting in a  black screen. [Full story here]("http://askubuntu.com/questions/236028/xorg-failsafe-error-screens-found-but-none-have-a-usable-configuration-nvid")
  
If I replace the high-res monitor with a lower resolution 1600 x 900 monitor it works fine.

  I want to force my video card to the resolution I need. NVidia's Xserver settings doesn't change anything. The xorg.conf configuration file is deprecated and the file is untouched by 12.04, so I tried xrandr with similar results to cement_head. 

First I queried the Modeline for my resolution:

```
john@Vivid01:~$ cvt 2560 1440 60
# 2560x1440 59.96 Hz (CVT 3.69M9) hsync: 89.52 kHz; pclk: 312.25 MHz
Modeline "2560x1440_60.00"  312.25  2560 2752 3024 3488  1440 1443 1448 1493 -hsync +vsync
```Then set up a new mode for it:

```
john@Vivid01:~$ xrandr --newmode "2560x1600_60.00"  348.50  2560 2760 3032 3504  1600 1603 1609 1658 -hsync +vsync
```And attempted to attach it to a display - with a similar error:

```
john@Vivid01:~$ xrandr --addmode DVI-I-1 "2560x1440_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32
```Perhaps xrandr doesn't allow complete customisation - or maybe it is built on code which is no longer relevant?

      Does anyone know how to get this to work for Ubuntu 12.04 and recent NVidia drivers?

---

### Post by cwsnyder on 2013-01-06
What is the output of **xrandr** on a line by itself in the terminal?  The reason I am asking is to be sure of two things: 1) That the DVI-I-1 is the proper name for the **connected** display listed by **xrandr**, and 2) That you are not getting any other error messages, such as the one about not reading the gamma correctly from the monitor.

If your problem is 1) above, of course you know how to correct the problem.  If it is the gamma error, you would not have gotten the X error you reported, but to correct that error, on the setting line use: ```
xrandr --output DVI-I-1 --gamma 1:1:1 --mode "2560x1440_60.00"
```Correct the output name as in 1) above, of course.

---

### Post by frogotronic on 2013-01-08
> **cwsnyder said:**
> What is the output of **xrandr** on a line by itself in the terminal?  The reason I am asking is to be sure of two things: 1) That the DVI-I-1 is the proper name for the **connected** display listed by **xrandr**, and 2) That you are not getting any other error messages, such as the one about not reading the gamma correctly from the monitor.

If your problem is 1) above, of course you know how to correct the problem.  If it is the gamma error, you would not have gotten the X error you reported, but to correct that error, on the setting line use: ```
xrandr --output DVI-I-1 --gamma 1:1:1 --mode "2560x1440_60.00"
```Correct the output name as in 1) above, of course.

Here's the output of xrandr

```
$ xrandr
Screen 0: minimum 8 x 8, current 3280 x 1050, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected 1600x900+1680+0 (normal left inverted right x axis y axis) 310mm x 174mm
   1600x900       60.1*+   40.3  
DP-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 430mm x 270mm
   1680x1050      60.0*+
   1280x1024      60.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3  
   640x480        75.0     72.8     59.9  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
```

I'm still not sure how to correct the problem.  Assume I'm totally ignorant about this (please).

How can I specify a resolution other than 1600x900 for the laptop display?

- CH

---

### Post by cwsnyder on 2013-01-08
This should work to give a 1280x800@60Hz display:```
cvt 1280 800
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr --newmode 1280x800 83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr --addmode LVDS-0 1280x800
xrandr --output LVDS-0 --mode 1280x800
```Change the last line to this if you get the error code about unable to read gamma of LVDS-0: ```
xrandr --output LVDS-0 --gamma 1:1:1 --mode 1280x800
```Hopefully this _finally_ gets your display to the resolution you wish to use.

---

### Post by frogotronic on 2013-01-10
> **cwsnyder said:**
> This should work to give a 1280x800@60Hz display:```
cvt 1280 800
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr --newmode 1280x800 83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr --addmode LVDS-0 1280x800
xrandr --output LVDS-0 --mode 1280x800
```Change the last line to this if you get the error code about unable to read gamma of LVDS-0: ```
xrandr --output LVDS-0 --gamma 1:1:1 --mode 1280x800
```Hopefully this _finally_ gets your display to the resolution you wish to use.

Error on the second command

```
$ cvt 1280 800
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
$ xrandr --addmode LVDS-0 1280x800
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  37
  Current serial number in output stream:  38
```

hmmmm......

---

### Post by BicyclerBoy on 2013-01-10
Internal LVDS panels do not have a pre-scaler & are driven directly from GPU.
Your panel only has one resolution..
You can enable GPU native scaling if you have an app that need "bigger" full screen.
GPU native scaling has performance overhead.

You can change the display dimensions or dpi to scale the desktop gadgets.
Why do you want a non-native resolution?

---

### Post by cwsnyder on 2013-01-10
> **cwsnyder said:**
> This should work to give a 1280x800@60Hz display:```
cvt 1280 800
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr --newmode 1280x800 83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr --addmode LVDS-0 1280x800
xrandr --output LVDS-0 --mode 1280x800
```Change the last line to this if you get the error code about unable to read gamma of LVDS-0: ```
xrandr --output LVDS-0 --gamma 1:1:1 --mode 1280x800
```Hopefully this _finally_ gets your display to the resolution you wish to use.

I messed up, again.  I included both the **cvt 1280 800** command and the next two lines are the *output of the cvt command*.  Just the needed commands by themselves with no extra:```
xrandr --newmode 1280x800 83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr --addmode LVDS-0 1280x800
xrandr --output LVDS-0 --mode 1280x800
```

:(:oops::redface:

---

