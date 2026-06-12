---
title: "3 monitor configuration"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by Jdog1928 on 2007-01-09
Hello, I am new to the site, and Ubuntu.
I Would like to be able to have display on three monitors. I have used this configuration with xandros and it worked great.
I have 2 video cards. I have twinview working right now, thanks to Ziox's excellent walk through. I love the speed of Xubuntu and was hoping it was possible to get all three of my monitors working.     Any help is greatly appreciated, Thanks!

---

### Post by majoridiot on 2007-01-10
i'm running 3 heads with an nvidia 5500 agp and a 5500 pci... two heads on the agp and one
on the pci.  it works very, very well.  here are the relevant bits from my xorg.conf to hopefully
help point the way.  the most important is probably the int10h option, to have x initialize your
your second card.

make sure this is included (with the other modules already listed):

```
Section "Module"
    Load           "int10"
EndSection
```

this defines the first card (substitute your pci bus address... discover with **lspci**):

```
Section "Device"
    Identifier      "NVIDIA Corporation NV34 [GeForce FX 5500]"
     Driver         "nvidia"
     BusID          "PCI:1:0:0"
     Option         "RenderAccel"      "True"
     Option         "ConnectedMonitor" "CRT, CRT"
EndSection

```

this defines the second (substitute your pci bus address... discover with **lspci**):
```
Section "Device"
   Identifier "PCI"
    Driver      "nvidia"
    BusID       "PCI:2:8:0"
    Option      "UseInt10Module" "1"
    Option      "NoLogo"   "1"
    Option      "RenderAccel"      "True"
EndSection
```

the screen definitions (one for heads 1&2, one for head 3):
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5500]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TwinView"
    Option         "NoTwinViewXineramaInfo" "1"
    Option         "NoLogo" "1"
    Option         "CursorShadow" "1"
    Option         "CoolBits" "1"
    Option         "NoPowerConnectorCheck"
    Option         "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 800x600,800x600; 1024x768,NULL; 800x600,NULL"
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Default Screen2"
    Device         "PCI"
    Monitor        "Generic Monitor2"
    DefaultDepth    24
    Option         "NoLogo" "1"
    Option         "CursorShadow" "1"
    Option         "CoolBits" "1"
    Option         "NoPowerConnectorCheck"
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

and the server layout:

```
Section "ServerLayout"
    Identifier     "idiot's three screen rig"
    Screen         "Default Screen" 0 0
    Screen         "Default Screen2" RightOf "Default Screen"
    InputDevice    "Configured Mouse"
    InputDevice    "Generic Keyboard"
EndSection

```

note that with this setup, heads 1&2 will be one large desktop and windows will maximize
to fill both screens.  head 3 will be an independent desktop.  you can drag icons, etc.
between 1/2 and 3, but not windows.  also, windows will not span across 1/2 & 3.

good luck! :D

---

### Post by Jdog1928 on 2007-01-11
My xorg,conf already had int10 option enabled, so I continued editing, one section at a time as to not completely goof it up. And my inexperience broke it. ](*,) 
Yes, I did have it backed up, but again, with my lack of experience of linux I was unable to roll back to my previous state.  I can't get X to load. 
Maybe I should be posting in the Complete Newbie section?
Thank you for the help. Hopefully I can get this worked out

---

### Post by majoridiot on 2007-01-11
forums are for learning, so no worries...

ok, first thing is to be able to quickly get a bare-bones x server working if you need to.  if you
mess things up beyond repair (or just want to start from scratch) use this command-

```
sudo dpkg-reconfigure xserver-xorg
```

this will generate a basic config file you can boot into x with.

next, to get you up to speed on restoring backed up files... 

```
 sudo cp /etc/X11/xorg.conf xorg.works
```

will back up the config file and to restore it-

```
 sudo cp /etc/X11/xorg.works xorg.conf
```

i'm betting that what's messing you up are the bus ids...  please post the complete result of the
foillowing command and we'll go from there:

```
lspci
```

we'll get a good config generated and get all 3 heads working before you know it :D

---

### Post by Jdog1928 on 2007-01-12
Ok, so I am starting from a fresh xorg.conf. Heres my lspci:

```
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
[COLOR="Red"]01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)[/COLOR]
02:00.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
02:01.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
[COLOR="Red"]02:02.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)[/COLOR]

```

Those are the two I used when I tried it the first time. I have my left two monitors on the FX 5200
and have to boot with PCI as primary video controller for all three to work in WIndows

Thanks so much for the help.  I apologize for taking so long to reply, but school has me pretty busy these days.

---

### Post by majoridiot on 2007-01-12
for the sake of expediency, please post your current (working) xorg.conf and answer the
following:

is  MX440 AGP or PCI?
is FX5200 AGP or PCI?
is bios set to boot from agp or pci video?

---

### Post by Jdog1928 on 2007-01-16
Weekends are usually s crazy time, my apologies.

My Xorg.conf:
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
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"ULTRASCANP99"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"ULTRASCANP99"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
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

MX 440 AGP single monitor
FX5200 PCI dual monitor
I have it set to AGP right now, because Xubuntu won't boot when set to PCI, though I assume PCI will have to be set once configured.
Thanks

---

### Post by majoridiot on 2007-01-17
ok... i think we've got it.  backup your xorg.conf, download the attached one, rename it 
xorg.conf, (make sure anything you don't want to lose is saved) and hit crtl-alt-bkspc to test
it.

if there are problems, be sure to post a copy of your /var/log/Xorg.0.log with your reply.

good luck!

---

### Post by Jdog1928 on 2007-01-22
Sorry, I haven't be able to try this. Been grounded for the past few days :(
I am gonna work on it tonight if I can. Hopefully we can get it too work.

---

