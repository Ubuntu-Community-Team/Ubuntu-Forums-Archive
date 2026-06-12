---
title: "flgrx and 2880x900..."
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by zbyszek_zbl on 2007-11-26
Hi
I have Acer TM 7520 with 64bit Gutsy and newest ATI (catalyst 7.11) drivers instaled and working:
zbl@Ubuntu-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 2400 XT
OpenGL version string: 2.1.7059 Release

I tried to do some experiments with dual display and now I want to go back to standard settings (for one display only). During my experiments system made additional resulution for dual head - 2880x900 (my Acer's screen is 1449x900). And now I have problem because this mode is still present in gnome resoution settings but it isn't at xorg.conf. I like to play some games sometimes and now most of games with support of wide screen doesn't work. For example when I try to launch warsow set on 1440x900 I get:
1440x900 -> 2880x900: 0
1440x900 -> 1440x900: 0
2880x900 selected
...setting fullscreen mode 15:
X Error of failed request:  BadValue (integer parameter out of range for operation)

So system by "himeself" change 1440x900 to 2880x900. Why? How to remove this "feature".
Here are Device, Monitor and Screen sections from my xorg.conf:
Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
#	Option	"DesktopSetup"  "horizontal" #Enable Big Desktop
#	Option	"Mode2"         "1024x768" #Resolution for second monitor
#	Option	"DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO
	BusID		"PCI:1:0:0"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31-56
	VertRefresh	56-75
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	Subsection	"Display"
		Modes	"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

And in resolutions settings in gnome I have: 2880x900, 1440x900, 1152x864, 1024x768, 800x600 and 640x800 - two modes more than in xorg.conf!

I tried aticonfig and I've got something like this:
zbl@Ubuntu-laptop:~$ sudo aticonfig --resolution=0,1440x900,1024x768,800x600,640x480
error at set screen resolution : screen0 does not exist
aticonfig: parsing the command-line failed.

Any sugestions? Is somewhere another place for resolution settings for fglrx than xorg.conf?


--------

I found the issue :-). fglrx drivers have additional settings stored in /etc/ati folder. My problem was in file /etc/ati/amdpcsdb. Some options removed in xorg were still present in this file. Editing it solved the problem with this "additional resolution".

---

