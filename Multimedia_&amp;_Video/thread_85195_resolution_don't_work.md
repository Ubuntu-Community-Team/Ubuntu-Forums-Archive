---
title: "resolution don't work"
date: 2005-11-02
forum: Multimedia &amp; Video
---

### Post by Vitaliy on 2005-11-02
can't setup resolution 1125x864,  my hardw:
lg flatron t711b "17, internal video card  on i810 (detected by installation process)

my xorg.conf:


Section "Device"
        Identifier      "Intel Corporation 82865G Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        32768 (and 65536 i've tried too)
EndSection

Section "Monitor"
        Identifier      "T711B"
        Option          "DPMS"
        HorizSync       30-71
        VertRefresh     50-160
        # 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
        Modeline "1152x864_75.00"  104.99  1152 1224 1352 1552  864 865 868 902  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics Device"
        Monitor         "T711B"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768"
        EndSubSection
EndSection



so when i restart gnome (gdm), "Screen Resolution"  show standard resolutions: "1280x1024" "1024x768" "800x600" "640x480", but there is not 1152x864

help me please :)

---

### Post by Teroedni on 2005-11-02
Your near:)
I added "1152x864@75" to display at 24 depth should work now



```
Section "Device"
Identifier "Intel Corporation 82865G Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
VideoRam 32768 (and 65536 i've tried too)
EndSection

Section "Monitor"
Identifier "T711B"
Option "DPMS"
HorizSync 30-71
VertRefresh 50-160
# 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
Modeline "1152x864_75.00" 104.99 1152 1224 1352 1552 864 865 868 902 -HSync +Vsync
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82865G Integrated Graphics Device"
Monitor "T711B"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1152x864" "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1152x864" "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1152x864" "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1152x864" "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1152x864" "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1152x864@75" "1280x1024" "1152x864" "1024x768"
EndSubSection
EndSection
```

---

### Post by Vitaliy on 2005-11-04
[QUOTE=Teroedni]Your near:)
I added "1152x864@75" to display at 24 depth should work now

```

Depth 24
Modes "1152x864@75" "1280x1024" "1152x864" "1024x768"
EndSubSection
EndSection
```[/QUOTE]

thanks for your reply, 

but it isn't work...:(

---

### Post by Teroedni on 2005-11-05
can you post your xorg log



write code in terminal:

sudo gedit /var/log/Xorg.0.log

then you post the log file in this forum

---

### Post by Vitaliy on 2005-11-05
[QUOTE=Teroedni]can you post your xorg log

[/QUOTE]

ok

```


(II) I810(0): T711B: Using hsync range of 30.00-71.00 kHz
(II) I810(0): T711B: Using vrefresh range of 50.00-160.00 Hz
(II) I810(0): Not using mode "1152x864@75" (no mode of this name)
(II) I810(0): Not using mode "1152x864" (no mode of this name)
(II) I810(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(1152x864@75,T711B) mode clock 100000MHz exceeds DDC maximum 110MHz
(1152x864,T711B) mode clock 100000MHz exceeds DDC maximum 110MHz
(1600x1200,T711B) mode clock 162MHz exceeds DDC maximum 110MHz
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(--) I810(0): Virtual size is 1280x1024 (pitch 2048)
(**) I810(0): *Built-in mode "1280x1024"
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"


```

it's peace of log, where i found 1152x864

---

### Post by Teroedni on 2005-11-05
I modified some thing removed things you dont need .
Also i upped horinz from 71 to 75
You are soure your monitor support 1152*864 right. Did it work at 75 herz in windows?

here is modified 
Use it and post all of xorg.log next time as i need to see it;)

```
Section "Device"
Identifier "Intel Corporation 82865G Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
VideoRam 32768 
EndSection

Section "Monitor"
Identifier "T711B"
Option "DPMS"
HorizSync 30-75
VertRefresh 50-160
Modeline   "1152x864_75.00" 104.99 1152 1224 1352 1552 864 865 868 902 
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82865G Integrated Graphics Device"
Monitor "T711B"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1152x864" "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1152x864" "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1152x864" "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1152x864" "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1152x864" "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1152x864@75" "1280x1024" "1152x864" "1024x768"
EndSubSection
EndSection
```

---

### Post by Vitaliy on 2005-11-06
there is limitation on size of file, than i put it on bzip2

---

### Post by Teroedni on 2005-11-06
hmm
First off all the 1152x864 is not even loaded:confused: 

