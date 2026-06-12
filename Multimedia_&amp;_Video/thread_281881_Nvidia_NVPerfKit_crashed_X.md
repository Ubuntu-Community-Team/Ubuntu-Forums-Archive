---
title: "Nvidia NVPerfKit crashed X"
date: 2006-10-21
forum: Multimedia &amp; Video
---

### Post by steveneddy on 2006-10-21
** EDIT ** 

Go to my fourth entry for the solution

** ** ** ** ** ** ** ** ** *

This morning I saw something that I thought I might want to play with, so I installed it. 

The NVPerfKit (Nvidia Performance Kit) was supposed to be a tool kit to tweak the performance of my Nvidia software. I am running Beryl and had just updated the night before and it was looking so sweet, this is real disapointing to happen at such a time. The desktop will only start if I configure the xorg.conf file to the "nv" driver, won't work if I use the acceleration or composite options. The desktop isn't crashing completely, but no buttons, no shortcuts, no mouse movement.....that's a crash, isn't it? OK - it crashes and I need to get it back. 

NVidia 5700 GeForce card, Ubuntu Dapper fully updated, beryl, XGL (disabled) Gnome (gdm) - I'm on my daughter's PC to get an answer hopefully tonight. 

Why won't the Ubuntu Live CD boot on  my system? 

I've even thought of reinstalling, but the Live CD won't give me an X screen.

The machine has always run well until this install. I think that it may have installed another Nvidia driver, maybe even Beta. I'll be honest, I clicked yes all the way through the install just to get to the end before I had to go outside and work. 

Someone please help. There's too much on this machine to loose.

I installed it by using the ./<program>.deb method. I just don't know where it is so maybe I could look for an uninstall script.

Thanks in advance - StevenEddy

---

### Post by steveneddy on 2006-10-21
If there were some way that I could go back - I would be very happy.

I am currently working with the live cd to try and get it to boot into a gui screen, but so far no luck.

Help......](*,)

---

### Post by steveneddy on 2006-10-21
OK - finally got it working with the vesa driver - I need help - I don't know what nvidia driver I am running or how to get my desktop back. Here is the xorg.conf file:

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
	Load	"bitmap"
	Load	"ddc"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"  "/dev/input/mice"
	Option		"Protocol"              "ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons" "true"
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
	Identifier	"NVidia"
	Driver		"vesa"
	VideoRam	 65536
#	Option		"RenderAccel"	      "true"
#	Option		"AllowGLXWithComposite" "On"
EndSection

Section "Monitor"
	Identifier	"P110"
	HorizSync	30-130
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVidia"
	Monitor		"P110"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

#Section "Extensions"
#    Option "Composite" "Enable"
#EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by steveneddy on 2006-10-22
OK - found the problem. When I installed the new nVidia performance kit, it tried to install a driver that wasn't compatable with, well, probabnly my kernel or Dapper...needless to say, after uninstalling everything nVidia, everything works well.

Note: No need for this when running the Beta nVidia driver (9625):


> #Section "Extensions"
#   Option "Composite" "Enable"
#EndSection


-especially if you have composite Optioned in the Device section for the video card.

To check the version of your nVidia video driver:
> 
cat /proc/driver/nvidia/version

I enabled the "nvidia" driver first, then restarted the machine, yes - a full restart.

Then added the:

> Option "RenderAccel" "true"
Option "AllowGLXWithComposite" "On"

 and restarted again.

ALSO of note:

for some reason, during all of this nVidia performance kit installation fiasco, I lost the admin privilidges.

I know, strange, but got them back by:


> sudo -i

which will give you a root prompt,
then-


> usermod -G adm,admin <your user name>

restart - again. Yes, I know, but it is important.

I added the XGL entries in the gdm.conf-custom file and restarted again.

I start beryl from the beryl manager incase of a small crash, so I started beryl and got the perfect blue shimmy. I have never been happier.

BTW - running Dapper, fully updated and the nVidia beta driver (9625) seems to be working well so far.

Next step, to get the Xorg 7.1 or higher working on Dapper. Unless someone know of a reason why it wouldn't, then you may see another cry for help in the near future.

Thank you for reading my tale of grief.

-SE

references:

[http://www.ubuntuforums.org/showthread.php?t=279330&page=3&highlight=lost+root](http://www.ubuntuforums.org/showthread.php?t=279330&page=3&highlight=lost+root)

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by Gorduntu on 2006-10-22
I am glad that you have figured out your problem, and am thankfull that you posted all steps here to help anyone else who runs into this.

---

### Post by steveneddy on 2006-10-23
> **Gorduntu said:**
> I am glad that you have figured out your problem, and am thankfull that you posted all steps here to help anyone else who runs into this.

I am fortunate that none of the stuff that plagues other folks using Ubuntu effects me. I just make some uneducated blunders that do nothing more than educate me a little more about Linux, and how to be very careful when installing something that I know nothing about. 

Usually I come to these forums first to see who is having problems. 

I wonder if anyone else is using this NVPerfKit and having better luck with it than I did.

Love the penguins - SE

---

