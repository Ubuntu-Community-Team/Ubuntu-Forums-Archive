---
title: "Low resolution only, cannot change"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by itchy88 on 2007-11-09
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=592683&amp;highlight=low+resolution](http://ubuntuforums.org/showthread.php?t=592683&amp;highlight=low+resolution) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Total newbie here.

I've been using ubuntu for a few days now and I changed the xorg.conf file for my mouse to see if I could get a mouse wheel speed adjuster to show up in the mouse properties.  That didn't work but no biggie.  However, the next time I booted up, ubuntu told me I was set to low resolution and I had to configure.  I tried the configure page it offered, but wasn't able to change a single setting.  Now I'm stuck at 800x600 for my screen resolution with only 640x480 as another option.

I've looked up a lot of other forum answers and have reset the xorg.conf using sudo dpkg-reconfigure xserver-xorg.  On reboot I got the same problem.  My xorg.conf now reads:


Section "Device"
	Identifier	"via k8m890"
	Driver		"amd"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"samsung syncmaster 955df"
	Option		"DPMS"
	HorizSync	30-92
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"via k8m890"
	Monitor		"samsung syncmaster 955df"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"


I have a Samsung SyncMaster 955df and an onboard video card for an MSI VIA K8M890 Chipset motherboard.

The thing is most threads end, "you're screwed, get a new video card" etc.  But mine was working fine until this afternoon, so I'm assuming I can tweak something to get it back.  Right?

---

### Post by Steven_B on 2007-11-09
You might want to try removing the resolutions that you don't intend to use or your monitor doesn't support (probably everything except 1600 x 1200).

You could also try changing the refresh rates to match those in the [spec sheet:]("http://product.samsung.com/cmc_upload/product/brochure/955DF.pd")
Horizontal
30-85 kHz
Vertical
50-160 Hz

No, you do not need to get a new video card.

---

### Post by itchy88 on 2007-11-14
Hi all, 

thanks for the tips, steven.  after more fiddling, i'm now in real trouble as the screen seems to be in some kind of hyper resolution and i can't read the details of my text.  there's some five copies of the screen in tiny print running into each other across the top 2/3 of the screen, the bottom part blank except for a strip of jibberish at the bottom.  

so now i can only boot in through ubuntu live.  that screen is perfect.  i read elsewhere about reading the xorg file for the live version and copying it to the hard drive or installed version.  can anyone tell me how to find those two versions while in ubuntu live?

---

### Post by Yellow Pasque on 2007-11-14
Just a thought...
Your driver in the Device section is set to amd, but you have Via graphics, no?

How about installing:
```
sudo apt-get install xserver-xorg-video-via
```
and making sure the driver in your xorg.conf is set to "via"

---

### Post by itchy88 on 2007-11-14
i'm at work right now and i will try that, but i can still only successfully boot in through ubuntu **live**.  so i'm not sure where the xorg.conf file is when i'm in live.  is the main file menu i see the one live is using or is it the one on the hard drive?  how can i find both files?

and if i use that sudo command, will it change only the parameters for that live session, or will it apply the changes to my installed version?  is there a way to direct it to apply the sudo to my hard drive (installed) ubuntu?

---

### Post by Daelyn on 2007-11-15
> **itchy88 said:**
> i'm at work right now and i will try that, but i can still only successfully boot in through ubuntu **live**.  so i'm not sure where the xorg.conf file is when i'm in live.  is the main file menu i see the one live is using or is it the one on the hard drive?  how can i find both files?

and if i use that sudo command, will it change only the parameters for that live session, or will it apply the changes to my installed version?  is there a way to direct it to apply the sudo to my hard drive (installed) ubuntu?

I have answered your priv message with a short guide. I hope it sorts it. Post some results here of what you find out.

A copy of the xorg.conf.bad (the installed one we renamed) could be interesting to look at btw. Just paste it in a code section if you feel up for it. Thanks.

---

### Post by itchy88 on 2007-11-16
IT WORKED!   a million thanks.

i found my hard drive's x11 folder as you said on /media/disk-1

there were lots of old and backed up xorg.conf files.  but i just followed your steps and copied the live version into the folder as the official xorg.conf file.

here's the "bad" code:

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"nodeadkeys"
	Option		"XkbOptions"	"altwin:meta_win"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 905DF(X)/955DF(X)/CD195A"
	Horizsync	30-85
	Vertrefresh	50-160
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1024x768@85" "800x600@85"	"800x600@60"	"800x600@75"	"832x624@75"	"800x600@72"	"1024x768@85"	"800x600@56"	"1024x768@75"	"640x480@85"	"1024x768@70"	"640x480@75"	"1024x768@60"	"640x480@72"	"1024x768@43"	"640x480@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1792x1344@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection

and here's the good one:

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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1792x1344" "1280x1024" "1024x768" "800x600" "640x480"
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
EndSection

---

### Post by tahitiwibble on 2007-11-16
> **Daelyn said:**
> I have answered your priv message with a short guide. I hope it sorts it. Post some results here of what you find out.

A copy of the xorg.conf.bad (the installed one we renamed) could be interesting to look at btw. Just paste it in a code section if you feel up for it. Thanks.

**Daelyn**, I wonder if you would be kind enough to send me your short guide as I seem to have a very similar problem to Itchy88?

---

### Post by itchy88 on 2007-11-16
here's the original private message:

When you look in "places/computer" you will see "FILESYSTEM". that is the live CD file system.

The HDD install will pop in under "/media/[disk label]" or something.
What I usually do is look in Computer, identify two "filesystem" partitions (I have more) and once I click on them, it will automount to the /media folder.

What you need to do:

sudo mv /media/[insert label]/etc/X11/xorg.conf /media/[insert label]/etc/X11/xorg.conf.bad

sudo cp /etc/X11/xorg.conf /media/[insert label]/etc/X11/xorg.conf

This will backup the non working xorg and then you can identify fault source later if you're interested. The second command will copy the live CD's xorg to the installed xorg.

If this does not work of some reason, boot the live CD into "failsafe graphics" and use that xorg file instead. That one will almost always work right out of the box. Don't remember all the device and identifyers to change manually.

---

### Post by tahitiwibble on 2007-11-16
Thank you Sir ......... a gentleman and scholar!

This thing is driving me crazy ...... got about ten hours in it so far and no progress yet .......... I'll let you know what happens.

Once again, thanks!

---

### Post by tahitiwibble on 2007-11-21
I now have a completely useless computer and can no longer stop the machine from defaulting to a resolution that is not supported by my monitor .......... I really have no idea what to do .............. heeeeeeeeelp

---

### Post by tahitiwibble on 2007-11-22
I just couldn't take it any more and I ended up doing a lovely fresh install of Feisty 7.04 and everything works perfectly again ........... I will not be re-installing the update to Gutsy for quite some time to come, if ever!?

---

