---
title: "How do i check i have Nvidia Drivers"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by CameronCalver on 2007-12-17
Hello i decided that i wanted to use some desktop effects but every time i click even the basic one it says it cannot be enables i check in the system -- admin -- restricted drivers that the nvidia one is in there and it is being used but how do i really check if it is being used and why the desktop effects arnt working?

---

### Post by Tarmael on 2007-12-17
Use this command to open up the xorg settings.

gedit /etc/X11/xorg.conf

closer to the bottom should be 

Section "Device"

with your Graphics card (Maybe, sometimes it's not listed in there) as the identifier

Then post here what is listed in the driver part of Section "Device".

Cheers,
Basil.

---

### Post by CameronCalver on 2007-12-17
thanks here it is here
```
Section "Device"
	Identifier	"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

```

is there any reason desktop effects wouldnt be working because of that?

---

### Post by Tarmael on 2007-12-17
Well that tells me that your xorg server is trying to use the nvidia drivers.

Have you checked that you are using the right drivers listed in the synaptic? Because even though the restricted driver manager is supposed to manage properly, it sometimes gets things wrong (Like thinking a 6600GT should use the series 8 drivers... that annoyed me).

You should be using the nvidia-glx-legacy driver that is NOT supported by Ubuntu, means you may want to blacklist nvidia drivers from the update thing. Can someone tell the Original Poster the code to bring that up? I've forgotten...

---

### Post by CameronCalver on 2007-12-17
ok cool then yeah just let me no the command anyone

---

### Post by Tarmael on 2007-12-17
That command is only supposed to stop the Restricted Driver Manager from changing the driver if you try and use the Restricted Driver Manger.

What I mean:

Install the legacy driver, don't use the restricted driver manager, don't even THINK about the restricted driver manager, and hopefully the legacy driver should work for you.

The command will be just for finishing touches.

I'll keep searching for it...

wait, found it

```

gksu gedit /etc/default/linux-restricted-modules-common

```

change from

```

DISABLED_MODULES=""

```

and add

nvidia

to the quotes

glad I could remember where I read that from.

Cheers,
Basil.

---

### Post by CameronCalver on 2007-12-17
Ok well i intalled the legacy driver added nvidia in the quotation mark and now i restart and i see the nvidia logo on bootup which is good but now i dont have my resolutions i have now
1280x1024 1024x768 800x600 640x480 etc but i dont have my 1440x900 which i always use! this is my xorg conf and it says i should have 1440x900 but i dont??

```
Section "Files"
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
	Identifier	"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"False"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-80
	Vertrefresh	60-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x900"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by Tarmael on 2007-12-17
O.K for one, if you don't want to see the logo, then where it says Option "NoLogo" "False" change to "True"

And I'd have no idea how to change the screen resolution.

Hows about this, is your 1440x900 listed in the System > Admin > Screens and Graphics?

If not check System > Preferences > Screen Resolution.

Cheers,
Basil.

---

### Post by CameronCalver on 2007-12-17
ok iv done that and resoulutions are all good buy when i try to enable desktop effects it says it is unable to enable the effects why?

---

### Post by Tarmael on 2007-12-17
I think I'm gonna have to stop trying to help at this stage.

I'm an ATi user and have no experience with getting Compiz to work on nvidia.

So mark this thread as solved, and make a new one but give reference to this thread in the new one I guess.

Cheers,
Basil.

---

