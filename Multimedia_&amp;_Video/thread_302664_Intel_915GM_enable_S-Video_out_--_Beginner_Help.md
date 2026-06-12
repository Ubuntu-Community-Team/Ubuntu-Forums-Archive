---
title: "Intel 915GM enable S-Video out -- Beginner Help"
date: 2006-11-19
forum: Multimedia &amp; Video
---

### Post by LinLenLap on 2006-11-19
Hi,

I've been going through the forums looking for a way to enable the Function F7 key to switch between my LCD laptop display, and the TV or Projector I connect to via the S-Video out port on my laptop. There seem to be solutions, but they are very confusing. There doesn't seem to be a good, easy how-to yet, so I thought I'd use this thread to get one going. 

If you look below you can see how far I've gotten. So far, I'm able to identify my card, backup xorg.conf, and open xorg.conf to edit it. Also, I've added a bit on how to restore the xorg.conf files if any problems should arise.

My goal is to make this into a simple how-to that others can follow, so please excuse the layout. Any help at all is appreciated and will be credited as appropriate.

Thanks in advance!

==========================================================
This guide is for Intel Mobile 915GM cards.

**STEP 1. Confirm that you have the same video card.**
```
lspci | grep 915
```
Which should return something like this:
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
```

**STEP 2. Backup your xorg.conf:**
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
```

**STEP 3. Open xorg.conf:**
```
sudo gedit /etc/X11/xorg.conf
```
Which shows something like the following after a default install of Edgy:
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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
```

...

**STEP ?: If any of the changes you've made have screwed up your display, you'll need to restore your last working backup of xorg.conf.** 

Here are a few different methods:

1. I found that when I buggered up X, it would leave me sitting at a blank screen. I would hit, alt+F2 which would open up a new session I think. After entering my user name and password I'd either try to fix X (if I thought I knew what the problem was) or else replace it altogether with the original one that I knew worked fine.

To try and fix it type:
```
sudo nano /etc/X11/xorg.conf
```
To simply replace it with the one you know works type:
```
sudo cp /etc/X11/xorg.bak /etc/X11/xorg.conf
``` 
A this point I was unable to restart X immediately, but a reboot works fine.
```
sudo reboot
```

2. If you can't see the terminal or get into it, you might try rebooting using the live cd to do so. Once booted up you'll need to mount the partition where your messed up xorg.conf file resides. Once mounted, do this, assuming that you already mounted your hard drive where / is (in /mnt/ubuntu):
```
sudo cp /etc/X11/xorg.conf  /mnt/ubuntu/etc/X11/xorg.conf
```
Then reboot normally.

3. Instead of using the live cd, you might just use the recovery boot option from within grub, if you still have it available. Choose recovery, then do:
```
dpkg-reconfigure xserver-xorg
```
Then reboot.

LLL

**Credits**

The most important part. Thanks to everyone who helped!

Recovery of xorg.conf methods 2 & 3 taken (and lightly edited) from posts by  [TAURUS]("http://ubuntuforums.org/member.php?u=43398"). Any mistakes in those steps are entirely my own.

---

### Post by LinLenLap on 2006-11-22
Ok, I've updated a few things here and broken X quite a few times trying to figure it out. I've been trying to modify the xorg.conf file shown at this post [here]("http://ubuntuforums.org/showthread.php?t=239894&highlight=xorg.conf"), but to no avail.

On the plus side, I've gotten quite good at restoring X. 

Here are my outstanding questions:

1. How to edit xorg.conf file to enable video output switching via the Function keys.

2. Failing 1, how to adapt the xorg file linked above to suit my needs. What needs to be changed and why?

3. Another forum thread said that typing something like "init --2" let you test drive your changes. That would save a lot of time, but when I tried it it didn't work for me. It just went to a blank screen. I've lost the original link and I don't think that the code above is right, but it was something along those lines. How to do that properly?

4. When I break X and read the error messages I can sometimes switch to another "session"?, then sudo nano the errors, but I can't get X to restart to test if I've fixed them. I seem to have to do a sudo reboot. Is this correct?

---

