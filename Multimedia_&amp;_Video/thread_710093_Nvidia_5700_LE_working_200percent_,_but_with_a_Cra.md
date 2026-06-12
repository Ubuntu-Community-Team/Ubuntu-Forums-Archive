---
title: "Nvidia 5700 LE working 200percent , but with a Crappy Refresh rate ... :("
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by stevh0 on 2008-02-28
Recently deleted Xp off my system , good riddance ! 

I installed gutsy and have been extremely happy with it for the past 2 weeks.

since my business is media , i need to run programs like Indesign and Photoshop , 

I got around that by running vmware and installed Xp on there , but running 1024 x 768 on here and the same res on there hurts my eyes.

now it seems that theres been some bugs in the nvidia driver, is there any fix yet? 

im running on 50hz, and the highest it can really push me is 54hz.. 

Any ideas?

---

### Post by erginemr on 2008-02-28
The "Screens and Graphics" tool is buggy. I am also using an NVIDIA card, and it reports my refresh rate wrong as 50-56 Hz, whereas my actual refresh rate is 75 Hz.

Can you please post your /etc/X11/xorg.conf file here? You can run 
```
gedit /etc/X11/xorg.conf
```
from a terminal and copy its contents here.

Also please inform about your monitor, what resolution you are comfortable with, and whether you have enabled the binary NVIDIA driver from "restricted drivers manager".

---

### Post by stevh0 on 2008-02-29
This is why i love this forum, theres just so much support

here is my xorg.cong file

> Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"za"
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
	Identifier	"nVidia Corporation NV36 [GeForce FX 5700LE]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV36 [GeForce FX 5700LE]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
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

im running a 17inch WEN Monitor, usually run about 1024x768 @ 85hz

I cant choose any other display either.

Thanx :)

---

### Post by erginemr on 2008-02-29
Hi again,

Can you please correct your latest post (i.e. the content of the xorg.conf file). It seems you have pasted it twice.

> im running a 17inch WEN Monitor, usually run about 1024x768 @ 85hz

I cant choose any other display either. 

Are you happy with 1024x768 (which is the one I am also using in my 17" Samsung CRT monitor with a 4:3 ratio, or do you prefer, say 1280x1024?

---

### Post by stevh0 on 2008-02-29
The 1024 x 768 is good , 

the only problem i have is when i boot xp on vmware and i run it in 1024x 768 full screen, the refresh rate kill's my eyes. 

Obviously this has something todo with the host's Settings?

---

### Post by erginemr on 2008-02-29
Are you happy with the refresh rate when vmware is not running? If this is the case, I began to believe that this is a setting in vmware that needs to be adjusted.

How about the xorg.conf file? Is it really like the one you have posted? There are sections written twice there.

There must be tool (nvidia-settings) in your system coming from the binary driver installation, which should report your resolution and refresh rate correctly. Can you please check its existence:
Alt+F2 -> nvidia-settings

---

### Post by Officer Dibble on 2008-03-02
> **erginemr said:**
> 
There must be tool (nvidia-settings) in your system coming from the binary driver installation, which should report your resolution and refresh rate correctly. Can you please check its existence:
Alt+F2 -> nvidia-settings

Big thanks to you for your help with this - knowing about this nVidia config screen has solved a million and one problems for me... it's a pity I can only click the thanks button the once. :)

---

### Post by stevh0 on 2008-03-02
> **erginemr said:**
> Are you happy with the refresh rate when vmware is not running? If this is the case, I began to believe that this is a setting in vmware that needs to be adjusted.

How about the xorg.conf file? Is it really like the one you have posted? There are sections written twice there.

There must be tool (nvidia-settings) in your system coming from the binary driver installation, which should report your resolution and refresh rate correctly. Can you please check its existence:
Alt+F2 -> nvidia-settings

The sections written twice is me and a trigger happy Ctrl + V :) 

Thanx alot , ill try and sort out my vmware ...  other then that Buntu' is running SWEET!

---

### Post by erginemr on 2008-03-02
Swweeeet! You are most welcome. 

While I am not used to vmware, I have been using VirtualBox ([http://www.virtualbox.org/](http://www.virtualbox.org/)) at work under crappy Windoze to emulate my Ubuntu and am very happy with its performance so far under Windoze. 

I am not sure how it will perform compared to VMWare, but there should be a Debian installer package and you might want to give it a go.

Take Care & Have Fun! :cool:

---

