---
title: "Strange NVIDIA resolution problem..."
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by censored77 on 2008-01-15
I could never get Ubuntu 6 to work with my video card (geForce 5200) at anything other than 640 x 480, - it simply didn't give me the option for anything else, so I gave up.

Now, I've installed 7.10 and it works fine with the open source drivers. However, if I switch to the restricted drivers to get all the visual wizzy stuff, it reverts to 640 x 480. Even if I set the Monitor to be a 1280 x 1024 LCD, and set the Screen Resolution to be 1280 x 1024.

All this does is to give me a much bigger desktop, complete with whizzy visuals, but displayed at low res and I have to scroll around it!

Any ideas?

---

### Post by andrew5859 on 2008-01-16
Unfortunatly you're gonna have to go in and edit your xorg.conf file manually through the terminal with root privliges, example; "sudo nano /etc/X11/xorg.conf" then hit enter. It then should bring up your xorg file for you to edit.  I had to do the same to my machine and I'm running Ubuntu 6.06LTS, and unfortunately the stock configuration for nvidia is "nv", when it should be "nvidia".  Here's a copy of what mine looks like now:      


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
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"NEC FP955"
	Option		"DPMS"
	HorizSync	30.0 - 110.0
	VertRefresh	50.0 - 160.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"NEC FP955"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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


 Look at the sections where it says device and the other says monitor.  You have to have the name of the device, which is nvidia, and then the monitor should hve the horizsync and vertrefresh rates.  If you can, go to or find the website for your monitor and download the manual
for it to check out the horizontal and vertical refresh rates.  Like mine is: HorizSync  30.0 - 110.0
                                                                                                                    VertRefresh  50.0 - 160.0

You can find the nvidia driver in the restricted area of synaptic package manager under miscellaneous-graphical (restricted).  It's the nvidia-glx driver, click on it to install.  Once that it done, then type: sudo nvidia-glx-config enable.  When that is done, go into the terminal with root 
privliges and typ sudo nano /etc/X11/xorg.conf, it should bring up the file, then go in and take care of business.  If you have and further problems or questions, give me or write me back and let me know.             Andrew   8)

---

### Post by censored77 on 2008-01-17
The driver is enabled - I know that because I get the nvidia splash screen on startup. Also, I can use sudo nvidia-settings to get up the control panel: and it's in here where it only gives the option for 640x480 despite 1280x1024 appearing on the Preferences menus.

---

