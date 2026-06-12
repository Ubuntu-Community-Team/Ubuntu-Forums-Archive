---
title: "Mode Limit in xorg.conf?"
date: 2010-04-18
forum: Multimedia Software
---

### Post by BJ_Covert_Action on 2010-04-18
Howdy All,


I am trying to fine tune the S-video output settings for my xubuntu box running 9.10.  I  am having some trouble getting modes loaded via xorg.conf. Currently,  my xorg.conf file looks like:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"dead"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Radeon_9600"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"TVDACLoadDetect" "TRUE"
	Option 		"ATOMTvOut" "TRUE"
	#Option		"XAANoOffscreenPixmaps"
	Option		"Monitor-S-video" "SVid_Out"
	#<ENABLE_VGA_HERE>
	#<ENABLE_SVID_HERE>
EndSection

Section "Monitor"
	Identifier	"VGA-0"
	#Option		"Ignore" "true"
	#Horizsync	31.5	-	35.1
	#Vertrefresh	50.0	-	61.0
EndSection

Section "Monitor"
	Identifier	"SVid_Out"
	Modeline	"640x480_59.9"  23.82  640 656 720 800  480 481 484 497  -HSync +Vsync
	#Modeline	"800x600_54"  33.69  800 824 904 1008  600 601 604 619  +HSync +Vsync
	Modeline	"800x600_60"  38.22  800 832 912 1024  600 601 604 622  +HSync +Vsync
	Modeline	"720x576_60"  32.67  720 744 816 912  576 577 580 597  +HSync +Vsync
	Modeline	"720x576_50"  26.57  720 736 808 896  576 577 580 593  +HSync +Vsync
	Option		"PreferredMode" "800x600_60"
	DisplaySize	952 724
	#Option		"Above" "VGA-0"
	Option		"Enable" "true"
	#Horizsync	31.5	-	35.1
	#Vertrefresh	50.0	-	61.0
EndSection

Section "Screen"
	Identifier	"TV_Screen"
	Device		"Radeon_9600"
	#Monitor		"Rear_TV"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		#FbBpp	32
		#Modes	"800x600" "640x480"
		#Virtual 800 600
		Virtual	800  1200
		#Virtual 3000 2000
	EndSubsection
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen		"TV_Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

If you notice,  in the SVid-Out monitor section, I list about 5 or 6 display modes that I would like the option of working with. However, when I run my xrandr command in the terminal I only see a few:


```

Screen 0: minimum 320 x 200, current 800 x 600, maximum 800 x 1200
VGA-0 disconnected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600_60     60.0*+
   800x600        59.9 +
  800x600 (0x4f)   40.0MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz

```

So why is it that only a few modes in the xorg.conf load? Is there  a limit to the number of modes you can add to a monitor in xorg.conf?

I tried adding the modes using xrandr itself, but when I issue the command combination:

```

gtf 720 576 50
xrandr --newmode "720x576_50"  26.57  720 736 808 896  576 577 580 593  -HSync +Vsync
xrandr --addmode S-video 720x576_50

``` 

I end up getting the following error message after the addmode command:

```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26

``` 

So can anyone tell me why X  is having so much trouble with this 720x576_50 mode? Is it incompatible with an S-video output for some reason?

Thanks in advance guys.

---

### Post by BJ_Covert_Action on 2010-04-20
24 hour bump, any ideas guys?

---

