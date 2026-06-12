---
title: "Rough fonts"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by MadMac on 2007-05-09
I have upgraded my video card from legacy to non-legacy. The new card is a e-GeForce FX 5500, has DVI connection to the monitor, the video card seats into a PCI slot, and has replaced a legacy Nvidia card. The monitor is a Hanns-G JC199D 19 inch LCD.

The problem is that the fonts are sort of "rough" and "edgy", not "smooth".  I know that's hard to understand, but it's the best I can do, since I have already made screenshots and they show up fine on another computer.  From what I can tell, the digital does photos great, and I watched a movie that was just outstanding in the video, too.

One main thing is that the makers of the card do not support Linux - that is direct from them via e-mail.  They recommended that I use the video drivers on the Nvidia site - which I have done, via synaptic.  I have changed the xorg.conf file to default to 60hz on the refresh, since the drivers default to 50Hz and I cannot change it.  I can't tell if it is working, since I have no way to change the refresh rate to check.  The change to the xorg file is (in bold):

================
Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia"
	Monitor		"Hanns-G JC199D"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"**1280x1024_60**" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"

=================

Anyone any ideas on how I can "smooth out" the fonts and/or change the refresh rate?

Thanks!

(Oh, and I don't want to use Envy - using that caused me to re-install Ubuntu twice - not really ready for another install, again.)

---

### Post by reclusivemonkey on 2007-05-10
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty)

This worked well for me; there was a noticeable improvement with my fonts.

---

### Post by airtonix on 2007-05-10
id you look at the sub-pixel rendering controls that are presented to you when you choose your system wide fonts?

apparently a pixel can be divided into three further segments, which are of course the red, green and blue segments.

if your device is mis-interpreting these arrangment signals then most likely the end result will look utterly horrible.

but of course...I have absolutley no idea if this will solve your problem.

does the font rendering issue still occur if you install enlightment 1.7?
Reason i mention e17, is that i noticed on my system that the font rendering and all that goes with delivering pixels to the screen is different.

just a suggestion

---

### Post by MadMac on 2007-05-10
Reclusivemonkey:  I ran the changes and it seems to have made a slight improvement.  Thanks!

Airtonix:  I downloaded Enlightenment thru synaptic but no matter what I do it keeps popping up with a warning about a window manager already running.  Also, what changes to my startup will I see when this is ran?  I have already had a bad experience with Envy doing things that  led to a hard drive reformat, so I am understandably curious.  Thanks!

---

### Post by reclusivemonkey on 2007-05-11
MadMac: You may be interested in this thread;

