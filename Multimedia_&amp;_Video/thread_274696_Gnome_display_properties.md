---
title: "Gnome display properties"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by jthirt on 2006-10-10
I'm experiencing trouble with screen resolution in gnome, as detailed in a seperate [post]("http://www.ubuntuforums.org/showthread.php?t=233958") but no one cared to reply to Blaineus or myself. ](*,)  So I think we have to look elsewere for answers ...

As explained in that [thread ]("http://www.ubuntuforums.org/showthread.php?t=233958") our laptop monitors do have a default or native resolution of 1024x768, but it comes up in Dapper with 800x600 and we haven't been able to change it despite xorg.cong indicating nothing else but that 1024x768 resolution.  

Where does gnome gets the listed resolutions ? As it does offer both 600x800 and 640x480 but I have no clue where that comes from. 

These low resolutions are far from satisfactory and the system is almost unusable with it. You have to move the tool bars to the sides in order to view what your options are, even for the install ...

Help would be really appreciated.

After installing Dapper without trouble on many systems I felt confident I could do it again on another one. Everything else is fine, but that issue is a really pain !

I suspect there is a simple fix for this, :D only I don't know what it is ... 

Cheers

---

### Post by pragmatine on 2006-10-10
You'll need to edit /etc/X11/xorg.conf and add the extra resolutions to the
Modes parameter under the Screen section

This is what mine looks like, but this is a Desktop machine..

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV41.0"
        Monitor         "BenQ FP937s"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
EndSection

```

---

### Post by jthirt on 2006-10-10
Nope! 

Sorry to contradict you, but the only mode that's listed there now is 1024x768 and it's the one that doesn't show in gnome-display-properties, nor does it appear in xrandr. So at least that's consistent.

Extract from xorg.conf (as generated at install):
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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

```

and xrandr output:
```

 SZ:    Pixels          Physical       Refresh
*0    800 x 600    ( 271mm x 203mm )  *60  
 1    640 x 480    ( 271mm x 203mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none

```

So my simple conclusoin is that gnome display properties / xrandr are not based on what's defined in xorg.conf ! :-k 

So, what is that drives them ?

---

### Post by CatKiller on 2006-10-10
> **jthirt said:**
> Where does gnome gets the listed resolutions ? As it does offer both 600x800 and 640x480 but I have no clue where that comes from.

It's still X getting the resolutions and reporting them to Gnome through XRandR. And X gets those resolutions from the BIOS of your graphics card as VESA modes.

I don't know whether it's even relevent to an LCD screen, but have you tried setting appropriate HorizSync and VertRefresh values in your xorg.conf?

EDIT: The X log is stored at /var/log/Xorg.0.log. You could look at that to get some clue why your screen isn't functioning properly.

---

### Post by jthirt on 2006-10-10
Now we're talking !

I must run now, but I'll investigate further ASAP.

I had a quick look into Xorg.0.log and indeed it says something like :

Not using "1024x768" (no mode of this name)

while before that it clearly indicated that it is the LCD panel resolution. 

I'll post my findings here as I make progress, hopefully. 

Thanks for the tip ...

---

### Post by CatKiller on 2006-10-10
Just as a warning, lots of people have reported trouble with Intel integrated graphics. I have no idea whether those problems were caused by inadequate drivers, or inadequate configuration, or what. There are some packages in the repositories that deal specifically with "modifying the video BIOS of the 800 and 900 series Intel graphics chipsets". I have no idea if this is a good thing, and I have no experience of using them.

But hey, maybe we can get you configured, and we'll both learn something.

---

### Post by jthirt on 2006-10-11
I'm affraid I'm in for a serious dose of frustration with that one and considering the posts that I've seen, I'm not the only one who's been there. 

So I looked into this xorg.0.log and indeed it says a lot, but apart from the fact that it doesn't recognise the 1024x768 resolution:

```
(II) I810(0): Laptop pannel: Using hsync range of 28.00-51.00 kHz
(II) I810(0): Laptop pannel: Using vrefresh range of 43.00-60.00 Hz
(II) I810(0): Not using mode "1024x768" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (800 -> 1024).
(--) I810(0): Virtual size is 800x600 (pitch 1024)
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
(==) I810(0): DPI set to (75, 75)
```

I tried many diferent settings in xorg.conf, combined with many tries to set/force mode using 915resolution, also found something that mentionned Option "ForceBIOS" but that didn't do anything I could notice except an additional message in the log saying 'Not using "ForceBIOS" ...

So I'm back to base and no wiser ... ](*,) 

I don't know what to do next !

If someone has a clue ... :-k

---

### Post by jthirt on 2006-10-11
Sadly, it appears that it can't be fixed by setup or software as the driver relies on the BIOS that doesn't support the panel's 1024x768 resolution. 

