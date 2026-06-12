---
title: "Xinerama on a laptop with Intel GMA950"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by Jonathan Métillon on 2006-08-20
I have a laptop [Sony Vaio TX3]("http://crave.cnet.co.uk/laptops/0,39029450,49281462,00.htm") with a 11.1“ TFT WXGA 1366x768 mounted on a [Intel GMA950]("http://www.intel.com/products/chipsets/gma950/index.htm") which is part of the [Intel 945GM]("http://www.intel.com/products/chipsets/945gm/index.htm") chipset.

Now I want to connect an external TFT monitor [Dell 2007FPW]("http://support.dell.com/support/edocs/monitors/2007WFP/en/index.htm") using the VGA port.

My friend next to me use the same hardware setup and Windows XP. He just plugged and it worked. :o 

So I plugged the cord and it just went from "No VGA cable" to "Entering power save" and then blank screen... ](*,) 

The laptop runs Ubuntu 6.06 LTS. The GMA950 uses the i810 driver.

Following the [Xinerama HowTo]("http://ubuntuforums.org/showthread.php?t=221174") I tried to edit xorg.conf. I noticed in Xorg.0.log that the external display is detected and recognized. But it does not lite up.

I wonder if I did not inverted some references to internal display that should refer to the external and vice-versa. :-k 

Worse, the internal display is now displaying only 1024x768. I mean, the 1366x768 resolution is in use, but it really displays 1024. So it shows two black stripes on left and right of the display and I need to scroll with the cursor to go from one side to another. Very annoying. And I don't know how to fix this. And I didn't backup the original xorg.conf...

I googled a lot and tried everything I could to modify xorg.conf and get the internal display back to the good resolution and the external display to work. Please help! [-o< 

Here is the interesting output of *lspci* command

```

0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)

```

And here is my xorg.conf file (fonts, mouse and keyboard stuff removed)

```

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

# some parts from http://doc.gwos.org/index.php/Dual_Monitor_Intel_i810_i915
Section "Device"
	Identifier	"gma950"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev" "true"
	Option 		"MonitorLayout" "CRT,LFP"
	Option 		"DisplayInfo" "False"
	Screen		0
	Option 		"DevicePresence" "true"
	Option 		"ForceBIOS" "800x600=1366x768"
	# Option		"FlipPrimary" "true"
	Option		"VideoRAM" "131072"
	Option		"DRI" "True"
	Option		"XvMCSurfaces" "6"
EndSection

Section "Device"
	Identifier	"vgaout"
	Driver		"i810"
	BusID		"PCI:0:2:1"
	Option		"UseFBDev" "true"
	Option		"MonitorLayout" "CRT,LFP"
	Option		"DisplayInfo" "False"
	Screen		1
	# Option		"Rotate" "CCW"
	Option		"DevicePresence" "true"
	Option		"ForceBIOS" "1024x768=1680x1050"
	# Option		"FlipPrimary" "true"
	Option		"VideoRAM" "131072"
	Option		"DRI" "True"
	Option		"XvMCSurfaces" "6"
EndSection

Section "Monitor"
	Identifier	"internal"
	Option		"DPMS"
	# 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
  	Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795
EndSection

# specs here: http://support.dell.com/support/edocs/monitors/2007WFP/en/about.htm#Specifications
Section "Monitor"
	Identifier	"dell2007fpw"
	Option		"DPMS"
	HorizSync       30-81
        VertRefresh     56-76
	# 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  	Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087
EndSection

Section "Screen"
	Identifier	"builtinlcd"
	Device		"gma950"
	Monitor		"internal"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1366x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"externallcd"
	Device		"vgaout"
	Monitor		"dell2007fpw"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerFlags"
	Option		"Xinerama" "true"
EndSection

Section "ServerLayout"
	Identifier	"xinerama"
	Screen 0 	"builtinlcd" 0 0
	Screen 1 	"externallcd" Above "builtinlcd"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option 		"Xinerama" "true"
	# Option		"Xinerama" "on"
	Option		"MonitorLayout" "CRT,LFP"
	Option		"Clone" "off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

And finally, the output from Xorg.0.log. Empty line means removed unrelated or too verbose stuff.

```

Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 21 00:52:34 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "xinerama"
(**) |-->Screen "builtinlcd" (0)
(**) |   |-->Monitor "internal"
(**) |   |-->Device "gma950"
(**) |-->Screen "externallcd" (1)
(**) |   |-->Monitor "dell2007fpw"
(**) |   |-->Device "vgaout"

(**) Option "Xinerama" "true"
(**) Xinerama: enabled

(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
        i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
        915GM, 945G, 945GM
(II) Primary Device is: PCI 00:02:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 945GM found

(II) Setting vga for screen 0.

(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(**) I810(0): Option "DRI" "True"
(**) I810(0): Option "DisplayInfo" "False"
(**) I810(0): Option "DevicePresence" "true"
(**) I810(0): Option "MonitorLayout" "CRT,LFP"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) unknown chipset
(--) I810(0): Chipset: "945GM"
(--) I810(0): Linear framebuffer at 0xC0000000
(--) I810(0): IO registers at addr 0xD4100000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 7932 kB stolen memory.
(II) I810(0): Kernel reported 238592 total, 1 used
(II) I810(0): Checking Available AGP Memory: 954364 kB available (total 954368 kB, used 4 kB)
(II) I810(0): Monitoring connected displays enabled
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 12288 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 7932 kByte
(==) I810(0): VideoRAM: 65536 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 1281
(II) I810(0): Using new Pipe switch code
(**) I810(0): Device Presence: enabled.
(II) I810(0): Display Presence: CRT: attached: TRUE, encoder: TRUE
(II) I810(0): Display Presence: TV: attached: FALSE, encoder: FALSE
(II) I810(0): Display Presence: DFP (digital flat panel): attached: FALSE, encoder: FALSE
(II) I810(0): Display Presence: LFP (local flat panel): attached: TRUE, encoder: TRUE
(II) I810(0): Display Presence: CRT2 (second CRT): attached: FALSE, encoder: FALSE
(II) I810(0): Display Presence: TV2 (second TV): attached: FALSE, encoder: FALSE:
(II) I810(0): Display Presence: DFP2 (second digital flat panel): attached: FALSE, encoder: FALSE
(II) I810(0): Display Presence: LFP2 (second local flat panel): attached: FALSE, encoder: FALSE
(**) I810(0): Display Info: disabled.
(II) I810(0): No active displays on Pipe A.
(II) I810(0): Currently active displays on Pipe B:
(II) I810(0):   LFP (local flat panel)
(II) I810(0): No display size information available for pipe B.
(**) I810(0): Display is using Pipe B
(--) I810(0): Maximum frambuffer space: 65368 kByte
(II) I810(0): VESA VBE PanelID read successfully
(II) I810(0): PanelID returned panel resolution : 1366x768
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: DEL  Model: a018  Serial#: 810233932
(II) I810(0): Year: 2006  Week: 18
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) I810(0): Sync:  Separate  Composite  SyncOnGreen
(II) I810(0): Max H-Image Size [cm]: horiz.: 43  vert.: 27
(II) I810(0): Gamma: 2.20
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): Default color space is primary color space
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) I810(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): 1280x1024@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 146.2 MHz   Image Size:  434 x 270 mm
(II) I810(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) I810(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) I810(0): Serial No: HF7326560K0L
(II) I810(0): Monitor name: DELL 2007WFP
(II) I810(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 83 kHz, PixClock max 150 MHz
(--) I810(0): A non-CRT device is attached to pipe B.
        No refresh rate overrides will be attempted.
(--) I810(0): Maximum space available for video modes: 12288 kByte
(II) I810(0): Using detected DDC timings
(II) I810(0):   HorizSync 30-83
(II) I810(0):   VertRefresh 56-76

(II) I810(0): internal: Using hsync range of 30.00-83.00 kHz
(II) I810(0): internal: Using vrefresh range of 56.00-76.00 Hz
(II) I810(0): Not using mode "1366x768" (no mode of this name)
(1360x768,internal) mode clock 100000MHz exceeds DDC maximum 150MHz
(1360x768,internal) mode clock 100000MHz exceeds DDC maximum 150MHz
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1368 -> 2048).(--) I810(0): Virtual size is 1368x768 (pitch 2048)
(**) I810(0):  Built-in mode "1024x768"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
(++) I810(0): DPI set to (100, 100)

