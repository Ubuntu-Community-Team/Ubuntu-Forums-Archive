---
title: "Ati, Matrox MergedFB"
date: 2006-11-17
forum: Multimedia &amp; Video
---

### Post by Ziox on 2006-11-17
[FONT=Verdana]**[SIZE=4]Dual Monitor Support With MergedFB[/SIZE]**

[/FONT]          [LEFT][FONT=Verdana]The following attempts to enable Dual Monitor support by activating the MergedFB function that is implemented within the recent Xorg's open-source 'radeon' or 'mga' graphics driver.
[/FONT] [FONT=Verdana]
[/FONT][/LEFT]
        [LEFT][FONT=Verdana]**[SIZE=3]System Requirements:[/SIZE]**[/FONT][/LEFT]
    [LEFT][FONT=Verdana]ONE Dual-Output ATI (or Matrox Graphics card <= unsure, since I have never tested it before).[/FONT][/LEFT]
    [LEFT][FONT=Verdana]A recent version of the free Xorg, **WITHOUT **any binary graphics driver installed.
[/FONT] [FONT=Verdana]
[/FONT][/LEFT]
        [LEFT][FONT=Verdana][B]Let's get started!!!

[/B][/FONT][/LEFT]
    [LEFT][FONT=Verdana]***[COLOR=Red]1. Open up Xorg.conf using ONE of the following commands:[/COLOR]***[/FONT][/LEFT]
        [LEFT][FONT=Verdana]Gnome (Ubuntu):[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
gksudo gedit /etc/X11/xorg.conf
```[/FONT][/LEFT]
    [LEFT][FONT=Verdana]KDE (Kubuntu):[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
kdesu kate /etc/X11/xorg.conf
```[/FONT][/LEFT]
    [LEFT][FONT=Verdana]Xfce4 (Xubuntu):[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
gksudo mousepad /etc/X11/xorg.conf
```[/FONT][/LEFT]
    [LEFT][FONT=Verdana]Command-Line Based:[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
sudo nano /etc/X11/xorg.conf
```[/FONT][/LEFT]
        [LEFT][FONT=Verdana]***[COLOR=Red]2. This is about the simplest HowTo, simply copy the following lines to your "Device" Section:[/COLOR]***[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
**Option "MergedFB" "true" **#Enable MergedFB function
**  Option "MonitorLayout" "LVDS (TMDS), CRT" **# LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port **NOT MONITOR TYPE!**
**  Option "CRT2Hsync" "30-65" **#Horizontal Sync of the Monitor (check your monitor's manual for correct values)
**  Option "CRT2VRefresh" "50-75"** #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
**  Option "OverlayOnCRTC2" "true"**
**  Option "CRT2Position" "LeftOf" **#Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
**  Option "MetaModes" "1280x1024-1280x1024"** #Monitor Resolutions for Primary-Secondary monitors 
#**Option "MergedXineramaCRT2IsScreen0" "true" **#determines which screen is going to be the primary screen; value can be "true" or "false"
```[/FONT][/LEFT]
        [LEFT][FONT=Verdana][COLOR=Red][I][B]3. Next, go to the "Monitor" Section and add the following
[/B][/I][/COLOR]```
**Horizsync    28-64** #You may wish to change the values to fit your specific monitor
    **Vertrefresh    43-60**
```[/FONT][FONT=Verdana][COLOR=Red][I][B]
Save the file, and restarted X (ctrl+alt+backspace), or reboot.

[/B][/I][/COLOR][/FONT][/LEFT]
        [LEFT][FONT=Verdana]**Now Dual Monitor support should be enabled, if not please post your problem.**[/FONT][/LEFT]

---

### Post by pinworm on 2006-12-10
does this work with the ati driver that comes installed standard with ubuntu? also is this the only option to use a composite manager with a dual head ati card?  im using xinerama right now, but i dont have direct rendering so i cant try any of the cool composite managers.

---

### Post by Ziox on 2006-12-10
stupid post

---

### Post by ttolstead on 2006-12-10
I just tried this with a Matrox G550 normal install Edgy Eft, to no avail.  

Whenever I reboot (before or after changes), Xinearama will not start the second monitor until I restart the X server.  Does the following snip from my xorg.conf look like what you had in mind?

snip/

Section "Device"

	Identifier	"Matrox Graphics, Inc. MGA G550 AGP 0"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	Screen 0
	Option "backingstore"
	Option "AGPMode" "4"
	Option "MergedFB" "true" #Enable MergedFB function
	Option "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
 	Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
	Option "OverlayOnCRTC2" "true"
	Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor.
	Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors
EndSection

Section "Device"

	Identifier	"Matrox Graphics, Inc. MGA G550 AGP 1"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	Screen 1
	Option "backingstore"
	Option "AGPMode" "4"
	Option "MergedFB" "true" #Enable MergedFB function
	Option "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
 	Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
	Option "OverlayOnCRTC2" "true"
	Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor.
	Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors
EndSection

/snip

---

### Post by Ziox on 2006-12-11
just delete the whole second device section.  
You are mixing two methods together, Xinerama and MergedFB.  I don't recommend mixing unless you know exactly what you are doing...

---

### Post by pinworm on 2006-12-11
i just got mergedfb working.  the advantage over xinerama in my particular case, using the open "ati" driver, is that i have direct rendering now.  im goign to see if i can get beryl working with aiglx. by the way, thanks for the how to's they have been very helpful.

---

### Post by sneekie on 2006-12-13
how do i get 2 different resolutions to work?  I'm guessing

	Option		"MetaModes"	"1024x768-1280x1024"

should do it, but it doesn't seem to work.  My external lcd is 1280x1024 and my notebook's resolution is the same.  I want one to be at 1280x1024 and one to be at 1024x768.

---

### Post by goggleBOX on 2006-12-21
I use a Compaq 2418AU laptop which has a 14" WXGA screen (1280x768 ) which also has a VGA out. I have a CMV CT-720D 17" LCD monitor (1280x1024) that I wish to connect. 

Following this guild it appears that my desktop is streching across both monitors but the external LCD does not render correctly. the desktop is usally some form of scambled pattern while the pointer appears as a square of vertical coloured stripes.

I have tried adjusting the Horizontal Sync and Vertical Refresh rate from the defaults given in the example using my monitor guild as a reference. While I can set them to various settings nothing seems to work, I have tried dozens of combinations. It appears that my monitor prefers 30kHz horizontal by 60Hz vertical as when I adjust the ranges to exclude these numbers I just get a copy of the desktop on the second monitor. 

I am using the ATI drives currently (21st Dec 2006) available using Easy ubuntu.

Attached in my xorg.conf in a text file.

---

### Post by TheCat on 2006-12-22
Thanks - this worked perfectly for me.  I was using Xinerama, but the secondary screen had odd mouse cursor display issues.

I have a Radeon 9000, the fglrx driver and I used the instructions in the first message in this thread.

---

### Post by mättu on 2006-12-23
No joy with Matrox G400.
Second screen remains black.
I think there once was an xorg-output saying that only G450 and G550 are supported, but I have not been able to reproduce it so far.
Here is a link for G400 & xinerama:
[http://www.linuxquestions.org/questions/showthread.php?t=447802](http://www.linuxquestions.org/questions/showthread.php?t=447802)
I will check that out & post back.
Would be nice to use mergedFB anyway, so help is much appreciated.

Btw. there is a bug in edgy's mga-driver. Workaround if first screen remains black after upfrade / install:
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-mga/+bug/64853](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-mga/+bug/64853)

:m)

---

### Post by ClintiePoo on 2006-12-23
I'm having a hard time getting my second monitor to work correctly.  What I get is a mirror image of the first monitor.  Since the second is only set to 1280x1024 and the first is 1600x1200, I get this weird picture scrolling effect going on.  Here's the device section from my xorg.conf.

```
Section "Device"
	Identifier	"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option "MergedFB" "true" #Enable MergedFB function
 	Option "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
 	Option "CRT2Hsync" "30-70" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
 	Option "CRT2VRefresh" "50-160" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
 	Option "OverlayOnCRTC2" "true"
 	Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor.
 	Option "MetaModes" "1600x1200-1280x1024" #Monitor Resolutions for Primary-Secondary monitors
EndSection
```

Thanks in advance for the help.

---

### Post by Ziox on 2006-12-25
> **ClintiePoo said:**
> I'm having a hard time getting my second monitor to work correctly.  What I get is a mirror image of the first monitor.  Since the second is only set to 1280x1024 and the first is 1600x1200, I get this weird picture scrolling effect going on.  Here's the device section from my xorg.conf.

```
Section "Device"
    Identifier    "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
    Driver        "fglrx"
    BusID        "PCI:1:0:0"
    Option "MergedFB" "true" #Enable MergedFB function
     Option "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
     Option "CRT2Hsync" "30-70" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
     Option "CRT2VRefresh" "50-160" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
     Option "OverlayOnCRTC2" "true"
     Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor.
     Option "MetaModes" "1600x1200-1280x1024" #Monitor Resolutions for Primary-Secondary monitors
EndSection
```Thanks in advance for the help.

you are trying to enalbe mergedFB with a proprietary (binary) driver.  Please refer to the BigDesktop thread for the correct method to enable dual monitors.

---

### Post by davbeck on 2007-01-07
Wow this worked great exept for one thing
my primary monitor is the monitor jack on my laptop and not the built in lcd. For my purposes I really need the built in to be the primary.

---

### Post by Ziox on 2007-01-07
I may finally have found the answer to the primary monitor problem. Add this line to the "Device" Section:

Option "MergedXineramaCRT2IsScreen0" "boolean"

replace the boolean with either True or False. You just have to play around with the values.

---

### Post by subliminal on 2007-01-08
Trying to get it working with a laptop and an external (goodmans LD1701) monitor. No joy :-(
The external monitor works at 1280x1024@60Hz, but when I try to give it this size using the metamodes line e.g. Option "MetaModes" "1280x800-1280x1024"
It says in /var/log/Xorg.0.log
(WW) RADEON(0): Mode 1280x1024 is out of range.
And later says the MergedFB has been disabled.

So I change the metamodes, they are both 1280x800 and on my external monitor I get a warning saying "Unsupported Mode" and it's all black. Yet there is nothing in the log file as X seems to think it's worked. I'm wondering if it's to do with the refresh rate, the manual says 60Hz, yet the log file states it's being run at 85Hz. Is there anyway I can specify this?

I've found I can set the minimum dot clock, and after examining the log file found a mode (1024x768 ) which had +hsync and +vsync and managed to force this by changing the hsync and vrefresh to specific values (found using my tv's options). There is atleast no error on my external monitor, but it is still all black. :-(

---

### Post by xr82 on 2007-01-09
Is there a way to set up the displays so that each one represents a different workspace?

---

### Post by xr82 on 2007-01-09
Sorry I forgot to include this in the last post, I'd like to either do the one screen per workspace option, or if not just disable one screen altogether (I'm using a laptop screen and I don't want the lid open all the time) so I'm wondering if this is possible?

---

### Post by BungaMan on 2007-01-10
My screen section had 1280x800 as the maximum mode.  This made the CRT use that resolution which gave a fast wave effect on it because that mode was not supported.  I've added 1280x1024 to the mode line.  This fixed the res for the CRT but also put the LCD in that res so the LCD screen had to scroll up and down.

For whoever need to have different resolutions using the ATI opensource driver...  I found the following text in someones conf file:
> #               MergedFB does not let me have a non-rectangular virtual desktop,
#               so if I configure a 1024x768 + 1280x1024 setup, the smaller one
#               will scroll inside a bigger a virtual desktop (only vertically,
#               also, when scrolling down the mouse cursor casts strange green
#               bars all the way to the top).  Try it with
#                   startx -- -layout MergedFB2Layout
#               Actually, there is an option to disable the vertical scrolling
#               and set xinerama hints appropriately.  It needs a newer version
#               of the radeon driver (from Xorg 6.9):
#                   Option "MergedNonRectangular" "true"

So I added 
```
Option "MergedNonRectangular" "true"
```
to the device section et voila, got me a desktop strechted across 1280x1024 (CRT) and 1280x800 (laptop LCD).  This is of course in addition to the lines mentioned in the first post.  The only drawback is that my wallpaper is still streched to 1024 high on my LCD but I can live with that.

---

### Post by mrWoot on 2007-01-11
I've been trying to get dual head (monitor) working for a while now (I would say 2 weeks). I have tried many things. MergedFB seems to work somewhat. 

**What is happening is** I get my dual monitor working but the secondary monitor doesn't register. Let me try to explain it better. I have ONE video card which is a Radion 9600. There are two ports/heads on it and TV out.  Look at the attached. My main monitor is on the right and the secondary is on the left. The seconday uses DVI.

As you can see in the picture, the secondary monitor just shows black. It says something about not getting anything sent to it and then turns off (power saver or something). **However** the desktop IS extended. What is there to do?

Here is my **/etc/X11/xorg.conf**
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

Section "Device"
	Identifier      "Radeon 9600"
	Driver          "ati"
	BusID           "PCI:1:0:0"
#	Option          "XAANoOffscreenPixmaps"
#	Option          "AGPMode"       "8"
#	Option          "AccelMethod"   "EXA"
#	Option          "ColorTiling"   "on"

#	Option          "MonitorLayout"                 "LCD, CRT"
#	Option          "CRT2Position"                  "LeftOf"
#	Option          "MetaModes"                     "1280x1024-1280x1024"
#	Option          "MergedXinerama"                "on"
#	Option          "MergedNonRectangular"          "false"

	Option          "MergedFB"			"true"			# Enable MergedFB function
	Option          "MonitorLayout" 		"LCD, CRT" 		# Use LCD and CRT even if you have 2 LCD's or CRT's
#	Option          "CRT2Hsync" 			"30-65" 		# Horizontal Sync of the Monitor (check your monitor's manual for correct values)
#	Option          "CRT2VRefresh" 			"50-75" 		# Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
#	Option          "OverlayOnCRTC2" 		"true"
	Option          "CRT2Position" 			"RightOf" 		# Physical location of your secondary monitor in relationship to your primary monitor.
	Option          "MetaModes" 			"1280x1024-1280x1024" 	# Monitor Resolutions for Primary-Secondary monitors 
	Option          "MergedXineramaCRT2IsScreen0" 	"true" 			# determines which screen is going to be the primary screen; value can be "true" or "false"

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon 9600"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Option          "AIGLX"         "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
        
Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

[SIZE="4"]Any help? Thank you ahead of time.[/SIZE]

---

### Post by BungaMan on 2007-01-11
comment out the HorizSync and VertRefresh in the Monitor section.  These settings will be applied to both monitors.  looking at the photo you got 2 different models so they probably don't have the same h and v refresh rates.  without these settings it will try to detect for each individually.

---

### Post by mrWoot on 2007-01-11
Yes, I do have two different models and each monitor are different sizes.
[list]
[*]One is a 17" (the one that turns on)
[*]One is a 19" (Registers but doesn't turn on.)
[/list]

I tried what you said and both of them didn't work. I had to go back into text-only mode to fix it.

The best I could do is this:
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
#	VertRefresh	43-60
EndSection

```

However that doesn't do anything for me.

I include a screenshot to show that the big desktop REGISTERS but from my previous image, you can see my secondary monitor just turns off.

---

### Post by BungaMan on 2007-01-11
Play around a bit with your settings for left and right.

I have 
Option "CRT2Position" 	"LeftOf"
Option "MergedXineramaCRT2IsScreen0" "false"

Since your secondary is on the left I suggest you use LeftOf.  I just read your first post again and you said that the secondary mentioned something about not getting anything.  That means the screen does not receive a signal.  Could be because of the left and right.

Hope it helps

---

### Post by mrWoot on 2007-01-11
From what I have seen, anything I do doesn't seem to get my DVI to turn on. I tried what you said and all it did was switch the order of my monitors. Now it just thinks that the seconday monitor is on the right side, not left. The left monitor (positioned in the picture posted before) seems to always work and turn on. This monitor is the VGA one. The 19" seconday monitor is DVI and never turns on. Do you think that's the problem?

Here is another look at what my xorg.conf looks like.

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

Section "Device"
	Identifier      "Radeon 9600"
	Driver          "ati"
	BusID           "PCI:1:0:0"
#	Option          "XAANoOffscreenPixmaps"
#	Option          "AGPMode"       "8"
#	Option          "AccelMethod"   "EXA"
#	Option          "ColorTiling"   "on"

#	Option          "MonitorLayout"                 "LCD, CRT"
#	Option          "CRT2Position"                  "LeftOf"
#	Option          "MetaModes"                     "1280x1024-1280x1024"
#	Option          "MergedXinerama"                "on"
#	Option          "MergedNonRectangular"          "false"

	Option          "MergedFB"			"true"			# Enable MergedFB function
	Option          "MonitorLayout" 		"LCD, CRT" 		# Use LCD and CRT even if you have 2 LCD's or CRT's
#	Option          "CRT2Hsync" 			"30-65" 		# Horizontal Sync of the Monitor (check your monitor's manual for correct values)
#	Option          "CRT2VRefresh" 			"50-75" 		# Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
#	Option          "OverlayOnCRTC2" 		"true"
	Option          "CRT2Position" 			"LeftOf" 		# Physical location of your secondary monitor in relationship to your primary monitor.
	Option          "MetaModes" 			"1280x1024-1280x1024" 	# Monitor Resolutions for Primary-Secondary monitors 
	Option          "MergedXineramaCRT2IsScreen0" 	"false"			# determines which screen is going to be the primary screen; value can be "true" or "false"

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
#	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon 9600"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Option          "AIGLX"         "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
        
Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

---

### Post by BungaMan on 2007-01-12
Do you get anything on the left screen when you boot up your pc?  If not then either you don't have the power on for that screen or there is something wrong with the dvi output.  Do/did you have windows with a working dual monitor setup?

---

### Post by mrWoot on 2007-01-12
> **BungaMan said:**
> Do you get anything on the left screen when you boot up your pc?  If not then either you don't have the power on for that screen or there is something wrong with the dvi output.  Do/did you have windows with a working dual monitor setup?
Yes, I am dual booting. Everything works in Windows and the DVI Monitor displays stuff on load up too. When testing, I removed my analog monitor and put a analog to dvi and plug it in the DVI port and it worked for that monitor. I don't know what's wrong.

I checked the VSync and Horizontal refresh from the manufacturer and set it accordingly. 

Here is the website for the monitor: [http://www.rosewill.com/product/product.aspx?productId=221](http://www.rosewill.com/product/product.aspx?productId=221)

---

### Post by anthurt on 2007-01-12
well, i have the same problem than you, but I think that I resolved. I only included this:

Option "MergedFB" "true" #Enable MergedFB function
 Option "MonitorLayout" "TMDS, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
 Option "OverlayOnCRTC2" "true"
 Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor.
 Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false

I include in the section device

My configuration is: 

One monitor CRT (Secondary-->connected by VGA (D-Sub15))
One monitor LCD (Primary-->connected by DVI)
My graphics card is Radeon 9600 (pro? i think so)

I hope that this information help you

> **mrWoot said:**
> Yes, I am dual booting. Everything works in Windows and the DVI Monitor displays stuff on load up too. When testing, I removed my analog monitor and put a analog to dvi and plug it in the DVI port and it worked for that monitor. I don't know what's wrong.

I checked the VSync and Horizontal refresh from the manufacturer and set it accordingly. 

Here is the website for the monitor: [http://www.rosewill.com/product/product.aspx?productId=221](http://www.rosewill.com/product/product.aspx?productId=221)

---

### Post by mrWoot on 2007-01-12
> **anthurt said:**
> well, i have the same problem than you, but I think that I resolved. I only included this:

Option "MergedFB" "true" #Enable MergedFB function
 Option "MonitorLayout" "TMDS, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
 Option "OverlayOnCRTC2" "true"
 Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor.
 Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false

I include in the section device

My configuration is: 

One monitor CRT (Secondary-->connected by VGA (D-Sub15))
One monitor LCD (Primary-->connected by DVI)
My graphics card is Radeon 9600 (pro? i think so)

I hope that this information help you
Could you include your whole xorg.conf in a [****code][****/code]? That would be very useful.

---

### Post by anthurt on 2007-01-13
OK!I post my whole xorg.conf file!

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
Option "MergedFB" "true" #Enable MergedFB function
 Option "MonitorLayout" "TMDS, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
 Option "OverlayOnCRTC2" "true"
 Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor.
 Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false
EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"Monitor genérico"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```



Try with the code...and send us the results!


> **mrWoot said:**
> Could you include your whole xorg.conf in a [****code][****/code]? That would be very useful.

---

### Post by mrWoot on 2007-01-13
> **anthurt said:**
> OK!I post my whole xorg.conf file!

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
Option "MergedFB" "true" #Enable MergedFB function
 Option "MonitorLayout" "TMDS, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
 Option "OverlayOnCRTC2" "true"
 Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor.
 Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false
EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"Monitor genérico"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```



Try with the code...and send us the results!
Worked perfectly. Let me explain what was the problem.

For the DVI to work, it needed ```
Option "MonitorLayout" "**TMDS**, CRT"
``` not ```
Option "MonitorLayout" "**LCD**, CRT"
```.

Here is my complete xorg.conf for anyone else to use.
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

Section "Device"
	Identifier	 "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver		 "ati"
	BusID           "PCI:1:0:0"
	Option          "MergedFB" 			"true"						# Enable MergedFB function
	Option		"MonitorLayout"	"TMDS, CRT"					# Use LCD and CRT even if you have 2 LCD's or CRT's
	Option		"OverlayOnCRTC2"	"true"
	**Option		"CRT2Position"		"RightOf"**					# Physical location of your secondary monitor in relationship to your primary monitor.
	Option		"MetaModes"			"1280x1024-1280x1024"	# Monitor Resolutions for Primary-Secondary monitors 
	Option		"MergedXineramaCRT2IsScreen0"	"true"		# determines which screen is going to be the primary screen; value can be "true" or "false
EndSection

Section "Monitor"
	Identifier	"Digital Monitor"
	Option		"DPMS"
	**HorizSync	30-83**
	**VertRefresh	55-75**
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"Digital Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I made a few changes from what others have.

First, be sure to look up your monitor's Vertical Refresh and Horizontal Sync. Usually you will find that information on the company's product page.

Second, my second monitor is on the RIGHT, not left.

---

### Post by Leonaken on 2007-01-14
Okay, not working 100% yet. Here´s my issue.

I have an HP laptop with an ATi Radeon Mobility X600 and a VGA Out port going to my 20¨ HP 2035 LCD monitor. Cutting and pasting the code from the first post into the Devices section of my xorg.conf enables dual-head, but setting things the way I want them doesn´t work.

Namely, setting my primary monitor to 1280x800 (my laptop is widescreen) and the secondary to 1280x1024 gives me the scrolly thing, not displaying the entire screen and scrolling to the parts not shown when I move my cursor down. I also tried setting the monitor location to ¨TopOf¨, as my secondary monitor is perched above my laptop´s, but that setting appears to be invalid as it duplicates everything on the first monitor onto the second.

Here´&#347; my xorg.conf file in its entirety.

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
	Option		"XkbVariant"	"intl"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "MergedFB" "true" #Enable MergedFB function
	Option "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
	Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
	Option "OverlayOnCRTC2" "true"
	Option "CRT2Position" "RightOf" #Physical location of your secondary monitor  relationship to your primary monitor.
	Option "MetaModes" "1280x800-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
	Option "MergedXineramaCRT2IsScreen0" "false" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Thanks for any help in advance.

---

### Post by BungaMan on 2007-01-15
You'll need to add 
```
Option "MergedNonRectangular" "true"
```
to your device section.

---

### Post by Ziox on 2007-01-15
i think instead of "TopOf" the actual command is "Above", also make sure you play around with the resolutions abit, cuz what you label as Monitor 1 might not be what the computer label as Monitor 1.  Also the Modes line in your "Screen" section have some effect as well...

---

### Post by pollox87 on 2007-01-16
I am having trouble getting my second monitor to function properly.  I have a mobility x300 and the monitor I have plugged into the laptop but it is just a clone of the main screen.  (although it is only zoomed in on the center of what the main screen shows).  here is my xorg:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option 	"MergedFB" "true" #Enable MergedFB function
 	Option "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
 	Option "CRT2Hsync" "28-60" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
 	Option "CRT2VRefresh" "43-60" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
 	Option "OverlayOnCRTC2" "true"
 	Option "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor.
 	Option "MetaModes" "1200x800-1200x800" #Monitor Resolutions for Primary-Secondary monitors 
	Option "MergedXineramaCRT2IsScreen0" "true"
	Option "MergedNonRectangular" "true"
EndSection

Section "Monitor"
	Identifier	"lid LCD"
	Option		"DPMS"
	HorizSync	28-60
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor		"lid LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1200x800" "1152x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1200x800" "1152x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1200x800" "1152x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1200x800" "1152x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1200x800" "1152x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1200x800" "1152x768"
	EndSubSection
EndSection
```

---

### Post by mohrt on 2007-01-17
Hello,

I have two Radeon 7000 VE PCI cards, each have a DVI and VGA output. The VGA output seems to put interference on the screen (wavey lines), so I am using the DVI (digital) outputs on each of the cards for a dual-head configuration. I use Xinerama to create one virtual desktop across both LCDs. Both LCDs are Dell 2005FPW, running 1680x1050 24bit on both screens, giving me a 3360x1050 virtual desktop. I am using the "radeon" device driver.

Xinerama disables DRI, so I would like to use MergedFB to take advantage of DRI acceleration. It seems that this only works with the DVI/VGA output on one card. Is there a way to make it work across two separate cards using the DVI outputs?

I have attached my current xorg.conf

Thanks for any help!

---

### Post by BungaMan on 2007-01-19
I cannot test it out for you but you'll have to make a device section for each of the cards.  specify their busid.  make a monitor section for each monitor and combine the device and monitor in a screen section for each.  put both screens in the server section giving each a unique number and define for the second where it is located to the first.

Actually here's a link that shows you how to:
[http://gentoo-wiki.com/HOWTO_Dual_Monitors#Setting_up_Two_Graphics_Cards](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Setting_up_Two_Graphics_Cards)

---

### Post by henkstubbe on 2007-01-25
Hi all.

I managed to get dual screen working on a Dell Latitude D600 laptop with a Radeon Mobility 9000 M9 in combination with a 2001FP 20inch TFT screen.

My requirements:
1) At the office, I want to use dual screen with the menu bar on the external screen.
2) Outside the office, I only want (can) use the laptop screen, of course with the menu bar visible.
3) When booting, I want to be able to log on using a visible logon textfield
4) When I plug out my laptop, I want to switch from dual to single screen very easily

What I did:
This is the xorg.conf file I use:
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
	Load	"bitmap"
	Load	"dbe"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option	  "backingstore" "true"
	Option	  "EnablePageFlip" "true"
	Option	  "SubPixelOrder" "none"
	Option	  "AccelMethod" "XAA"
	Option	  "RenderAccel" "true"
	Option	  "AGPMode" "4"
	Option	  "ColorTiling"   "on"
	Option	  "DynamicClocks" "on"
	Option	  "mtrr" "on"
	Option	  "VideoOverlay" "on"
	Option	  "OpenGLOverlay" "off"
Option "MergedFB" "true" #Enable MergedFB function
 Option "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
 Option "CRT2Hsync" "56-76" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
 Option "CRT2VRefresh" "31-80" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
 Option "OverlayOnCRTC2" "true"
 Option "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor.
 Option "MetaModes" "1400x1050 1400x1050-1280x1024 1400x1050-1600x1200 1024x768" #Monitor Resolutions for Primary-Secondary monitors 
Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-33
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Virtual        3000 1200 
		# You can put your modes below, for your own resolutions, these are mine:
		Modes		"1600x1200" "1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection



```

This setup makes my laptop boot very weird, I can see half of the screen. However, I can logon. Then I see a screen without the menu bar, so I have a problem. I solved this with creating a launcher file (right click on the desktop, create launcher) with this command 

xrandr -s 0

This command changes my screen settings to the first meta mode with a single screen. When I run 

xrandr -s2

I get a nice dual screen set up. When booting with the external screen connected, everything is fine. It's even possible to use System/Preferences/Screen Resolution and do it the GUI way.

Does this make me happy?

Well, it's not perfect yet, but it works for me. Actually this is one of the issues I had to solve before switching from Windows to Ubuntu on the business desktop - my boss did not invest in a huge screen without expecting me to use it.

Maybe someone can tell me how I can make my laptop autodetect if there is one or two screens?

---

### Post by SimonTheMime on 2007-02-01
Okay I've tried this, modifying it, doing everything I can. Basically, dual monitors works.. but instead of it being one workspace, it's two duplicate screens.

Also, somebody suggested with the DVI heads, you use TMDS, not LCD, and I've tried both. Still doesn't work. Here's my xorg.conf.

[PHP]
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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
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

Section "ServerFlags"
	Option	    "AIGLX" "off"
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

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "565"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
Option "MergedFB" "true" #Enable MergedFB function
 Option "MonitorLayout" "TMDS, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
 Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
 Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
 Option "OverlayOnCRTC2" "true"
 Option "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor.
 Option "MetaModes" "1024x768-1024x768" #Monitor Resolutions for Primary-Secondary monitors 
Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
Option "MergedNonRectangular" "false"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "565"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "On"
EndSection

[/PHP]

**Please help**

---

### Post by dano2769 on 2007-02-01
I have a Toshiba laptop, trying to use the external monitor attached to the vga output while using the built-in lcd as the main screen. I copied this code exactly and nothing happened at all. Ideas?

[php]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option "MergedFB" "true"
 	Option "MonitorLayout" "LCD, CRT"
 	Option "CRT2Hsync" "30-81" 
 	Option "CRT2VRefresh" "50-75" 
 	Option "OverlayOnCRTC2" "true"
 	Option "CRT2Position" "RightOf"
 	Option "MetaModes" "1280x800-1280x1024" 
	Option "MergedXineramaCRT2IsScreen0" "false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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
EndSection[/PHP]

---

### Post by houseofmore on 2007-02-05
> **xr82 said:**
> Is there a way to set up the displays so that each one represents a different workspace?

BUMP!

---

### Post by Ryan Marcus on 2007-02-06
I'm trying to get dual monitors working, and I'm having some trouble.

I've got an IBM R40 with a VGA port and a HP L1706. I modified my xorg.conf file and rebooted. The boot screen (grub information and Ubuntu progress bar) both displayed on my laptop and my external HP LCD. However, at both the login screen and after login, the laptop screen went completely black and the external LCD worked as if it where the main display.

Here is my xorg.conf file:
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "MergedFB" "true" #Enable MergedFB function
 	Option "MonitorLayout" "LCD, TMDS" # Use LCD and CRT even if you have 2 LCD's or CRT's
 	Option "CRT2Hsync" "30-83" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
 	Option "CRT2VRefresh" "50-76" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
 	Option "OverlayOnCRTC2" "true"
 	Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor.
 	Option "MetaModes" "1280x768-1280x768" #Monitor Resolutions for Primary-Secondary monitors 
	Option "MergedXineramaCRT2IsScreen0" "false" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Thanks in advance!

---

### Post by filloy on 2007-02-07
Somebody should do an app for configuring MergedFB, Xinerama, BigDesktop and all...
I could do it, but i need like 3 years to learn how to, and then it will be too late :(


Anyway...im trying hard to get his dual monitor / XGL thing working...i dont know if i will be able to...ill let you know if i can do it...


(BTW: Thanks for the howto, its incredible...)

---

### Post by music_man_420 on 2007-02-09
I am trying to properly setup a desktop dual display system.  I have 2 Samsung SyncMaster 940BF monitors plugged into my ATi Radeon x800XL video card.  There is one querky feature of my setup; I have one DVI and one VGA connector rather then dual DVIs, this proved to be no trouble at all under windoze.  The ATi driver didn't work for me, but the radeon driver seems to be working fine and I see that there i at least one other poster here using the radeon driver rather then the ATi and he is having some sort of luck dualing, so I assume this is at most part of my problem.  ATM I haven't been able to get anywhere, it seems any attempt to use MergedFB results in my secoundary LCD (the one connected to the VGA) outputting only 800x600 res and my DVI won't display anything at all.

My config is currently as follows:

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
	Identifier	"ATI Technologies, Inc. R430 UM [Radeon X800 XL] (PCIe)"
	Driver		"radeon"
	BusID		"PCI:5:0:0"
	Option 	"MergedFB" "true" 
 	Option "MonitorLayout" "LCD, CRT" 
 	Option "CRT2Hsync" "30-65" 
 	Option "CRT2VRefresh" "50-75" 
 	Option "OverlayOnCRTC2" "true"
 	Option "CRT2Position" "LeftOf" 
 	Option "MetaModes" "1280x1024-1280x1024" 
	Option "MergedXineramaCRT2IsScreen0" "true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. R430 UM [Radeon X800 XL] (PCIe)"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

I have also tryed the following variants:

```
	#1

	Option 	"MergedFB" "true" 
 	Option "MonitorLayout" "LCD, CRT" 
 	Option "CRT2Hsync" "80" 
 	Option "CRT2VRefresh" "75" 
 	Option "OverlayOnCRTC2" "true"
 	Option "CRT2Position" "LeftOf" 
 	Option "MetaModes" "1280x1024-1280x1024" 
	Option "MergedXineramaCRT2IsScreen0" "true"

 #2

	Option 	"MergedFB" "true" 
 	Option "MonitorLayout" "LCD, CRT" 
 	Option "CRT2Hsync" "74.6" 
 	Option "CRT2VRefresh" "70" 
 	Option "OverlayOnCRTC2" "true"
 	Option "CRT2Position" "LeftOf" 
 	Option "MetaModes" "1280x1024-1280x1024" 
	Option "MergedXineramaCRT2IsScreen0" "true"

#3

	Option 	"MergedFB" "true" 
 	Option "MonitorLayout" "LCD, CRT" 
 	Option "CRT2Hsync" "30-65" 
 	Option "CRT2VRefresh" "50-75" 
 	Option "OverlayOnCRTC2" "true"
 	Option "CRT2Position" "RightOf" 
 	Option "MetaModes" "1280x1024-1280x1024" 
	Option "MergedXineramaCRT2IsScreen0" "false"

#4

	Option 	"MergedFB" "true" 
 	Option "MonitorLayout" "LCD, CRT" 
 	#Option "CRT2Hsync" "30-65" 
 	#Option "CRT2VRefresh" "50-75" 
 	Option "OverlayOnCRTC2" "true"
 	Option "CRT2Position" "LeftOf" 
 	Option "MetaModes" "1280x1024-1280x1024" 
	Option "MergedXineramaCRT2IsScreen0" "true"

etc

```

All of these and a few I have forgotten produce the same, aforementioned result.

---

### Post by Gromsempai on 2007-02-14
Hi, strange problem it's working but i have a 2560x1024 resolution **on each screen** like a spacy clone mode  (it's very very incomfortable) instead of a 2560x1024 big desktop.
My xorg.conf : 


> ......
......



Section "Monitor"
	Identifier  "SyncMaster"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "radeon"
	BusID       "PCI:3:0:0"
#       Option      "AccelMethod" "EXA"
	Option      "AGPMode"  "8"
	Option      "MergedFB"  "true"
	Option      "MonitorLayout"  "TMDS, CRT"
	Option      "CRT2Position"  "RightOf"
	Option      "MetaModes" "1280x1024-1280x1024"
	Option	    "MergedXineramaCRT2IsScreen0" "true"
	Option      "CRT2Hsync" "30-65"
	Option      "CRT2VRefresh" "50-75"
EndSection


Section "Screen"
	Identifier "Screen1"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth	24
		Modes	"1280x1024"
	EndSubSection
EndSection



Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Screen1"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection


Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	"render"	"enable"
	Option	"Composite"	"enable"
EndSection



---

### Post by Gromsempai on 2007-02-14
fount it =_=

> Section "Screen"
	Identifier "Screen1"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth	24
		**Virtual 2560 1024**
		Modes	"1280x1024" "1280x768" "800x600"
	EndSubSection
EndSection


---

### Post by ola on 2007-02-16
Hi,

Is there anybody that has successfully done the following on an ATI Mobility Radeon 7500 (ThinkPad T40):

* When the external monitor is plugged in use that (my resolution on this screen 1280x1024) and disable the laptop monitor
* When the external monitor is NOT plugged in use the laptop screen (resolution on this screen is 1024x768)

I gave it two days this fall without any success, but after reading so many success stories here it might be time to try again now ^_^ Any advices?

Best regards,

Ola

---

### Post by SourceV on 2007-02-18
I would appreciate some assistance in getting the dual screen work. I ave followed the instructions, bt could not make it work.

I have bought an Acer Aspire 5100. and I am trying to connect a second 19" Acer monitor AL1917.

I would like to set up the screens to work as follow: the laptop screen with 1280x800 resolution on the right and the 19" screen with 1280x1024 resolution on the left. the external screen should be the primary while it is connected and the laptop screen primary when the external screen is disconnected.

The problem seems to be that when I connect the external screen it becomes automatically the primary screen with the wrong resolution. the laptop screen remain blank the whole time (not black as it lits up but it remain blank.

Here is the configuration in the xorg.conf file:

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option "MergedFB" "true" #Enable MergedFB function 
	Option "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's 
	Option "CRT2Hsync" "30-80" #Horizontal Sync of the Monitor (check your monitor's manual for correct values) 
	Option "CRT2VRefresh" "55-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values) 
	Option "OverlayOnCRTC2" "true" 
	Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor. 
	Option "MetaModes" 1280x800"1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
	Option "MergedXineramaCRT2IsScreen0" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Gromsempai on 2007-02-22
Try this,

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option "MergedFB" "true" #Enable MergedFB function 
	Option "MonitorLayout" **"TMDS, CRT"** # Use TMDS and CRT even if you have 2 LCD's or CRT's 
	Option "CRT2Hsync" "30-80" #Horizontal Sync of the Monitor (check your monitor's manual for correct values) 
	Option "CRT2VRefresh" "55-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values) 
	Option "OverlayOnCRTC2" "true" 
	Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor. 
**	Option "MergedNonRectangular" "true"**
	**Option "MetaModes" "1280x800-1280x1024"** #Monitor Resolutions for Primary-Secondary monitors 
	Option "MergedXineramaCRT2IsScreen0" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
        **Virtual 2560 1024** ##or try with 2560 800 , i'm not sure with a non rectangular dual screen config
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Ansible on 2007-02-24
Ok, here's my device section, where I put the suggested Option config lines.  I now have video on both monitors, but it is the same desktop and not an expanded desktop; my 1920x1200 monitor shows the same thing as my 1440x900 laptop screen, both are at 1440x900 resolution.  Help!

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "MergedFB" "true" #Enable MergedFB function
	# Use LCD and CRT even if you have 2 LCD's or CRT's
	Option "MonitorLayout" "LCD, CRT" 
	#Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	Option "CRT2Hsync" "30-65" 
	#Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
	Option "CRT2VRefresh" "50-75" 
	Option "OverlayOnCRTC2" "true"
	#Physical location of your secondary monitor in relationship to your primary monitor.
	Option "CRT2Position" "LeftOf" 
	#Monitor Resolutions for Primary-Secondary monitors 
	Option "MetaModes" "1440x900-1920x1200" 
	#determines which screen is going to be the primary screen; value can be "true" or "false"
	Option "MergedXineramaCRT2IsScreen0" "false" 
EndSection

```

---

### Post by Gromsempai on 2007-02-24
Option "MergedFB" "true" #Enable MergedFB function <--- GOOD
	# Use LCD and CRT even if you have 2 LCD's or CRT's
	#Option "MonitorLayout" "LCD, CRT"  <--- USE ONLY IF THE X SERVER DON'T DETECT PROPERLY YOUR MONITORS TYPE. YOU SHOULD KNOW THE PRIMARY IS AUTOMATICLY ON THE DVI PORT AND THE SECOND ON THE VGA IF YOU HAVE DVI/VGA CARD

	#Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	Option "CRT2Hsync" "30-65" <--- GOOD IF IT'S ABOUT YOU'RE SECOND MONITOR
	#Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
	Option "CRT2VRefresh" "50-75" <--- GOOD IF IT'S ABOUT YOU'RE SECOND MONITOR
	Option "OverlayOnCRTC2" "true"
	#Physical location of your secondary monitor in relationship to your primary monitor.
	Option "CRT2Position" "LeftOf" 
	#Monitor Resolutions for Primary-Secondary monitors 
	Option "MetaModes" "1440x900-1920x1200" <----- DON'T FORGET PUT THE DVI FIRST
	#determines which screen is going to be the primary screen; value can be "true" or "false"
	#Option "MergedXineramaCRT2IsScreen0" "false"  <---- USELESS ON MERGEDFB, IT S FOR MERGEDXINERAMA

      ##you forget this :
      [B]Option "MergedNonRectangular" "true" <---- VERY IMPORTANT ON NON RECTANGULAR BIG DESKTOP
[/B]



EndSection

---

### Post by Ansible on 2007-02-24
Thanks, I tried that but no dice.  My device section looks like this now, but gives the same result:

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "MergedFB" "true" #Enable MergedFB function
	# Use LCD and CRT even if you have 2 LCD's or CRT's
	Option "MonitorLayout" "LCD, CRT" 
	#Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	Option "CRT2Hsync" "30-65" 
	#Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
	Option "CRT2VRefresh" "50-75" 
	Option "OverlayOnCRTC2" "true"
	#Physical location of your secondary monitor in relationship to your primary monitor.
	Option "CRT2Position" "LeftOf" 
	#Monitor Resolutions for Primary-Secondary monitors 
	Option "MetaModes" "1440x900-1920x1200" 
	#Option "MetaModes" "1920x1200-1440x900" 
	#determines which screen is going to be the primary screen; value can be "true" or "false"
	#Option "MergedXineramaCRT2IsScreen0" "false" 
	# VERY IMPORTANT ON NON RECTANGULAR BIG DESKTOP
	Option "MergedNonRectangular" "true" 
EndSection
```

 I wonder why that "MergedXineramaCRT2IsScreen0" is in the MergedFB how-to if it doesn't belong with MergedFB?  

The only other thing I've changed in the xorg.conf file was this section:

```
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection

```
Which I changed to look like this:
```

	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1920x1200"
	EndSubSection
```

This allowed me to reboot and change the resolution on my external monitor to 1920x1200.  At that time I was only able to see the external monitor.  Now, with the MergedFB changes above I can see both monitors, but they are both 1440x900 and both show the same thing.

I removed the 1920x1200 from the display subsection, above, on the chance that it was breaking something (according to this how-to you should start with a fresh xorg.conf)

---

### Post by Gromsempai on 2007-02-26
I said "Option "MonitorLayout" "LCD, CRT" " is useless, plus is not LCD but TMDS for LCD screen and LVDS for laptop. (cf. man radeon)

On a Laptop/Ext. Monitor configuration the laptop's screen is the primary screen so Option "MetaModes" "1440x900-1920x1200" is right. Test like that, with just the correction on MonitorLayout line.

otherwise i'm wondering if you should put radeon instead of ati on driver line and ```
SubSection "Display"
		Depth		24
		Modes		"1440x900" "1920x1200"
	EndSubSection
``` like that. Test with different Modes like just "1440x900" or 1920 first etc.

---

### Post by mtxf on 2007-03-09
hey, ive been trying to get this working on my dual-headed Radeon 9250 card in Ubuntu 6.10, but im having some problems

The card has a vga and dvi port, and if i dont turn MergedFB on both monitors work perfectly in clone mode. however when i added the mergedfb options to the device section in my xorg.conf the dvi screen (its a desktop lcd screen) no longer works, it goes blank and goes into standby mode.

From what i could gather from the log it wasnt detecting the resolution and refresh rates correctly for that monitor, so i tried to specify some values manually. This got it to at least turn on, and it somewhat works now... although all the graphics are garbled. It doesnt appear to redraw correctly, i can drag a window onto it and that window functions fine, yet it leaves a trail much like what happens when (ms) Windows freezes and doesnt repaint fast enough. Also the desktop background doesnt draw/refresh correctly either...

Here are my currect xorg.conf and Xlog

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
	Load	"dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID			"PCI:1:0:0"
	Option       	"AGPMode"     		  	"8"
	Option          	"XAANoOffscreenPixmaps"
	Option		"DRI"					"true"
	Option		"ColorTiling" 			"on"
	Option		"EnablePageFlip" 			"true"
	Option		"AccelMethod" 			"EXA"
	Option 		"RenderAccel" 			"true"
      Option  		"MergedFB"                    "true"
	Option		"MonitorLayout" 			"TMDS, CRT"
      Option 		"CRT2Position"                "LeftOf"
      Option  		"MetaModes"                   "1024x768-1024x768"
      Option  		"MergedXinerama"              "on"
      Option  		"MergedNonRectangular"        "true"
      Option 		"MergedXineramaCRT2IsScreen0"	"false"
EndSection

Section "Monitor"
	Identifier	"VM71RDA"
	Option		"DPMS"
	HorizSync	28-72		# These seem to allow the TMDS monitor on the DVI port to work
	VertRefresh	17-60		#
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Monitor		"VM71RDA"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Option          "AIGLX" "true"
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

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

Xorg.0.log is too large to paste, it is attached (sorry about the zip, but its larger than the max filesize allowed for txt files, and im posting this from my windows install)

I hope someone who knows their stuff can point me in the right direction here

I have managed to dig this page up on the wiki: [https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI)

Seems this might be causing my problems, however i am unable to follow the instructions provided; when i run sudo apt-get build-dep xserver-xorg-driver-ati, it says it cannot find the package. I have all the boxes checked on the Internet tab of the Software Sources dialog... are there other repositories i need to add?

Any help will be greatly appreciated!
thanks

---

### Post by Gromsempai on 2007-03-13
Did you read this how to and posts ??
In your xorg.conf you put on MergedFB and MergedXinerama !! You have to chose only one !!
MergednonRectangular is for non rectangular double screen, not your case, you have a double 1024-768 !!


Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID			"PCI:1:0:0"
	Option       	"AGPMode"     		  	"8"
	Option          	"XAANoOffscreenPixmaps"
	Option		"DRI"					"true"
	Option		"ColorTiling" 			"on"
	Option		"EnablePageFlip" 			"true"
#	Option		"AccelMethod" 			"EXA"
	Option 		"RenderAccel" 			"true"
      Option  		"MergedFB"                    "true"
	Option		"MonitorLayout" 			"TMDS, CRT"
      Option 		"CRT2Position"                "LeftOf"
      Option  		"MetaModes"                   "1024x768-1024x768"
EndSection


This is more correct.

---

### Post by mtxf on 2007-03-14
yeah, i did read this guide, what it and you suggest wont work for me... my lcd just doesnt recieve a signal.

I got the MergedXinema options from [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) (scroll to the [MergedFB]("https://help.ubuntu.com/community/RadeonDriver#head-793a669ccaf959871b32b81503e56817861c8c50") section)

---

### Post by houseofmore on 2007-03-15
I've got my readon 9500 using the open source drivers and mergedFB working great (two monitors).  Compiz runs, but the far right of the right monitor is "clipped".   See the attached screenshot.

Digging around, it looks like it may have something to do with the MAX_TEXTURE_SIZE... but not really sure.

Anyone have compiz or berly with MergedFB / Radeon?

---

### Post by mtxf on 2007-03-16
thats almost exactly like how the whole of my lcd looks (when it works at all)

if you sort it out, please post how :)

---

### Post by SGoodyer on 2007-03-20
I currently have 2 19" widescreen hooked up both set as 1440x900 in xorg.conf
My alt monitor though doesn't show correctly, its like half the screen

Possibly the H/V Sync but i set it correctly nothing changes, I also can take a screenshot and it registers  as 2880x900 but just getting monitor2 to show correctly.

Is there a command i can set refresh rate? like Option CRT2rfshrate" "75" ?

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
	Identifier	"ATI RADEON X800XT"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option "MergedFB" "true" #Enable MergedFB function
	Option "MonitorLayout" "LCD, CRT" 
	Option "CRT2Hsync" "28-72" 
	Option "CRT2VRefresh" "43-75" 
	 Option "OverlayOnCRTC2" "true"
	 Option "CRT2Position" "LeftOf"
	 Option "MetaModes" "1440x900-1440x900"
	Option "MergedXineramaCRT2IsScreen0" "false"
	Option "MergedNonRectangular" "false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X800XT"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
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

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

---

### Post by srouquette on 2007-03-23
I have a video projector Panasonic PT-AE500, and when I read xorg.log, it seems my projector doesn't send dcc information.
I googled a little bit and I found there was a patch in the SiS driver to fix that.

When I try to use MergedFB, my videoproj is blank.
my CRT is connected to the VGA output, and my videoproj is connected to the DVI output.

here is a part of my xorg.conf :

```

Section "Device"
	Identifier	"ATI RADEON 9700"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"false"
	Option "MergedFB" "true"
	Option "MonitorLayout" "LCD, CRT" 
	Option "CRT2Hsync" "30-70"
	Option "CRT2VRefresh" "60" 
	 Option "CRT2Position" "RightOf"
	 Option "MetaModes" "1600x1200-1280x720"
	Option "MergedNonRectangular" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON 9700"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x720" "1024x768"
	EndSubSection
EndSection

```

I tried some stuff with MonitorLayout, and I had a result with "CRT, LCD", my videoproj seemed to be my main screen in 1024x768, and my CRT was in clone mode.

is there a way to force the DVI output as a secondary screen and to force the resolution with mode lines ?
(CRT2ForceOn doesn't work, and I didn't try mode lines yet...)

I also have a warning in xorg's log, there's an undefined controller in PCI:1:0:1, is it my second output ?

---

### Post by jmattos on 2007-03-24
My configuration is as follows.

on the left, a dell 2001fp (secondary) and on the right a Dell 2405fpw (primary). I used the ubuntu-built in ATI Radeon Drivers (I have an ATI Radeon x1800).

when I restart xwindows, I have the same thing, which is the 2405 (24" wide monitor) looks fine, but I see the exact same stuff on the 2001fp (20" 4:3 secondary monitor) though on the secondary, the resolution is set to wide screen mode, meaning it scrolls around as I use the mouse

HELP!

I added the following to my xorg.conf
```

	# Added this this section from [http://www.ubuntuforums.org/showthread.php?p=1773710](http://www.ubuntuforums.org/showthread.php?p=1773710)
	Option "MergedFB" "true"
 	Option "MonitorLayout" "LCD, CRT" 
 	Option "CRT2Hsync" "31-80 # Got this from [http://support.dell.com/support/edocs/monitors/2001fp/EN/specs.htm](http://support.dell.com/support/edocs/monitors/2001fp/EN/specs.htm)
 	Option "CRT2VRefresh" "56-76" #Got this from [http://support.dell.com/support/edocs/monitors/2001fp/EN/specs.htm](http://support.dell.com/support/edocs/monitors/2001fp/EN/specs.htm)
 	Option "OverlayOnCRTC2" "true"
 	Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor.
 	Option "MetaModes" "1920x1200-1600x1200" #Monitor Resolutions for Primary-Secondary monitors 
	Option "MergedXineramaCRT2IsScreen0" "false" #determines which screen is going to be the primary screen; value can be "true" or "false"

```

---

### Post by jmattos on 2007-03-28
Anyone have any idea what im doing wrong?

---

### Post by BungaMan on 2007-04-03
That problem is addressed in this thread.  Try searching this thread on mergednonrectangular.

---

### Post by paulwill on 2007-04-04
Hi,

I'm using a Matrox G550 dual head gfx card with VGA & DVI outputs. I seem the have the same thing displayed on both monitors all the time. I have tried the Big Desktop solution & the MergedFB but nothing seems to change.

Any ideas?

---

### Post by krammer on 2007-04-15
I'm not sure if I should be using the MergedFB option, but I gave it a try with my Radeon X700 Pro.  I have a 17 Daewoo and I'm trying to get a dual onto my 20in Sony tv.  When trying this option, I just get a blank screen on my tv.  I can see that the option is enabled because I can drag the mouse off the screen...here is my xorg.conf:

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
	Identifier	"ATI RADEON X700"
	Driver		"ati"
	BusID		"PCI:2:0:0"
	Option "MergedFB" "true" #Enable MergedFB function
 	Option "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
 	Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
 	Option "OverlayOnCRTC2" "true"
 	Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor.
 	Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
	Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection


Section "Monitor"
	Identifier	"Daewoo"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X700"
	Monitor		"Daewoo"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x768" "1024x768" "800x600" "640x480"
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

Thanks to anyone who can help...

---

### Post by Angeluz on 2007-04-16
Xorg-radeon-Driverr, Feisty and 1680x1050 on a Widescreen-TFT, 1280x1024 on my 19"-CRT and it works perfectly. Thank you!

---

### Post by krammer on 2007-04-16
Is feisty known to have better support for dual monitor then edgy?

---

### Post by krammer on 2007-04-16
Ok so I finally got this working...this page really helped me out:

[http://www.darkartistry.com/content/view/74/41/](http://www.darkartistry.com/content/view/74/41/)

But there is another problem...I noticed when playing video clips, that it is very choppy.  Does anyone know how to fix this?  Let me know, thanks.

---

### Post by harty83 on 2007-04-24
I know that this is for the ati graphics card but I've used this post in part to get mergedfb set up with my intel card.

My xorg.conf is as follows:

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
# again, run the following command:I h
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

Section "ServerFlags"
       Option "AllowMouseOpenFail"
       Option "RandR" "on"
EndSection

Section "Module"
       Load "i2c"
       Load "GLcore"
       Load "bitmap"
       Load "ddc"
       Load "dbe"
       Load "dri"
       Load "extmod"
       Load "freetype"
       Load "glx"
       Load "int10"
       Load "type1"
       Load "vbe"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier				"Intel Mobile"
	Driver					"i810"
	BusID					"PCI:0:2:0"
      	Option  "DRI"                           "true"
      	Option  "MergedFB"                      "true"
       	Option  "MonitorLayout"                 "CRT,LFP"
       	Option  "SecondPosition"                "LeftOf"
       #Option  "MetaModes"                     "1024x768-1024x768"
	Option  "MetaModes"                     "1280x800-1280x1024"
       	Option  "SecondMonitorHorizSync"        "30-81"
       	Option  "SecondMonitorVertRefresh"      "56-76"
       	Option "MergedNonRectangular" 		"true"
EndSection

Section "Monitor"
	Identifier	"Laptop"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Mobile"
	Monitor		"Laptop"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
       Option "Composite" "Enable"
EndSection

```

I want my monitor resolution as 1280x1024 and my laptop res 1280x800.  The xorg file above gets mergefb working, but my both displays have a resolution of 1280x1024.  As you can see I have "MergedNonRectangular" set to true but it does not seem to have any affect.   Any ideas?

Thanks!
Alan

---

### Post by itsdaveperdue on 2007-04-25
Hiya  folks,

I've got an HP nx6125 laptop with the ATI 200M.  I've configured the MergedFB and it produces some weird results.  I get the exact same thing with Xinerama.  

The 2nd screen is blank, but on, and when I move my mouse cursor I get a box with colored lines.  It's kind of garbled, but a perfect box.

I have the sync set properly and other than that it seems to work okay, heh.  I read through this entire thread and I've been searching for hours...Any ideas?

---

### Post by joshkuo on 2007-04-25
I have followed this thread and tried a few setups, I think I am getting close, but I can't figure out what's going on here...

I have two 19" LCDs that have the same resolution (1280x1024), and an ATI x600 card.  This setup works fine under Windows XP.  I have installed Ubuntu Edgy on this machine (tried Feisty, but it won't install VMware, which I need for work, so I had to go back to Edgy).

I get a 1024x768 screen resolution on my first monitor, and a 1280x1024 resolution on my second monitor, and my mouse movement is weird on the first monitor (have a hard time clicking on the right placement). Here is a screenshot of my current desktop, the screen on the left is my first screen with a GAIM window maxed out.  The green areas are not visible on the monitor.  The second screen (the one on the right) fills the monitor, but has some green areas to the right side that is no visible.

Here is my xorg.conf.  Any help is appreciated.

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
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
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
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Mode2" "1280x1024"
	Option	    "ForceMonitors" "lvds,crt1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

---

### Post by gloomygod on 2007-05-05
Hi all.

I've tried many of the options in this post, and can't manage to get working my second screen.

My setup is:

Ati mobility Radeon 9000 64Mb, in a fujitsu-siemens 7830-D Laptopn.

I want to have the laptop lcd as the primary monitor, and another TFT19'' connected in the VGA connector of the laptop working as my second monitor.

My ***_initial xorg.conf_*** is detailed below. My current problem, is that when i start the laptop with the external monitor plugged in, both screens show me the boot linux screens, but when the X start, only the external monitor becomes active, and the laptop LCD remains black.

If i turn on the computer, with the external screen unplugged, the LCD works as usual. Then, once the X are fully started, and my desktop up and running, i connect the external screen, and i can see the same image in both monitors.

I've tried the options in the initial post, modifying the horzs and verts freqs, and tried the "virtual" tag in the screen section, and it does not work properly.

Anyone has a similar setup,  or an idea of what i'm doing wrong??

Thanks a lot.

Xorg.conf:

```
# xorg.conf (Xorg X Window System server configuration file)
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
# again, run the following commands as root:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum
#   dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/share/fonts/X11/CID"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
EndSection

Section "Module"
	Load	"dbe"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"vbe"


EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbVariant"	"es_ES@Euro"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	option		"SHMConfig"		"on"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [FireGL 9000]"
	Driver		"radeon"

	
	BusID	"PCI:1:0:0"

	##SETTINGS PARA AIGLX 
	Option		"XAANoOffscreenPixmaps" "true"
	Option		"DRI"	"true"

EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R250 Lf [FireGL 9000]"
	Monitor		"Monitor genérico"
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
	InputDevice	"Synaptics Touchpad"

	#SETTINGS PARA AIGLX
	Option		"AIGLX"	"true"

EndSection

Section "DRI"
	Mode	0666
EndSection

#SETTINGS PARA EXTENSIONES COMPOSITE(REQUERIDO PARA EL COMPIZ?)
Section "Extensions"
	Option "Composite" "Enable"
#	Option "RENDER" "Enable"
EndSection



```

---

### Post by Psicolonia on 2007-05-08
hi everyone, this should be easy for you!

I've got everything working fine (almost) my only problem is that my primaryscreen is not the Laptop LCD!

here's my device section:

```
Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option  "DRI"                           "true"
        Option  "MergedFB"                      "true"
        Option  "MonitorLayout"                 "CRT,LFP"
        Option  "SecondPosition"                "LeftOf"
        Option  "MetaModes"                     "1280x768-1024x768"
	Option  "MergedXineramaSecondIsScreen0" "true"
        Option  "SecondMonitorHorizSync"        "28-49"
        Option  "SecondMonitorVertRefresh"      "60-72"
        Option  "MergedNonRectangular"          "true"
EndSection
```

Everything is fine even the screen sizes: 1024 at the left and 1280 at the main screen. (wich is not...)

So basically i would like to make the laptop screen the main screen without changing anything else. By the way I'm treid false on MergedXinerama.

Addicional, anyone can tell me how to enable compiz like this? everything goes blank if I have compiz activated!

Thanks in advance!!

---

### Post by etnoy on 2007-05-15
This setup works with my old T30, giving impressive results with beryl 0.2.1 if I run single-screen. :) 
It also autodetects the monitors, starting either single- or dualheaded. MergedFB is truly great.
```

101 Section "Device"
102         Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
103         Driver          "radeon"
104         BusID           "PCI:1:0:0"
105         Option          "CRT2VRefresh" "30-82"
106         Option          "CRT2Hsync" "50-75"
107         Option          "XaaNoOffscreenPixmaps" "true"
108         Option          "CRT2Position"                  "LeftOf"
109         Option          "MergedXineramaCRT2IsScreen0" "false"
110         Option          "AGPMode" "4"
111         Option          "OverlayOnCRTC1"        "on"
112         Option          "OverlayOnCRTC2"        "on"
113         Option         "MetaModes"                     "1024x768-1280x1024"
114         Option         "MergedXinerama"                "on"
115         Option         "MergedNonRectangular"          "true"
116         Option           "DRI" "true"
117         BusID           "PCI:01:00:0"
118 EndSection
```

Note that MergedFB line and MonitorLayout are gone, radeon actually calculates this itself it seems. Easy!

Line numbers are atached, if you got questions, ask me!

---

### Post by eyemean on 2007-05-17
Thanx for that tip etnoy, i used it in my xorg and worked nicely.

Only problem i have now is that my cube isnt a cube anymore, lol, its got eight sides.
When i use the cube and change to different desktop each screen rotates independently.

Im sure im just missing a command of some sort, hope some1 can help me.  

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "MergedFB" "true"
  	Option "MonitorLayout" "CRT (TMDS), CRT"
  	Option "CRT2Hsync" "48.4-68.7"
  	Option "CRT2VRefresh" "60-85"
  	Option "OverlayOnCRTC2" "true"
  	Option "CRT2Position" "LeftOf"
  	Option "MetaModes" "1024x768-1024x768"
	Option "MergedXineramaCRT2IsScreen0" "true"
	Option "MergedNonRectangular" "true"
EndSection

Section "Monitor"
	Identifier	"DELL D1226H"
	Option		"DPMS"
	Horizsync    	28-64
    	Vertrefresh    	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"DELL D1226H"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection 

Thanx in advance.

---

### Post by FUbuf on 2007-05-17
> **xr82 said:**
> Is there a way to set up the displays so that each one represents a different workspace?

This is exactly what I would like to do! If someone knows how to setup this, I really would love it.

Problem without this option is that Gnome for some reason loves to open new windows to another screen which is behind me. And that's not too handy. It makes my neck hurt bad!

- Thanks!

---

### Post by eyemean on 2007-05-17
> 
Quote:
Originally Posted by xr82 View Post
Is there a way to set up the displays so that each one represents a different workspace?
This is exactly what I would like to do! If someone knows how to setup this, I really would love it.

Problem without this option is that Gnome for some reason loves to open new windows to another screen which is behind me. And that's not too handy. It makes my neck hurt bad!

- Thanks!

Im new to linux, but cant you just change which screen is set to  primary screen?

---

### Post by Halonut1 on 2007-05-21
Ok, i am using dapper on a dell Inspiron 600M with a mobileRADEON9000 graphics card, i followed the MergedFB tutorial and it still dont work, the only difference is that not my windows partition wont open(windows still runs, i just cant access the partition through linux, It used to show up as a unremovably icon on my desktop) now i get this when i try to acess it though computer

error: device /dev/hda1 is not removable

error: could not execute pmount



Here is my xorg.conf.


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
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
Option "MergedFB" "true" #Enable MergedFB function
  Option "MonitorLayout" "LVDS (TMDS), CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
  Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  Option "OverlayOnCRTC2" "true"
  Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
Horizsync    28-64 #You may wish to change the values to fit your specific monitor
    Vertrefresh    43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Rosenrot on 2007-05-21
-

---

### Post by Rosenrot on 2007-05-21
it has been about a year since ive set up dual monitors in linux and that was with a nvidia card using xinerama

but now i have an ati card that for some reason isn't working with xinerama, and with mergedFB all i get is 2 cloned screens with a 'virtual' physically missing second screen i can drag and drop to but not see

<a href="http://www.putfile.com/pic.php?img=5504351"><img src="http://img2.putfile.com/thumb/5/14017091152.jpg" alt="Click to enlarge"></a>

all i see is the left portion of the image on BOTH screens and the right screen is present as part of the desktop, but not physically present to me

i have tried 8 hours yesterday and 4 hours today trying to get this to work

any help would be most greatly appreciated

here is my current xorg.conf

```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
	Identifier	"ATI RADEON X850"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "MergedFB" "true" 
  	Option "MonitorLayout" "TMDS, CRT" 
  	Option "CRT2Hsync" "30-65" 
  	Option "CRT2VRefresh" "50-75" 
 	Option "OverlayOnCRTC2" "true"
  	Option "CRT2Position" "LeftOf"
  	Option "MetaModes" "1024x768-1024x768"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X850"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by vazcom on 2007-06-01
Hmmm, i have the Radeon 9000 PCI Dual VGA head card, and 2 - Hanns-G 19" wide screen LCDs

Currently both screens work great, only problem is they show the same thing!!!

When i followed the instructions posted above, both screens had half of them unreadable, i was able to go back into gedit and remove the 2 sections, which had things revert back to normal.

Both screens still showed identical information, only the right 1/2 of the screen was distorted beyond readablilty.

If anyone has any ideas, please let me know. If i can get this to work correctly, i plan on trying to get my company to abandon Windoze and make the switch to Ubuntu.

Thanks

---

### Post by Deathwish238 on 2007-06-06
It worked for me with a little bit of tweaking.  It would however only work when the VGA port was primary.  If the Laptop's LCD was primary the VGA port didn't seem to be active at all.

Here's the relevant parts of my xorg file:
Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "MergedFB" "true"
	  Option "MonitorLayout" "LVDS, CRT" 
	  Option "CRT2Hsync" "30-65" 
	  Option "CRT2VRefresh" "50-75" 
	  Option "OverlayOnCRTC2" "true"
	  Option "CRT2Position" "Clone"
	  Option "MetaModes" "1280x1024-1280x1024" 
	  Option "MergedXineramaCRT2IsScreen0" "false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

---

### Post by Deathwish238 on 2007-06-06
Now there's one more thing I'ld like to automate.  If I disconnect the external montior connected to the VGA port, I'ld like the resolution to change to 1680x1050 and the laptop's LCD to become primary.  Is this possible and if so how can I achieve this?

---

### Post by p388l3s on 2007-06-07
Truly inspirational, thanks alot for this guys, I now have a dual head mergedfb with TV working using the ati drivers

This helped a lot thanks :D

---

### Post by hrehf on 2007-06-08
All i was getting were two screens in clone mode, but after some experimentation, it looks like all you have to do is play with the MonitorLayout:


```

Option "MonitorLayout" "TDSM, CRT" #Gives me cloned screens
Option "MonitorLayout" "CRT, TDSM" #Gives me a correct left half on the second screen, but disables the primary screen.
Option "MonitorLayout" "CRT, CRT" #Works as expected for me, even though my primary screen is on the DVI out (but with a vga converter)

```

I didn't try out anymore combinations, but if you're having trouble, you might want to try combinations of those first.

The relevant parts of my xorg.conf:
```

Section "Device"
	Identifier	"ATI Radeon X800 (R430)"
	Driver		"ati"
	BusID		"PCI:1:0:0"

	#Option		"UseFBDev"	"true"

	#Enable MergedFB function
	Option "MergedFB" "true"

	# LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port
	Option "MonitorLayout" "CRT, CRT"

	#Monitor Resolutions for Primary-Secondary monitors 
	Option "MetaModes" "1024x768-1024x768"

	#Horizontal Sync of the 2nd Monitor
	#Option "CRT2Hsync" "30-65"
	#Vertical Refresh rate of the 2nd Monitor
	#Option "CRT2VRefresh" "56-81"
        Option          "CRT2VRefresh" "30-82"
        Option          "CRT2Hsync" "50-75"
#	Option  "SecondMonitorHorizSync"        "30-65"
#	Option  "SecondMonitorVertRefresh"      "56-76"

	Option "EnablePageFlip" "True"
	Option "AGPMode" "4"
	Option "AGPFastWrite" "True"

	Option "OverlayOnCRTC1" "true"
	Option "OverlayOnCRTC2" "true"
	#Physical location of your secondary monitor in relationship to your
	#primary monitor. LeftOf, RightOf, Above, Below, and Clone.
	Option "CRT2Position" "LeftOf"

	#"true" or "false"
	#Option "MergedXineramaCRT2IsScreen0" "false"

	#Option "MergedNonRectangular" "true"
	Option	"DRI"	"true"
EndSection

Section "Monitor"
	Identifier	"LG 500LC"
	Option		"DPMS"
#	HorizSync	27-86
#	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon X800 (R430)"
	Monitor		"LG 500LC"
	DefaultDepth	24

	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

---

### Post by FUbuf on 2007-06-11
> **p388l3s said:**
> Truly inspirational, thanks alot for this guys, I now have a dual head mergedfb with TV working using the ati drivers

Do you use Gnome? How did you solve problem of windows being opened to WRONG display. I find that very annoying and I haven't found any solution to fix that.

---

### Post by bohsocks on 2007-06-27
Hello.  I tried what was listed in the first post of this thread, and it worked fine.  I then wanted to tweak the resolution of the 2nd screen so I edited xorg.conf... when I reloaded X, my 2nd monitor is a test pattern.  When I turn the monitor off and on (via a PC to Video Component) I see my second workspace for a split second then it goes to a test pattern again.

What did I mess up on?   I mean, it worked the first time!

---

### Post by royg on 2007-06-30
> **Ziox said:**
> I may finally have found the answer to the primary monitor problem. Add this line to the "Device" Section:

Option "MergedXineramaCRT2IsScreen0" "boolean"

replace the boolean with either True or False. You just have to play around with the values.


While I am a complete new to Ubuntu and trying this on a age old laptop of mine, your posting did the trick on my old ATI Mobility Radeon 7500 M7 on my Compaq X1000. Xinerama doesn't seem to work at all. 

Thanks again for all the postings this really helped.

---

### Post by osfriese on 2007-07-02
Hi there,

I have an ATI Radeon X300 with dvi and srt.
at dvi is a SamsungSyncMaster (1650x1050,)
at crt is a ACER AL 1711 (1280x1024)

heres my xorg.conf:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
	Option		"XkbOptions"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"ATI RADEON X300"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option 		"MergedFB" 			"true"
  	Option 		"MonitorLayout" 		"TMDS, CRT"
	Option 		"CRT2Hsync" 			"30-90"
	Option 		"CRT2VRefresh" 			"50-60"
	Option 		"OverlayOnCRTC2" 		"true"
	Option 		"CRT2Position" 			"LeftOf"
	Option 		"MetaModes" 			"1680x1050-1280x1024"  
	Option 		"MergedXineramaCRT2IsScreen0" 	"false"
EndSection

Section "Monitor"
	Identifier	"Samsung Sync"
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X300"
	Monitor		"Samsung Sync"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Its seems to be all right, but my left (second) Monitor is black. Why?

---

### Post by lofgren on 2007-07-02
Love your work - up and running for me.

My config:
Feisty w/ Ati radeon 9250 Pro.
Benq FP91G+ on VGA (runs at 1280x1024) and Chimei T39D on DVI (1400x1050).

My only question is whether you can have two different resolutions in dual screen?
I have entered those values into xorg.conf and have ended up with 2680x1050 (so it has made the larger height the common value).

I haven't played with it further yet though and skipped pages 3-9 in this thread ;) 
So more reading for me and I dare say my question will already have been answered.

cheers!

---

### Post by lofgren on 2007-07-02
> **osfriese said:**
> Its seems to be all right, but my left (second) Monitor is black. Why?

At a guess I would say that it is your Sync Rate. Either that or like me, the resolution is being forced across both screens and your acer can't handle it.

You have entered your Samsung's sync values for both monitors. 
I did a quick search and couldn't find horizonal and vertical sync values for your monitor.
Perhaps find the correct values for the acer (hopefully in the manual) and enter them in the CRT2 options under your Device config.

luck!

---

### Post by don durito on 2007-07-09
Hi 
i am using a [ati mobility radeon 7000 on an thinkpad x31]("http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000"); And i would like to use this lcd as my primary monitor. as the secondary montior i have a belinea 10 60 75;

I am realy despratly trying to get dual head work but it won't.
there are two bugs which i am fighting:
1. if my secondary montior is connected and i start x my laptop lcd is just black;
2. if i start x before connecting my second montior and then connect my CRT i get clone mode

here's my xorg.conf: 
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
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
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"ati"

# options for increased performance	

	Option          "AGPMode"        "4"
        Option          "AccelMethod"    "XAA" 		#is supported for some of the cards with "experimental" 3d acceleration
        Option          "ColorTiling"    "on"
        Option          "EnablePageFlip" "true" 	#only works with accelmethod "XAA"
        Option          "AccelDFS"       "true" 	#seemed to speed things up using EXA acceleration
        Option          "TripleBuffer"   "true" 	#This *might* help if you use something like Beryl and have slow video playback.
        Option          "DynamicClocks" "on"    	#This is for laptop users, it saves energy when in battery mode.

[B]#options for dual-head via merge

	Option "MergedFB" "true" 			#Enable MergedFB function
  	Option "MonitorLayout" "LVDS (TMDS), CRT" 	# LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
 	Option "CRT2Hsync" "30-82" 			#Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  	Option "CRT2VRefresh" "50-110" 			#Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  	Option "OverlayOnCRTC2" "true"
  	Option "CRT2Position" "RightOf" 		#Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  	Option "MetaModes" "1024x768-1152x864" 		#Monitor Resolutions for Primary-Secondary monitors 
	#Option "MergedXineramaCRT2IsScreen0" "true" 		#determines which screen is going to be the primary screen; value can be "true" or "false"
	Option "MergedNonRectangular" "true"
[/B]	
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
# fuer mergefb eingefügt	
	Horizsync      30-82 				#You may wish to change the values to fit your specific monitor
    	Vertrefresh    50-110
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

would be nice if anyone can help me

thanks
don

---

### Post by taugenichts on 2007-07-09
hey!
i've read nearly every post in this threat. because of many backups, i don't know what to do with my xorg. I hope you do. So please, please give me some hints to get:
two 19" screens working. one is flatpanel, the other is an older one... and how should i get glx working?
here is the part of my xorg.conf: 

[PHP]Section "Device"
  identifier "ATI Technologies Inc RV350 AR [Radeon 9600]"
  boardname "ati"
  busid "PCI:1:0:0"
  driver "ati"
  screen 0
  option "MergedFB" "off"
EndSection

Section "Monitor"
  identifier "Overview"
  vendorname "Miro Computer Products AG"
  modelname "Miro miroD1568"
  HorizSync 31.5-68.0
  VertRefresh 50.0-100.0
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
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies Inc RV350 AR [Radeon 9600]"
  Monitor "Overview"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1400 1050
    modes "1280x1024@60" "1400x1050@60" "1280x960@60" "1152x864@75" "1024x768@43" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "device" #      
  identifier "device1"
  boardname "ati"
  busid "PCI:1:0:0"
  driver "ati"
  screen 1
  option "MergedFB" "off"
EndSection
Section "screen" #      
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
  SubSection "Display"
    depth 24
    modes "1280x1024@60" "1400x1050@60" "1280x960@60" "1600x1200@60" "1024x768@60" "1792x1344@60" "800x600@60" "1856x1392@60" "640x480@60" "1920x1440@60"
  EndSubSection
EndSection
Section "monitor" #      
  identifier "monitor1"
  vendorname "Generic"
  modelname "Flat Panel 1280x1024"
  HorizSync 31.5-90
  VertRefresh 60
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  gamma 1.0
EndSection

Section "Extensions"
  option "Composite" "Disable"
EndSection

Section "ServerFlags"
  option "AIGLX" "off"
  
EndSection[/PHP]

---

### Post by FUbuf on 2007-07-10
I got it working. But there are sill some issues as I mentioned. So it's not working as well as it should be. But both screens are able to show video and work pretty well. But I got problems with mouse pointer, I found out that it's "normal" that it doesn't work correctly. And also I got very big problem with windows opening to wrong screen which is very annoying. But no can do, no body knows how to fix that.

In my configuration another screen is 20.1" screen and other is flat screen television. So this is quite near what you're asking for.

HTH!

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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

	Identifier     "L1"
	Screen         0 "S1"
	Screen         1 "S2" RightOf "S1"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"

	# Option	"Xinerama" "on"

	# Option	"Clone" "on"

EndSection

Section "ServerFlags"

	# Option "Xinerama" "on"

EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
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
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "fi"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "false"
	Option	    "Buttons" "7"
	Option	    "ButtonMapping" "1 2 3 6 7"
EndSection

Section "Monitor"
	Identifier  "D1"
	Option	    "DPMS"
	VertRefresh 60
EndSection

Section "Monitor"
	Identifier  "D2"
	Option	    "DPMS"
	VertRefresh 50
EndSection

Section "Device"

	Identifier  "A1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
        Screen      0
	Option      "VideoOverlay" "on"
	Option      "OpenGLOverlay" "on"
EndSection

Section "Device"

	Identifier  "A2"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
        Screen      1
	Option      "VideoOverlay" "on"
	Option      "OpenGLOverlay" "on"
EndSection

Section "Screen"
	Identifier "S1"
	Device     "A1"
	Monitor    "D1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1600x1200"
	EndSubSection
EndSection

Section "Screen"
	Identifier "S2"
	Device     "A2"
	Monitor    "D2"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "800x600"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

---

### Post by Trevster on 2007-07-10
taugenichts,

Here is my xorg.conf file for you to look at. I have the same card as you. Just got it working with two CRT monitors.

I had beryl working using fglrx on one monitor but couldn't get it working on two, An error log directed me to this option. Working perfectly on two monitors now.

Thank you Ziox for sharing your knowledge.

```


Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
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
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "MergedFB" "true" #Enable MergedFB function
  Option "MonitorLayout" "CRT , CRT"
  Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  Option "CRT2VRefresh" "75-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  Option "OverlayOnCRTC2" "true"
  Option "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  Option "MetaModes" "1024x768-1024x768" #Monitor Resolutions for Primary-Secondary monitors 
#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	75-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by taugenichts on 2007-07-11
thank you travster for the answer! i'll test your config in a few minutes....

but what i don't understand: where should i write down e.g. the different hz-frequencies of the monitors?

---

### Post by taugenichts on 2007-07-12
ok... 
I tested your xorg. even if i took my own monitor-settings the result was, that each monitor got the same picture (cloned). this picture was in low resolution and the desktop scrolled vertical with the mouse, but on the left side of the screen it didn't work so it was impossible to get to the menus on the left top (system etc)...

so: where is my fault?

---

### Post by FUbuf on 2007-07-13
> **taugenichts said:**
> so: where is my fault?

DUNNO, but I think it's great that if I got it right, they know that this xorg configuration system sucks totally and they're going to fix it for future releases.

All this xorg stuff should be FAQ matter and much simpler than it is now.

I still need to fix "super key" feature. But I think I found enough information from this forum without asking questions.

I think that this xorg.conf is the worst part of Ubuntu at this moment. It took more time to fix than everything else gathered.

---

### Post by Ziox on 2007-07-13
> **FUbuf said:**
> DUNNO, but I think it's great that if I got it right, they know that this xorg configuration system sucks totally and they're going to fix it for future releases.

All this xorg stuff should be FAQ matter and much simpler than it is now.

I still need to fix "super key" feature. But I think I found enough information from this forum without asking questions.

I think that this xorg.conf is the worst part of Ubuntu at this moment. It took more time to fix than everything else gathered.

As far as I know, you are correct, they are planning a new Xorg editor in gutsy.  I just hope it's mature enough to be better than editing the xorg.conf file manually.

---

### Post by Trevster on 2007-07-13
taugenichts,

I don't know why it won't work for you. You do have the restricted ati driver removed?

I didn't play with the HZ freq, I  just used what I was using on the previous working single screen configuration.

---

### Post by Ziox on 2007-07-13
@taugenichts:

Sorry that I have neglected to answer the questions for a long time. Life is a roller coaster ride with now..ughhh...

Anyhoo, I've noticed that you are attempting Xinerama instead of MergedFB (which I don't recommend by the way). 

I would suggest to generate a clean (default) xorg.conf file:

```
sudo dpkg-reconfigure xserver-xorg
```

make sure, when prompted, to select "ati" as the driver.

Next follow my guide closely, and see what the results are.  I personally haven't used MergedFB in a long time, but I think I can still help you out.

Good luck!

---

### Post by don durito on 2007-07-19
Sorry for flooding this thread but i still haven't mergefb got to work.

First of all i am using a thinkpad x31 with an ati mobility readon m6 which is perfectly supported by the opensource ati driver. 
I d'like to use my thinkpad lcd as my primary and my belinea 10 60 75 crt as my secondray monitor. and i would like to use one virtual big screen, so i can move apps from one to another. 
But i can't get it work, i keep searching and searching but still no answer. 

right now i got 2 problems: 
1. if i plug in my external crt after starting x i got clonemode
2. if i plug in my external crt before starting x only the crt works. But the crt uses the resolution of my lcd so i got a blank lcd and 1024x768 on my crt.

here's my xorg.conf
```
 # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
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
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"ati"
	Option          "AGPMode"        "4"
        Option          "AccelMethod"    "XAA" #is supported for some of the cards with "experimental" 3d acceleration
        Option          "ColorTiling"    "on"
       	Option          "EnablePageFlip" "true" #only works with accelmethod "XAA"
       #Option          "AccelDFS"       "true" #seemed to speed things up using EXA acceleration
       #Option          "TripleBuffer"   "true" #This *might* help if you use something like Beryl and have slow video playback.
        Option          "DynamicClocks" "on"    #This is for laptop users, it saves energy when in battery mode.
[B]
# options for mergefb

	Option "MergedFB" "true" 		#Enable MergedFB function
 	Option "MonitorLayout" "LCD, CRT" 	# Use LCD and CRT even if you have 2 LCD's or CRT's
 	Option "CRT2Hsync" "30-98" 		#Horizontal Sync of the Monitor (check your monitor's manual for correct values)
 	Option "CRT2VRefresh" "50-160" 		#Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
 	Option "OverlayOnCRTC2" "true"
 	Option "CRT2Position" "RightOf" 	#Physical location of your secondary monitor in relationship to your primary monitor.
 	Option "MetaModes" "1024x768-1152x864" 	#Monitor Resolutions for Primary-Secondary monitors
[/B]
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Standardbildschirm"
	DefaultDepth	16

	
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```


any help would be appriciated and ones again sorry for flooding this great thread

yours 
don

---

### Post by james.wilde on 2007-08-01
Thanks, Ziox, for taking the trouble to document the four methods of getting dual screens working.  I have a Matrox G450 so only two are relevant for me, Xinerama and MergedFB.  I've finally got Xinerama working (but couldn't see how to delete this message in Merged FB and move it to Xinerama).

Incidentally I couldn't get dpkg-reconfigure xserver-xorg to work.  It hung during the postinst phase.  However, I had a copy of the original xorg.conf from installation to fall back on.

TIA

James

---

### Post by therudle on 2007-08-06
Nevermind.

---

### Post by amir1 on 2007-08-07
Hi... 

i am new to ubuntu and linux in general and i have problem connecting my second monitor.
primary monitor a ViewSonic VG191b
secondary monitor Dell M780 15"

what i know from the system after running lspci
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]


> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
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
	Identifier	"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

after adding the following to Device
Option "MergedFB" "true" #Enable MergedFB function
  Option "MonitorLayout" "LVDS (TMDS), CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
  Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  Option "OverlayOnCRTC2" "true"
  Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"

nothing changed

can anyone help me
thank you 
:confused:

---

### Post by asgardfleet on 2007-08-07
Hey,

Thanks for the info but unfortunately no good for me unless I have something wrong.

I am running a Radeon Mobility 9000 (laptop) and attempting to span to external monitor

Mobility - 1024x768
External - 1280x1024

All I can get is both monitors working - but not spanning and the external is only at 1024x768.

I have tried with ati/radeon driver and no difference.

Any ideas?

Here is my xorg.conf (appropriate info):

```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"

Option "MergedFB" "true" #Enable MergedFB function
  Option "MonitorLayout" "LVDS (TMDS), CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
  #Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  #Option "CRT2VRefresh" "50-65" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  Option "OverlayOnCRTC2" "true"
  Option "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  Option "MetaModes" "1024x768-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
#Option "MergedXineramaCRT2IsScreen0" "false" #determines which screen is going to be the primary screen; value can be "true" or "false"
Option "MergedNonRectangular" "true"

EndSection
```

Thanks

---

### Post by AxelBlade on 2007-08-15
> **houseofmore said:**
> I've got my readon 9500 using the open source drivers and mergedFB working great (two monitors).  Compiz runs, but the far right of the right monitor is "clipped".   See the attached screenshot.

Digging around, it looks like it may have something to do with the MAX_TEXTURE_SIZE... but not really sure.

Anyone have compiz or berly with MergedFB / Radeon?

This is happening with me too,but I have the X700 series, any body have found a solution to this problem. I tried every possible solution but no luck.

10x alot

AxelBlade

---

### Post by Haze1979 on 2007-08-15
> **AxelBlade said:**
> This is happening with me too,but I have the X700 series, any body have found a solution to this problem. I tried every possible solution but no luck.

10x alot

AxelBlade

I'm working on this too with my Radeon 9600, no luck as of yet. This subject deserves its own thread IMHO. Anyone noticed that the "rain effect" (shift-F9) renders ok when a window is placed inside the area, but not outside the window, even during the cube switch. Amazing! Opacity doesn't work however in this area. Could this be hardware limits?

---

### Post by zer0efx on 2007-08-22
Ok... I got it working, but the second monitors refresh rate is terrible. really blurry.
Any way to fix this?
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
	Identifier	"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option "MergedFB" "true" #Enable MergedFB function
  Option "MonitorLayout" "TMDS , CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
  Option "CRT2Hsync" "24-80" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  Option "CRT2VRefresh" "56-60" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  Option "OverlayOnCRTC2" "true"
  Option "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  Option "MetaModes" "1440x900-1440x900" #Monitor Resolutions for Primary-Secondary monitors 
#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"AL1917W"
	Option		"DPMS"
	HorizSync	24-80
	VertRefresh	56-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor		"AL1917W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by FXFman1209 on 2007-09-01
Okay, I have completed the steps (by copying EXACTLY what you said to copy to xorg.conf), but my second monitor is just a clone of the first monitor. I think I might have set it up awhile ago so that, if I ever needed to plug my laptop into a projector, it would copy.

Can anyone please help??

---

### Post by J_Palito on 2007-09-13
Hi everyone

I have a small problem...
I have a setup made of an AGP matrox G550 Dualhead and a ATI 3d rage 128 (which I could exchange for an s3 trio 64).

i wanted to have dual head using the matrox (one 19" TFT primary and a 15" CRT secondary) and use the TV out from the ATI (pal).

is there any way to achieve this?

I would be happy too if i used instead, the tv out from the G500 and the secondary CRT in the ATI or S3, whichever is the simpler.

here's my actual (and not working) xorg.conf:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"mga"
	Load	"r128"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
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
	Driver		"mga"
	BusID		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"ATI Rage 128"
	Driver      "r128"
	BusID      "PCI:00:0d.0"
EndSection

Section "Monitor"
	Identifier	"HP w19b/w19e"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"HP d4830a"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"HP w19b/w19e"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Secondary Screen"
	Device		"ATI Rage 128"
	Monitor		"HP d4830a"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
option "Xinerama" "true"
EndSection
```

thanks in advance

---

### Post by senor_smile on 2007-09-24
> **itsdaveperdue said:**
> Hiya  folks,

I've got an HP nx6125 laptop with the ATI 200M.  I've configured the MergedFB and it produces some weird results.  I get the exact same thing with Xinerama.  

The 2nd screen is blank, but on, and when I move my mouse cursor I get a box with colored lines.  It's kind of garbled, but a perfect box.

I have the sync set properly and other than that it seems to work okay, heh.  I read through this entire thread and I've been searching for hours...Any ideas?

I have the exact same problem.  I have an HP dv5000 series laptop with ATI radeon express 200M Graphics.  My main LCD(built in) monitor displays fine, but the 17" monitor attached displays dark lines, and when I put the mouse over there there's a small box that follows where the mouse would be.  

Anyone know what the problem is?

---

### Post by rampage355 on 2007-09-25
I have a ati 9600pro 256mb i can install the drivers per the forum with no problem.
I have one x2gen 17" wide panel lcd and a sony 17" regular lcd
Two problems that I have are it i reboot the screen has changed resolution and the mouse is out of position if that makes sense, meaning were the mouse is, is not where it clicks. The second problem is that no matter what i put the the config file it never works.


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "X2gen"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ati 9600"
	Driver      "fglrx"
	VideoRam    262144
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:3:0:0"
	Option "MergedFB" "true" #Enable MergedFB function
  	Option "MonitorLayout" "LVDS (TMDS), CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
  	Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  	Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  	Option "OverlayOnCRTC2" "true"
  	Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  	Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
	#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ati 9600"
	Monitor    "X2gen"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1440x900" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1440x900" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1440x900" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1440x900" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1440x900" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1440x900" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "disable"
EndSection

Any help would be much appreciated

---

### Post by bnollar on 2007-10-19
I am using an IBM Thinkpad A31 with a ATI Radeon Mobility 7500 graphics card, vga output and a SyncMaster 755df Monitor and having trouble getting Dual Monitor support to work.  I am getting identical output on both the laptop LCD and the Monitor.  I've attached my xorg.conf.  Any help would be appreciated.

Thanks.

---

### Post by worldwidemv on 2007-10-22
@rampage355 MergedFB is available only with the free radeon driver. search dualhead and you will find a way with fglrx.

@bnollar Ubuntu 7.10 comes with a new X.org and this seems to cause the problems because of randr support. I managed to get dualhead partly working. You have to set up your xorg.config with a virtual option and then use xrandr or grandr to set up dualhead. See [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)

However this is not the best solution but I would let you know that the problems you have applying the HowTos available are because of a new  X.org in ubuntu.

---

### Post by draven on 2007-10-23
I have a Dell ATI 102-A924 which is a single DVI that supposedly supports dual head via Y-cable. Does anyone know if this method in this thread will work with this? I don't understand how to properly identify the two interfaces from one cable in xorg.conf..

My proposed setup is a 19" widescreen Dell monitor (1440x900) and a Samsung 17" (1280x1024).

---

### Post by 186000MiPerSec on 2007-10-25
SB just fine- I have put in a bunch in such various configs.(They seem 2 B fine w/no fan.)

---

### Post by pneaveill on 2007-10-26
Not wanting to cross-post/dual post (uncertain what to call it), but dealing with matrox g450 dual vga system not working properly also.

[edit]
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
[/edit]

---

### Post by ClownyShoes on 2007-11-07
Hi, 
I'm on Gutsy PPC64, running on Apple G5 with ATI Radeon 9650 dual head.

I'm having trouble getting my dual head ATI card to display one large desktop.
I can get it to clone the screen using the Screens and Graphics utility.
It doesn't show both screens/monitors in the setup panels - but when I quit the utility, my second monitor starts up - but is a clone of the first monitor.

I have tried pretty much everything, following all the xorg.conf edits. Most just crash X and I'm presented with two black screens and have to replace my backup xorg.conf and reboot to get the GUI back.

The only edit that doesn't crash X is this mergedFB method - but it also doesn't give me two monitors - right one iis always powered off (no signal) and black.

Here is my .conf file contents.
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:lwin_switch"
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
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:240:16:0"
	Option		"UseFBDev"		"true"
Option "MergedFB" "true" #Enable MergedFB function
Option "MonitorLayout" "TMDS, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
Option "OverlayOnCRTC2" "true"
Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor.
Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors
Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false
EndSection

Section "Monitor"
	Identifier	"BenQ FP91E"
	Option		"DPMS"
	HorizSync	31-83
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"BenQ FP91E"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1368x1094" "1280x1024" "1272x1017" "1024x768" "880x660" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1368x1094" "1280x1024" "1272x1017" "1024x768" "880x660" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1368x1094" "1280x1024" "1272x1017" "1024x768" "880x660" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1368x1094" "1280x1024" "1272x1017" "1024x768" "880x660" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1368x1094" "1280x1024" "1272x1017" "1024x768" "880x660" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1368x1094" "1280x1024" "1272x1017" "1024x768" "880x660" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Any help appreciated.
Clowny

---

### Post by oswaldkelso on 2007-11-09
> **ClownyShoes said:**
> Hi, 
I'm on Gutsy PPC64, running on Apple G5 with ATI Radeon 9650 dual head.

I'm having trouble getting my dual head ATI card to display one large desktop.
I can get it to clone the screen using the Screens and Graphics utility.
It doesn't show both screens/monitors in the setup panels - but when I quit the utility, my second monitor starts up - but is a clone of the first monitor.

I have tried pretty much everything, following all the xorg.conf edits. Most just crash X and I'm presented with two black screens and have to replace my backup xorg.conf and reboot to get the GUI back.

The only edit that doesn't crash X is this mergedFB method - but it also doesn't give me two monitors - right one iis always powered off (no signal) and black.

Clowny

Hi Clownyshoes did your cloning work? I have just setup my g4 867 with dual screens as one big monitor. I have an ati 9800pro card  and a different pair of monitors but here's my xorg.conf.

---

### Post by ClownyShoes on 2007-11-09
wow - thanks oswaldkelso.
I did see another post of yours with a config file - I tried your techniques but didn't get anywhere at the time. I think I need to start with a blank slate.

Cloning went well, thanks for your advice on that.
I ended up booting my G5 into Target Disk mode and cloning over FW.
All went smooth.


I successfully got my G4 867 up and running with Edgy (so far)
I was having problems and narrowed it down to kernel versions.

So far...  I have discovered that 2.6.12-9-powerpc  and 2.6.17-12-powerpc are the only two kernel versions that I can get to boot on the G4 867.

Once again - thanks very much for your help.
Clowny

---

### Post by ClownyShoes on 2007-11-09
Hmmmm....
well, I still can't get this to work.
I just get two black screens.
I re-ran the graphics detection to generate a clean file.
Made my changes - as per the above suggestion by oswaldkelso.

Here is my xorg.conf 
```

a# xorg.conf (xorg X Window System server configuration file)
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"macintosh"
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
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]0"
	Driver		"ati"
	BusID		"PCI:240:16:0"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]1"
	Driver		"ati"
	BusID		"PCI:240:16:0"
EndSection


Section "Monitor"
	Identifier	"BenQ FP91E-0"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier	"BenQ FP91E-1"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]0"
	Monitor		"BenQ FP91E-0"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]1"
	Monitor		"BenQ FP91E-1"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier 	"Mulihead Layout"
	Screen	0  	"Screen0" LeftOf "Screen1"
    	Screen	1  	"Screen1" RightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option 		"Xinerama" "on"
    	Option      "Clone" "off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by ClownyShoes on 2007-11-09
Hmmm . . .  perplex-o-rama

If I comment out the "Xinerama" "on" or "true"  option - I get the main screen back - but still no second monitor.
Maybe it's just not gunna work with Xinerama ???

I know I shouldn't be on about that since this is the MergedFB thread - but I had the same results with that method - black second screen.

Any guru's out there ??

regards
Clowny

---

### Post by oswaldkelso on 2007-11-09
> **ClownyShoes said:**
> Hmmm . . .  perplex-o-rama

If I comment out the "Xinerama" "on" or "true"  option - I get the main screen back - but still no second monitor.
Maybe it's just not gunna work with Xinerama ???

I know I shouldn't be on about that since this is the MergedFB thread - but I had the same results with that method - black second screen.

Any guru's out there ??

regards
Clowny

I'm no guru but if you want to risk it you can try this one. But Im running debian and your running ubuntu. so there may be incompatabilities. 

If it all goes bottom up you'll just have to follow my ["How to install debian on ppc post" ]("http://www.my2bits.org/?p=76")  :)

---

### Post by ClownyShoes on 2007-11-10
thanks oswaldkelso - your modifications worked in debian.
now have large desktop. cool

---

### Post by oswaldkelso on 2007-11-10
> **ClownyShoes said:**
> thanks oswaldkelso - your modifications worked in debian.
now have large desktop. cool

Great!:lolflag::guitar::popcorn::KS

---

### Post by xlr8ed on 2007-11-16
Ran through the instructions and have ended up with dual monitors displaying the same exact thing (with proper resolution), any help would be very appreciated. 

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

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "auto"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7 4 5 6"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "MergedFB" "true" #Enable MergedFB function
        Option          "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
        Option          "OverlayOnCRTC2" "true"
        Option          "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monito
r.
        Option          "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
        Option          "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can b
e "true" or "false
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

---

### Post by pneaveill on 2007-11-19
> **pneaveill said:**
> Not wanting to cross-post/dual post (uncertain what to call it), but dealing with matrox g450 dual vga system not working properly also.

[edit]
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
[/edit]

Due to some creativity and ingenuity, I did a google search and found this site [http://matrox.tuxx-home.at/viewtopic.php?p=2799#2799](http://matrox.tuxx-home.at/viewtopic.php?p=2799#2799)
 which solved my matrox problems and I now have widescreen.:guitar:

Hope this helps someone else.:popcorn:

---

### Post by cpricejones on 2007-11-19
> **xlr8ed said:**
> Ran through the instructions and have ended up with dual monitors displaying the same exact thing (with proper resolution), any help would be very appreciated. 

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

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "auto"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7 4 5 6"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "MergedFB" "true" #Enable MergedFB function
        Option          "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
        Option          "OverlayOnCRTC2" "true"
        Option          "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monito
r.
        Option          "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
        Option          "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can b
e "true" or "false
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

i am getting this same issue, and i will see if i can solve it later today, so maybe i'll be able to help. post your solution if you come across anything too!

cheers,
cpj:)

---

### Post by pneaveill on 2007-11-23
> **cpricejones said:**
> 
```
 
Section "Device"
        Identifier      "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
       ** [COLOR=Blue]Option          "MergedFB" "true" #Enable MergedFB function[/COLOR]**
        Option          "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
        Option          "OverlayOnCRTC2" "true"
        Option          "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monito
r.
        Option          "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
        [B][COLOR=Blue]Option          "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can b
e "true" or "false[/COLOR][/B]
```
EndSectioni am getting this same issue, and i will see if i can solve it later today, so maybe i'll be able to help. post your solution if you come across anything too!

cheers,
cpj:)

I am still a newb at the dual monitor thing/ X11 thing, but it looks like you are attempting to load both mergedFB and xinerama at the same time (which, I understand, is a major taboo). IF I missed something, please let me know, as I want to learn on this too.

---

### Post by stubbs on 2008-01-26
Yeah that threw me off at first too pneaveill, but on the second page of posts Ziox explains that it is used to deal with a primary monitor problem.

I am also having the cloned monitor problem.

```

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

Section "Device"
	Identifier	"Failsafe Device"
	#Boardname	"vesa"
	#Busid		"PCI:1:7:0"
	Driver		"ati"
	
	Option	"MergedFB"	"true"
	Option	"MonitorLayout"	"LCD, CRT"
	#Option	"CRT2Hsync"	"30-82"
	#Option	"CRT2VRefresh"	"50-85"
	Option	"OverlayOnCRTC2" "true"
	Option	"CRT2Position"	"LeftOf"
	#Option	"MetaModes"	"1024x768-1024x768"
	Option	"MetaModes"	"1280x1024-1280x1024"
	Option	"MergedXineramaCRT2IsScreen0" "true"
	Option	"MergedNonRectangular"	"true"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"ViewSonic"
	Modelname	"ViewSonic VP191b"
	Option		"DPMS"
	Horizsync	30-82
	Vertrefresh	50-85
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
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"800x600@85"	"800x600@60"	"800x600@75"	"832x624@75"	"800x600@72"	"1024x768@85"	"800x600@56"	"1024x768@75"	"640x480@85"	"1024x768@70"	"640x480@75"	"1024x768@60"	"640x480@72"	"1152x864@75"	"640x480@60"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "ServerFlags"
EndSection

```

No idea where to go from here

---

### Post by miesnerd on 2008-02-15
Hey guys-
Tried to get this to work. 
My setup is this:
Radeon X1250 card; attached to the HDMI is a 19" widescreen. Resoltuion at 1440 x 900.
On the VGA is a 19" (not widescreen) , resoltuion either 1280x1024 or something similar.
I thought I had set it up so they both would work, but then when i plugged the vga in, the vga turned on and the HDMI turned off. Maybe I need a different line of code since these will be  at different resolutions?
Please help.

Here's the xorg.conf:

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
	Identifier	"Radeon X1250"
	Driver		"vesa"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
Option "MergedFB" "true" #Enable MergedFB function
  Option "MonitorLayout" "LVDS (TMDS), CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
  Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  Option "OverlayOnCRTC2" "true"
  Option "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"VA1912wSERIE"
	Option		"DPMS"
	Horizsync    28-64 	#You may wish to change the values to fit your specific monitor
    	Vertrefresh    43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon X1250"
	Monitor		"VA1912wSERIE"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
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

### Post by Lderan on 2008-02-25
I have 2 LCD displays, my 2nd monitor is through a dvi port with a dvi to vga converter.
The 2nd monitor is over bright and is a clone of the main monitor.
What am I doing wrong? 

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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"XkbLayout"	"gb"
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
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"

	Option "MergedFB" "true" #Enable MergedFB function
	  Option "MonitorLayout" "TMDS, CRT" 
	  Option "OverlayOnCRTC2" "true"
	  Option "CRT2Position" "LeftOf"
	  Option "MetaModes" "1280x1024-1280x1024"
          Option "MergedXineramaCRT2IsScreen0" "true"

EndSection

Section "Monitor"
	Identifier	"H750"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-77
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor		"H750"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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
```

---

### Post by bantam59 on 2008-02-26
> **Ziox said:**
> [FONT=Verdana]**[SIZE=4]Dual Monitor Support With MergedFB[/SIZE]**

[/FONT]          [LEFT][FONT=Verdana]The following attempts to enable Dual Monitor support by activating the MergedFB function that is implemented within the recent Xorg's open-source 'radeon' or 'mga' graphics driver.
[/FONT] [/LEFT]
        [LEFT][FONT=Verdana]**[SIZE=3]System Requirements:[/SIZE]**[/FONT][/LEFT]
    [LEFT][FONT=Verdana]ONE Dual-Output ATI (or Matrox Graphics card <= unsure, since I have never tested it before).[/FONT][/LEFT]
    [LEFT][FONT=Verdana]A recent version of the free Xorg, **WITHOUT **any binary graphics driver installed.
[/FONT] [/LEFT]
        [LEFT][FONT=Verdana][B]Let's get started!!!

[/B][/FONT][/LEFT]
    [LEFT][FONT=Verdana]***[COLOR=Red]1. Open up Xorg.conf using ONE of the following commands:[/COLOR]***[/FONT][/LEFT]
        [LEFT][FONT=Verdana]Gnome (Ubuntu):[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
gksudo gedit /etc/X11/xorg.conf
```[/FONT][/LEFT]
    [LEFT][FONT=Verdana]KDE (Kubuntu):[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
kdesu kate /etc/X11/xorg.conf
```[/FONT][/LEFT]
    [LEFT][FONT=Verdana]Xfce4 (Xubuntu):[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
gksudo mousepad /etc/X11/xorg.conf
```[/FONT][/LEFT]
    [LEFT][FONT=Verdana]Command-Line Based:[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
sudo nano /etc/X11/xorg.conf
```[/FONT][/LEFT]
        [LEFT][FONT=Verdana]***[COLOR=Red]2. This is about the simplest HowTo, simply copy the following lines to your "Device" Section:[/COLOR]***[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
**Option "MergedFB" "true" **#Enable MergedFB function
**  Option "MonitorLayout" "LVDS (TMDS), CRT" **# LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port **NOT MONITOR TYPE!**
**  Option "CRT2Hsync" "30-65" **#Horizontal Sync of the Monitor (check your monitor's manual for correct values)
**  Option "CRT2VRefresh" "50-75"** #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
**  Option "OverlayOnCRTC2" "true"**
**  Option "CRT2Position" "LeftOf" **#Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
**  Option "MetaModes" "1280x1024-1280x1024"** #Monitor Resolutions for Primary-Secondary monitors 
#**Option "MergedXineramaCRT2IsScreen0" "true" **#determines which screen is going to be the primary screen; value can be "true" or "false"
```[/FONT][/LEFT]
        [LEFT][FONT=Verdana][COLOR=Red][I][B]3. Next, go to the "Monitor" Section and add the following
[/B][/I][/COLOR]```
**Horizsync    28-64** #You may wish to change the values to fit your specific monitor
    **Vertrefresh    43-60**
```[/FONT][FONT=Verdana][COLOR=Red][I][B]
Save the file, and restarted X (ctrl+alt+backspace), or reboot.

[/B][/I][/COLOR][/FONT][/LEFT]
        [LEFT][FONT=Verdana]**Now Dual Monitor support should be enabled, if not please post your problem.**[/FONT][/LEFT]

Could you be a little more specific as to WHICH monitor these settings apply to?
are these settings for BOTH monitors or just the monitor i am adding?
do i leave the CURRENT configuration and just ADD this and edit it according to the monitor i am going to add?
im a little confused, as i am currently using xinerama but i would like the 3d for BOTH monitors not just 1
sorry if this sounds ridiculous, but im just a n00b.
Also when you say not to have any binary drivers installed do you mean Proprietary drivers?
im using an ATI radeon x600 dual head card and i currently have the ATI Proprietary drivers installed

---

### Post by bantam59 on 2008-02-26
> **Ziox said:**
> [FONT=Verdana]**[SIZE=4]Dual Monitor Support With MergedFB[/SIZE]**

[/FONT]          [LEFT][FONT=Verdana]The following attempts to enable Dual Monitor support by activating the MergedFB function that is implemented within the recent Xorg's open-source 'radeon' or 'mga' graphics driver.
[/FONT] [/LEFT]
        [LEFT][FONT=Verdana]**[SIZE=3]System Requirements:[/SIZE]**[/FONT][/LEFT]
    [LEFT][FONT=Verdana]ONE Dual-Output ATI (or Matrox Graphics card <= unsure, since I have never tested it before).[/FONT][/LEFT]
    [LEFT][FONT=Verdana]A recent version of the free Xorg, **WITHOUT **any binary graphics driver installed.
[/FONT] [/LEFT]
        [LEFT][FONT=Verdana][B]Let's get started!!!

[/B][/FONT][/LEFT]
    [LEFT][FONT=Verdana]***[COLOR=Red]1. Open up Xorg.conf using ONE of the following commands:[/COLOR]***[/FONT][/LEFT]
        [LEFT][FONT=Verdana]Gnome (Ubuntu):[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
gksudo gedit /etc/X11/xorg.conf
```[/FONT][/LEFT]
    [LEFT][FONT=Verdana]KDE (Kubuntu):[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
kdesu kate /etc/X11/xorg.conf
```[/FONT][/LEFT]
    [LEFT][FONT=Verdana]Xfce4 (Xubuntu):[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
gksudo mousepad /etc/X11/xorg.conf
```[/FONT][/LEFT]
    [LEFT][FONT=Verdana]Command-Line Based:[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
sudo nano /etc/X11/xorg.conf
```[/FONT][/LEFT]
        [LEFT][FONT=Verdana]***[COLOR=Red]2. This is about the simplest HowTo, simply copy the following lines to your "Device" Section:[/COLOR]***[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
**Option "MergedFB" "true" **#Enable MergedFB function
**  Option "MonitorLayout" "LVDS (TMDS), CRT" **# LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port **NOT MONITOR TYPE!**
**  Option "CRT2Hsync" "30-65" **#Horizontal Sync of the Monitor (check your monitor's manual for correct values)
**  Option "CRT2VRefresh" "50-75"** #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
**  Option "OverlayOnCRTC2" "true"**
**  Option "CRT2Position" "LeftOf" **#Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
**  Option "MetaModes" "1280x1024-1280x1024"** #Monitor Resolutions for Primary-Secondary monitors 
#**Option "MergedXineramaCRT2IsScreen0" "true" **#determines which screen is going to be the primary screen; value can be "true" or "false"
```[/FONT][/LEFT]
        [LEFT][FONT=Verdana][COLOR=Red][I][B]3. Next, go to the "Monitor" Section and add the following
[/B][/I][/COLOR]```
**Horizsync    28-64** #You may wish to change the values to fit your specific monitor
    **Vertrefresh    43-60**
```[/FONT][FONT=Verdana][COLOR=Red][I][B]
Save the file, and restarted X (ctrl+alt+backspace), or reboot.

[/B][/I][/COLOR][/FONT][/LEFT]
        [LEFT][FONT=Verdana]**Now Dual Monitor support should be enabled, if not please post your problem.**[/FONT][/LEFT]

I cannot get it working, when it boots up i get a blank screen with the cursor blinking and nothing happens
i am not sure about your instructions, in the 1st half of the instructions, am i making changes to reflect MY MAIN monitor? or the monitor i am Adding?
and the 2nd section for the horizsynch & vertRefresh do i add the settings for my MAIN monitor or the second monitor?
also am i appending those additons to the current monitor section? or am i adding an identifier?
here is what ive got.

Section "Device"
	Identifier	"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option "MergedFB" "true"
	Option "MonitorLayout" "CRT, CRT"
 	Option "CRT2Hsync" "30-95"
 	Option "CRT2VRefresh" "50-160"
	Option "OverlayOnCRTC2" "true"
 	Option "CRT2Position" "RightOf" 
  	Option "MetaModes" "1024-768" "1024-768" 
	Option "MergedNonRectangular" "True"
##Option "MergedXineramaCRT2IsScreen0" "true" 
	
EndSection

Section "Extensions"
	Option		"Composite"	"1"
EndSection

Section "Monitor"
	Identifier	"eView 17f2"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160

EndSection

NOW, the 1st half (DEVICE) those are the settings reflecting my 2nd monitor(CRT2) is that correct? or should all those settings reflect my main monitor?
and the 2nd half (Monitor section)  reflects my MAIN monitor.

any help i can get will be ENORMOUSLY APPRECIATED

---

### Post by xdarkgokux on 2008-02-27
ok someone help..lol...i get the exact same thing on my second monitor.. i tried to read the posts and seee but i dono, i tried everything..

---

### Post by wsams on 2008-04-11
I spent a lot of time on this dual monitor thing and documented a solution that doesn't really involve editing your xorg.conf except to add a Virtual monitor depth.

Look for the section titled "Span across two monitors (dual monitors)" at [http://www.wjsams.com/Wiki/Debian]("http://www.wjsams.com/Wiki/Debian") . It should work on Ubuntu also, as long as you can use xrandr.

---

### Post by bharat411 on 2008-04-20
Wow... my first post as a Ubuntu user and I never thought I might be solving a problem... Thanks to Wsams for the previous post about xrandr... I did some digging and found a GUI version of it that makes everything much easier... No xconf editing whatsoever... But I loved all the xconf editing I did in the first place.. learnt tons from it :) thanks...

anyway... here's the [link]("http://www.albertomilone.com/urandr").. hope it works for you too.. this made it so incredibly easy for me.. two button clicks was all it took.. give it a go!

PS - It's an alpha.. so be wary...

---

### Post by bobo99 on 2008-04-21
Since I've been trying to get dual monitors to work for some time now i have dozens of built up old config files and drivers. How do i know if i have a binary graphics driver installed, and if so how do i remove it ? Which driver should I use with my Radeon 9200pro?(i'm guessing not the fglrx, because i read that it doesnt support cards below 9500) I've been trying to follow everything in this thread for a few days now. 

Also coupled with this problem is sometimes when I reboot (only sometimes) it automaticly reverts to the Vesa generic driver and failsafe xorg file.. any suggestions ? 
Thanks

---

### Post by Macbeth417 on 2008-04-26
I've been reading for three days now and still can't get this to work. I have had no issue getting a cloned screen, but would like my desktop to extend not clone. 

ati radeon 800x (one dvi output one vga)
open source ati fglrx driver I believe
2 19" samsung lcd's 1280x1024@60

Ive tried following the tutorial, but X has me reconfigure when i restart and this is my current xorg.conf

```

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
	Load		"dri"
	Load		"v4l"
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
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Buttons"	"7"
	Option		"ButtonMapping"	"1 2 3 6 7"
	Option		"Emulate3Buttons"	"false"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"on"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 931BF (VGA)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1600x1200@65"	"1152x864@75"	"1600x1200@60"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	1
	Vendorname	"ATI"
	Option		"MergedFB"	"on"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1600x1200@65"	"1152x864@75"	"1600x1200@60"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 931BF (DVI)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

I get cloned screens just fine, i am looking to extend the desktop with full compiz support. When i try to use the xorg video gui I can select either monitor as the default but can not enable a secondary. When i can see the enable button and try to test it the gui crashes.

I will continue to google and try things, but any help at all would be greatly appreciated.

---

### Post by peakshysteria on 2008-05-05
Running latest 8.04 Hardy Heron 64. Gnome 2.22.1. ATI EXCALIBUR X700 PRO. 3 GB Memory. AMD Athlon 64 3000+

You guys are way ahead of me. I can't even get the ATI driver properly installed. Not via the restricted manager or via ENVY. I've also tried a manuall install, but it also failed. At the time i have no tv out and no compiz. And yes X reconfigures in my end everytime I restart x/reboot after installation of a new driver.

I'm not sure how to proceed really. The output of my xorg.con:

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x960@60"	"1280x1024@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection

Section "Module"
	Load		"dri"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0	-	65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Extensions"
EndSection

Can anybody give me a push here? Kids are driving me nuts since they don't have access to their movies anymore :)

---

