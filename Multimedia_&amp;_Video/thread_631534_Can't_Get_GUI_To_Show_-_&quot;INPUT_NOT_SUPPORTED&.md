---
title: "Can't Get GUI To Show - &quot;INPUT NOT SUPPORTED&quot; message is shown - Ubuntu 7.10"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by andrew.pope on 2007-12-04
I have an Acer AL1716 LCD Monitor. I am having trouble using it with the GUI of Ubuntu.

I downloaded Ubuntu Desktop 7.10 Live CD and in order for it to start I had to choose Start In Safe Graphics mode. I Think this is relevent.

I realised that I didn't have enough RAM to install from the Live CD so I Downloaded Ubuntu Server 7.10 Text Installer. I installed it and everything was fine with it. I wanted to install gnome desktop so i did

sudo apt-get update
sudo apt-get install ubuntu-desktop

and my installation took about 1hr30mins. After this i restarted and booted into ubuntu. it went through several sages to set up my pc and then the screen went blank then after about 2 seconds a mesage came up saying "Input Not Supported". i can press ctrl+alt+f1-6 and get ttys but the desktop won't show, i can hear the sound as the desktop pops up but i can't see it on my screen.

On windows I have a smiliar problem on resolutions higher than 800x600, but only before I install the driver for my graphics card (SiS 650/651/740/660FX1/741/760 Series) then I can set it to what ever I like.

How can I make my screen work in Ubuntu? I am new to linux and so only know a few basic commands. But I am willing to learn.

If there's a way to boot into the same mode as the Safe Graphics Mode on the LiveCD? Or not? if so, what is it.

If you need any more info please ask!

thanks in advance for any support!!

cheers,

Andy

---

### Post by bailey^ on 2007-12-04
This is like the problem i have at the minute

Monitor : Acer AL1716

Whenever i boot up a live CD or the OS after a text based installation i recieve input not supported. Only ever got it to work after installing Ubuntu in safe graphics mode. But then when i tried to set up my Radeon 9000 properly for 3D Accelleration and support, when i rebooted once again got the message Input not supported ...

---

### Post by bailey^ on 2007-12-04
[http://www.linuxquestions.org/questions/fedora-35/monitor-works-until-x-is-restarted-fc7-571874/](http://www.linuxquestions.org/questions/fedora-35/monitor-works-until-x-is-restarted-fc7-571874/)

Hope this helps, i cant try it at the minute but im going to attempt changing my xorg.conf this way tomorrow. Let me know how things go ...

---

### Post by Letori on 2007-12-15
I'm having a similar problem, but for me the trigger is when an application goes fullscreen, ie. wine or totem movie player.

as soon as fullscreen is achieved, I get this little gray box that floats around my screen (over top of my gui, my gui and it's performance are apparently unaffected by this). No matter what I do, the damn box will float around overtop my workspace until I restart X. it's really annoying, as I enjoy watching video fullscreened and playing games as well.

I have the same monitor, ACER AL1716, with an ATI Radeon X700 pro (it's the AGP version, that pretends it's pci-e, apparently). Using the most recent flgx (or w/e) drivers.

I have tried a few different posted fixes to no avail, adding a line in the xorg.conf under the device section (Option "UseEDID" "false")
Also tried to find the refresh rates of my monitor, but was unable to, despite finding ACER's user documentation on their site. AL1716 is apparently one of the few models not available in the monitor configuration menu, so I'm stuck on the "Generic Monitor" setting there unless someone knows something I don't (very likely).
the fix posted in the post above mine... I don't see how to implement it, as there are no listed resolutions in my xorg.conf file.

I'm going to post my xorg.conf file in a moment here... on a different box atm.

---

### Post by Letori on 2007-12-15
<Edit: screwed myself with a bad conf file, reverted to this one - the one that works.>

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "UseEDID" "FALSE"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
EndSection

Section "Extensions"
	Option	    "Composite" "disable"
EndSection


Any assistance would be much appreciated guys. <3 Ubuntu.

---

### Post by Letori on 2007-12-15
anyone? :(

---