That's what I gathered drilling down to the i810 driver bugs pages. 

](*,)

---

### Post by DarkN00b on 2006-10-11
From Synaptic Package Manager"
Regarding "915 Resolution"

[quote-"Synaptic"]
resolution modify tool for Intel graphic chipset
915resolution is a tool to modify the video BIOS of the 800
and 900 series Intel graphics chipsets. This includes the 845G,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
This modification is necessary to allow the display of certain
graphics resolutions for an Xorg or XFree86 graphics server.

915resolution's modifications of the BIOS are transient.
There is no risk of permanent modification of the BIOS.
This also means that 915resolution must be run every time the
computer boots inorder for it's changes to take effect.
If you want to automatically set the resolution on each boot
and before X is launched, see /usr/share/doc/915resolution/README.Debian
for information about configuring the provided initscript.

Web site: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)[/quote]

Considering your earlier post, I assume you have probably seen this. I thought I'd put it up on the off chance you hadn't.

I have Intel's i855 graphics chipset and it worked right "out of the box".

---

### Post by jthirt on 2006-10-13
At last some progress ! :D 

Thank to DarkN00b, I've spent some more time plying with xorg.conf

I have to admit that I'm quite stubborn at times and this resolution issue really annoys me ! 

While  I haven't gotten any further with the laptop panel resolution, I managed to setup something that delivers 1024x768 on an attached external CRT. 

So that proves at least the video card CAN deliver that resolution using the current driver !

Now the Graal is to do it with the LDC panel.

For info, here is my xorg.conf now :

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
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout" "CRT,NONE"
#	Option		"ForceBIOS"	"640x480=1024x768"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device 2"
	Driver		"i810"
	BusID		"PCI:0:2:1"
EndSection

Section "Monitor"
	Identifier	"Laptop"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"External"
	Option		"DPMS"
	HorizSync	30-68
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Default"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Laptop"
	DefaultDepth	16
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		32
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Optional"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device 2"
	Monitor		"External"
	DefaultDepth	16
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		32
		Modes		"1024x768" "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default"
	Screen		1 "Optional"
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

I realise that it is somewhat confusing, but I'm no expert, so don't blame me for experimenting. I have not managed to get my hands on a clear HowTo for Dual monitor, so I'm doing what I can ...

I hope I'll have more specific and even better news later.

---

### Post by CatKiller on 2006-10-13
What's the model number of your laptop? The HorizSync and VertRefresh numbers for your laptop screen seem a little low.

---

### Post by jthirt on 2006-10-13
It's a Gateway 400VTX. 

I wish I had the exact details. But I couldn't find that on Gateways web site. Do you think this could make a difference ?

---

### Post by DarkN00b on 2006-10-13
You're welcome.  You might want to look at i810switch, also in the repos:

[quote="Synaptic"]Enables/disables video output to CRT/LCD on i810 video hardware
i810switch enables/disables the output to the CRT display and LCD,
depending on the i810 graphics controller hardware. Such hardware is found
on some laptops (eg, Sony Vaios, some Dell models, etc). Chipsets also
supported include i855, i830, i845.

This package includes the i810rotate script, which toggles the output
between three states: LCD only, LCD + CRT, and CRT only.[/quote]

I haven't tried it, mainly because I don't have an extra monitor sitting around. This might help you.

Sometimes just reading through the "All" tab in Synaptic can be entertaining. There is lots of stuff in there that you wouldn't think was available.

Also if you're going to be messing with your xorg.conf file, it is a really good idea back that sucker up somewhere safe. I found it a lot easier to reboot in recovery mode and replace than trying to edit it from the CLI.

Good luck.

---

### Post by jthirt on 2006-10-13
I do venture in synaptic quite frequently, but usually following a tip or with intentions ...

I have been caught by xorg errors a few times already, so I am careful and take copies if I get serious messing about. 

In fact, the first time I had to was as I installed Xubuntu 6.06 for one laptop, on another, as for some reason, I couldn't get it to install on the target one. Probably because the spec was too low (PII/300Mhz/96Mb).

So I had to retrieve another config that matched. I had managed to install ubuntu 5.10 on that laptop before, but I didn'd want to try again on that same disk. 

In the end, I don't use the xubuntu one,; as I found the sound quality to be quite poor as opposed to the ubuntu one. I hoped xubuntu would run better, but since the laptop essentially plays music, it doesn't matter. 

Kind of off topic here!

Cheers.

---

### Post by CatKiller on 2006-10-14
> **jthirt said:**
> Do you think this could make a difference ?

It certainly makes a difference on CRTs - if the range is set wrong then the monitor refuses to do a whole bunch of modes. I don't have enough experience of LCDs to know if they would experience the same symptoms, or if they might be damaged by setting the rate too high for experimental purposes.

---

