---
title: "No Resolution higher than 640x480"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by andrew5859 on 2007-12-24
Hello everyone,

I have this problem with getting resolutions higher than 640x480.  My xorg.conf file says that all those are seemingly possible, but when I go to get the dropdown to do what it's suppose to do, it don't and @ 60Hz. I have an MSI motherboard with intigrated nVidia Geforce4 MX.  This is what my xorg.conf file says:


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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"NEC FP955"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"NEC FP955"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
 

  Can somebody please tell me how to fix the resolution settings?  It would be greatly 
  appreciated.  Thank you so much and have a Merry Christmas.

 Andrew

---

### Post by dany3l on 2007-12-24
did you try nvidia-settings ?

---

### Post by andrew5859 on 2007-12-25
What do you mean?.....I can't try nvidia settings because I can't install the drivers for the intigrated graphics.  It won't go with utf-8 or western iso.  I really and honestly don't know enough about ubuntu to really get around or find anything to make any kind of changes, though I'm willing to learn new stuff all the time, especially when I've been playing and working with Windows since early 1990.  If you'll be patient with me, I'll do my part :)

---

### Post by andrew5859 on 2007-12-25
where are the settings so that I can change them?  :-(

---

### Post by Warren Watts on 2007-12-25
You might look into providing the horizontal and vertical sync ranges for your monitor in the xorg.conf file.
Here is a snippet from my xorg.conf file:```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30.0 - 70.0
        VertRefresh     50.0 - 120.0
EndSection
```
My guess would be that X is unable to determine what refresh rates the monitor is capable of and is defaulting to the lowest common denominator, so to speak.

You can look thru the xorg error log for help too..

---

### Post by andrew5859 on 2007-12-26
I've tried to put the refresh rates and vertsync rates in, but it won't let me save the changes.  It says that I don't have the permissions to complete the task and that I'm not the owner.  What do I do now?  I feel like I'm stuck with a system that's faulty, with the exception of reinstalling and starting from scratch.  I'm very frustrated at this point](*,)
Please help....I really want this to work.

Andrew



                                Horizontal:  30 kHz to 110 kHz                              Automatically
Synchronization
                                   Vertical: 50 Hz to 160 Hz                                Automatically
Range
                                                                                            Some systems may not support
                                             640 x 480 @ 50 to 160 Hz
Resolutions Supported
Resolution based on horizontal and           800 x 600 @ 50 to 160 Hz                       all modes listed.
vertical frequencies only                    832 X 624 @ 50 to 160Hz
                                             1024 x 768 @ 50 to 132 Hz
                                             1152 x 870 @ 50 to 118 Hz
                                             1280 x 1024 @ 50 to 101 Hz ................... NEC-Mitsubishi Electronic Display cites
                                             1600 x 1200 @ 50 to 87 Hz                      recommended resolution at 85 Hz for
                                             1792 x 1344 @ 50 to 78 Hz                      optimal display performance.
                                             1800 x 1440 @ 50 to 73 Hz
                                             1856 x 1392 @ 50 to 75 Hz
                                             1920 x 1440 @ 50 to 73 Hz

---

### Post by Warren Watts on 2007-12-27
The xorg.conf file has to be edited by root, so you either have to edit it from the command line with something like:
```
sudo nano /etc/X11/xorg.conf
```
or drop to the command line and run gedit as root with a command like:
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by andrew5859 on 2007-12-28
:)  Well I finally got into the xorg.config file and got it edited just like you had instructed me to with the command prompt and it took, but, and this is a BIG BUTT.....:frown: when I saved it, then restarted the system, I couldn't get back into my system:cry:.  Was I suppose to adjust the resolution first?   Needless to say, I'm very upset :twisted:.  What did I do wrong and why didn't it work, what can I do to fix this so that it does work :confused::confused:?  I'm getting kind of tired of having to reinstall the OS over and over again....PLEASE Help.  Thank you four help thus far, it's been greatly appreciated, but I still need it.

Andrew

---

### Post by sornen on 2007-12-28
If you look on the panel under System/Adminstration/Restricted Driver Manager it should tell you if the nvidia drivers are installed.  Normally they will be installed.

Under Preferences find Screen Resolution and see what options you have there.

Now if you cant get back to your window environment you should still be able to log on and use a terminal.

If you edit xorg.conf make a backup copy.  

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Then if you can get the window environment back you can

```

sudo rm /etc/X11/xorg.conf
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```

You will then be able to reboot your computer with the old settings.

You can also edit xorg.conf in a terminal.

```

sudo nano /etc/X11xorg.conf

```

Remember if you play around with system files you have to use sudo to get the right permission to make changes.

Now do this

```

sudo cat /var/log/Xorg.0.log

```

or use gedit to open Xorg.0.log

This is where xorg devices messages are logged.  Do you have any errors, which are marked with (XX)

It can be frustrating when first learning linux, worth persisting though IMHO ;)

---

### Post by sornen on 2007-12-28
Ok just noticed that you do not have the nvidia device drivers installed or at least it is not recorded in the xorg.conf file.

```

Section "Device"
Identifier "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
Driver "nv"
BusID "PCI:1:0:0"
EndSection

```

Whereas you should have something like this:
```

Section "Device"
    Identifier     "NVIDIA Corporation NV36 [GeForce FX 5700]"
    Driver         "nvidia"
EndSection

```

The Driver has to be "nvidia"
This is why you cannot get higher resolution.

Ok you need to install the nvidia binary drivers

open a terminal and in the terminal type:
```

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings

```

ok it then says you should type
```

sudo nvidia-glx-config enable

```

which will automatically configure xorg.conf



or use synaptic to install these packages.  This hopefull should fix things.  If you have a very old gfx card you may need to use
```

sudo apt-get install nvidia-glx-legacy

```
instead

Use nvidia-settings to adjust your nvidia gfx properties.  You'll find it somewhere on the gnome panel menus once you have installed the nvidia-settings package.

If you cannot get XWindows to start just use nano to edit the xorg.conf and change Driver line back to "nv" instead of "nvidia" and reboot and see what the Xorg.0.log says.

---

### Post by andrew5859 on 2007-12-31
I'm getting really sick of this program, I try to edit the xorg.config file and it brings up a blank screen with a bunch of symbols for commands which don't work.  It happens wheather i'm in terminal or any other type of console, I'm just really frustrated with the whole thing.  I'm use to just plugging something in and the drivers are found and loaded automatically, not having to search around for this or that file or go to this terminal to load this or that file.  And if I want to get new files, I just get them and launch them and they work without any hassles.....I did what you said and still nothing is working , and no resolution.....:(

---

### Post by andrew5859 on 2007-12-31
Well to start with, I want to appologize for being so obnoxious on here.  Secondly I want to thank everyone for there hard efforts and assistance in helping me with solving this issue.  It is now finally fixed and everything is working just fine with all the refresh rates I need :-D  
I am now the happy clam I said I was going to be and I'm so greatful for everyone's patients with me through this, thank you all again and have yourselves a Very Happy New Year=D>\\:D/

---

### Post by sornen on 2007-12-31
With Ubunutu most of the drivers are there ready to be installed for all common hardware configurations, and are usually installed on the first installation.  Glad you got it fixed.

---

### Post by andrew5859 on 2008-01-15
Just wanted to drop everyone a short line to say hello and to let you all know that all your help with my previous problem with resolution has been tremendous.  I've been learning a lot.  I also want to let you know that I'll be aquiring my A+ cert next week.  If there's anything I can do for anyone else, I will try my best to do so.  Take care all.

Andrew  8)

---

