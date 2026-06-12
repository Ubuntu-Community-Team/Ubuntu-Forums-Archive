---
title: "Dual monitor with intel integrated graphics broke after upgrade"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by makhand on 2006-10-31
In this last upgrade to edgy, i've had some trouble getting X to work. At first, i would be able to log in and then after a few seconds in Gnome, my screen would go black and go back to the login screen. I was able to fix this using the 'sudo dpkg-reconfigure xserver-xorg'. 

Now, I'm trying to get my second monitor setup. I'm using mostly settings from my previous configuration which worked fine for dapper. I'm getting the same problem. Both monitors start up after i log in as expected. Then, sometime before all of the icons in the notification area are able to load, the screens go black and i'm taken to the log in screen. It may do this a couple times and then give me some X error output log. 

Here is the xorg.conf file i'm trying. I've played with a bunch of options and am getting quite frustrated at my inability to maintain a gnome session for longer than a few seconds. Please help. 

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
	#Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	#Load	"vbe"
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
	#Option		"UseFBDev"		"true"
	Option		"MonitorLayout" "CRT,LFP"	
	Screen 		0
EndSection
Section "Device"
	Identifier	"Intel1"
	Driver		"i810"
	#VideoRam	64000
	Option		"VBERestore" "no"
	#Option		"MonitorLayout" "CRT,LFP"
	Option		"DevicePresence"	"yes"
	BusID		"PCI:0:2:0"
	#Option		"AGPMode" "4"
	Screen		1
EndSection
Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection
Section "Monitor"
#	Option 		"CalcAlgorithm" "CheckDesktopGeometry"
	Identifier	"External Monitor"
#	HorizSync	30-70
	#HorizSync    	30-96
	#VertRefresh	50-150
	#HorizSync    	20-70
	#VertRefresh	40-100
	#Gamma		1.00
	Option		"DPMS"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
Section "Screen"
	Identifier	"VGA"
	Device		"Intel1"
	Monitor		"External Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
#				"1280x1024"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	#Screen		"Default Screen"
	Screen 0	"Default Screen"
	Screen 1 	"VGA" RightOf "Default Screen"
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

---

### Post by TigerCR1200 on 2006-10-31
Can you run a tail on your Xorg.0.log file and post that. It is in the /var/log. The command would be tail /var/log/Xorg.0.log. If they last 10 lines do not show an error try expanding it to be larger.

---

### Post by makhand on 2006-10-31
It looks like the first and second time it fails, there are two different log files.
The first one has: 

(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) AIGLX: Suspending AIGLX clients for VT switch
(WW) I810(0): Extended BIOS function 0x5f64 failed.
(WW) I810(0): Extended BIOS function 0x5f64 failed.
(WW) I810(0): Failed to set display devices to 0x900.
(WW) I810(0): Enabling LVDS directly. Pipe B.
(WW) I810(0): Enabling ADPA directly. Pipe B.
(WW) I810(0): Writing config directly to SWF0.
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
	the saved state
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(II) I810(0): xf86UnbindGARTMemory: unbind key 8
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(WW) I810(0): Successfully set original devices (2)

The second one has: 
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(**) I810(0): Option "MonitorLayout" "CRT,LFP"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(EE) I810(0): unknown reason for exception
(II) I810(0): EAX=0x00004f00, EBX=0x00000000, ECX=0x00000000, EDX=0x00000000
(II) I810(0): ESP=0x00000ffa, EBP=0x00000000, ESI=0x00000000, EDI=0x00002000
(II) I810(0): CS=0x7442, SS=0x0100, DS=0x0040, ES=0x0000, FS=0x0000, GS=0x0000
(II) I810(0): EIP=0x00010000, EFLAGS=0x00033246
(II) stack at 0x00001ffa:
 00 06 00 00 00 32
(II) I810(0): code at 0x00074420:
 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
(EE) I810(0): cannot continue
(II) I810(0): VESA BIOS not detected
(EE) I810(0): VBE initialization failed.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules/libvgahw.so
(**) I810(1): Depth 24, (--) framebuffer bpp 32
(==) I810(1): RGB weight 888
(==) I810(1): Default visual is TrueColor
(**) I810(1): Option "VBERestore" "no"
(**) I810(1): Option "DevicePresence" "yes"
(**) I810(1): Option "MonitorLayout" "CRT,LFP"
(II) I810(1): Integrated Graphics Chipset: Intel(R) 855GM
(--) I810(1): Chipset: "852GM/855GM"
(--) I810(1): Linear framebuffer at 0xE8000000
(--) I810(1): IO registers at addr 0xE0000000
(II) I810(1): 2 display pipes available.
(II) I810(1): detected 32636 kB stolen memory.

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/X11R6/bin/X(InitOutput+0x9c2) [0x809ff12]
3: /usr/X11R6/bin/X(main+0x276) [0x806e506]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d498cc]
5: /usr/X11R6/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting

The first on claims that i have a 'non-CRT' device connected. could that be the problem? One monitor is my laptop lcd, the other is a viewsonic p810 monitor (21 inch, huge old monitor). 

thanks for looking at this.

---

### Post by makhand on 2006-11-07
Can the problem be some of my configuration files? The fact is, the monitors both start up and load a few things but only 'crap out' right before all of the icons/shortcuts/system tray items load. Even with the second monitor disconnected, it doesnt work until i reset everything. Is there a way to clear all shortcuts, settings, etc that i had configured for the second screen. For example, when i look in ~/.gconf, i see a few settings set specifically for screen '1' (the second screen).

EDIT: Yes, it appears it was a problem with some configuration files. I dont really know which ones. I created a new test user on my laptop and reused the previous settings. Everything seems to be working fine for now. 

Does anyone know how can i clear the settings that apply to this second screen without deleting all of them?

---

### Post by makhand on 2006-11-07
This has got to be one of the most ridiculous bugs ever. 

I have narrowed down that the problem is not in:
~/.gconf
~/.gconfd
~/.gnome
~/.gnome2
~/.gnome2_private
~/.metacity
~/.nautilus

I have deleted all of the above with no effect. (well, it wiped out all my settings, but didnt fix the problem)

Still, when i have a two monitor setup. i have no issues logging in with a new user. When i try to log in using my previous user, where i have all my data, work, things installed, etc, X crashes a few seconds after gnome starts up. I have no more ideas left. Can someone please help me out?

---