ther got to be something thats not right there

You have dcc which are protection your monitor.Do you have a manual which states the maximum frequenzy of your monitor??. I like to know if dcc are right

Could you post your x.org file?? I want to go over it and inspect a little.
Can you post it exactly how its look in  code .Dont zip it.Just paste the whole 
xorg inside the wrap code option

I hope you have the patience cause we will fix this;)

---

### Post by Vitaliy on 2005-11-06
sorry, i forgot about that i tried 1152 in windows, it was normal.. 75Hz

---

### Post by Vitaliy on 2005-11-06
[QUOTE=Teroedni]hmm
You have dcc which are protection your monitor.Do you have a manual which states the maximum frequenzy of your monitor??. I like to know if dcc are right
[/QUOTE]
i don't fully understand what is dcc, but i found in spec
DDC : DDC 2B

> 
Could you post your x.org file?? I want to go over it and inspect a little.
Can you post it exactly how its look in  code .Dont zip it.Just paste the whole 
xorg inside the wrap code option

I hope you have the patience cause we will fix this;)

:) i have patience

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
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	65536	
EndSection


Section "Monitor"
	Identifier	"T711B"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-160
	# 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
        Modeline "1152x864_75.00"  104.99  1152 1224 1352 1552  864 865 868 902  
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"T711B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864@75" "1280x1024" "1152x864" "1024x768"
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

---

### Post by Teroedni on 2005-11-06
i removed this
# 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
        Modeline "1152x864_75.00"  104.99  1152 1224 1352 1552  864 865 868 902  
EndSection

the # tell the xserver  to ignore the whole line .Therefore we tell x to ingnore the modeline, and we dont want that. Therefore i removed it.



Here is the new modified code which should work:)


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
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	65536	
EndSection


Section "Monitor"
	Identifier	"T711B"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-160
	Modeline        "1152x864_75.00"  104.99  1152 1224 1352 1552  864 865 868 902  
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"T711B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864@75" "1280x1024" "1152x864" "1024x768"
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

---

### Post by jvictor on 2005-11-07
try changing H-refresh to 30-70 I use it and 1152x864 works at 75 Hz , no flicker

---

### Post by Vitaliy on 2005-11-08
[QUOTE=jvictor]try changing H-refresh to 30-70 I use it and 1152x864 works at 75 Hz , no flicker[/QUOTE]

doesn't work :(

---

### Post by Vitaliy on 2005-11-08
[QUOTE=Teroedni]i removed this
# 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
        Modeline "1152x864_75.00"  104.99  1152 1224 1352 1552  864 865 868 902  
EndSection

the # tell the xserver  to ignore the whole line .Therefore we tell x to ingnore the modeline, and we dont want that. Therefore i removed it.

Here is the new modified code which should work:)

[/QUOTE]

should work, but it doesn't :(

maybe i should generate another modeline...? i generated it by gtf 1152 864 75, is it right?

---

### Post by Teroedni on 2005-11-08
so your used my new modified code and i dint work?.
With the new atleast the modeline should be  loaded, could i see your latest x.org.log to see whats wrong now???

---

