---
title: "NVIDIA TV-Out: Overscan Problems."
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by DannyW on 2007-05-15
Hello

I'm using an 8600GT NVIDIA graphics card (with latest binary beta drivers 100.14.03, via latest envy) and have enabled TwinView. My TV is a clone of my primary DFP display.

I have set TVOverScan to 0 in my xorg.conf yet the picture on the TV still looks overscanned.

At a guess there is about 5% of the picture missing at each edge of the screen. Task bar, scroll bar missing, etc.

Below is my xorg.conf. I hope someone can point me in the right direction.

Thank you.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Dell"
    ModelName      "2407WFP"
#    HorizSync      "DFP-0: 30.0 - 81.0; TV-0: 30.0 - 50.0"
#    VertRefresh    "DFP-0: 60.0; TV-0: 60.0"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "ConnectedMonitor" "DFP, TV"
    Option         "TwinView" "True"
    Option         "MetaModes" "1920x1200,1024x768 @1920x1200; 1024x768,1024x768"
    Option         "TwinViewOrientation" "Clone"
    Option         "TVStandard" "PAL-I"
    Option         "TVOverScan" "0.00000"
    Option         "TVOutFormat" "SVIDEO"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1024x768"
    EndSubSection
EndSection
```

---

### Post by tgm4883 on 2007-05-15
I dont have overscan on my tv (i use an lcd tv) so this is just a guess, but setting TVOverScan to 0 sounds like your not compansating for overscan.

---

### Post by DannyW on 2007-05-15
Thanks for the prompt response.

I have tried 0, 1 and even a mid value of 0.5

I don't see any noticeable differences.

From the nvidia driver readme:
> The "TVOverScan" option can be used to enable Overscan, when the TV encoder supports it. Valid values are decimal values in the range 1.0 (which means overscan as much as possible: make the image as large as possible) and 0.0 (which means disable overscanning: make the image as small as possible). Overscanning is disabled (0.0) by default.

Also note that the TV out worked fine with my old ATI Radeon X800XT card.

Kind regards

---

### Post by tgm4883 on 2007-05-15
When you say that 5% is missing on each side, do you mean that you can't see it because it extends beyond the edge of the tv screen, or that you have a black border around it?

---

### Post by NT4usB on 2007-05-15
Did you try running```
nvidia-settings
```and play with those overscan settings?

---

### Post by DannyW on 2007-05-16
> When you say that 5% is missing on each side, do you mean that you can't see it because it extends beyond the edge of the tv screen, or that you have a black border around it?
The picture extends beyond the edge of the screen. There is no black border


> Did you try running
```
nvidia-settings
```
and play with those overscan settings?
I've looked through nvidia-settings and didn't see any overscan settings.
I would assume the overscan settings would be at: GPU 0 > TV-0, but the only settings here are digital vibrance and image sharpening.

Thanks
Danny

---

### Post by chadlongstaff on 2007-05-20
I'm having the same problem but with an 8500GT. The 9775 driver is failing for me, but it did provide an overscan control when I used it with a 7300GS. It seems to me that the beta driver just isn't feature complete, adding Option "TVOverScan" "x.x", for values of x.x between 0.0 and 1.0, is having no effect whatsoever. Experimenting with modes on the TV seems to confirm that the bits of the screen that are missing just aren't being sent by the card.

---

### Post by chadlongstaff on 2007-05-20
Setting the Option "TVStandard" "PAL-I" seems to have helped a little, losing less at top and bottom, still losing the same amount at the sides. "PAL-I" is for the UK and HK, you can find codes for other territories in the nvidia readme.

---

### Post by DannyW on 2007-05-20
> **chadlongstaff said:**
> Setting the Option "TVStandard" "PAL-I" seems to have helped a little, losing less at top and bottom, still losing the same amount at the sides. "PAL-I" is for the UK and HK, you can find codes for other territories in the nvidia readme.

Yes, I'm from the UK and setting PAL-I didn't fix this for me.

It's reassuring that there are overscan options in previous non-beta drivers. I guess we'll just have to wait.

---

### Post by chadlongstaff on 2007-05-22
Bit of progress, bought some composite cable and connected with that, still a slight overscan, but something like 5-10 pixels, so far more acceptable. Found I didn't get colour till after a reboot, but that's acceptable as the picture is looking quite a lot nicer now with far fewer artifacts.

---

removing     Option         "TVOutFormat"        from /etc/X11/xorg.conf got rid of the colour problem

---

### Post by doas777 on 2008-06-25
I see that this thread is rather stale, so please pardon me for adding to it.

I'm having the problem same problem with my 8500GT and standard def TV.


I have turned overscan all the way down, and switched from svid to composite (by running 1 yellow rca line from the blue port on the accompanying RGB composite adapter). Unfortunately these didn't reduce the amount of  non-visible screen. 

has anyone found another fix for the issue? 

Thanks,
Franklin

---

### Post by dmiller40 on 2008-07-02
I just upgraded to Hardy, and I was using Nvidia Settings installed by envy on Gutsy. I need to set my overscan, but I looked in my xorg.conf file and there is no overscan option. I ran sudo nvidia-settings and got "command not found" Here is whats in my xorg.conf

```
Section "Device"
	Identifier	"Device0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Device0"
	Monitor		"Monitor0"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection
```

thanks
dm

---

### Post by doas777 on 2008-07-06
> **dmiller40 said:**
> I just upgraded to Hardy, and I was using Nvidia Settings installed by envy on Gutsy. I need to set my overscan, but I looked in my xorg.conf file and there is no overscan option. I ran sudo nvidia-settings and got "command not found" Here is whats in my xorg.conf

```
Section "Device"
	Identifier	"Device0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Device0"
	Monitor		"Monitor0"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection
```

thanks
dm


well first off, you have to install nvidia-settings with:
```
sudo apt-get install nvidia-settings
```
in the terminal. after that run 
```
sudo nvidia-settings

```
be carefull to always run it with sudo or gksu, because it needs admin rights to access /etc/X11/xorg.conf .

as for overscan, add this line to your screen section of your xorg.conf (the one that configs your TV, not the monitor):
```

    Option         "TVOverScan" "0.0"

```
the 0.0 sets the amount of overscan you want. the valid values are between 0.0 (no overscan) and 1.0 (maximum overscan).

hope that helps

---