(WW) I810(0): Direct rendering is not supported when Xinerama is enabled
(EE) I810(0): [dri] DRIScreenInit failed. Disabling DRI.
(II) I810(0): Updated framebuffer allocation size from 8192 to 16384 kByte
(II) I810(0): Updated pixmap cache from 256 scanlines to 1280 scanlines

(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x00000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)

(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): direct rendering: Failed
(WW) I810(0): Option "UseFBDev" is not used
(WW) I810(0): Option "ForceBIOS" is not used
(WW) I810(0): Option "VideoRAM" is not used
(WW) I810(0): Option "XvMCSurfaces" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA

```

Thank you for your time!

---

### Post by Jonathan Métillon on 2006-08-21
> **Jonathan Métillon said:**
> Worse, the internal display is now displaying only 1024x768. I mean, the 1366x768 resolution is in use, but it really displays 1024. So it shows two black stripes on left and right of the display and I need to scroll with the cursor to go from one side to another.

Maybe I've not clearly described the issue. Here's a photo.

---

### Post by Jonathan Métillon on 2006-08-21
Also please notice that I installed [i810switch.]("http://packages.ubuntu.com/dapper/utils/i810switch") This tool should help me to enable the output to my external LCD panel, as the keyboard shortcut Fn+F7 to cycle around LCD, CRT and both displays does nothing with Ubuntu.

But when I run it, it says:

```
PCI id of i810 is not recognized.
```

I googled for that and I found this guy [here]("http://translate.google.com/translate?u=http%3A%2F%2Fblogs.globalinfinity.de%2F%3Fp%3D21&langpair=de%7Cen") that patched the app so his hardware is recognized.

Should I try that?

---

### Post by Jonathan Métillon on 2006-08-21
Finaly I downloaded sources [here]("http://packages.ubuntu.com/dapper/source/i810switch") and patched i810switch_0.6.5.orig.tar.gz with i810switch_0.6.5-2.diff.gz then edited i810switch.c and tried to add detection for my GMA950. But I don't really understand all this stuff :???: 

If someone could help me patch it, if only it's possible?

Here's some info about the PCIID:

```

$ lspci
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
$ lspci -n
0000:00:02.0 0300: 8086:27a2 (rev 03)
0000:00:02.1 0380: 8086:27a6 (rev 03)