### Post by Vitaliy on 2005-11-08
[QUOTE=Teroedni]so your used my new modified code and i dint work?.
[/QUOTE]
yes, i did
> 
With the new atleast the modeline should be  loaded, could i see your latest x.org.log to see whats wrong now???

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux zevs 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov  9 09:41:00 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "T711B"
(**) |   |-->Device "Intel Corporation 82865G Integrated Graphics Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1849,2570 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2572 card 1849,2572 rev 02 class 03,00,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24d2 card 1849,24d0 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1849,24d0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1849,24d0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1849,24d0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1849,24d0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1849,24d0 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1849,24d0 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1849,9739 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:05:0: chip 10ec,8139 card 1849,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe500000 - 0xfe5fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corp. 82865G Integrated Graphics Device rev 2, Mem @ 0xf0000000/27, 0xfe780000/19, I/O @ 0xec00/3
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xfe800000 from 0xfebfffff to 0xfe7fffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfe5ffc00 - 0xfe5ffcff (0x100) MX[B]
	[1] -1	0	0xfe77b400 - 0xfe77b4ff (0x100) MX[B]
	[2] -1	0	0xfe77b800 - 0xfe77b9ff (0x200) MX[B]
	[3] -1	0	0x3e000000 - 0x3e0003ff (0x400) MX[B]
	[4] -1	0	0xfe77bc00 - 0xfe77bfff (0x400) MX[B]
	[5] -1	0	0xfe800000 - 0xfe7fffff (0x0) MX[B]O
	[6] -1	0	0xfe780000 - 0xfe7fffff (0x80000) MX[B](B)
	[7] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[11] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[12] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe5ffc00 - 0xfe5ffcff (0x100) MX[B]
	[1] -1	0	0xfe77b400 - 0xfe77b4ff (0x100) MX[B]
	[2] -1	0	0xfe77b800 - 0xfe77b9ff (0x200) MX[B]
	[3] -1	0	0x3e000000 - 0x3e0003ff (0x400) MX[B]
	[4] -1	0	0xfe77bc00 - 0xfe77bfff (0x400) MX[B]
	[5] -1	0	0xfe800000 - 0xfe7fffff (0x0) MX[B]O
	[6] -1	0	0xfe780000 - 0xfe7fffff (0x80000) MX[B](B)
	[7] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[10] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[11] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[12] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[16] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3dffffff (0x3df00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3dffffff (0x3df00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfe5ffc00 - 0xfe5ffcff (0x100) MX[B]
	[6] -1	0	0xfe77b400 - 0xfe77b4ff (0x100) MX[B]
	[7] -1	0	0xfe77b800 - 0xfe77b9ff (0x200) MX[B]
	[8] -1	0	0x3e000000 - 0x3e0003ff (0x400) MX[B]
	[9] -1	0	0xfe77bc00 - 0xfe77bfff (0x400) MX[B]
	[10] -1	0	0xfe800000 - 0xfe7fffff (0x0) MX[B]O
	[11] -1	0	0xfe780000 - 0xfe7fffff (0x80000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[18] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
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
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "i810"
(II) Loading /usr/X11R6/lib/modules/drivers/i810_drv.o
(II) Module i810: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.4.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G
(II) Primary Device is: PCI 00:02:0
(--) Chipset 865G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3dffffff (0x3df00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfe5ffc00 - 0xfe5ffcff (0x100) MX[B]
	[6] -1	0	0xfe77b400 - 0xfe77b4ff (0x100) MX[B]
	[7] -1	0	0xfe77b800 - 0xfe77b9ff (0x200) MX[B]
	[8] -1	0	0x3e000000 - 0x3e0003ff (0x400) MX[B]
	[9] -1	0	0xfe77bc00 - 0xfe77bfff (0x400) MX[B]
	[10] -1	0	0xfe800000 - 0xfe7fffff (0x0) MX[B]O
	[11] -1	0	0xfe780000 - 0xfe7fffff (0x80000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[18] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[19] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3dffffff (0x3df00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfe5ffc00 - 0xfe5ffcff (0x100) MX[B]
	[6] -1	0	0xfe77b400 - 0xfe77b4ff (0x100) MX[B]
	[7] -1	0	0xfe77b800 - 0xfe77b9ff (0x200) MX[B]
	[8] -1	0	0x3e000000 - 0x3e0003ff (0x400) MX[B]
	[9] -1	0	0xfe77bc00 - 0xfe77bfff (0x400) MX[B]
	[10] -1	0	0xfe800000 - 0xfe7fffff (0x0) MX[B]O
	[11] -1	0	0xfe780000 - 0xfe7fffff (0x80000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[21] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 32576 kB
(II) I810(0): VESA VBE OEM: Intel(r)865G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)865G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 865G
(--) I810(0): Chipset: "865G"
(--) I810(0): Linear framebuffer at 0xF0000000
(--) I810(0): IO registers at addr 0xFE780000
(II) I810(0): 1 display pipe available.
(II) I810(0): detected 32636 kB stolen memory.
(II) I810(0): I830CheckAvailableMemory: 930812 kB available
(--) I810(0): Pre-allocated VideoRAM: 32636 kByte
(**) I810(0): VideoRAM: 65536 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 3202
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: TV: attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: LFP (local flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: CRT2 (second CRT): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0): 	CRT
(==) I810(0): Display is using Pipe A
(--) I810(0): Maximum frambuffer space: 65368 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Will use BIOS call 0x5f05 to set refresh rates for CRTs.
(--) I810(0): Maximum space available for video modes: 32576 kByte
(II) I810(0): Using detected DDC timings
(II) I810(0): 	HorizSync 30-71
(II) I810(0): 	VertRefresh 50-160
(WW) I810(0): config file hsync range 30-75kHz not within DDC hsync range 30-71kHz
Mode: 30 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 100
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 100
	LinNumberOfImagePages: 100
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 32 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 71
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 71
	LinNumberOfImagePages: 71
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 34 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 41
	LinNumberOfImagePages: 41
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 38 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 3a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 3c (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 1920
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1920
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 41 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 55
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 55
	LinNumberOfImagePages: 55
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 43 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 32
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 32
	LinNumberOfImagePages: 32
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 45 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 20
	LinNumberOfImagePages: 20
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 49 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000

```

---

### Post by Vitaliy on 2005-11-08
continue

```

Mode: 4b (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4d (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 50 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 25
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 25
	LinNumberOfImagePages: 25
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 52 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 54 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(WW) (1280x1024,T711B) mode clock 135MHz exceeds DDC maximum 110MHz
(WW) (1280x1024,T711B) mode clock 157.5MHz exceeds DDC maximum 110MHz
Mode: 58 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(WW) (1600x1200,T711B) mode clock 162MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 175.5MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 189MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 202.5MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 229.5MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 234.576MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 204.326MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 195.84MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 195.84MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 195.84MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 190.247MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 190.247MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,T711B) mode clock 148.759MHz exceeds DDC maximum 110MHz
Mode: 5a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(WW) (1920x1440,T711B) mode clock 234MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 297MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 341.35MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 339.068MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 297.395MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 297.395MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 297.395MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 297.395MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 297.395MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 297.395MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 297.395MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 297.395MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 297.395MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 297.395MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 283.392MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 283.392MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 283.392MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 275.152MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 275.152MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 233.155MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 233.155MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 233.155MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 233.155MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 233.155MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 233.155MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 233.155MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 233.155MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 233.155MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 233.155MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 217.027MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 217.027MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 217.027MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 217.027MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 162.367MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 162.367MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 162.367MHz exceeds DDC maximum 110MHz
(WW) (1920x1440,T711B) mode clock 162.367MHz exceeds DDC maximum 110MHz
Mode: 5c (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00057b7
	BytesPerScanline: 7680
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 7680
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 60 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 61 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 62 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 63 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 64 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 65 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 66 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0


```

---

### Post by Vitaliy on 2005-11-08
```

Mode: 67 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 68 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
(II) I810(0): T711B: Using hsync range of 30.00-71.00 kHz
(II) I810(0): T711B: Using vrefresh range of 50.00-160.00 Hz
(II) I810(0): Not using mode "1152x864@75" (no mode of this name)
(II) I810(0): Not using mode "1152x864" (no mode of this name)
(II) I810(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(II) I810(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(1152x864@75,T711B) mode clock 100000MHz exceeds DDC maximum 110MHz
(1152x864,T711B) mode clock 100000MHz exceeds DDC maximum 110MHz
(1600x1200,T711B) mode clock 162MHz exceeds DDC maximum 110MHz
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
(II) I810(0): Attempting to use 85.00Hz refresh for mode "1024x768" (854)
(II) I810(0): Attempting to use 85.14Hz refresh for mode "800x600" (852)
(II) I810(0): Attempting to use 85.01Hz refresh for mode "640x480" (850)
(--) I810(0): Display dimensions: (330, 240) mm
(--) I810(0): DPI set to (78, 81)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) I810(0): VBE Restore workaround: enabled.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/X11R6/lib/modules/libshadow.a
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfe780000 - 0xfe7fffff (0x80000) MS[B]
	[1] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MS[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3dffffff (0x3df00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfe5ffc00 - 0xfe5ffcff (0x100) MX[B]
	[8] -1	0	0xfe77b400 - 0xfe77b4ff (0x100) MX[B]
	[9] -1	0	0xfe77b800 - 0xfe77b9ff (0x200) MX[B]
	[10] -1	0	0x3e000000 - 0x3e0003ff (0x400) MX[B]
	[11] -1	0	0xfe77bc00 - 0xfe77bfff (0x400) MX[B]
	[12] -1	0	0xfe800000 - 0xfe7fffff (0x0) MX[B]O
	[13] -1	0	0xfe780000 - 0xfe7fffff (0x80000) MX[B](B)
	[14] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] 0	0	0x0000ec00 - 0x0000ec07 (0x8) IS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[24] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[25] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[29] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 32576 kB
(II) I810(0): VESA VBE OEM: Intel(r)865G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)865G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 512 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 5120 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0x7fff000
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0x7ffb000
(II) I810(0): Allocated 4 kB for Overlay registers at 0x7ffa000 (0x35776000).
(II) I810(0): Allocated 64 kB for the scratch buffer at 0x7fea000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) I810(0): [drm] loaded kernel module for "i915" driver
(II) I810(0): [drm] DRM interface version 1.2
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [drm] added 8192 byte SAREA at 0xf8c52000
(II) I810(0): [drm] mapped SAREA 0xf8c52000 to 0xb7d24000
(II) I810(0): [drm] framebuffer handle = 0xf0020000
(II) I810(0): [drm] added 1 reserved context for kernel
(II) I810(0): Allocated 3072 kB for the back buffer at 0x7800000.
(II) I810(0): Allocated 3072 kB for the depth buffer at 0x7400000.
(II) I810(0): Allocated 32 kB for the logical context at 0x73f8000.
(II) I810(0): Allocated 54016 kB for textures at 0x520000
(II) I810(0): Updated framebuffer allocation size from 5120 to 5128 kByte
(II) I810(0): Updated pixmap cache from 512 scanlines to 514 scanlines
(II) I810(0): 0x85a9be4: Memory at offset 0x00020000, size 5128 kBytes
(II) I810(0): 0x839cad0: Memory at offset 0x07fff000, size 4 kBytes
(II) I810(0): 0x857b9a8: Memory at offset 0x07ffb000, size 16 kBytes
(II) I810(0): 0x8541f44: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x85a9c24: Memory at offset 0x07fea000, size 64 kBytes
(II) I810(0): 0x8440d60: Memory at offset 0x07ffa000, size 4 kBytes
(II) I810(0): 0x85a9c74: Memory at offset 0x07800000, size 3072 kBytes
(II) I810(0): 0x85a9c94: Memory at offset 0x07400000, size 3072 kBytes
(II) I810(0): 0x85a9cd4: Memory at offset 0x073f8000, size 32 kBytes
(II) I810(0): 0x85a9cb4: Memory at offset 0x00520000, size 54016 kBytes
(II) I810(0): Activating tiled memory for the back buffer.
(II) I810(0): Activating tiled memory for the depth buffer.
(II) I810(0): [drm] Registers = 0xfe780000
(II) I810(0): [drm] Back Buffer = 0xf7800000
(II) I810(0): [drm] Depth Buffer = 0xf7400000
(II) I810(0): [drm] ring buffer = 0xf0000000
(II) I810(0): [drm] textures = 0xf0520000
(II) I810(0): [drm] dma control initialized, using IRQ 16
(II) I810(0): [drm] Initialized kernel agp heap manager, 55312384
(II) I810(0): [dri] visual configs initialized
(==) I810(0): Write-combining range (0xf0000000,0x8000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x01fdf000 (pgoffset 8159)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x07fff000 (pgoffset 32767)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x07ffb000 (pgoffset 32763)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x07fea000 (pgoffset 32746)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x07ffa000 (pgoffset 32762)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x07800000 (pgoffset 30720)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x07400000 (pgoffset 29696)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x073f8000 (pgoffset 29688)
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(II) I810(0): Setting refresh with VBE 3 method.
(II) I810(0): Display plane A is enabled and connected to Pipe A.
(II) I810(0): Enabling plane A.
(II) I810(0): Display plane A is now enabled and connected to Pipe A.
(II) I810(0): PIPEACONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(WW) I810(0): Extended BIOS function 0x5f28 not supported.
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): X context handle = 0x00000001
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0

```

---

### Post by Teroedni on 2005-11-09
(1152x864@75,T711B) mode clock 100000MHz exceeds DDC maximum 110MHz
ddc protection


we need to add
Option          "NoDDC"

NB!!!Make sure to not use higher than 1152x864 at 75 hertz, as we remove protection now and if you set the values higher you may break your monitor!!!


```
Section "Device"
Identifier         "Intel Corporation 82865G Integrated Graphics Device"
Driver             "i810"
BusID             "PCI:0:2:0"
VideoRam        65536 
option            "NoDDC"
EndSection
```

---

### Post by Vitaliy on 2005-11-09
[QUOTE=Teroedni]we need to add
Option          "NoDDC"

NB!!!Make sure to not use higher than 1152x864 at 75 hertz, as we remove protection now and if you set the values higher you may break your monitor!!!

[/QUOTE]

ok, but doesn't work


here is xorg.log

```

(II) I810(0): T711B: Using hsync range of 30.00-75.00 kHz
(II) I810(0): T711B: Using vrefresh range of 50.00-160.00 Hz
(II) I810(0): Not using mode "1152x864@75" (no mode of this name)
(II) I810(0): Not using mode "1152x864" (no mode of this name)
(II) I810(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(II) I810(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
(II) I810(0): Attempting to use 85.00Hz refresh for mode "1024x768" (854)
(II) I810(0): Attempting to use 85.14Hz refresh for mode "800x600" (852)
(II) I810(0): Attempting to use 85.01Hz refresh for mode "640x480" (850)


```

disappear lines about exceed ddc, but "no mode of this name" stayed

---

### Post by Teroedni on 2005-11-09
hmm could you post the lastest of both X.org and xorg.0.log
in pastebin here.
[http://pastebin.com/](http://pastebin.com/)


I need to look at thoose to find out what i have done wrong.It should work now:(  I need to see the whole part of both x.org and xorg.0.log to be able to find out what is wrong.

Please have patience with me:smile:

---

### Post by Teroedni on 2005-11-09
lets try with different xorgs

```
Section "Monitor"
	Identifier	"T711B"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-160
	# 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
        Modeline "1152x864@75.00"  104.99  1152 1224 1352 1552  864 865 868 902  
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"T711B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864@75" "1280x1024" "1152x864" "1024x768"
	EndSubSection
EndSection

```



```
Section "Monitor"
	Identifier	"T711B"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-160
	# 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
        Modeline "1152x864_75.00"  104.99  1152 1224 1352 1552  864 865 868 902  
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"T711B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864_75" "1280x1024" "1152x864" "1024x768"
	EndSubSection
EndSection

```


```
Section "Monitor"
	Identifier	"T711B"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-160
	# 1152x864 @ 75.00 Hz (GTF) hsync: 67.65 kHz; pclk: 104.99 MHz
        Modeline "1152x864_75.00"  104.99  1152 1224 1352 1552  864 865 868 902  
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"T711B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1280x1024" "1152x864" "1024x768"
	EndSubSection
EndSection

```

---

### Post by Teroedni on 2005-11-09
Here is another which is based on another modeline generator
Perhaps this will work



```
Section "Monitor"
	Identifier	"T711B"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-160
	# V-freq: 75.00 Hz  // h-freq: 67.85 KHz
        Modeline        "1152x864" 107.48  1152 1208 1336 1584   864  864  867  904  
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"T711B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1280x1024" "1152x864" "1024x768"
	EndSubSection
EndSection
```

---

### Post by fossean on 2005-11-09
A big thank-you to Teroedni. I have now got the monitor on my Acer 1362WLMi laptop running at the native 1280x800 @60Hz. 

Fixed it by following your suggestion above to add Option "NoDDC" under device section in xorg.conf. 

I'd been looking for a solution to this all week..:smile: Think I'll be sticking with Ubuntu.

---

### Post by Teroedni on 2005-11-09
Good to know fossean
Welcome to the Ubuntu Community:)

---

### Post by Vitaliy on 2005-11-10
all of this suggestions, not work :(

also i tried another modeline with different xorg from previous post...

btw, my friend have the same configuration of computer and he tried hoary, and it had worked well, till he installed breezy... maybe x server in breezy have big difference than hoary?

---

### Post by Teroedni on 2005-11-10
could you give me the xlog of the last one
try to remove horinz and vertical to see if that do something
also please try vesa and see if thats yield anything

---

### Post by BrotherWolf on 2007-03-19
Thanks Teroedni!

I was having similar troubles as Vitaliy in trying to set my resolution to 1280x1024.
Following your advice I've [finally] now got it working.

These were the modifications I had to make in case it helps anyone else:


Section "Monitor"
...
Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
...
EndSection




Section "Screen"
...
Modes		"1280x1024_75.00" "1024x768" "832x624" "800x600" "720x400" "640x480"
...
EndSubSection




For all the modelines under the monitor section I changed all the "1280x1024" entries I had manually added to read "1280x1024_75.00"

I'd hypothesize that changing the modeline under the "Monitor" section to start "1280x1024........." instead of  "1280x1024_75.00........." would allow all the entries under the section "Screen" to read "1280x1024" instead of  "1280x1024_75.00 as well but don't intend to check just yet since all is now well ;-)



In case it makes any difference to anyone with similar probs I'm using Ubuntu Edgy that was upgraded from Dapper.

---