[http://ubuntuforums.org/showthread.php?t=439412&goto=newpost](http://ubuntuforums.org/showthread.php?t=439412&goto=newpost)

---

### Post by MadMac on 2007-05-11
> **reclusivemonkey said:**
> MadMac: You may be interested in this thread;

[http://ubuntuforums.org/showthread.php?t=439412&goto=newpost](http://ubuntuforums.org/showthread.php?t=439412&goto=newpost)

Reclusivemonkey:  I checked into it, and it seems like a good deal.  The problem is that the fonts still look "rough" and the font on the screenshot you posted there looks really bad on my system.

I have a sneaking suspicion that this may have something to do with the refresh rate rather than fonts, but I'm not sure.  I checked the nvidia-settings and the refresh rate shows up as 60Hz with the option to go with "automatic".  However, the "Screen Resolution" under System Preferences only has 50Hz available and no other options or selections.  I dunno, do you?  :confused: 

Thanks!

---

### Post by reclusivemonkey on 2007-05-11
Can you;

[LIST]
[*]attach your xorg.conf
[*]take a screenshot with your fonts showing
[*]post the result of ```
xdpyinfo | grep resolution
```
[/LIST]

---

### Post by stchman on 2007-05-11
> **MadMac said:**
> I have upgraded my video card from legacy to non-legacy. The new card is a e-GeForce FX 5500, has DVI connection to the monitor, the video card seats into a PCI slot, and has replaced a legacy Nvidia card. The monitor is a Hanns-G JC199D 19 inch LCD.

The problem is that the fonts are sort of "rough" and "edgy", not "smooth".  I know that's hard to understand, but it's the best I can do, since I have already made screenshots and they show up fine on another computer.  From what I can tell, the digital does photos great, and I watched a movie that was just outstanding in the video, too.

One main thing is that the makers of the card do not support Linux - that is direct from them via e-mail.  They recommended that I use the video drivers on the Nvidia site - which I have done, via synaptic.  I have changed the xorg.conf file to default to 60hz on the refresh, since the drivers default to 50Hz and I cannot change it.  I can't tell if it is working, since I have no way to change the refresh rate to check.  The change to the xorg file is (in bold):

================
Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia"
	Monitor		"Hanns-G JC199D"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"**1280x1024_60**" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"

=================

Anyone any ideas on how I can "smooth out" the fonts and/or change the refresh rate?

Thanks!

(Oh, and I don't want to use Envy - using that caused me to re-install Ubuntu twice - not really ready for another install, again.)

Follow my procedure to give your desktop the M$ fonts treatment.  M$ fonts are nice.  Looks fabulous on my laptop and 19" LCD.

[http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html)

Very nice.

As far as the Envy it works great.

---

### Post by MadMac on 2007-05-11
> **reclusivemonkey said:**
> Can you;

[LIST]
[*]attach your xorg.conf
[*]take a screenshot with your fonts showing
[*]post the result of ```
xdpyinfo | grep resolution
```
[/LIST]

Alrighty, here goes.

Xorg.conf:
======
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
	Identifier	"Nvidia"
	Driver		"nvidia"
	BusID		"PCI:1:1:0"
EndSection

Section "Monitor"
	Identifier	"Hanns-G JC199D"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia"
	Monitor		"Hanns-G JC199D"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024_60" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024_60" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024_60" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024_60" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024_60" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024_60" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
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
======

Screenshot:
======
Attached.
======

Grep resolution:
======
xdpyinfo | grep resolution
  resolution:    85x86 dots per inch
======

Hope this helps!  And thanks again!

---

### Post by MadMac on 2007-05-11
> **stchman said:**
> Follow my procedure to give your desktop the M$ fonts treatment.  M$ fonts are nice.  Looks fabulous on my laptop and 19" LCD.

[http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html)

Very nice.

As far as the Envy it works great.

Thanks, but I checked the thread this came from and when I opened the thumbnail the fonts were not looking very good on my screen.  I have saved the process site, though, as I might wind up doing this.

I can understand that you are having good luck with Envy, but my experiences have not been good at all.  If it's not mandatory for my video card/monitor I really don't want to install it.

Thanks again!

---

### Post by reclusivemonkey on 2007-05-12
OK, firstly I would comment out the 

```

HorizSync 30-65
VertRefresh 50-75

```

In xorg.conf; DPMS would be fine. Also, lose the "_60" after your highest resolution, I know the Screen Resolution says "50", but it used to say that back when I had a CRT Monitor and 50 Hz would of been like watching a flickerbook...

I honestly don't think your fonts look that bad at all, but you may get some improvement by changing the DPI settings in the font settings. Try going to System --> Prefernces --> Font

Then go to the "Details" button and click it. Change the resolution to 86 and see if thats any better. You can try 85 as well. Make the "Smoothing" setting "Greyscale" and the "Hinting" setting "Slight". I don't really notice any change  in the Subpixel order myself, but you can try them if you want.

Other than that I can't really think of much else I'm afraid.

---

### Post by MadMac on 2007-05-14
> **reclusivemonkey said:**
> OK, firstly I would comment out the 

In xorg.conf; DPMS would be fine. Also, lose the "_60" after your highest resolution, I know the Screen Resolution says "50", but it used to say that back when I had a CRT Monitor and 50 Hz would of been like watching a flickerbook...

I honestly don't think your fonts look that bad at all, but you may get some improvement by changing the DPI settings in the font settings. Try going to System --> Prefernces --> Font

Then go to the "Details" button and click it. Change the resolution to 86 and see if thats any better. You can try 85 as well. Make the "Smoothing" setting "Greyscale" and the "Hinting" setting "Slight". I don't really notice any change  in the Subpixel order myself, but you can try them if you want.

Other than that I can't really think of much else I'm afraid.


Sorry for taking so long to get back to you.

Anyway, I did the changes and noticed no difference, except with the DPI changes.  It seems best right around 87, so that is where I left it.

I notice that everything looks good on the menus and such, but the actual text, like I am writing here, seems to be "rough".  Maybe just a font change?  I have tried but I can't seem to get this font to change.  I'll keep pluggin' away at it, though.  I will beat this thing!  If I can whip DOS and Windows into shape I can dang sure whip Ubuntu into shape, too.  :) 

Thanks for all your help!

---

### Post by reclusivemonkey on 2007-05-15
> **MadMac said:**
> 
I notice that everything looks good on the menus and such, but the actual text, like I am writing here, seems to be "rough".  Maybe just a font change?

If you want Firefox to use the font you specify, you need to make sure you untick "Allow pages to choose their own fonts, instead of my selections above" in the advanced font settings.

---

### Post by MadMac on 2007-05-15
> **reclusivemonkey said:**
> If you want Firefox to use the font you specify, you need to make sure you untick "Allow pages to choose their own fonts, instead of my selections above" in the advanced font settings.

That's bang on!  I made a change to the font and it now looks really good.  I do have to admit that I am somewhat chagrined in having to go through all this for something so simple.  Still, it's a learning experience, so that's okay.

Thanks again for all your help!  =D>

---

### Post by reclusivemonkey on 2007-05-15
No problem, glad you got things sorted in the end =]

Getting the fonts "just so" is a bit of a chore, but its good to learn things on the way. There's no aspect of fonts in Linux you aren't familiar with now! ;-)

---

