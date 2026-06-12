---
title: "VLC + XVideo + Wine = Yellow... something"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by eretron on 2008-04-14
Hello, I'm experiencing a very disturbing problem.

Here is info...

Power up
Go and play any video and it works perfect
start an win application with Wine
Go and play ANY video and all I get is perfect Audio with yellowish picture (screen shot attached)

Its all the same regardless which player I'm using VLC or Totem... 

I've tried do disable Allow the window manager to control ... option in wine but no help..
Maybe this is not Wine related, but Its the only thing that comes to my mind..

I've tried System>Preferences>Appearance and setting effects to None, bud that changed nothing

I'm using NVIDIA 6600 GT graphic on Ubuntu 7.10 x32

Below is my xorg.conf if it can help

Thanks In advance

[IMG]http://img98.imageshack.us/img98/999/screenshotut2.png[/IMG]

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
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Buttons"	"7"
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
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	Busid		"PCI:7:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600 GT]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
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

### Post by eretron on 2008-04-14
Ok, in meantime I've run Envy script and reinstalled NVIDIA driver... so far its working flawlessly... so I'll keep fingers crossed, and I'll write an update after a few hours of work if it is still working ok...


for now... THANK YOU ENVY :D

---

### Post by xc3RnbFO8P on 2008-04-14
Which application did you run in Wine.

---

### Post by eretron on 2008-04-14
ApexDC+ and NewsBin Pro... still everything is OK :D

---

### Post by xc3RnbFO8P on 2008-04-14
Sorry I don't know these programs, but do they use video drivers?

---

### Post by eretron on 2008-04-14
Oh, sorry for that. 

I guess they dont use Video driver.

ApexDC iz a DC++ client for DC types of networks... Very simple download client

NewsBin Pro is also simple Usenet reader and binary fetcher... 

Both are similar with IRC chat clients.... So nothing special, very small and lightweight programs...

I think now I can confirm that Envy did the trick, everything runs perfect now

---

### Post by eretron on 2008-04-16
SOLVED by Envy, now 100% sure...

---