```

I don't even know what is the device used for the external display. I would say that is 8086:27a2 because it's named *VGA compatible controller* but I might be wrong: in my xorg.conf the device used for the internal display also is 0:2:0 and not 0:2:1 so.... or maybe this is not even related :-k

---

### Post by Jonathan Métillon on 2006-08-21
Wow! I changed BusID "PCI:0:2:1" to BusID "PCI:0:2:0" in the "vgaout" device section and the external display is now working!

But I still have my issue with the resolution for the internal display.

Also, the external display is not using the good resolution. However I've set it to 1680x1050 in the "externallcd" screen section which is correct according to the [Dell specs.]("http://support.dell.com/support/edocs/monitors/2007WFP/en/index.htm")

Any idea?

---

### Post by Jonathan Métillon on 2006-08-21
I removed the ForceBIOS and Modeline options for both devices and both monitors and the external screen is now using the correct 1680x1050 resolution.

How that Dell panel rocks 8)

Well, now I need to fix that resolution issue for the internal display. Why would it only use 1024 pixels when the correct 1366 resolution is configured?  :confused:

---

### Post by Jonathan Métillon on 2006-08-23
Up!

Please someone help, I've been stuck with that for hours :cry:

---

### Post by loko on 2006-08-28
I cannot help you out, but maybe you can give some help.

I also have Intel GMA950 and i try to get the external LCD working.


I have also downloaded the i810switch and the diff, patched it, but i don't know what to change in the i810switch.c.

Is for the external source PCI:0:2:1, like you post it, correct, i read some posts with PCI:0:2:0 for external device also.

Can you tell me what exactly to do with it?

thanks a lot

loko

---

### Post by Jonathan Métillon on 2006-08-28
Hello Loko,

Me too I didn't know what to change in the i810switch.c.

And in fact the PCI:0:2:0 issue fixed my external display not being used. So I skiped the whole i810switch thing. It's not required as the vgaout is enabled by default!

So, to resume, don't use PCI:0:2:1 anywhere. Just use PCI:0:2:0 for both main display and external display. That's what worked for me.

---

### Post by loko on 2006-08-28
thanks for your fast answere.

i still have a problem to get vga out to work.

maybe you have an idea?

i used your xorg-conf, also i used this ```
Section "Device"
	Identifier "Intel Corporation Intel Default Card"
	Driver "i810"
	BusID "PCI:0:2:0"
	Option "MonitorLayout" "CRT,LFP"
	Option "Clone" "true"
EndSection
```

But the external screen, connected to the vga-out, keeps black.

if i disconnect the cable, then i get a message like "check your cable", comming up on the external mointor.

What is wrong?

---

### Post by Ziox on 2006-08-28
> **loko said:**
> thanks for your fast answere.

i still have a problem to get vga out to work.

maybe you have an idea?

i used your xorg-conf, also i used this ```
Section "Device"
	Identifier "Intel Corporation Intel Default Card"
	Driver "i810"
	BusID "PCI:0:2:0"
	Option "MonitorLayout" "CRT,LFP"
	Option "Clone" "true"
EndSection
```

But the external screen, connected to the vga-out, keeps black.

if i disconnect the cable, then i get a message like "check your cable", comming up on the external mointor.

What is wrong?

Anything that is connected via a VGA port is consider CRT, and, if using a laptop, the laptop screen is considered the main monitor...and "LVDS is laptop screen, and TMDS is externel LCD screen...

---

### Post by Jonathan Métillon on 2006-08-29
You have to explicitly number your screens. So in your first device definition, add this line:

```
Screen  0
```

And in your second device:

```
Screen  1
```

Then in your ServerLayout definition you will have something like:

```

Identifier  "xinerama"
Screen 0    "builtinlcd" 0 0
Screen 1    "externallcd" Above "builtinlcd"
Option      "Xinerama" "true"

```

As Ziox said, this may have something to do with your MonitorLayout option, but for me "CRT,LFP" works.

If you're still in trouble, post your full xorg.conf.

---

### Post by loko on 2006-08-29
I add my xord.conf, because i didn't get it to work with your tips.

I numbered my screens and put in the server-section like you said
Code:

```
Identifier  "xinerama"
Screen 0    "builtinlcd" 0 0
Screen 1    "externallcd" Above "builtinlcd"
Option      "Xinerama" "true"
```

but then the gdm did not start anymore so i think i missunderstood something.

so here is the xorg.conf


```
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
	Load	"v4l"
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
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		0
EndSection

Section "Device"
	Identifier "Intel Corporation Intel Default Card"
	Driver "i810"
	BusID "PCI:0:2:0"
	Option "MonitorLayout" "CRT,LFP"
	Option "Clone" "true"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Standardbildschirm"
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


Can you take a look please?

---

### Post by Jonathan Métillon on 2006-08-29
Loko,

First I think you have to understand the basics of xorg.conf with dual monitor!

This great  [Xinerama HowTo]("http://www.ubuntuforums.org/showthread.php?t=221174") from Ziox will help you.

Basically, you should add Monitor and Screen sections for you external display, then you will bind them in the ServerLayout. Currently you have two Devices defined, which is good, but you need one more Monitor and one more Screen.

---

### Post by Jonathan Métillon on 2006-09-26
Back in trouble again.

I reinstalled Ubuntu. My internal screen was again fully used. I mean, really 16:9 widescreen, not 4:3, having two black spaces on left and right like you can see on my attached photo, having to scroll to use the 1366 horizontal pixels.

And I wanted to retry the configuration of my external display. But this time I did not forget to backup my original xorg.conf.

I managed to get my external display working as expected. But my internal screen was using a 1368x768 resolution instead of 1366x768. So I tried different things I discovered while trying to get my external working. I added these lines to my first device. I don't really know what they all mean.

```
	Option		"UseFBDev" "true"
	Option 		"DisplayInfo" "False"
	Option 		"DevicePresence" "true"
	Option 		"ForceBIOS" "800x600=1366x768"
	Option		"VideoRAM" "131072"
	Option		"DRI" "True"
	Option		"XvMCSurfaces" "6"
```

Damn, my screen is back again to a 4:3 ratio! Ok no problem I remove these lines... OMG, it's not coming back to 16:9! I put back the original xorg.conf file, and it's still broken!!

How can this be? What line caused this? How is that possible that a setting seems now hardcoded in the device or somewhere else in the Ubuntu conf?

Oh please help, I don't want to reinstall Ubuntu one more time! ](*,)

---

### Post by Ziox on 2006-09-26
I know this command generates a basic xorg.conf file:

sudo dpkg-reconfigure xserver-xorg

but before you do that, what is in your xorg.conf file?

---

### Post by Jonathan Métillon on 2006-09-27
Thank you for your time Xiox!

