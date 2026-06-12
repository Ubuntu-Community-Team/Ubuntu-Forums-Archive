---
title: "[SOLVED] Nvidia driver error - Out of Range (and other complications)"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by Willvrny on 2008-03-10
This is my first time using Linux, and getting the Nvidia driver installed is causing me serious frustration. Have been attempting solutions now for several hours. I will list all that i have done and as much information as possible in the hope that someone can help find a solution.

Screen: LG M228WD (Flatron 22"inch)
Graphics Card: Nvidia 256mb 6600LE
OS: Ubuntu 7.10

During the installation it set up my graphics as Plug N Play, 800 x 600, 61Hz. However this is not correct. It prompted me to go to  System -> Preference -> Restricted Drivers - and install (Nvidia-GLX-New). However after the reboot i got the error message 'Out of Range' (however i heard the Ubuntu start up sounds, therefore it is a screen error).

I was aware this could be due to the refresh rates. Therefore i tried to edit /etc/X11/xorg.conf to change the Horiz and Vert refresh rates, however i could not find this data on the internet or in the manuals. However, i then tried to run DCCProbe as recommended by [http://www.cyberciti.biz/faq/howto-use-linux-ddcprobe-command/](http://www.cyberciti.biz/faq/howto-use-linux-ddcprobe-command/) however the error message said that there was a complication with EDID. 

I gave up on this approach as i was out of my league. I then tried to use Envy which seemed like the perfect solution. It ran excellently however upon reboot i still got the Out of Range error message. I un-installed using ctrl + alt + f1 and typed envy --unistall-all and then rebooted. Upon reboot the resolution was adjusted to the screen however upon trying to enable effects i was informed that the drivers were needed and this resulted in the same complications as before.

I also tried to install the driver via the Nvidia website (NVIDIA-Linux-x86-169.12.pkg1.run) however i was told that i needed to close X. I tried to use ctrl + alt + backspace etc. However this was to no prevail, because whenever i tried to run the driver i got the error message that X was still active. I tried to change the run level to 3 but this seemed to have no effect. However i am sure that it would register the out of range error even if it could run. 

Here is my xorg.conf gained by using gksudo nautilus to access it in /etc/X11. 

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
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

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

I hope someone can help me as i don't want to resort to windows as i think with 7.10 Linux really has something to offer me. However getting the graphics sorted is a must for me. 

(A friend with a slight amount of Linux experience helped me with these stages however he is also stumped)

Thanks.

Will.

---

### Post by tupactim on 2008-05-18
How did you solve it? im having this problem after uninstalling envy due to blank screen after boot.:(

---

