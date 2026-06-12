---
title: "[SOLVED] Intel i915 and S-video"
date: 2006-03-07
forum: Multimedia &amp; Video
---

### Post by groggyboy on 2006-03-07
**UPDATE:** Featherking has written an excellent howto [here]("http://ubuntuforums.org/showthread.php?t=361124") on setting up and using svideo for computers using the i810 driver.

Hello all.

I've been using Ubuntu for about two weeks now.  I love it!

Unfortunately, until I get a few quirks ironed out, I won't be getting rid of that dang Windows partition any time soon.

I watch a lot of movies on my laptop.  I was wondering if anyone has managed to get s-video working with an intel 915 gma video card.  There have been a lot of posts on this, but for the wrong video cards.  I'm a noob, so take it easy on me! :p 

Don't know if it's relevant at all, but my /etc/X11/xorg.conf file says I have an i810 driver.

---

### Post by groggyboy on 2006-03-08
<BUMP> Not to be a dink, but anyone got any ideas? I'm stumped. Switching to Windows just to watch movies on my TV is a pain. Would Dapper Drake fix this? The laptop wiki seems to imply that s-video is possible, but all my efforts point to no. </BUMP>

::EDIT::

A bit of googling has given me a bit more info.  The Mobile Intel 915 gma chipset actually uses the i810 driver in linux.

This forum has a bit of info on the latest drivers: > [http://www.linuxquestions.org/questions/showthread.php?t=311096](http://www.linuxquestions.org/questions/showthread.php?t=311096)

I also noticed that synaptic has a package called i810switch.  I'll poke around a bit this evening, and if I get it working I'll post my results so I might be able to help others.

---

### Post by groggyboy on 2006-03-10
Update:

I got s-video to work!  I took a lot of advice from a few other ubuntu forums, as well as some off-site forums.  Don't remember them all, but props goes out to those unnamed heroes nonetheless.

So, i810switch is useless for TV-out.  From what I gather, it is intended for a dual-monitor setup.

To get it working, make sure you have the latest drivers - use the link above for help with that.  Then you'll have to edit your /etc/X11/xorg.conf file.  The relevant section of mine:> Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
	Identifier 	"LCD"
	Driver		"i810"
	Option		"MonitorLayout" "TV,LFP"
	Screen		0
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
	Identifier	"TV"
	Driver		"i810"
	Option		"MonitorLayout" "TV,LFP"
	Option		"TVStandard" "NTSC"
	Option		"TVOutFormat" "SVIDEO" # "Composite"
	Option		"ConnectedMonitor" "TV"
	Screen		1
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
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

Section "Screen"
	Identifier	"TV"
	Device		"TV"
	Monitor		"TV"
	DefaultDepth	24
	Subsection	"Display"
		Depth		24
		Modes		"1024x768" "800x600"
	EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"LCDandTV"
	Screen 0	"LCD"
	Screen 1	"TV" RightOf "LCD_TV"
	InputDevice	"Dell Keyboard"
	InputDevice	"Cordless Mouse"
	InputDevice	"Touchpad"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandTV"
EndSection

Section "DRI"
	Mode	0666
EndSection


Some notes:
 *make a backup first - if your xorg.conf file has the slightest problem, GNOME won't start.
 *don't just copy/paste - your lcd (and other hardware) will have it's own specifications, and they might not be the same as mine. compare your file with mine, and only change the relevant parts!
 *my TV section has some vert and horiz data that i haven't fully tested - read your TV documentation to find out that sort of stuff!
 *you may have to log out or even reboot to get your laptop to recognize the TV - I don't remember what I had to do.
 *it's not perfect yet - altho I got my TV to clone my laptop screen, the TV picture froze right away, and wouldn't change to reflect my laptop.

When I get a chance (this weekend, for instance, or tonight), I'll test it further.  I'll post an update once I know more.  If anyone knows why my computer didn't configure the TV section of my xorg.conf automatically, I'd be happy to hear about it.  It seems like something that should have been set up automatically somewhere.  I know Windows set it all up automatically.  But then again, it's like comparing peas and carrots, I know.

---

### Post by motin on 2006-04-16
I love the way you are answering your own post. Have done a couple of alike posts myself. Great to be able to share one's solution with the community. 

I have not tried your method, but posted an follow-up asking for more plug'n'play. Hopefully some day this issue will not be a problem not even for for example my folks. :)