Here is the content of my current xorg.conf:

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
  FontPath  "/usr/share/X11/fonts/misc"
  FontPath  "/usr/share/X11/fonts/cyrillic"
  FontPath  "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath  "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath  "/usr/share/X11/fonts/Type1"
  FontPath  "/usr/share/X11/fonts/100dpi"
  FontPath  "/usr/share/X11/fonts/75dpi"
  # path to defoma fonts
  FontPath  "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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

Section "InputDevice"
  Identifier  "Generic Keyboard"
  Driver      "kbd"
  Option      "CoreKeyboard"
  Option      "XkbRules"    "xorg"
  Option      "XkbModel"    "pc105"
  Option      "XkbLayout"   "fr"
  Option      "XkbVariant"  "latin9"
EndSection

Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver      "mouse"
  Option      "CorePointer"
  Option      "Device"      "/dev/input/mice"
  Option      "Protocol"    "ExplorerPS/2"
  Option      "ZAxisMapping"     "4 5"
  Option      "Emulate3Buttons"  "true"
EndSection

Section "InputDevice"
  Identifier  "Synaptics Touchpad"
  Driver      "synaptics"
  Option      "SendCoreEvents"  "true"
  Option      "Device"      "/dev/psaux"
  Option      "Protocol"    "auto-dev"
  Option      "HorizScrollDelta"  "0"
EndSection

Section "Device"
  Identifier  "GMA950"
  Driver      "i810"
  BusID       "PCI:0:2:0"
  Option      "MonitorLayout" "CRT,LFP"
  Screen      0
EndSection

Section "Device"
  Identifier  "GMA950-VGAOUT"
  Driver      "i810"
  BusID       "PCI:0:2:0"
  Screen      1
EndSection

Section "Monitor"
  Identifier  "Internal"
  Option      "DPMS"
EndSection

Section "Monitor"
  Identifier  "2007FPW"
  Option      "DPMS"
  HorizSync   30-81
  VertRefresh 56-76
EndSection

Section "Screen"
  Identifier  "Screen-1"
  Device      "GMA950"
  Monitor     "Internal"
  DefaultDepth  24
  SubSection "Display"
    Depth     1
    Modes     "1366x768"
  EndSubSection
  SubSection "Display"
    Depth     4
    Modes     "1366x768"
  EndSubSection
  SubSection "Display"
    Depth     8
    Modes     "1366x768"
  EndSubSection
  SubSection "Display"
    Depth     15
    Modes     "1366x768"
  EndSubSection
  SubSection "Display"
    Depth     16
    Modes     "1366x768"
  EndSubSection
  SubSection "Display"
    Depth     24
    Modes     "1366x768"
  EndSubSection
EndSection

Section "Screen"
  Identifier  "Screen-2"
  Device      "GMA950-VGAOUT"
  Monitor     "2007FPW"
  DefaultDepth  24
  SubSection "Display"
    Depth     1
    Modes     "1680x1050"
  EndSubSection
  SubSection "Display"
    Depth     4
    Modes     "1680x1050"
  EndSubSection
  SubSection "Display"
    Depth     8
    Modes     "1680x1050"
  EndSubSection
  SubSection "Display"
    Depth     15
    Modes     "1680x1050"
  EndSubSection
  SubSection "Display"
    Depth     16
    Modes     "1680x1050"
  EndSubSection
  SubSection "Display"
    Depth     24
    Modes     "1680x1050"
  EndSubSection
EndSection

Section "ServerFlags"
  DefaultServerLayout "Multihead"
EndSection

Section "ServerLayout"
  Identifier  "Multihead"
  Option      "Xinerama" "true"
  Screen 0    "Screen-1" 0 0
  Screen 1    "Screen-2" Above "Screen-1"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "Synaptics Touchpad"
EndSection

Section "ServerLayout"
  Identifier  "Default"
  Screen      "Screen-1"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "Synaptics Touchpad"
EndSection
```

Should I try the dpkg-reconfigure?

---

### Post by Ziox on 2006-09-27
I've edited somethings in your xorg.conf file...see if these work:

```

Section "Device"
  Identifier  "GMA950"
  Driver      "i810"
  BusID       "PCI:0:2:0"
  Option      "MonitorLayout" "_LFP,CRT_"
  Screen      0
EndSection

Section "Device"
  Identifier  "GMA950-VGAOUT"
  Driver      "i810"
  BusID       "PCI:0:2:0"
  **Option      "MonitorLayout" "_LFP,CRT_"**
  Screen      1
EndSection

Section "Monitor"
  Identifier  "Internal"
  Option      "DPMS"
  [B]HorizSync       30-65
  VertRefresh     50-75[/B]
EndSection

Section "Monitor"
  Identifier  "2007FPW"
  Option      "DPMS"
  HorizSync   30-81
  VertRefresh 56-76
EndSection

Section "Screen"
  Identifier  "Screen-1"
  Device      "GMA950"
  Monitor     "Internal"
  DefaultDepth ** 24** #Try changing this to 16 or something lower
  SubSection "Display"
    Depth     1
    Modes     "1366x768"
  EndSubSection
  SubSection "Display"
    Depth     4
    Modes     "1366x768"
  EndSubSection
  SubSection "Display"
    Depth     8
    Modes     "1366x768"
  EndSubSection
  SubSection "Display"
    Depth     15
    Modes     "1366x768"
  EndSubSection
  SubSection "Display"
    Depth     16
    Modes     "1366x768"
  EndSubSection
  SubSection "Display"
    Depth     24
    Modes     "1366x768"
  EndSubSection
EndSection

Section "Screen"
  Identifier  "Screen-2"
  Device      "GMA950-VGAOUT"
  Monitor     "2007FPW"
  DefaultDepth  24
  SubSection "Display"
    Depth     1
    Modes     "1680x1050"
  EndSubSection
  SubSection "Display"
    Depth     4
    Modes     "1680x1050"
  EndSubSection
  SubSection "Display"
    Depth     8
    Modes     "1680x1050"
  EndSubSection
  SubSection "Display"
    Depth     15
    Modes     "1680x1050"
  EndSubSection
  SubSection "Display"
    Depth     16
    Modes     "1680x1050"
  EndSubSection
  SubSection "Display"
    Depth     24
    Modes     "1680x1050"
  EndSubSection
