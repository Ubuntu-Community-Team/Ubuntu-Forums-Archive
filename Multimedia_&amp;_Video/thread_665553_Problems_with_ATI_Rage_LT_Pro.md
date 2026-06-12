---
title: "Problems with ATI Rage LT Pro"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by rnjn.sinha on 2008-01-12
I have a perfectly working 865 with compiz for all the cool affects.

I was looking for a cheap alternative PCI VGA card and unfortunately landed up with this:
 
```
VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro (rev dc)
```

I connected two monitors, one to the onboard display controller and the other to the ATI card.

BTW I am using Xubuntu/gutsy

Now my problem is that X does not start. If I do an lsmod, there is nothing remotely available that can suggest that any kernel module is indeed available for the hardware. I looked around and came to the conclusion that ATI Mach64 is the correct kernel module. Here two things happen

if the primary display control in BIOS is set to onboard 80865, then no output is shown on the monitor connected to ATI card  and on insmodding the atyfb module I immediately get a kernel panic :(

If the primary control is auto, then while booting, the nice Xubuntu logo with the shining progress bar can be seen through monitor connected to ATI card but no output on the monitor connected to onboard controller. This much is fine. However X does not start.Now if I insmod the atyfb module these messages appear in the dmesg log


```
atyfb: using auxiliary register aperture
atyfb: 3D RAGE LT PRO (Mach64 LI, PCI) [0x4c49 rev 0xdc]
atyfb: Mach64 BIOS is located at c0000, mapped at c00c0000.
atyfb: BIOS frequency table:
atyfb: PCLK_min_freq 984, PCLK_max_freq 23600, ref_freq 2950, ref_divider 64
atyfb: MCLK_pwd 4200, MCLK_max_freq 7500, XCLK_max_freq 10000, SCLK_freq 5000
atyfb: BIOS contains driver information table.
atyfb: colour active matrix monitor detected:
atyfb:        id=1, 1024x768 pixels, 262144 colours (FDPI-2 mode)
atyfb:        supports refresh rates [60], default 60 Hz
 8M SDRAM (1:1), 29.498928 MHz XTAL, 236 MHz PLL, 75 Mhz MCLK, 100 MHz XCLK
atyfb: fb0: ATY Mach64 frame buffer device on PCI
```


However immediately the monitor (IBM E74) gets switched off. I thought it could be because of some issues with the refresh rate. So I disabled X and then tried to insmod the atyfb module. Again the monitor goes off. I then have to ssh to this machine and remove the module. Then the display can be seen again.

So here my questions are

1. What is the appropriate kernel module for the card?

2. How can I get X to run. I am not looking for 3-D acceleration. Only dual monitor support.

---

### Post by rnjn.sinha on 2008-01-13
I am really stuck with this.  I don't have anything new to report. Is there anywhere else where I can report this issue?

---

### Post by rnjn.sinha on 2008-01-21
Well I fixed this finally :popcorn: Posting the solution in the hope that it might help somebody someday.

I might be completely wrong here but as I have now understood, no kernel mode driver is actually needed unless we need DRI. Since I don't, the open source xorg driver "ati" is actually the only thing that was needed. Just to recap my setup is as follows

Onboard intel 80865 VGA Graphics Controller
ATI Technologies Inc 3D Rage LT Pro VGA controller on a PCI slot

Each connected to a separate Monitor.


**Mission** : To get Xinerama to work

As I found out after searching for a long time, we perhaps need to specify *MonitorLayout* in **Device** section only if we have a dual head card. Since I had two separate display cards, I could do without them. Similarly when I had specified the *Screen* number in **Device** section, the Xorg.0.log indicated that a suitable screen could not be found (whatever that meant). Also since there was no *dri* and consequently *glx* section, I had to provide instructions for unloading these options. As suggested at many places *Composite* option has to be disabled as well to get XInerama to work.

I also experienced display problems with the new **intel** driver, so had to fallback on the old **i810** driver. But it could be unrelated. Anyways here goes my config file

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

#Disable glx and dri for lack of support
Section "Module"
        Disable "glx"
        Disable "dri"
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
	Identifier	"ati"
	Driver		"ati"
	BusID		"PCI:1:0:0"
#        Option          "MonitorLayout" "CRT,CRT"
EndSection


Section "Device"
	Identifier	"Intel"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	#Option		"UseFBDev"		"true"
        #Option          "MonitorLayout" "CRT,CRT"
EndSection


Section "Monitor"
	Identifier	"IBM 6332 E74"
	Option		"DPMS"
EndSection


Section "Monitor"
	Identifier	"DELL E773s"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"ati"
	Monitor		"IBM 6332 E74"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel"
	Monitor		"DELL E773s"
	DefaultDepth	24
	SubSection "Display"
                Depth   24
		Modes   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Default  Screen"  
	Screen 1	"Second Screen" RightOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "Extensions"
        Option      "Composite" "disable"
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
EndSection

```


Restarted gdm and now I have my shiny dual monitor display with Xinerama :guitar:


PS: Does anybody know how to enable compiz with Xinerama ? Also my display is at 1280x1024@75. How can I get it to 60 hertz.

---