[http://www.ubuntuforums.org/showthread.php?p=926580](http://www.ubuntuforums.org/showthread.php?p=926580)

---

### Post by motin on 2006-04-16
[QUOTE=groggyboy]
Screen 1 "TV" RightOf "LCD_TV"
[/QUOTE]

I had to change this to

Screen 1 "TV" RightOf "LCD"

to be able to parse the xorg.conf. Otherwise, it complained about a screen not in screens list...

---

### Post by groggyboy on 2006-04-27
Thanks for your interest!  I thought nobody cared!

Anyway, after that one heady afternoon when I duplicated my LCD screen on the TV (which as I said immeadiately froze up), I have been unable to do it again.

Eventually, I just gave up.  I just recently upgraded to the Dapper Beta, but I've still had no luck with s-video.  I suspect that the linux i915 drivers simply do not support s-video functionality.

:( 
groggyboy

---

### Post by motin on 2006-04-27
[QUOTE=groggyboy]Thanks for your interest!  I thought nobody cared!

Anyway, after that one heady afternoon when I duplicated my LCD screen on the TV (which as I said immeadiately froze up), I have been unable to do it again.

Eventually, I just gave up.  I just recently upgraded to the Dapper Beta, but I've still had no luck with s-video.  I suspect that the linux i915 drivers simply do not support s-video functionality.

:( 
groggyboy[/QUOTE]

Even though the file did parse, i never got X to start with the file... 

I really hope someday linux to will be able to automatically configure X on-the-fly for LCD, CRT and S-video as well as make use of the Fn + F4 (or similar) switch for easy switch between the three. 

When I don't use the computer for programming, I use it for playing mame roms or watching movies, and I'd really like to be able to (on the 40" LCD hehe...) without having to resort to windows...

---

### Post by polpak on 2006-06-19
I've managed to get the display on my Dell Inpiron 200m to appear on both the CRT and LCD output using the following Xorg config:
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	Option		"MonitorLayout"	"CRT,LFP"
        Option		"Clone"		"True"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Internal LCD"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Monitor"
	Identifier	"External CRT"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Internal LCD"
	Monitor		"External CRT"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

But I still can't get the svideo working. Anyone familiar with how to do this?

Thanks

---

### Post by Hellkeepa on 2006-06-26
HELLo!

Using **Groggyboy**'s config above I was able to get TV out working on my Amilo Pro 2040, with two issues:
1. It's black and white only, regardless what TV mode & OutputMode I select.
2. The picture doesn't quite fill the TV, and is a bit distorted.

The chipset on my laptop is "Mobile 915GM/GMS/910GML Express Graphics", as copied from the "Device Manager". I'm using a S-Vid to composite plug converter, and the TV is able to auto-detect NTSC and PAL. It's a PAL TV though, normal 4:3 as well, since I live in Norway.
Here's a copy of my "xorg.conf":
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
	Option		"XkbLayout"	"no"
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
EndSection

Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "TV"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Option "TVStandard"	"NTSC"
	Option "TVOutFormat"	"COMPOSITE" # "SVIDEO"
	Option "ConnectedMonitor"	"TV"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
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
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"TV"
	Device		"TV"
	Monitor		"TV"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandTV"
	Screen		"LCD"
	Screen		"TV" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandTV"
EndSection

Section "DRI"
	Mode	0666
EndSection
```
Do anyone in here know what I can do to make it display in colours, please? I've tried for weeks now, to find a solution to this problem. I'm getting to the point where I think it may have something to do with a missing modline, or something to that effect.

Happy codin'!

---

### Post by LazyP on 2006-06-27
On Breezy I tried the same thing with my Dell inspiron 6000 (intel 915 card) and got the result of perfect image in black and white. Couldn't get it to work in any way with color.
Then I tried it with win xp (have to keep it on the drive not to void my warranty) and se what - Not even Winxp with all the factory drivers up to date can do it in color... that's interesting.

But my old crappy computer with an s-video out nvidia card can get s-video with colors to my TV (with composite format set in the nvidia driver). Thus it's intels crappy card i guess which can't send correct video trough s-video, at least not color and composite.

---

### Post by Hellkeepa on 2006-06-28
HELLo!

Hmm... That's interesting information indeed.
I have a friend who has almost the same laptop (only difference is it not being "Pro"), and she gets colours on hers (windows XP though). That is, only when she uses a spesific cable, as all the other she has tried yelds a black and white picture. So this might be a dual problem, one which requires both the correct setup and the correct cables to overcome. :\

Happy codin'!

---

### Post by bctechnzl on 2006-07-13
OK, I got it to work in colour, are you using the right SVideo to RCA output cable? I got one from Dick Smiths in NZ and its 4 pin SVideo to single RCA, the dual RCA splits croma and picture and is useless in a PAL tv environment.  I still have to work through the dual head stuff as totem doesn't sync but I can switch to the display ok.
Ive got a HP/Compaq nx6120 btw. And upgraded to dapper on the laptop, but have breezy on my desktop pc.

---

### Post by awaldram on 2006-09-02
The most probable reason it's BW is that the 915GM outputs ntsc as default

Even if you have switched it to pal in MSwindows it will still be ntsc in linux as its the hardware default.

This will result in a bw picture on many eu TV's 

I have not been able to locate a utility to swith the tvout to PAL in linux

---

### Post by kozik on 2006-09-19
I also has problem like Hellkeepa - image on TV does not fill TV - it uses about 2/3 of height.

FSC Amilo Pro 2060, Intel i915

I have tried two combinations:
 - cloning
 - dual displays
Results are the same - image on TV is resized in Y-axis. In X-axis it fills screen.

Xorg.conf - CLONING:
```

Section "ServerFlags"
	Option       "DefaultServerLayout" "Default Layout"
	Option       "blank time"   "2"
	Option       "standby time" "5"
	Option       "suspend time" "7"
	Option       "off time"     "8"
EndSection

Section "Files"
	FontPath     "/usr/share/fonts/misc"
	FontPath     "/usr/share/fonts/75dpi"
	FontPath     "/usr/share/fonts/100dpi"
	FontPath     "/usr/share/fonts/TTF"
	FontPath     "/usr/share/fonts/Type1"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dri"
	Load  "record"
	Load  "xtrap"
	Load  "dbe"
	Load  "glx"
	Load  "freetype"
	Load  "type1"
EndSection

Section "dri"
	Mode 0666
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option      "AutoRepeat"    "500 30"
	Option      "XkbLayout"     "pl"
EndSection

Section "InputDevice"
	Identifier  "Touchpad"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"		# Przy wlaczeniu w /etc/conf.d/usb X11_USBMICE_HACK
							# Touchpad zawsze bedzie pod /dev/input/mice
#	Option	    "ZAxisMapping" "4 5 6 7"
EndSection
Section "InputDevice"
	Identifier  "Mouse1"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mouse1"	# Myszka podlaczana pod ten sam port wyladuje
							# zawsze pod /dev/input/mouse1
#	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Device"
	Identifier  "Intel i915"
	Driver      "i810"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 915GM/GMS/910GML Express Graphics Controller"
	BusID       "PCI:0:2:0"
	Option      "DRI" "true"
	Option      "MonitorLayout" "TV,LFP"
	Option      "Clone" "true"
	Option      "CloneRefresh" "60"
	Option      "TVStandard" "PAL-B" # (mo&#380;liwe: "PAL-B" "PAL-D" "PAL-G"
	                                 # "PAL-H" "PAL-I" "PAL-K1" "PAL-M" "PAL-N" 
	                                 # "PAL-NC" "NTSC-J" "NTSC-M)
	Option      "TVOutFormat" "SVIDEO" # Sposób po&#322;&#261;czenia: "SVIDEO" dla po&#322;&#261;cze&#324; 
	                                   # (S-VIDEO=S-VIDEO)
	                                   # "COMPOSITE" : (S-VIDEO=EURO) 
	                                   # (S-IDEO=COMPOSITE) 
	                                   # (COMPOSITE=S-VIDEO) (COMPOSITE=EURO) 
	                                   # (COMPOSITE=COMPOSITE)
	Option      "ConnectedMonitor" "TV"
#	Option      "SecondMonitorVertRefresh" "60" # not used
	Option		"SWCursor"		"true"
EndSection 


Section "Monitor"
	Identifier   "LCD"
	Option       "DPMS"
EndSection
Section "Monitor"
  Identifier   "External TV"
EndSection	
Section "Screen"
	Identifier  "LCD"
	Device      "Intel i915"
	Monitor     "LCD"
	Monitor     "External TV"
	SubSection  "Display"
		Modes      "1024x768"
		Depth      24
	EndSubSection
EndSection

Section "ServerLayout"
	Option         "Xinerama" "false"
	Identifier     "Default Layout"
	Screen          0  "LCD" 0 0
	InputDevice    "Touchpad" "CorePointer"
	InputDevice    "Mouse1" "SendCoreEvents"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

```

Xorg.conf - two displays:
```
Section "ServerFlags"
	Option       "DefaultServerLayout" "Default Layout"
	Option       "blank time"   "2"
	Option       "standby time" "5"
	Option       "suspend time" "7"
	Option       "off time"     "8"
EndSection

Section "Files"
	FontPath     "/usr/share/fonts/misc"
	FontPath     "/usr/share/fonts/75dpi"
	FontPath     "/usr/share/fonts/100dpi"
	FontPath     "/usr/share/fonts/TTF"
	FontPath     "/usr/share/fonts/Type1"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dri"
	Load  "record"
	Load  "xtrap"
	Load  "dbe"
	Load  "glx"
	Load  "freetype"
	Load  "type1"
	Load  "i2c"
	Load  "ddc"
	Load  "vbe"
	Load  "int10"
EndSection

Section "dri"
	Mode 0666
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option      "AutoRepeat"    "500 30"
	Option      "XkbLayout"     "pl"
EndSection

Section "InputDevice"
	Identifier  "Touchpad"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"		# Przy wlaczeniu w /etc/conf.d/usb X11_USBMICE_HACK
							# Touchpad zawsze bedzie pod /dev/input/mice
#	Option	    "ZAxisMapping" "4 5 6 7"
EndSection
Section "InputDevice"
	Identifier  "Mouse1"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mouse1"	# Myszka podlaczana pod ten sam port wyladuje
							# zawsze pod /dev/input/mouse1
#	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Device"
	Identifier  "Intel i915"
	Driver      "i810"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 915GM/GMS/910GML Express Graphics Controller"
	BusID       "PCI:0:2:0"
	Screen      0
	Option      "DRI" "true"
	Option      "DDC" "true"
	Option      "MonitorLayout" "TV,LFP"
	Option      "VBERestore" "true"
EndSection

Section "Device"
	Identifier "Intel i915 External TV"
	Driver      "i810"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 915GM/GMS/910GML Express Graphics Controller"
	BusID       "PCI:0:2:0"
	Option      "DRI" "true"
	Option      "DDC" "true"
	Option      "TVStandard" "PAL-B" # (mo&#380;liwe: "PAL-B" "PAL-D" "PAL-G"
	                                 # "PAL-H" "PAL-I" "PAL-K1" "PAL-M" "PAL-N" 
	                                 # "PAL-NC" "NTSC-J" "NTSC-M)
	Option      "TVOutFormat" "SVIDEO" # Sposób po&#322;&#261;czenia: "SVIDEO" dla po&#322;&#261;cze&#324; 
	                                   # (S-VIDEO=S-VIDEO)
	                                   # "COMPOSITE" : (S-VIDEO=EURO) 
	                                   # (S-IDEO=COMPOSITE) 
	                                   # (COMPOSITE=S-VIDEO) (COMPOSITE=EURO) 
	                                   # (COMPOSITE=COMPOSITE)
	Screen      1
	Option      "Display" "TV" # Not sure if it does anything...
	Option      "ConnectedMonitor" "TV"
	Option      "MonitorLayout" "TV,LFP"
EndSection

Section "Monitor"
	Identifier   "LCD"
	Option       "DPMS"
EndSection
Section "Monitor"
	Identifier   "External TV"
	Option       "DPMS"
EndSection


Section "Screen"
	Identifier  "External TV"
	Device      "Intel i915 External TV"
	Monitor     "External TV"
	DefaultDepth 24
	SubSection  "Display"
		Viewport   0 0
		Depth      24
	EndSubSection
EndSection
Section "Screen"
	Identifier  "LCD"
	Device      "Intel i915"
	Monitor     "LCD"
	DefaultDepth 24
	SubSection  "Display"
		Modes      "1024x768"
		Depth      24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen          0  "LCD" 0 0
	Screen          1  "External TV" RightOf "LCD"
	InputDevice    "Touchpad" "CorePointer"
	InputDevice    "Mouse1" "SendCoreEvents"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection
```

I have tried different VertRefresh/HorizSync - no difference or no display.

Anyone has an idea?

P.S. Hellkeepa - your problem with black/white can be solved with proper cable (svideo-svideo, or svideo-special condensator-composite) or with:
```
Option      "TVStandard" "PAL-B"
```
in device section.

---

### Post by awaldram on 2006-09-20
As I stated I can see no way of getting the i915 to output pal

Option      "TVStandard" "PAL-B"

does not work for the i915m

Your 2/3 height could be your tv resolving the 525 lines of ntsc onto your 625 line pal telly.

---

### Post by kozik on 2006-09-20
Arghhh...

I found that poeple used nvtv to change display to PAL:
[https://bugs.freedesktop.org/show_bug.cgi?id=2782](https://bugs.freedesktop.org/show_bug.cgi?id=2782)
The problem is that nvtv does not support i915 (only i865 and lower). I have tried hack it a little but it exits with "Segmentation fault" after calling "I810UpdateTvState()" (debug: bi810_probe)...

So problem is not solved :/...

---

### Post by loboson on 2006-10-24
I'm almost there. The only problem I'm trying to solve for now is that the TV screen shows a cropped out version of the LCD on the middle, starting from the upper left corner... (*,) ](*,) 

All the time thinking how easy is on windows ARRGGGGHH!! :evil: Stay AWAY FROM MEEE EVILLLLL 


:rolleyes:

---

### Post by loboson on 2006-10-24
Ok, found a way to make it work. 

Take a look at:

[http://loboson.blogspot.com/2006/10/ubuntu-intel-gma-tv-out-xorgconf.html]("http://loboson.blogspot.com/2006/10/ubuntu-intel-gma-tv-out-xorgconf.html")

However, I've found that using this conf I can not restart the window manager (gdm). I get ```
(EE) I810(0): VBE initialization failed
``` on */var/log/Xorg.0.log* 

I think this is a very generic error, but I don't know where to look out for more info on it..

I was editing the */etc/X11/xorg.conf* file for tunning it up, and found I can not restart gdm. The only way to test out my changes is rebooting :neutral: ...

So.. still on this.. If anyone has a clue on what I'm confronting, please kindly help me sort this out..:neutral: 

```


~$ egrep "WW|EE" /var/log/Xorg.0.log
Current Operating System: Linux  2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Screen TV doesn't exist: deleting placement
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
(WW) I810: More than one matching Device section for instances
(WW) I810(0): Bad V_BIOS checksum
(EE) I810(0): unknown reason for exception
(EE) I810(0): cannot continue
(EE) I810(0): VBE initialization failed.
(EE) Screen(s) found, but none have a usable configuration.


```

---

### Post by loboson on 2006-10-25
I've found this page:


[http://intellinuxgraphics.org/man.html]("http://intellinuxgraphics.org/man.html")

Maybe it can shed more light on this... :confused:

---

### Post by loboson on 2006-10-25
I think this should be a Bug. Tested with various chnges and allways the same problem... :(

> **loboson said:**
> Ok, found a way to make it work. 

Take a look at:

[http://loboson.blogspot.com/2006/10/ubuntu-intel-gma-tv-out-xorgconf.html]("http://loboson.blogspot.com/2006/10/ubuntu-intel-gma-tv-out-xorgconf.html")

However, I've found that using this conf I can not restart the window manager (gdm). I get ```
(EE) I810(0): VBE initialization failed
``` on */var/log/Xorg.0.log* 


---

### Post by loboson on 2006-10-25
Ok, I've arrived to a point where I can see the TV (using mythtv) on my TV set conected to my laptop Travelmate 4500. However, the laptop display remains off so I can use the video overlay.

I would like to have output on both screens and the videos & TV card output on the TV.

I'm posting the xorg.conf in case anyone can lend me a hand...

Cheers..


Also the screen only shows fitted on the upper left corner with a 2-3cm band in the right and the bottom of the screen..](*,)

---

### Post by motin on 2006-11-16
Is this thread's latest posts also answering post: [http://ubuntuforums.org/showthread.php?p=1766202](http://ubuntuforums.org/showthread.php?p=1766202) ?

Just wondering. Thanks

---

### Post by LinLenLap on 2006-11-19
Hey everyone,

I'm also trying to get my output to go through my laptops s-video out so I can watch videos on the tv. I can't really understand what's going on in this thread though, for instance, those posts of the xorg.conf files, how do I know what I need to change from default?

I'm gonna start messing with it, but maybe someone could make a how-to, since this is the very best thread i've come across.

Thanks for contributing what you have, it's got me going anyway!

Best,

LLL

---

### Post by motin on 2006-12-01
> **LinLenLap said:**
> Hey everyone,

I'm also trying to get my output to go through my laptops s-video out so I can watch videos on the tv. I can't really understand what's going on in this thread though, for instance, those posts of the xorg.conf files, how do I know what I need to change from default?

I'm gonna start messing with it, but maybe someone could make a how-to, since this is the very best thread i've come across.

Thanks for contributing what you have, it's got me going anyway!

Best,

LLL

I tried to summarize this thread and many other findings on the matter in "Intel i915 GM with S-Video - Impossible or not? - Ubuntu Forums" - [http://ubuntuforums.org/showthread.php?p=1766202](http://ubuntuforums.org/showthread.php?p=1766202) 

But thereafter, people still posted some new stuff in this thread as well as in the other thread. 

The subject has not what I've seen lead to any definitive solution or even a tutorial on how to get it working half-way... 

This is very much needed. Proposals:
1. Start a Wiki-page on the matter instead of these forumposts
2. Summarize the information in "Intel i915 GM with S-Video - Impossible or not?" and the latest posts in this thread into what works and does not in the wiki. 
3. Please - someoen with a partial solution, could you re-do your solution on a "fresh" xorg.conf and then post a diff here?

---

### Post by featherking on 2007-02-20
I wrote up an actual 'How To' for this and it is posted [[COLOR="Red"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=361124"). It allows switching between different configurations but also enables svideo check it out

---

### Post by psypher on 2007-04-24
maybe i am missing something but I cannot seem to find a resolution on your howto for the black and white problem so many people are facing with this chipset. I myself have tried your howto and it's great to switch monitors. but no matter if i use SVIDEO or COMPOSITE and tried PAL, PAL-I(Sth africa), PAL-G i just don't get colour. i have searched for hours but nobody has a solution. somewhere somebody said change the cable. I guess that must be my only option. funny thing is this latop had cyberlink powercinema on it, which is a linux based media centre partition. unfortunately, formatted it with feisty. So I think that it should work fine. Just some config or the difference must be propriety drivers.

Can someone at least say this? Is this a graphics bug, can it be done, should we just give up

---

### Post by kozik on 2007-04-24
In version 2.0.0 of i810 X.Org driver everything have changed - there are no such options as MonitorLayout, Clone, CloneRefresh, TVStandard or TVOutFormat. With new modesetting branch it seems that it solves the issue... Check xorg.conf examples in bug (section "Screen"):
[https://bugs.freedesktop.org/show_bug.cgi?id=2782](https://bugs.freedesktop.org/show_bug.cgi?id=2782)

---

### Post by psypher on 2007-04-25
That link seems to still be listed as a bug. And if not a bug I cannot integrate his xorg with mine. Keep getting errors different to his. Is there any more links regarding the modesetting branches that have changed?

---

### Post by antievets on 2007-06-07
Re: black and white issue.  The seven pins on your "s-video out" are probably divided up as four for S-Video output, two for composite and one ???   I don't think there is any such thing as 7-pin s-video.  Anyway, look at an adaptor to convert your composit pins correctly.  A quick search found this:

[http://www.epanorama.net/circuits/svideo2cvideo.html](http://www.epanorama.net/circuits/svideo2cvideo.html)

You may find something better.

I am still hoping to get my intel 945gm s-video to work.  thanks for the help so far; this is what i like about linux.

Evets

---

### Post by vitamin on 2007-06-13
Hi everyone,
and many thanks to Hellkeepa! Using his xorg.conf I was able to get TV-out working nice on my HP nc6320. My card is Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller. And I have a PAL TV.

Here is my xorg.conf:

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
	Option		"XkbLayout"	"cz"
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
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "TV"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Option "TVStandard"	"PAL-B"
	Option "TVOutFormat"	"COMPOSITE" # "SVIDEO"
	Option "ConnectedMonitor"	"TV"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"TV"
	Device		"TV"
	Monitor		"TV"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandTV"
	Screen		"LCD"
	Screen		"TV" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandTV"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by ishey4 on 2007-06-22
ok.. i have also been trying for a while to get svideo out working on ubuntu cause i want to set up a mythtv setup but on my tv... but anywho.. i am not a very advanced linux user.. but i do know that my svideo work with puppy linux.....

so my question is.. would knowing that puppy works with the s-video out help you figure out how to adapt ubuntu to work with it? or.. is there a way  to install mythtv or any tv tuner/tv in card to work on puppy?
thankyou,
   -inbar

---

### Post by gmc on 2007-08-21
Hi Folks,

I too have been banging my head against the wall trying to get my Macbook to output to a composite (ntsc) tv. 

I've been able to get a black and white image on the TV, however the screen is offset horizontally and vertically and is rolling (very out of sync). I've been trying to tweak vitamin previously posted xorg.conf but with out much success. (and Yes I changed 'pal' to 'ntsc' in his example).

Anyone have any ideas? The only thing I can think of is trying to figure out how to generate a modeline entry for the TV, because what I'm seeing here really looks like the TV is receiving 50hz rather than 60hz.

I have to be honest, I had this working with my Acer laptop with an ATI X1400 card and that was a snap to get working, too bad it's not as easy with the Intel.


Gord

---