EndSection

Section "ServerFlags"
  DefaultServerLayout "Multihead"
EndSection

Section "ServerLayout"
  Identifier  "Multihead"
  Option      "Xinerama" "true"
  Screen 0    "Screen-1" 0 0
  Screen 1    "Screen-2" Above "Screen-1"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "Synaptics Touchpad"
EndSection

Section "ServerLayout"
  Identifier  "Default"
  Screen      "Screen-1"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "Synaptics Touchpad"
EndSection
```

---

### Post by Jonathan Métillon on 2006-09-28
The new HorizSync and VertRefresh for Internal Monitor did not help, neither changing the screens DefaultDepth.

The LFP,CRT lines caused X to fail and throw:

```
(EE) I810(1): Set VBE Mode failed!

Fatal server error:
AddScreen/ScreenInit failed for driver 1
```

And I noticed these warnings I get all the time, even with the original xorg.conf:

```
(1360x768,Generic Monitor) mode clock 100000Mhz exceeds DDC maximum 150Mhz
(1360x768,Generic Monitor) mode clock 100000Mhz exceeds DDC maximum 150Mhz
```

(it is repeated 2 times)

And when it failed because of the LFP,CRT lines, this warning appeared additionnaly:

```
(1600x1200,Generic Monitor) mode clock 162Mhz exceeds DDC maximum 150Mhz
```

Maybe this has something to do with my issue?

I think this is not related but I also have this error:

```
(EE) I810(0): [dri] DRIScreenInit failed. Disabling DRI.
```

I think this is due to the Load	"dri" line in the Module section.

Any clue?

---

### Post by Jonathan Métillon on 2006-09-28
None of the Generic Monitor warnings appear if I use 1024x768 instead of 1366x768 as Screen-1 Display Modes.

Something is tricking my system into thinking that my device or my monitor is not able to display more than 1024x768.

---

### Post by Jonathan Métillon on 2006-09-28
Here is the log of a X session starting, using the xorg.conf I posted yesteday. I removed some details, as messages are limited to 40000 chars.

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux john-tx 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 28 10:21:56 2006
(==) Using config file: "/etc/X11/xorg.conf"
(**) Option "defaultserverlayout" "Multihead"
(**) ServerLayout "Multihead"
(**) |-->Screen "Screen-1" (0)
(**) |   |-->Monitor "Internal"
(**) |   |-->Device "GMA950"
(**) |-->Screen "Screen-2" (1)
(**) |   |-->Monitor "2007FPW"
(**) |   |-->Device "GMA950-VGAOUT"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "true"
(**) Xinerama: enabled
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 7

(II) Intel Bridge workaround enabled
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM
(II) Primary Device is: PCI 00:02:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 945GM found
(--) Chipset 945GM found
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(**) I810(0): Depth 16, (--) framebuffer bpp 16
(==) I810(0): RGB weight 565
(==) I810(0): Default visual is TrueColor
(**) I810(0): Option "MonitorLayout" "CRT,LFP"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) unknown chipset
(--) I810(0): Chipset: "945GM"
(--) I810(0): Linear framebuffer at 0xC0000000
(--) I810(0): IO registers at addr 0xD4100000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 7932 kB stolen memory.
(II) I810(0): Kernel reported 363776 total, 1 used
(II) I810(0): Checking Available AGP Memory: 1455100 kB available (total 1455104 kB, used 4 kB)
(II) I810(0): Monitoring connected displays enabled
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12288 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 12288 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 7932 kByte
(==) I810(0): VideoRAM: 131072 kByte
(==) I810(0): video overlay key set to 0x83e
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 1281
(II) I810(0): Using new Pipe switch code
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: TRUE, present: TRUE, size: (640,400)
(II) I810(0): Display Info: TV: attached: FALSE, present: FALSE, size: (0,2313)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,2313)
(II) I810(0): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1366,768)
(II) I810(0): Display Info: CRT2 (second CRT): attached: FALSE, present: FALSE, size: (0,2313)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,2313)
(II) I810(0): Size of device LFP (local flat panel) is 1366 x 768
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0): 	CRT
(II) I810(0): Currently active displays on Pipe B:
(II) I810(0): 	LFP (local flat panel)
(II) I810(0): Lowest common panel size for pipe B is 1366 x 768
(==) I810(0): Primary head is using Pipe B
(--) I810(0): Maximum frambuffer space: 130904 kByte
(II) I810(0): VESA VBE PanelID read successfully
(II) I810(0): PanelID returned panel resolution : 1366x768
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: DEL  Model: a018  Serial#: 825444940
(II) I810(0): Year: 2006  Week: 18
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) I810(0): Sync:  Separate  Composite  SyncOnGreen
(II) I810(0): Max H-Image Size [cm]: horiz.: 43  vert.: 27
(II) I810(0): Gamma: 2.20
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): Default color space is primary color space
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) I810(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): 1280x1024@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 146.2 MHz   Image Size:  434 x 270 mm
(II) I810(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) I810(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) I810(0): Serial No: HF73265613JL
(II) I810(0): Monitor name: DELL 2007WFP
(II) I810(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 83 kHz, PixClock max 150 MHz
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(--) I810(0): Maximum space available for video modes: 12288 kByte
(II) I810(0): Using detected DDC timings
(II) I810(0): 	HorizSync 30-83
(II) I810(0): 	VertRefresh 56-76
Mode: 30 (640x480)
Mode: 32 (800x600)
Mode: 34 (1024x768)
Mode: 38 (0x0)
Mode: 3a (0x0)
Mode: 3c (0x0)
*Mode: 41 (640x480)
*Mode: 43 (800x600)
*Mode: 45 (1024x768)
Mode: 49 (0x0)
Mode: 4b (0x0)
Mode: 4d (0x0)
Mode: 50 (640x480)
Mode: 52 (800x600)
Mode: 54 (1024x768)
Mode: 58 (0x0)
Mode: 5a (0x0)
Mode: 5c (0x0)
Mode: 60 (1366x768)
*Mode: 61 (1366x768)
Mode: 62 (1366x768)
Mode: 63 (0x0)
Mode: 64 (0x0)
Mode: 65 (0x0)
Mode: 66 (0x0)
Mode: 67 (0x0)
Mode: 68 (0x0)
Mode: 69 (1360x768)
*Mode: 6a (1360x768)
Mode: 6b (1360x768)
Mode: 6c (0x0)
Mode: 6d (0x0)
Mode: 6e (0x0)
Mode: 6f (0x0)
Mode: 70 (0x0)
Mode: 71 (0x0)
(II) I810(0): Internal: Using hsync range of 30.00-83.00 kHz
(II) I810(0): Internal: Using vrefresh range of 56.00-76.00 Hz
(II) I810(0): Not using mode "1366x768" (no mode of this name)
(1360x768,Internal) mode clock 100000MHz exceeds DDC maximum 150MHz
(1360x768,Internal) mode clock 100000MHz exceeds DDC maximum 150MHz
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1368 -> 2048).
(--) I810(0): Virtual size is 1368x768 (pitch 2048)
(**) I810(0):  Built-in mode "1024x768"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
(++) I810(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(==) I810(0): VBE Restore workaround: enabled.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules/libvgahw.so
(**) I810(1): Depth 16, (--) framebuffer bpp 16
(==) I810(1): RGB weight 565
(==) I810(1): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(1): Integrated Graphics Chipset: Intel(R) unknown chipset
(--) I810(1): Chipset: "945GM"
(--) I810(1): Linear framebuffer at 0xC0000000
(--) I810(1): IO registers at addr 0xD4100000
(II) I810(1): 2 display pipes available.
(II) I810(1): detected 7932 kB stolen memory.
(II) I810(1): Monitoring connected displays enabled
(II) I810(1): Will attempt to tell the BIOS that there is 12224 kB VideoRAM
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12224 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(1): BIOS now sees 12224 kB VideoRAM
(--) I810(1): Pre-allocated VideoRAM: 7932 kByte
(==) I810(1): VideoRAM: 12288 kByte
(==) I810(1): video overlay key set to 0x83e
(**) I810(1): page flipping disabled
(==) I810(1): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(1): BIOS Build: 1281
(II) I810(1): Using new Pipe switch code
(==) I810(1): Device Presence: disabled.
(==) I810(1): Display Info: enabled.
(II) I810(1): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(II) I810(1): Display Info: CRT: attached: TRUE, present: TRUE, size: (720,400)
(II) I810(1): Display Info: TV: attached: FALSE, present: FALSE, size: (0,2313)
(II) I810(1): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,2313)
(II) I810(1): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1366,768)
(II) I810(1): Display Info: CRT2 (second CRT): attached: FALSE, present: FALSE, size: (0,2313)
(II) I810(1): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,2313)
(II) I810(1): Size of device LFP (local flat panel) is 1366 x 768
(II) I810(1): Currently active displays on Pipe A:
(II) I810(1): 	CRT
(II) I810(1): Currently active displays on Pipe B:
(II) I810(1): 	LFP (local flat panel)
(II) I810(1): Lowest common panel size for pipe B is 1366 x 768
(==) I810(1): Secondary head is using Pipe A
(--) I810(1): Using HW Cursor because it's enabled on primary head.
(--) I810(1): Maximum frambuffer space: 12120 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: DEL  Model: a018  Serial#: 825444940
(II) I810(0): Year: 2006  Week: 18
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) I810(0): Sync:  Separate  Composite  SyncOnGreen
(II) I810(0): Max H-Image Size [cm]: horiz.: 43  vert.: 27
(II) I810(0): Gamma: 2.20
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): Default color space is primary color space
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) I810(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): 1280x1024@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 146.2 MHz   Image Size:  434 x 270 mm
(II) I810(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) I810(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) I810(0): Serial No: HF73265613JL
(II) I810(0): Monitor name: DELL 2007WFP
(II) I810(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 83 kHz, PixClock max 150 MHz
(II) I810(1): Will use BIOS call 0x5f05 to set refresh rates for CRTs.
(--) I810(1): Maximum space available for video modes: 12120 kByte
(II) I810(1): Using detected DDC timings
(II) I810(1): 	HorizSync 30-83
(II) I810(1): 	VertRefresh 56-76
Mode: 30 (640x480)
Mode: 32 (800x600)
Mode: 34 (1024x768)
Mode: 38 (1280x1024)
Mode: 3a (1600x1200)
Mode: 3c (1920x1440)
*Mode: 41 (640x480)
*Mode: 43 (800x600)
*Mode: 45 (1024x768)
*(WW) (1280x1024,2007FPW) mode clock 157.5MHz exceeds DDC maximum 150MHz
Mode: 49 (1280x1024)
*(WW) (1600x1200,2007FPW) mode clock 162MHz exceeds DDC maximum 150MHz
(WW) (1600x1200,2007FPW) mode clock 175.5MHz exceeds DDC maximum 150MHz
(WW) (1600x1200,2007FPW) mode clock 189MHz exceeds DDC maximum 150MHz
(WW) (1600x1200,2007FPW) mode clock 202.5MHz exceeds DDC maximum 150MHz
(WW) (1600x1200,2007FPW) mode clock 229.5MHz exceeds DDC maximum 150MHz
Mode: 4b (1600x1200)
*(WW) (1920x1440,2007FPW) mode clock 234MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 297MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 341.35MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 297.395MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 297.395MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 297.395MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 297.395MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 283.392MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 283.392MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 283.392MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 275.152MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 275.152MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 233.155MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 233.155MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 233.155MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 233.155MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 233.155MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 233.155MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 233.155MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 233.155MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 233.155MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 233.155MHz exceeds DDC maximum 150MHz
(WW) (1920x1440,2007FPW) mode clock 217.027MHz exceeds DDC maximum 150MHz
Mode: 4d (1920x1440)
Mode: 50 (640x480)
Mode: 52 (800x600)
Mode: 54 (1024x768)
Mode: 58 (1280x1024)
Mode: 5a (1600x1200)
Mode: 5c (1920x1440)
Mode: 60 (1366x768)
*Mode: 61 (1366x768)
Mode: 62 (1366x768)
Mode: 63 (1280x800)
*Mode: 64 (1280x800)
Mode: 65 (1280x800)
Mode: 66 (1680x1050)
*(WW) (1680x1050,2007FPW) mode clock 214.51MHz exceeds DDC maximum 150MHz
Mode: 67 (1680x1050)
Mode: 68 (1680x1050)
Mode: 69 (1360x768)
*Mode: 6a (1360x768)
Mode: 6b (1360x768)
Mode: 6c (0x0)
Mode: 6d (0x0)
Mode: 6e (0x0)
Mode: 6f (0x0)
Mode: 70 (0x0)
Mode: 71 (0x0)
(II) I810(1): 2007FPW: Using hsync range of 30.00-83.00 kHz
(II) I810(1): 2007FPW: Using vrefresh range of 56.00-76.00 Hz
(II) I810(1): Correcting stride (1680 -> 3392)
(--) I810(1): Virtual size is 1680x1050 (pitch 1696)
(**) I810(1): *Built-in mode "1680x1050"
(II) I810(1): Attempting to use 60.00Hz refresh for mode "1680x1050" (867)
(++) I810(1): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules/libfb.so
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules/libxaa.so
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Reloading /usr/lib/xorg/modules/libramdac.so
(==) I810(1): VBE Restore workaround: enabled.
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 384 scanlines for pixmap cache
(II) I810(0): Secondary framebuffer allocation size: 4752 kByte
(II) I810(0): Allocating at least 384 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 4608 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0xffff000 (0x272f6000)
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0xfffb000 (0x1c840000)
(II) I810(0): Allocated 4 kB for Overlay registers at 0xfffa000 (0x17ea6000).
(II) I810(0): Allocated 64 kB for the scratch buffer at 0xffea000
(II) I810(0): Allocated 64 kB for the second scratch buffer at 0xffda000
(WW) I810(0): Direct rendering is not supported when Xinerama is enabled
(EE) I810(0): [dri] DRIScreenInit failed. Disabling DRI.
(II) I810(0): Updated framebuffer allocation size from 4608 to 8192 kByte
(II) I810(0): Updated pixmap cache from 384 scanlines to 1280 scanlines
(II) I810(0): 0x81ffcfc: Memory at offset 0x00020000, size 4752 kBytes
(II) I810(0): 0x81ffcdc: Memory at offset 0x004d0000, size 8192 kBytes
(II) I810(0): 0x8204a90: Memory at offset 0x0ffff000, size 4 kBytes
(II) I810(0): 0x8204bf0: Memory at offset 0x0fffb000, size 16 kBytes
(II) I810(0): 0x82047dc: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x81ffd1c: Memory at offset 0x0ffea000, size 64 kBytes
(II) I810(0): 0x81ffd3c: Memory at offset 0x0ffda000, size 64 kBytes
(II) I810(0): 0x8204938: Memory at offset 0x0fffa000, size 4 kBytes
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0ffda000 (pgoffset 65498)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(II) I810(0): Display plane A is enabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane A.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now enabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x80000000
(II) I810(0): PIPEBCONF is 0x80000000
(WW) I810(0): Correcting plane A stride (640 -> 1696)
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 126 Mbyte/s, 0 Mbyte/s
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		19 256x256 slots
		5 512x512 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): direct rendering: Failed
(==) RandR enabled
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12288 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(1): Extended BIOS function 0x5f05 failed.
(II) I810(1): Setting refresh with VBE 3 method.
(II) I810(1): Display plane A is enabled and connected to Pipe A.
(II) I810(1): Display plane B is enabled and connected to Pipe B.
(II) I810(1): Enabling plane A.
(II) I810(1): Enabling plane B.
(II) I810(1): Display plane A is now enabled and connected to Pipe A.
(II) I810(1): Display plane B is now enabled and connected to Pipe B.
(II) I810(1): PIPEACONF is 0x80000000
(II) I810(1): PIPEBCONF is 0x80000000
(II) I810(1): Mode bandwidth is 105 Mpixel/s
(WW) I810(1): Extended BIOS function 0x5f28 failed.
(II) I810(1): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		23 128x128 slots
		4 256x256 slots
(==) I810(1): Backing store disabled
(==) I810(1): Silken mouse enabled
(II) I810(1): Initializing HW Cursor
(**) Option "dpms"
(**) I810(1): DPMS enabled
(II) I810(1): direct rendering: Disabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "fr"
(**) Generic Keyboard: XkbLayout: "fr"
(**) Option "XkbVariant" "latin9"
(**) Generic Keyboard: XkbVariant: "latin9"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) Synaptics touchpad driver version 0.14.3
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found
ProcXCloseDevice to close or not ?
```

