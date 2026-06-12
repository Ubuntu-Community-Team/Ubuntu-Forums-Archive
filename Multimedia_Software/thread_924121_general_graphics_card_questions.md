---
title: "general graphics card questions"
date: 2008-09-19
forum: Multimedia Software
---

### Post by jammin2222 on 2008-09-19
I have dug out my old laptop that has been rotting in the cupboard upstairs since 2002 because the HDD failed and i decided to fix it up and give it to my mum for light web/office use. I have put a new HDD in it and reinstalled windows/ubuntu as a dual boot setup. once and if I can get everything working successfully in Ubuntu then ill get her using Ubuntu full time :wink:

My question is Ubuntu reports my graphics card as being 

01:00.0 VGA compatible controller: S3 Inc. 86C380 [ProSavageDDR K4M266] (rev 02)

which sounds about right to me. 

Is this card supported by default or is there a driver i need to install? I ask because in System> administration> hardware drivers I don't see anything listed, and i cant enable desk top effects either. Could i need a driver or a tweak or both? 

Many thanks 

Ben

---

### Post by soxs on 2008-09-19
S3 is a sis gpu right?
so you may check:

2D driver (no 3D, but much better 2D performance, usefull for movies etc):
[http://ubuntuforums.org/showthread.php?t=615094](http://ubuntuforums.org/showthread.php?t=615094)
Attempt to make board manufactureres give out the existant but not reelesed 3D driver:
[http://ubuntuforums.org/showthread.php?t=886463](http://ubuntuforums.org/showthread.php?t=886463)

---

### Post by jammin2222 on 2008-09-19
Thanks for the quick reply :) 

By sis gpu do you mean the graphics are built into the motherboard? if so then yes they are to the best of my knowledge.

My lap top is made by Tiny, it has a celeron 1.2ghz processor and 512 Mb ram. I got it in 2001 so i doubt many people are still using this setup.

The driver in windows is called S3 twister + hotkey if that means anything.

So At the moment it looks like 3D is not supported in linux as far i can tell with this gpu? are there any ways to further identify and set up my graphics?
Better yet, are there any user friendly GUI's i can use the tweak more advanced graphics settings? I'm no good with the terminal and always mess things up when i start typing code in.

Thanks


Ben

---

### Post by soxs on 2008-09-19
> **jammin2222 said:**
> Thanks for the quick reply :) 

By sis gpu do you mean the graphics are built into the motherboard? if so then yes they are to the best of my knowledge.

My lap top is made by Tiny, it has a celeron 1.2ghz processor and 512 Mb ram. I got it in 2001 so i doubt many people are still using this setup.

The driver in windows is called S3 twister + hotkey if that means anything.

So At the moment it looks like 3D is not supported in linux as far i can tell with this gpu? are there any ways to further identify and set up my graphics?
Better yet, are there any user friendly GUI's i can use the tweak more advanced graphics settings? I'm no good with the terminal and always mess things up when i start typing code in.

Thanks


Ben
Well, as you read the two threads i gave you as "freshmeat", you'll understand that there will hardly rise up a shine GUI until there isn't a 3D driver.
Either you jump through the hoop and get give ( the allmighty sugar-free) shell a chance :-P

btw use the thank button if you feel like :-P

---

### Post by jammin2222 on 2008-09-19
oh well i guess i cant have my Ubuntu and drink it.:lolflag:

I Didn't know there was a Thanks button either...?





Ah i found it, there you go

---

### Post by Yellow Pasque on 2008-09-19
The card should be supported by the "savage" driver. BTW, Savage is made by VIA, not SiS.

---

### Post by soxs on 2008-09-20
> **Temüjin said:**
> The card should be supported by the "savage" driver. BTW, Savage is made by VIA, not SiS.

I didn't really know, and google didn't spit any anti-proof...

---

### Post by jammin2222 on 2008-09-20
sorry to be a noob but how do i tell if the driver is installed?

01:00.0 VGA compatible controller: S3 Inc. 86C380 [ProSavageDDR K4M266] (rev 02)

this is the hardware right? not the driver? Is the savage driver a third party driver? is it included out of the box? where do i download it from if not? i have nothing listed in System> administration> hardware drivers.

Thanks everyone


