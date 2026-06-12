---
title: "Remote admin of myth backend"
date: 2007-12-24
forum: Mythbuntu
---

### Post by dougsnell on 2007-12-24
I'm running a backend with all output re-directed to a PVR-350 ... and since getting that working, I can't seem to get a VNC or ssh -X session working.  VNC validates the password, then simply stops functioning (cursor is working in background, but no error is given).  ssh -X connects to a regular ssh session.

xorg.conf is below:

> Section "Files"
	Fontpath	"/usr/share/X11/fonts/misc"
	Fontpath	"/usr/share/X11/fonts/cyrillic"
	Fontpath	"/usr/share/X11/fonts/100dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/75dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/Type1"
	Fontpath	"/usr/share/X11/fonts/100dpi"
	Fontpath	"/usr/share/X11/fonts/75dpi"
	Fontpath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

# Specific modules needed *this is important.*
Section "Module"
	Load		"dbe"
	Load		"v4l"
	Load		"extmod"
	Load		"type1"
	Load		"freetype"
	Load		"vnc"
EndSection

# Almost standard keyboard 
# Note: This setup doesn't require the keyboard to be present

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

# Almost standard mouse pointer
# Note: This setup doesn't require the mouse to be present

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
	Identifier	"Hauppauge PVR 350 iTVC15 Framebuffer"
	
	# the driver we installed - in Gutsy, this is NOT "ivtvdev".
	Driver		"ivtv"
	
	# frame buffer we found above
	Option		"fbdev"	"/dev/fb0"
	Option		"TVStandard"	"NTSC-M"
	Option		"VideoOverlay"	"on"
	Option		"XVideo"	"1"
	
	# below settings are optional I've seen lots of people with them commented out.
	# I believe that pal users should just comment below line out.
	
	# Not optional setting
	# BusID we found with lspci converted as shown above
	Busid		"PCI:0:09:0"
	
	Screen	0
	
EndSection

# these settings are generic (for TVs) but are specifically for TV

Section "Monitor"
	Identifier	"TV"
	Horizsync	30-68
	Vertrefresh	50-120
	Displaysize	183	122
  Mode "720x480"
		Dotclock	34.564
		Htimings	720	752	840	928
		Vtimings	480	484	488	504
		Flags		"-HSync"	"-VSync"
  EndMode
	
EndSection


# Our PVR-350 Driver entry
Section "Screen"
	Identifier	"TV Screen"
	Device		"Hauppauge PVR 350 iTVC15 Framebuffer"
	Monitor		"TV"
	Defaultdepth	24
	Defaultfbbpp	32
	SubSection "Display"
		Depth	24
		Fbbpp	32
		Modes		"720x480"
	EndSubSection
	Option		"SecurityTypes"	"VncAuth"
	Option		"UserPasswdVerifier"	"VncAuth"
	Option		"PasswordFile"	"/root/.vnc/passwd"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "TV Screen"
	
	# There is other ways to get rid of keyboard and mouse, but you can these settings as is.
	# This setup is designed to run without keyboard and mouse plugged in.
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666#	Not	specifically	needed	as	far	as	I	know.
	# I think it's specific to my computer's hardware
	# That said all my ubuntu boxes have this line.
	
EndSection


---

### Post by volkswagner on 2007-12-24
> ssh -X connects to a regular ssh session.

after logging in or during the log in you need to call the app you want to use.

```
IE: ssh -X user@ipaddress synaptic
```

see my thread here as I was also having trouble and most people recommend ssh over vnc on local LAN

[http://ubuntuforums.org/showthread.php?t=645608]("http://ubuntuforums.org/showthread.php?t=645608")

[http://ubuntuforums.org/showthread.php?t=645169](http://ubuntuforums.org/showthread.php?t=645169)

Hope this helps

---

### Post by dougsnell on 2007-12-26
I suppose that makes sense; just odd that before I got x running on the 350 I was using VNC the way you and I were thinking originally.

What's the xfce manager?  I'm running strictly backend frontend ... I don't have any of the 3 desktops selected on the Control Centre.

Or would the recommendation be to simply install one?

---