Display info seem correct:

```
(II) I810(0): Display Info: CRT: attached: TRUE, present: TRUE, size: (640,400)
(II) I810(0): Display Info: TV: attached: FALSE, present: FALSE, size: (0,2313)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,2313)
(II) I810(0): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1366,768)
(II) I810(0): Display Info: CRT2 (second CRT): attached: FALSE, present: FALSE, size: (0,2313)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,2313)
(II) I810(0): Size of device LFP (local flat panel) is 1366 x 768
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0): 	CRT
(II) I810(0): Currently active displays on Pipe B:
(II) I810(0): 	LFP (local flat panel)
(II) I810(0): Lowest common panel size for pipe B is 1366 x 768
(==) I810(0): Primary head is using Pipe B
(--) I810(0): Maximum frambuffer space: 130904 kByte
(II) I810(0): VESA VBE PanelID read successfully
(II) I810(0): PanelID returned panel resolution : 1366x768
```

Internal display is correctly detected at 1366x768. Why 640x400 for external display?

Then...

```
(II) I810(0): Internal: Using hsync range of 30.00-83.00 kHz
(II) I810(0): Internal: Using vrefresh range of 56.00-76.00 Hz
(II) I810(0): Not using mode "1366x768" (no mode of this name)
(1360x768,Internal) mode clock 100000MHz exceeds DDC maximum 150MHz
(1360x768,Internal) mode clock 100000MHz exceeds DDC maximum 150MHz
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1368 -> 2048).
(--) I810(0): Virtual size is 1368x768 (pitch 2048)
```