Ben

---

### Post by Yellow Pasque on 2008-09-20
I believe the savage driver is included in the standard Ubuntu CD install. I'm not sure how good Ubuntu is at detecting video chipsets.

Post output from:
```
sudo lshw -C display
cat /etc/X11/xorg.conf
cat /var/log/Xorg.0.log
```

Remember to use [ code ][ /code ] tags, escpecially with the Xorg log as it's a lot of text.

---

### Post by jammin2222 on 2008-09-20
Thanks i fear i cant post the results because i dont know how to use the [code] thing you said i had to use.
 I have tried putting the code in between the [ ] i have tried [ code ] then pasting the results and putting [code] again but cant get it in the box like you do.
 If i cant even work a forum properly how the heck am i going to cope with sorting out the graphics driver lol

I think Im going to go and hide in the corner. 

Im so stupid its unreal 


Thanks 

Ben

---

### Post by Yellow Pasque on 2008-09-20
Click the "New Reply" button and you'll see a '#' icon click that and paste your output between the tags.

---

### Post by jammin2222 on 2008-09-20
Wonderfull thanks for the tips, the result is as follows 

```
ben@ben-laptop:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 86C380 [ProSavageDDR K4M266]
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=64 maxlatency=255 mingnt=4
ben@ben-laptop:~$ 
```

```
ben@ben-laptop:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
ben@ben-laptop:~$ 


```


