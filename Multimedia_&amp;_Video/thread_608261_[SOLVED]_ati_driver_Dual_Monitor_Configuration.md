---
title: "[SOLVED] ati driver Dual Monitor Configuration"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by bit_racer on 2007-11-09
Hi! :)

I have been trying to solve this problems for a few days and still I couldn't.
 
Well the problem is, I installed ubuntu 7.10, on my laptop everything was fine,my laptop videocard was recognized automatically and was configured properly, even the 3d effects...or so I thought.

When I tried to connect an external monitor to the vga port in the back of my laptop, the laptop didn't even notice I had connected something. Well I restarted the X server still could not detect my monitor; then I rebooted and I noticed that in the ubuntu boot splash I had output in the external monitor until the X server loads up.

Then I checkout my xorg.conf and I noticed that the driver applied to my laptop is not fglrx but 'ati'.(I guess its the open source ati driver).

I have tried to find information about this 'ati' driver but still have not been successful.

So my question is, there is a way to configure this 'ati' driver to have dual display?

My video card is a radeon 9000 IGP ( ubuntu recognizes it as 9100 IGP)

And my laptop is a toshiba satellite A70.

Thanks any help is appreciate!!

My xorg.conf is....

 ```


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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"

#TouchPad Custom configuration Starts!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
	Option	    "AccelFactor" "0.1"
	Option	    "BottomEdge" "650"
	Option	    "Buttons" "5"
	Option	    "CircScrollDelta" "0.1"
	Option	    "CircScrollTrigger" "2"
	Option	    "CircularScrolling" "1"
	Option	    "Device" "/dev/input/mice"
	Option	    "EdgeMotionMaxSpeed" "15"
	Option	    "EdgeMotionMinSpeed" "15"
	Option	    "Emulate3Buttons" "on"
	Option	    "EmulateMidButtonTime" "75"
	Option	    "FingerHigh" "15"
	Option	    "FingerLow" "14"
	Option	    "HorizScrollDelta" "20"
	Option	    "InputFashion" "Mouse"
	Option	    "LeftEdge" "120"
	Option	    "MaxSpeed" "1"
	Option	    "MaxTapMove" "110"
	Option	    "MaxTapTime" "180"
	Option	    "MinSpeed" "0.2"
	Option	    "Name" "ALPS;Touchpad"
	Option	    "Protocol" "auto-dev"
	Option	    "RightEdge" "830"
	Option	    "SHMConfig" "on"
	Option	    "TopEdge" "120"
	Option	    "UpDownScrolling" "1"
	Option	    "Vendor" "Sysp"
	Option	    "VertScrollDelta" "20"
	Option	    "ZAxisMapping" "4 5"

#TouchPad Custom configuration Ends!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection


```

---

### Post by bit_racer on 2007-11-15
Hello!

At last I was able to set up the dual-head display on my laptop using a radeon 9000 mobile on ubuntu Gusty. 

First I have to say that gusty, at least with this videocard is incompatible with videorama.
So the only thing we have is xrandr....but the funny thing is that with xrandr is even easier, I didnt even had to mess with my xorg file, well maybe a little....:P, I had to change in the xorg file the device driver from 'ati' to 'radeon'.

Well what I did was...

At first I had a problem because xrand could not detect my external vga monitor, what I did to solve this problem was type in terminal

```
 xrandr --addmode VGA-0 1024x768

```
 
this will add a vga monitor with 1024x768 resolution to xrandr, if your external monitor uses another resolution you could change it.

then I wrote in terminal

```
xrandr --output VGA-0 --mode 1024x768

```

and waalaa! :P I had dual output!
but the image in the vga monitor was incomplete because it seems that the radeon 9000 mobile can only output 1024x768 when using it in dual head mode, even in windows with the official drivers when I used dual head the resolution automaticatly lowers from 1280x800 to 1024x768(maybe there could be a way to solve this limitation, but I only need 1024x768 output)

so now we have to lower the laptop resolution...

```
 xrandr --output LVDS --mode 1024x768
```
now we have the image as we wanted it with dual output

you could play with other commands and configurations that better suits your :), but I hope this gives you the idea...:)
for more information check this blog, this is where I got most of this information
[http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/](http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/)

I hope this helps :)

P.S. sorry about my grammar,I rarely speak english :/

---

