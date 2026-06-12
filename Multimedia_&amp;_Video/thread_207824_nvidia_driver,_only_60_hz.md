---
title: "nvidia driver, only 60 hz"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by ruvil on 2006-07-02
Hello!
Today i installed ubuntu 6.06 and it worked perfectly but i saw that i could only choose "60hz" in the "refresh rate" box, so i installed the nvidia-glx driver and i still only could choose 60 hz after that?
How do i change the refresh rate?

i know there is something i need to change in the xorg.conf file, but WERE and WHAT do i change in that file?

---

### Post by woedend on 2006-07-02
gksudo /etc/X11/xorg.conf
under section "Device", change the value "Driver"  to "nvidia"
At the top, under section "Module", put a # sign in front of the line 
Load "Dri"

If you've already done this and still doesnt fix the problem after you've rebooted(or restarted X), open xorg.conf back up and  look towards the bottom at the subsection "display".  Find the one that uses the depth you use (mostl likely depth 24) and try adding _85 to the resolution you want, for example
	SubSection "Display"
		Depth		24
		Modes		"1024x768_85" "800x600" "640x480"
	EndSubSection

---

### Post by ruvil on 2006-07-02
Well, i tried all that but thet just didnt work. I tried it with 1280x1024 and 1024x768, i could only choose 60 hz with both of them and after i tried to change the config (and "redo" it) the 1280x1024 dissaperared from the gnome "chane screen resolution"
So.. is there any other way to solve this?
Heres my xorg.conf:
```
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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
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
	Option		"XkbLayout"	"se"
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
	Identifier	"NVIDIA Corporation NV36.4 [GeForce FX 5700VE]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36.4 [GeForce FX 5700VE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024_85" "1024x768" "800x600"
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

---

### Post by fordfan753 on 2006-07-02
Add this to your graphics card section.

```
Option     "UseEDID"    "FALSE"
```

And you'll definitely want to install nvidia-glx and use the "nvidia" driver instead of "nv".

---

### Post by ruvil on 2006-07-02
Well, i tried add that, and change "nv" to "nvidia" but now it says something like this: "Failed to start xserver its like that is not setup correclty..."
[QUOTE=fordfan753]Add this to your graphics card section.

```
Option     "UseEDID"    "FALSE"
```

And you'll definitely want to install nvidia-glx and use the "nvidia" driver instead of "nv".[/QUOTE]

---

### Post by evil_elman on 2006-07-02
Does your monitor support anything higher / lower than 60Hz?

---

### Post by ruvil on 2006-07-02
When i used windows i could use 75 hz with 1280x1024 and 85 hz with 1024x768

---

### Post by Starmartyr on 2006-07-02
What you need to do is to set your refresh rates (horizontal and vertical) according to the manufacturer specs.  This will then set your refresh rate to 75.

I have a Sceptre X9 nagaIV and my refresh is set at 75 with horizontal @ 15-80 and vertical @ 50-90.

Hope that helps.

---

### Post by ruvil on 2006-07-02
well, then i just hope i find the manual or something similar on the internet, if i dont i guess iam "screwed".

Now i found this guide: [http://ubuntuforums.org/showpost.php?p=406856&postcount=4](http://ubuntuforums.org/showpost.php?p=406856&postcount=4)
Lets try it!
---
Later:
Nope, that didnt work :S
and by the way... when i try to change the "nv" thing to "nvidia" it says: "failed to load module nvidia (module does not exist)".

---

### Post by woedend on 2006-07-02
did you install the nvidia-glx package from the repo's?  Did it come with restricted modules?
nvidia is the driver you want to be using...nv I hate.

---

### Post by ruvil on 2006-07-02
Yes, i installed it from the repo's. How can i see wich modules it came with?

---

### Post by woedend on 2006-07-02
sorry...you need a package called restricted modules...which im sure you already have but just in case
in synaptic search for linux-restricted-modules
there will be a number after modules, indicating your kernel.  If you have the newest kernel, it may look something like
linux-restricted-modules-2.6.15-25

this number must match your running kernel.  to find out your running kernel, in terminal do
uname -r

---

### Post by Starmartyr on 2006-07-02
I had the same issues with my graphics card, or I thought, until I manually added in my xorg.conf file the info on my monitor.  After I did that all was nice.

```
Section "Monitor"
    Identifier     "Sceptre X9"
    HorizSync       15.0 - 80.0
    VertRefresh     50.0 - 90.0
    Option         "DPMS"
EndSection
```

---

### Post by ruvil on 2006-07-02
Oh, Thanks.
And if i understand everything right now.. i can use the 'nvidia' driver instead of 'nv', right?
[QUOTE=woedend]sorry...you need a package called restricted modules...which im sure you already have but just in case
in synaptic search for linux-restricted-modules
there will be a number after modules, indicating your kernel.  If you have the newest kernel, it may look something like
linux-restricted-modules-2.6.15-25

this number must match your running kernel.  to find out your running kernel, in terminal do
uname -r[/QUOTE]

---

