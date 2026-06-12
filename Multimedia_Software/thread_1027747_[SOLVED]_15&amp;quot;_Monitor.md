---
title: "[SOLVED] 15&amp;quot; Monitor"
date: 2009-01-01
forum: Multimedia Software
---

### Post by eckeroo on 2009-01-01
Hello all,

I'm currently stuck with an old DELL 15" Monitor. The model number is DELL E551. My Graphics card is a nVidia GeForce3 Ti 200.

I can get a good screen resolution of 1024x768 @80Hz, but I need to use 
a gnome shell program called 'NVIDIA X Server Settings' which I installed from the Synaptic Package Manager to select it. On the 'X Server Display Configuration' tab, there's a button to update the Xorg.conf file, this however doesn't work and as a result I have to select my 1024x768 screen resolution every time I start up my computer.

The standard 'Screen Resolution' gnome shell only goes as high as 800x600. My guess is that because of my small monitor size, Xorg will only go up to 800x600.

Why can the gnome shell 'NVIDIA X Server Settings' select a higher resolution than the 'Screen Resolution' shell? Will a larger monitor solve this problem?

Any advice will be much appreciated:)

---

### Post by ajgreeny on 2009-01-01
Tryb adding the resolutions you need to your /etc/X11/xorg.conf file with a similar layout to mine as shown here, but with your own figures, of course:-

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

I've omitted all the commented out lines at the top of the file as it is just confusing in this situation.

---

### Post by eckeroo on 2009-01-02
I've tried a few times in the past to solve my problem by amending the xorg.conf file, but it always crashed and reverted to the backup xorg.file.

I don't understand the commands in the xorg.conf file and I can see too many differences between your proposed xorg.conf and mine. There are whole sections missing on your one. Will mine work without them?

Here is my current xorg.conf file with the top comments lines removed:

> Section "InputDevice"
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

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by ajgreeny on 2009-01-02
By the looks of that you must be running an old version of ubuntu, certainly not 8.04 or 8.10, as both of those have an almost empty xorg.conf file.

I suggest you try running sudo dpkg-configure xserver-xorg in terminal and answer all the queries as best you can, using the defaults if you are not sure.  That should give you a choice of driver for your video card and also a chance to choose resolutions, but it does depend on you having the older version of ubuntu and xorg; if you do by some chance have an up-to-date version, that command will not work.

EDIT:  I've looked again and it looks like you could be using 8.04.  If so try running ```
gksudo displayconfig-gtk
``` or in the menus try *System > Preferences > Screen Resolution*

---

### Post by eckeroo on 2009-01-02
Yes, I'm using Ubuntu 8.04

Here's what the gksudo displayconfig-gtk did to my xorg.conf file:

> Section "InputDevice"
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

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"nvidia"
	Busid		"PCI:1:5:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

I was still unable to select a screen resolution of 1024x768 and it left me at a buggy screen resolution of 640x480, which is less than 800x600. I've reverted to the backup xorg.conf

What is it about the NViDIA X Sever Settings program that can configure my screen resolution in a way that the standard Ubuntu programs cannot? It's unfortunate that this program causes the system to crash when it attempts save my configuration to the xorg.conf file which would look this:

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E551"
    HorizSync       30.0 - 54.0
    VertRefresh     50.0 - 120.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce3 Ti 200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0"
EndSection

What are the crucial differences between all the xorg.conf files pasted up on this thread?

---

### Post by ajgreeny on 2009-01-03
If possible go back to your original xorg.conf and just try adding the lines
```
SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
```to the next to bottom paragraph so it looks like this
```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
SubSection "Display"
        Modes       "1024x768" "832x624" "800x600" "720x400" "640x480"
    Option        "AddARGBGLXVisuals"    "True"
EndSection
```Restart x and hopefully--?

---

### Post by heatpumpcontrol on 2009-01-03
I've found that one sure way to fix video issues is the install 'envy' from synaptic package manager. Run the program and have it remove your old 'drivers'. Use the program to install your desire video drivers and reboot. It has always worked for me.

Or you may visit [Alberto's home page]("http://albertomilone.com/").

have fun.

---

### Post by eckeroo on 2009-01-03
I amended my xorg.conf as per instruction:

> Section "InputDevice"
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

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

Unfortunately it still crashed and reverted to a backup xorg.conf file. Although you have put down screen resolutions that are not available in the 'NVIDIA X Sever Settings' program, so now I'm just going to try one setting: 1024x768, and see if that works.

With regards to envy, I don't need it. The proprietary driver for Geforce3 Titanium 200 work fine along with the 3D acceleration. So I will not be changing my driver.

My hunch is that the presence of my small 15" monitor is somehow prohibiting the selection of higher screen resolutions above 800x600 using the standard Ubuntu screen configuration programs. What I would like to know is how the 'NVIDIA X Sever Settings' program manages to select a higher screen resolution using the same drivers.

---

### Post by eckeroo on 2009-01-03
I now tried it with this in the xorg.conf file:

> Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
SubSection "Display"
        Modes        "1024x768" "800x600"
	Option		"AddARGBGLXVisuals"	"True"
EndSection

This also crashed on reboot and I now back to my original xorg.conf file.

---

### Post by ajgreeny on 2009-01-03
OK, I think I'm out of suggestions now.  Sorry, and I hope you do get it fixed soon.

---

### Post by eckeroo on 2009-01-04
Good News!

I noticed on the 'NVIDIA X Sever Settings' program that the resolution settings I was selecting were 'metamodes'. The 'metamode' command is visible from the earlier 'NVIDIA X Sever Settings' xorg.conf output I pasted earlier [Last Paragrapsh]:

> 
Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "0"
Option "TwinViewXineramaInfoOrder" "CRT-0"
[COLOR="Red"]Option "metamodes" "1024x768 +0+0"[/COLOR]
EndSection 

I then simply added this line (and an extra setting) to my original xorg.conf file as thus:

> Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	[COLOR="Red"]Option         "metamodes" "1024x768 +0+0; 800x600 +0+0"[/COLOR]
	Option		"AddARGBGLXVisuals"	"True"
EndSection

And it worked!, when I restarted my computer, the 1024x768 screen resolution was up and running!

:cool:

---

