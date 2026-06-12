---
title: "How to change screen res to 720x480?"
date: 2008-06-18
forum: Multimedia Software
---

### Post by lowwall on 2008-06-18
I've got an ASUS Z96Fm "barebones" notebook running Feisty.  It has integrated graphics and an S-video out port.  S-video works fine,  except the graphics controller doesn't do a particularly good job of converting what's on the laptop screen to NTSC.  The image is always either stretched or cut off.  The closer I can get the laptop screen resolution to the native format of the video (like NTSC's 720x480), the less distorted the image. But my only choices at the low end are either 640x480 or 800x600, both of which result in distortion. 

Is there a way to force 720x480 as an option in the Screen Resolution Preference dialog?  I tried adding it to Modes line in the Screen section of xorg.conf, but it doesn't show up.  I then tried adding a 720x480 ModeLine I found somewhere to the Monitor section.  Still no dice.

If I can't force it to 720x480, is there another way to handle this?

I'll paste my current xorg.conf below (minus the remarks section):

```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
    Identifier "Synaptics Touchpad"
    Driver "synaptics"
    Option "SendCoreEvents" "true"
    Option "Device" "/dev/psaux"
    Option "Protocol" "auto-dev"
    Option "HorizScrollDelta" "0"
    Option "TapButton1" "0"
    Option "SHMConfig" "on"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
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
		Modes		"1280x800" "720x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "Synaptics Touchpad" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by pietjanjaap on 2008-06-19
ubuntu 8.04
dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

### Post by lowwall on 2008-06-19
I don't understand.  Are you saying I should upgrade to Ubuntu 8?

---

### Post by Pjotr123 on 2008-06-19
> **lowwall said:**
> I don't understand.  Are you saying I should upgrade to Ubuntu 8?

That's a good idea...... :-) Do it with a clean install of 8.04, not by upgrading.

However, it's not necessary to solve your problem with 7.04. Do this:

first:
```
sudo apt-get install xresprobe
```

then:
```
sudo dpkg-reconfigure xserver-xorg
```

Answer the questions you will be posed then, by using the following keys: TAB, spacebar, ENTER, arrows. The proposed answers are the right ones, so agree with them all.

Then full reboot.

Greeting, Pjotr.

---

### Post by johnkaiman on 2008-12-14
That didn't do anything - any way of forcing it?
Thanks in advance!

---