Now it refuses the 1366x768. Why?

```
(II) I810(1): BIOS now sees 12224 kB VideoRAM
(--) I810(1): Pre-allocated VideoRAM: 7932 kByte
(==) I810(1): VideoRAM: 12288 kByte
```

[The specs]("http://www.intel.com/products/chipsets/gma950/index.htm") tells that it can borrow up to 244MB. Why not increase that? Maybe it can help for higher resolution?
Or this is only related to the speed? The specs tells the core is running at 400MHz. So what is that DDC maximum 150MHz?

---

### Post by Jonathan Métillon on 2006-10-24
I finally found what's causing this mess: I have to unplug the external display before booting, then logging and when GNOME is loaded, I plug the display. Now it works: I have correct resolutions on my internal (1366x768) and external (1680x1050) displays using my GMA950 GPU.

I think that if the external display is connected at boot, it sends informations to the video BIOS which makes it in turn sends false information to the xserver.

Also I disabled Xinerama. That way I can plug/unplug my external display at will, without restarting my X session and use different ServerLayouts.

---

### Post by barak on 2006-10-24
Could you do me a favour and post your xorg.conf so I could take a look - I have been having trouble with my external monitor and its default resolution with the i810 driver and think that you're solution might be applicable to me.  Thanks!

---

### Post by Jonathan Métillon on 2006-10-24
Here it is barak:

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
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "fr"
    Option        "XkbVariant"    "latin9"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