```
(II) SAVAGE(0): Not using default mode "320x200" (vrefresh out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 720x400 85Hz.
(II) SAVAGE(0): Not using default mode "720x400" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 360x200 85Hz.
(II) SAVAGE(0): Not using default mode "360x200" (no mode of this name)
(--) SAVAGE(0): Chose mode 112 at 60Hz.
(--) SAVAGE(0): Chose mode 134 at 72Hz.
(--) SAVAGE(0): Chose mode 112 at 72Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 134 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 112 at 75Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 134 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 112 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 134 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 115 at 60Hz.
(--) SAVAGE(0): Chose mode 144 at 72Hz.
(--) SAVAGE(0): Chose mode 115 at 60Hz.
(--) SAVAGE(0): Chose mode 144 at 72Hz.
(--) SAVAGE(0): Chose mode 115 at 72Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 144 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (hsync out of range)
(--) SAVAGE(0): Chose mode 115 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 144 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 115 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 144 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (hsync out of range)
(--) SAVAGE(0): Chose mode 118 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 154 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 118 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 154 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 118 at 70Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 154 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 118 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 154 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 118 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 154 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 75Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x960" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 112 at 60Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1280x960" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 112 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1280x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 60Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 75Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 85Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 115 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 115 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 115 at 72Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 115 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 115 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1792x1344" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 60Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1792x1344" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 75Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 60Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 75Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 60Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 75Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 832x624 74Hz.
(II) SAVAGE(0): Not using default mode "832x624" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 416x312 74Hz.
(II) SAVAGE(0): Not using default mode "416x312" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x768" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 640x384 60Hz.
(II) SAVAGE(0): Not using default mode "640x384" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x800" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 11e at 70Hz.
(II) SAVAGE(0): Not using default mode "640x400" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1152x768" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x384 54Hz.
(II) SAVAGE(0): Not using default mode "576x384" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 59Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 70Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 74Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 85Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1440x900" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 720x450 60Hz.
(II) SAVAGE(0): Not using default mode "720x450" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1600x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 800x512 60Hz.
(II) SAVAGE(0): Not using default mode "800x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 60Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1200" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 60Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1200" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 72Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 85Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "2048x1536" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 118 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 118 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 118 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 118 at 60Hz.
(--) SAVAGE(0): Chose mode 118 at 60Hz.
(--) SAVAGE(0): Chose mode 115 at 60Hz.
(--) SAVAGE(0): Chose mode 115 at 60Hz.
(--) SAVAGE(0): Chose mode 112 at 60Hz.
(--) SAVAGE(0): Chose mode 144 at 72Hz.
(--) SAVAGE(0): Chose mode 144 at 72Hz.
(--) SAVAGE(0): Chose mode 134 at 72Hz.
(--) SAVAGE(0): Virtual size is 1024x768 (pitch 1024)
(**) SAVAGE(0): *Driver mode "1024x768": 56.0 MHz, 47.3 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "1024x768"x59.9   56.00  1024 1072 1104 1184  768 771 775 790 +hsync -vsync (47.3 kHz)
(**) SAVAGE(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SAVAGE(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SAVAGE(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) SAVAGE(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SAVAGE(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) SAVAGE(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) SAVAGE(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) SAVAGE(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) SAVAGE(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) SAVAGE(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MS[B]
	[1] 0	0	0xe0100000 - 0xe017ffff (0x80000) MS[B]
	[2] -1	0	0x00100000 - 0x2bffffff (0x2bf00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0x2c000000 - 0x2c001fff (0x2000) MX[B]
	[7] -1	0	0xe0001000 - 0xe0001fff (0x1000) MX[B]
	[8] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[9] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0100000 - 0xe017ffff (0x80000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xe00000ff (0x100) MX[B]
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00001038 - 0x0000103b (0x4) IX[B]
	[18] -1	0	0x0000103c - 0x0000103f (0x4) IX[B]
	[19] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[20] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[21] -1	0	0x00001020 - 0x0000102f (0x10) IX[B]
	[22] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[23] -1	0	0x00001030 - 0x00001037 (0x8) IX[B]
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 2.0
(II) SAVAGE(0): VESA VBE Total Mem: 31680 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Incorporated. Twister BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 1.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 2.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 1.1
(==) SAVAGE(0): Write-combining range (0xf0000000,0x8000000)
(II) SAVAGE(0): 9348 kB of Videoram needed for 3D; 32768 kB of Videoram available
(II) SAVAGE(0): Sufficient Videoram available for 3D
(II) SAVAGE(0): [drm] bpp: 32 depth: 24
(II) SAVAGE(0): [drm] Sarea 2200+284: 2484
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "savage" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) SAVAGE(0): [drm] Using the DRM lock SAREA also for drawables.
(II) SAVAGE(0): [drm] framebuffer handle = 0xf0000000
(II) SAVAGE(0): [drm] added 1 reserved context for kernel
(II) SAVAGE(0): X context handle = 0x1
(II) SAVAGE(0): [drm] installed DRM signal handler
(II) SAVAGE(0): [agp] Mode 0x1f000201 [AGP 0x1106/0x0605; Card 0x5333/0x8d01]
(II) SAVAGE(0): [agp] 16384 kB allocated with handle 0x00000001
(II) SAVAGE(0): [agp] command DMA handle = 0xe8000000
(II) SAVAGE(0): [agp] agpTextures handle = 0xe8100000
(II) SAVAGE(0): [drm] aperture handle = 0xf2000000
(II) SAVAGE(0): [drm] Enabling ShadowStatus for DRI.
(II) SAVAGE(0): [drm] Status handle = 0x043cb000
(II) SAVAGE(0): [drm] Status page mapped at 0xb7b87000
(II) SAVAGE(0): [dri] visual configs initialized
(**) SAVAGE(0): DRI is enabled
(--) SAVAGE(0): Chose mode 118 at 60Hz.
(II) SAVAGE(0): virtualX:1024,virtualY:768
(II) SAVAGE(0): bpp:32,tiledwidthBytes:4096,tiledBufferSize:3145728 
(II) SAVAGE(0): bpp:32,widthBytes:4096,BufferSize:3145728 
(II) SAVAGE(0): videoRambytes:0x02000000 
(II) SAVAGE(0): textureSize:0x014df000 
(II) SAVAGE(0): textureSize:0x014df000 
(II) SAVAGE(0): textureOffset:0x00b00000 
(II) SAVAGE(0): depthOffset:0x00800000,depthPitch:4096
(II) SAVAGE(0): backOffset:0x00500000,backPitch:4096
(II) SAVAGE(0): Reserved back buffer at offset 0x500000
(II) SAVAGE(0): Reserved depth buffer at offset 0x800000
(II) SAVAGE(0): Reserved 21372 kb for textures at offset 0xb00000
(II) SAVAGE(0): Using 511 lines for offscreen memory.
(II) SAVAGE(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Image Writes
	Setting up tile and stipple cache:
		24 128x128 slots
(==) SAVAGE(0): Backing store disabled
(II) SAVAGE(0): DPMS enabled
(II) SAVAGE(0): [DRI] installation complete
(II) SAVAGE(0): [junkers]pSAVAGEDRIServer:
(II) SAVAGE(0): [junkers]	reserved_map_agpstart:0x00000000
(II) SAVAGE(0): [junkers]	reserved_map_idx:0x00000000
(II) SAVAGE(0): [junkers]	sarea_priv_offset:0x00000000
(II) SAVAGE(0): [junkers]	chipset:0x00000000
(II) SAVAGE(0): [junkers]	sgram:0x00000000
(II) SAVAGE(0): [junkers]	frontbufferSize:0x00300000
(II) SAVAGE(0): [junkers]	frontOffset:0x00000000
(II) SAVAGE(0): [junkers]	frontPitch:0x00001000
(II) SAVAGE(0): [junkers]	backbufferSize:0x00300000
(II) SAVAGE(0): [junkers]	backOffset:0x00500000
(II) SAVAGE(0): [junkers]	backPitch:0x00001000
(II) SAVAGE(0): [junkers]	depthbufferSize:0x00300000
(II) SAVAGE(0): [junkers]	depthOffset:0x00800000
(II) SAVAGE(0): [junkers]	depthPitch:0x00001000
(II) SAVAGE(0): [junkers]	textureOffset:0x00b00000
(II) SAVAGE(0): [junkers]	textureSize:0x014df000
(II) SAVAGE(0): [junkers]	textureSize:0x014df000
(II) SAVAGE(0): [junkers]	logTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]	agp:handle:0x00000001
(II) SAVAGE(0): [junkers]	agp:offset:0x01000000
(II) SAVAGE(0): [junkers]	agp:size:0x01000000
(II) SAVAGE(0): [junkers]	agp:map:0x00000000
(II) SAVAGE(0): [junkers]	registers:handle:0xe0100000
(II) SAVAGE(0): [junkers]	registers:offset:0x00000000
(II) SAVAGE(0): [junkers]	registers:size:0x00080000
(II) SAVAGE(0): [junkers]	registers:map:0x00000000
(II) SAVAGE(0): [junkers]	status:handle:0x043cb000
(II) SAVAGE(0): [junkers]	status:offset:0x00000000
(II) SAVAGE(0): [junkers]	status:size:0x00001000
(II) SAVAGE(0): [junkers]	status:map:0xb7b87000
(II) SAVAGE(0): [junkers]	agpTextures:handle:0xe8100000
(II) SAVAGE(0): [junkers]	agpTextures:offset:0x00100000
(II) SAVAGE(0): [junkers]	agpTextures:size:0x00f00000
(II) SAVAGE(0): [junkers]	apgTextures:map:0x00000000
(II) SAVAGE(0): [junkers]	logAgpTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]	cmdDma:handle:0xe8000000
(II) SAVAGE(0): [junkers]	cmdDma:offset:0x00000000
(II) SAVAGE(0): [junkers]	cmdDma:size:0x00100000
(II) SAVAGE(0): [junkers]	cmdDma:map:0x00000000
(II) SAVAGE(0): [junkers]pSAVAGEDRI:
(II) SAVAGE(0): [junkers]	chipset:0x00000005
(II) SAVAGE(0): [junkers]	width:0x00000400
(II) SAVAGE(0): [junkers]	height:0x00000300
(II) SAVAGE(0): [junkers]	mem:0x02000000
(II) SAVAGE(0): [junkers]	cpp:4
(II) SAVAGE(0): [junkers]	zpp:4
(II) SAVAGE(0): [junkers]	agpMode:1
(II) SAVAGE(0): [junkers]	bufferSize:65536
(II) SAVAGE(0): [junkers]	frontbufferSize:0x00300000
(II) SAVAGE(0): [junkers]	frontOffset:0x00000000
(II) SAVAGE(0): [junkers]	backbufferSize:0x00300000
(II) SAVAGE(0): [junkers]	backOffset:0x00500000
(II) SAVAGE(0): [junkers]	depthbufferSize:0x00300000
(II) SAVAGE(0): [junkers]	depthOffset:0x00800000
(II) SAVAGE(0): [junkers]	textureOffset:0x00b00000
(II) SAVAGE(0): [junkers]	textureSize:0x01400000
(II) SAVAGE(0): [junkers]	logTextureGranularity:0x00000015
(II) SAVAGE(0): [junkers]	agpTextureHandle:0xe8100000
(II) SAVAGE(0): [junkers]	agpTextureSize:0x00f00000
(II) SAVAGE(0): [junkers]	logAgpTextureGranularity:0x00000014
(II) SAVAGE(0): [junkers]	apertureHandle:0xf2000000
(II) SAVAGE(0): [junkers]	apertureSize:0x05000000
(II) SAVAGE(0): [junkers]	aperturePitch:0x00002000
(II) SAVAGE(0): [junkers]	statusHandle:0x043cb000
(II) SAVAGE(0): [junkers]	statusSize:0x00001000
(II) SAVAGE(0): [junkers]	sarea_priv_offset:0x00000898
(II) SAVAGE(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/savage_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(--) Synaptics Touchpad touchpad found
SetGrabKeysState - disabled
SetGrabKeysState - enabled
ben@ben-laptop:~$ 


```



