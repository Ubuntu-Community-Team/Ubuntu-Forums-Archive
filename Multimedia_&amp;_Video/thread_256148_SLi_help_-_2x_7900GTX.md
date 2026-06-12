---
title: "SLi help - 2x 7900GTX"
date: 2006-09-12
forum: Multimedia &amp; Video
---

### Post by mildly_amused on 2006-09-12
Hi,

I'm trying to get my two BFG 7900GTX cards to work in SLi mode, but it seems Ubuntu is only detecting the one card.

I'm using the latest nvidia drivers from the package manager, the 686 SMP kernel and the 6.06 lts version of Ubuntu.

I can't find anywhere where it says anything about SLi, and i tried *sudo nvidia-xconfig --SLI="auto"*. This made changes to my xorg.conf which caused a black screen on reboot.

This is what I have in the xorg.conf for the display:

```
Section "Module"
	Load	"i2c"
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

*snip*

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"F900P"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"F900P"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

Also, I am used to having a resolution of 2048x1536x32 in Windows. Am I right in thinking that if I add that resolution to the display modes in the above, that will enable that resolution?

---

### Post by tseliot on 2006-09-12
> **mildly_amused said:**
> Hi,

I'm trying to get my two BFG 7900GTX cards to work in SLi mode, but it seems Ubuntu is only detecting the one card.

I'm using the latest nvidia drivers from the package manager, the 686 SMP kernel and the 6.06 lts version of Ubuntu.

I can't find anywhere where it says anything about SLi, and i tried *sudo nvidia-xconfig --SLI="auto"*. This made changes to my xorg.conf which caused a black screen on reboot.

This is what I have in the xorg.conf for the display:

```
Section "Module"
	Load	"i2c"
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

*snip*

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"F900P"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"F900P"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

Also, I am used to having a resolution of 2048x1536x32 in Windows. Am I right in thinking that if I add that resolution to the display modes in the above, that will enable that resolution?

The command is:
```
sudo nvidia-xconfig --SLI=Auto
```

but try fixing the resolution problem first:
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by mildly_amused on 2006-09-12
> **tseliot said:**
> The command is:
```
sudo nvidia-xconfig --SLI=Auto
```

but try fixing the resolution problem first:
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

Ahh, the resolution thing worked really nicely.

However the SLI bit didn't. At first, I typed that command and it executed sucessfully. I restarted X to see if it would take effect. This left me at a white screen with the nvidia logo in the middle, which was frozen.

I rebooted and was left at a black screen in the same place (just before the login prompt). Any ideas? The SLI works fine in Windows.

---

### Post by tseliot on 2006-09-12
> **mildly_amused said:**
> Ahh, the resolution thing worked really nicely.

However the SLI bit didn't. At first, I typed that command and it executed sucessfully. I restarted X to see if it would take effect. This left me at a white screen with the nvidia logo in the middle, which was frozen.

I rebooted and was left at a black screen in the same place (just before the login prompt). Any ideas? The SLI works fine in Windows.

boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line)

type:
```
sudo nano -w /etc/X11/xorg.conf
```

and remove the SLI option

then press CTRL+X (save and exit)

then reboot:
```
reboot
```

---

### Post by mildly_amused on 2006-09-12
That's done. Is the identifier in the xorg.conf supposed to say default device? I would have thought it would say 7900GTX or something. The card is definately supported by nvidia for Linux, I looked it up in the supported cards list.

---

### Post by Coolit on 2006-09-14
I have a pair of 7900gtx cards working in SLI under dapper, heres my xorg.conf. 

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
InputDevice     "Logitech MX1000" "CorePointer"
    #InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

#	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
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
    Load           "type1"
    Load           "vbe"
load "xkb"
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
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB RECEIVER"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    #Identifier     "stylus"
    #Driver         "wacom"
    #Option         "Device" "/dev/wacom"          # Change to 
    #Option         "Type" "stylus"
    #Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Monitor"
    Identifier     "L1715S"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
Option "SLI" "1"
Option "NoLogo"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "L1715S"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


If you go to /var/log/Xorg.0.log you can see if its enabled and if not what went wrong, your looking for something like this, taken from my log file:-

> (**) NVIDIA(0): Option "SLI" "1"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): NVIDIA SLI enabled; using auto-selected rendering method.
(II) NVIDIA(0): NVIDIA GPU GeForce 7900 GTX at PCI:5:0:0> 

Hope this helps :)

---

### Post by mildly_amused on 2006-09-14
I'll give it a try, thanks!

---

### Post by mildly_amused on 2006-09-14
Still having problems. Adding the SLI bit to the Device section caused the black screen effect I had before.

I did notice this in my Xorg.0.log file:

(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:6:0:0) found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"

The PCI:6:0:0 is the other card. I tried modifying my Xorg.conf file with another Device section with basically the same as the other section but with the other BusID. This caused Xorg to fail with a parse error, something along the lines of "this keyword should not be here.".

I'm really stumped.

---