EndSection

Section "Device"
    Identifier    "GMA950"
    Driver        "i810"
    BusID        "PCI:0:2:0"
    Screen        0
  Option      "MonitorLayout" "CRT,LFP"
EndSection

Section "Device"
    Identifier    "GMA950-VGAOUT"
    Driver        "i810"
    BusID        "PCI:0:2:0"
    Screen        1
EndSection

Section "Monitor"
    Identifier    "Internal"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier    "2007FPW"
    Option        "DPMS"
    HorizSync       30-81
  VertRefresh     56-76
EndSection

Section "Screen"
    Identifier    "Screen-1"
    Device        "GMA950"
    Monitor        "Internal"
    DefaultDepth    16
    SubSection "Display"
        Depth        1
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1366x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1366x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Screen-2"
    Device        "GMA950-VGAOUT"
    Monitor        "2007FPW"
    DefaultDepth    16
    SubSection "Display"
        Depth        1
        Modes        "1680x1050"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1680x1050"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1680x1050"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1680x1050"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1680x1050"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1680x1050"
    EndSubSection
EndSection

Section "ServerFlags"
    DefaultServerLayout    "Multihead"
EndSection

Section "ServerLayout"
    Identifier    "Multihead"
    Option        "Xinerama" "false"
    Screen 0     "Screen-1" 0 0
    Screen 1     "Screen-2" Above "Screen-1"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice "Synaptics Touchpad"
EndSection

Section "ServerLayout"
    Identifier    "Default"
    Screen        "Screen-1"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice "Synaptics Touchpad"
EndSection
```Notice that with this configuration I don't have direct rendering (DRI) on any screen. I've read that if Xinerama is not enabled it's possible to enable DRI for both screens. Someone have a tip for that?

---

### Post by wmadan on 2006-11-21
Jonathan,

I just wanted you to know that I have the same GMA950 integrated graphics card on my Lenovo laptop. I copied your xorg.conf file, changed the resolutions to match my laptop LCD and external monitor and everything works.

I spent hours trying to get my external monitor to work with Edgy. Thanks a ton!

Bill

---

### Post by Jonathan Métillon on 2006-11-21
I'm really glad to hear it :-)

But I'm experiencing a bad issue with Edgy: whatever application using a certain lib, I think one related to 3D rendering like OpenGL, will cause the X server to crash.

It happens for example with any screensaver, with glxgears, and even OpenOffice.org applications!

Do you experience that?

---

### Post by MTZeon on 2006-11-22
You'll need to add at the end

Section "Extensions"
 Option "Composite" "true"
EndSection

;)

---

### Post by Jonathan Métillon on 2006-11-22
Thank you MTZeon!

I tried this, but no luck. I created a [new thread]("http://ubuntuforums.org/showthread.php?p=1793987#post1793987") for my issue.

---

### Post by wmadan on 2006-11-24
> **Jonathan Métillon said:**
> I'm really glad to hear it :-)

But I'm experiencing a bad issue with Edgy: whatever application using a certain lib, I think one related to 3D rendering like OpenGL, will cause the X server to crash.

It happens for example with any screensaver, with glxgears, and even OpenOffice.org applications!

Do you experience that?

Jonathan,

Yes, if the screensaver starts, I lose the X server. Have you had any breakthroughs yet on what may be causing this?

Bill

---

### Post by Jonathan Métillon on 2006-11-24
Yes I think this is related to XGL. Please see the thread where I pointed to in my last post.

---