cheers 

ben

---

### Post by Yellow Pasque on 2008-09-20
It looks like the driver is installed properly and using Direct Rendering (DRI). From Googling, it appears that the driver does not support compiz as of the Ubuntu Gutsy release.

You can try it though. Fire up the terminal (Applications -> Accessories -> Terminal) and enter:
```
gksudo gedit /usr/bin/compiz
```

You'll want to make the following changes in bold
```
COMPIZ_BIN_PATH="**/usr/bin/**" # For window decorators and compiz
PLUGIN_PATH="**/usr/lib/compiz/**" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="**compiz.real**" # Final name for compiz (compiz.real)
....
WHITELIST="nvidia intel ati radeon i810 **savage**"

```
Save and quit. Now that you're back in the terminal, enter the command:
```
compiz
```
Joy?

---

### Post by jammin2222 on 2008-09-20
Ok i found this 

```
COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real) 
```

and what you pasted looks like this

```
COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real)
....
WHITELIST="nvidia intel ati radeon i810 savage"
```


so You just want me to remove the word local from two of the lines and add .real after compiz then save it and go back the the terminal and paste  

```
WHITELIST="nvidia intel ati radeon i810 savage"
```

then 
```
compiz
```

Sorry im just making sure before i change stuff i know nothing about.

