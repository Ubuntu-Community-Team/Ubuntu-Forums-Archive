---
title: "duel monitor help please"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by Dwiman89 on 2007-09-26
Hi, i got a new graphics card. It is a nVidia NV34 [GeForce FX 5200]. i plugged it in and everything seems to be fine. its got two monitor jacks in it.  I plugged a second monitor in and booted up.  the immages are on both screens till it gets to the login and the other monitor goes out. Can you please help me get them both working? What are the different options of this, and will beryl work?

this is what it says under device manager for my card:
```

Vendor: nVidia Corporation
Device: NV34 [GeForce FX 5200]
Status: Status
Bus type: PCI
Device Type: Unknown
Capabilities: Unknown

```  

This is whats in Xorg.conf:
```
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:3:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Thanks. :)

---

### Post by Dwiman89 on 2007-09-26
, i got a new graphics card. It is a nVidia NV34 [GeForce FX 5200]. i plugged it in and everything seems to be fine. its got two monitor jacks in it. I plugged a second monitor in and booted up. the immages are on both screens till it gets to the login and the other monitor goes out. Can you please help me get them both working? What are the different options of this, and will beryl work?

this is what it says under device manager for my card:
```
Vendor: nVidia Corporation
Device: NV34 [GeForce FX 5200]
Status: Status
Bus type: PCI
Device Type: Unknown
Capabilities: Unknown

```


This is whats in Xorg.conf:
```

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:3:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

Thanks.

---

### Post by Dwiman89 on 2007-09-26
Hi, i got a new graphics card. It is a nVidia NV34 [GeForce FX 5200]. i plugged it in and everything seems to be fine. its got two monitor jacks in it. I plugged a second monitor in and booted up. the immages are on both screens till it gets to the login and the other monitor goes out. Can you please help me get them both working? What are the different options of this, and will beryl work?

this is what it says under device manager for my card:
```
Vendor: nVidia Corporation
Device: NV34 [GeForce FX 5200]
Status: Status
Bus type: PCI
Device Type: Unknown
Capabilities: Unknown
```

his is whats in Xorg.conf:
```
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:3:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by uchuunoyanushi on 2007-09-26
You need to set up Twinview.  Instructions here: [http://ubuntuforums.org/showthread.php?t=221174&highlight=dual+monitor](http://ubuntuforums.org/showthread.php?t=221174&highlight=dual+monitor)

---

### Post by WiFi Ed on 2007-09-26
Make a backup copy of "/etc/X11/xorg.conf" first!!

The place to start (for me) was to install the restricted driver for nvidia:-System/Administration/Restricted Drivers Manager. After installing and rebooting, open a terminal and type "sudo nvidia-settings".

Click on "X Server Display Configuration", click on "Configure" and choose "TwinView". Save and reboot. If all went well, you'll have one large desktop extending across two monitors. If not, you'll be at a command prompt wondering what the hell went wrong. It happened to me several times.

To get back your original configuration copy your xorg.conf backup over the one nvidia-settings just made. Another recovery method that works for me is to type "sudo dpkg-reconfigure -phigh xserver-xorg" at the command prompt.

It will ask you to pick a video card (choose nvidia)  and then ask you to pick a screen resolution (pick your monitors native resolution). Restart and you should be back where you started.

You might have to experiment several times with various settings and options in the nvidia-settings application to get it right. And, of course, search the forums here for more info...


Best of luck to you!

---

### Post by Dvorakis on 2007-09-26
Go to terminal and type. ```
gksudo nvidia-settings
```

That should help you with everything.

---

### Post by Dwiman89 on 2007-09-26
It work great as far as i can tell. The color is off one my left moitor. is there a way to ajust this on just one monitor? and can i make things rotate on a cube. i once had beryl working. Im not sure what the real difference is between beryl,compiz fusion, and compiz. i tried to enable it in desktop effects but it doesnt work with two monitors.
I liked beryl because it had a lot of features and possible tweakage. but i worry about the instiblity people talk about. which one shoud i use that is the best and how do i do it?

---

### Post by Dwiman89 on 2007-09-26
It work great as far as i can tell. The color is off one my left moitor. is there a way to ajust this on just one monitor? and can i make things rotate on a cube. i once had beryl working. Im not sure what the real difference is between beryl,compiz fusion, and compiz. i tried to enable it in desktop effects but it doesnt work with two monitors.
I liked beryl because it had a lot of features and possible tweakage. but i worry about the instiblity people talk about. which one shoud i use that is the best and how do i do it?

---

### Post by WiFi Ed on 2007-09-27
> **Dwiman89 said:**
> It work great as far as i can tell. The color is off one my left moitor. is there a way to ajust this on just one monitor? and can i make things rotate on a cube. i once had beryl working. Im not sure what the real difference is between beryl,compiz fusion, and compiz. i tried to enable it in desktop effects but it doesnt work with two monitors.
I liked beryl because it had a lot of features and possible tweakage. but i worry about the instiblity people talk about. which one shoud i use that is the best and how do i do it?

Glad to hear it worked for you! I can't help on the compiz/beryl stuff:(

My two monitors have a different color cast too, but I think it's because one is a LCD and the other is a CRT. I haven't figured out how to adjust each one individually from within Ubuntu. The LCD looks best to me...

---

### Post by Dwiman89 on 2007-09-27
Ok something is really mesed up now. everything was working well tiut i went to do some updates and restarted. now the bars on the top and bottom only go across one screen. and i cant close windows or minimize because there is no x or line at the top of windows. i can still move my mouse to the other screen. can you help please?

---

### Post by WiFi Ed on 2007-09-27
> **Dwiman89 said:**
> Ok something is really mesed up now. everything was working well tiut i went to do some updates and restarted. now the bars on the top and bottom only go across one screen. and i cant close windows or minimize because there is no x or line at the top of windows. i can still move my mouse to the other screen. can you help please?

When I activated Twin View I only had panels (or bars) on the primary monitor. To add them to the second screen I right-clicked on a panel (top or bottom, doesn't matter) and chose "Add Panel". A panel appeared on the right-hand side of the screen. I dragged it to the second monitor, right-clicked on it and from the menu chose "Top" as position. I repeated the process for another panel which I placed on the bottom. I then added menus, etc. to the new panels as needed. I'm not at my Ubuntu pc right now so I can't note the specific clicks needed for that.

As for no "x or line at the top of windows" (I assume you mean the title bar), do you have beryl or compiz running? If so, that's where the problem is, but I'm not sure how to fix that.

---

### Post by Dwiman89 on 2007-09-27
no i havent installed beryl or anything. i can guess that the updates or twinview did it. i cant type anything in terminal ether. Can you please help? this is scaring me. if not where else should l look?

---

### Post by WiFi Ed on 2007-09-27
When you reboot, do you have a choice of kernels to load? Do any of them say "recovery mode"? If so, choose one and when (if) you get to a command prompt you could try running the "sudo dpkg-reconfigure -phigh xserver-xorg" fix. It should reset your machine to a single monitor again (I think) and hopefully resolve your other problems.

I've reached the limits of my Ubuntu knowledge, maybe someone else will know what to do...

---

### Post by Dwiman89 on 2007-09-29
Thing apparently seem to be working now. i dont know what i did but it works

---

### Post by WiFi Ed on 2007-09-29
> **Dwiman89 said:**
> Thing apparently seem to be working now. i dont know what i did but it works

If you are happy with the current configuration I suggest you make a backup copy of your xorg.conf file. I've been able to restore my pc to TwinView fuctionality several times by just copying my backup xorg.conf file over my buggered up one. It even worked on fresh re-installation of Ubuntu...

---