thanks once again


Ben

---

### Post by jammin2222 on 2008-09-20
just an update, i dont think it worked 

```
ben@ben-laptop:~$ WHITELIST="nvidia intel ati radeon i810 fglrx"
ben@ben-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```


Dose this mean its not supported or there is no driver installed or something completly different? 

cheers for all your help i would be totaly stuck otherwise

Ben

---

### Post by Yellow Pasque on 2008-09-20
The Whitelist= line is not a terminal command; it is found in /usr/bin/compiz (~line 80 IIRC). You need to add your video driver (savage) to it so compiz doesn't complain
> No whitelisted driver found

It may complain about something else lacking in the driver or it may work after you do this.

---

### Post by jammin2222 on 2008-09-20
doh im so stupid lol

ok i added savage to the list and saved it and  the results are 

```
ben@ben-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 5333:8d01 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
aborting and using fallback: /usr/bin/metacity 
```

not looking good i fear

thanks for being patient 

Ben

---

### Post by Yellow Pasque on 2008-09-20
Sorry, Ben, but it looks like you're SOL. This was reported as a bug to the mesa developer list two years ago. My guess is that the hardware itself is not capable of the functions that Compiz needs or it would have been fixed by now.
[http://www.mail-archive.com/dri-devel@lists.sourceforge.net/msg28895.html](http://www.mail-archive.com/dri-devel@lists.sourceforge.net/msg28895.html)

---

### Post by jammin2222 on 2008-09-20
oh well, Im not really surprised to be honest. The laptop was purchased in 2001 and they have come along way since then. Its a pity it wont work but its not the end of the world i guess.

 Before i go i want to ask if there is a way to stop windows leaving a trail of windows behind when you drag it around the desktop? its only while dragging. Its probably bad compatibility with the graphics card but was just wondering?

A big thank you for trying to sort it out 

Best of luck


Ben

---

