---
title: "Nvidia Twinview working only as root"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by Merkwurdigliebe on 2006-07-27
I got Twinview working fine in Dapper until I logged in as a user other than root.  When I did that the right display shut off.  If I kill gdm and restart it and X as root it works fine again until I log in as another user.  Then it messes up. When I log out of the session as the non-root user, the right display comes back on but the display is spread across both LCD's with the login box crammed against the left side of the right screen. 

This is really weird.  I've have this working in Centos 4.3 on this machine and on several other NV-based boxes, but none has ever done anything like this.  

Any ideas?

*************************  xorg.conf ********************************

Section "ServerLayout"
	Identifier "TwinView Configuration"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	Screen 0 "Default Screen" 0 0
	Option "Xinerama" "Off"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/X11/fonts/misc/"
	FontPath     "/usr/share/X11/fonts/TTF/"
	FontPath     "/usr/share/X11/fonts/OTF"
	FontPath     "/usr/share/X11/fonts/Type1/"
	FontPath     "/usr/share/X11/fonts/CID/"
	FontPath     "/usr/share/X11/fonts/100dpi/"
	FontPath     "/usr/share/X11/fonts/75dpi/"
EndSection

Section "Module"
	Load  	"dbe"
	Load  	"dri"
	Load  	"extmod"
	Load  	"glx"
	Load  	"record"
	Load  	"xtrap"
	Load  	"freetype"
	Load  	"type1"
EndSection

Section "InputDevice"
	Identifier  	"Keyboard0"
	Driver      	"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules" "xorg"
	Option		"XkbModel" "pc104"
	Option		"XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  	"Mouse0"
	Driver      	"mouse"
	Option		"CorePointer"
	Option	    	"Protocol" "ExplorerPS/2"
	Option	    	"Device" "/dev/input/mice"
	Option	    	"ZAxisMapping" "4 5"
	Option		"Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   	"Monitor0"
	VendorName   	"SAM"
	ModelName    	"SyncMaster"
	HorizSync    	30.0 - 81.0
	VertRefresh  	56.0 - 75.0
	Option	    	"DPMS"
EndSection

Section "Monitor"
	Identifier   	"Monitor1"
	VendorName   	"SAM"
	ModelName    	"SyncMaster"
	HorizSync    	30.0 - 81.0
	VertRefresh  	56.0 - 75.0
	Option	    	"DPMS"
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
Driver "nvidia"
VendorName "Videocard vendor"
BoardName "NVIDIA GeForce 6600 GT"
BusID "PCI:1:0:0"
Option "NvAGP" "2"
Option "NoLogo" "1"
Option "RenderAccel" "0"
Option "CursorShadow" "1"
Option "Coolbits" "1"
Option "ConnectedMonitor" "dfp, dfp"
Option "NoPowerConnectorCheck"
Option "TwinView" "1"
Option "TwinViewOrientation" "RightOf"
Option "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 800x600,800x600; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
Option "SecondMonitorHorizSync" "30-81"
Option "SecondMonitorVertRefresh" "56-75"
# Option "NoTwinViewXineramaInfo"
EndSection


Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
#	Option 	"Composite" "Enable"
	Option 	"Composite" "Disable"
EndSection

---

### Post by reuben on 2006-07-27
Why are you using twinview as opposed to xinerama? I found the latter to be much better (altho perhaps I didn't have twinview configured properly). Here's my succesful setup: [http://flavor8.com/index.php/2006/07/27/howto-dual-monitors-on-linux/](http://flavor8.com/index.php/2006/07/27/howto-dual-monitors-on-linux/)

I'm not an expert on all of the configuration, but the following looks a little suspicious to me:

Load "dri"
...
Section "DRI"
Mode 0666
EndSection

I thought that dri was not supposed to be used with the official nvidia driver. Also, what is mode 666 doing?

Also, in your server layout section, you are only defining your main screen...maybe twinview is compensating, but I think to be correct you need to define the other screen too. (Again, check out the link above).

---

### Post by Merkwurdigliebe on 2006-07-27
I don't like the behavior of Xinerama.  I prefer two distinct screen edges and so do several of the programs I run, especially VMWare.

I stuck the DRI thing in as the last thing I tried before giving up.  It was in an example xorg.conf file that used the same card and same basic layout.  It didn't do anything, as far as I could tell.  I only tried it because I think I am looking at a permissions problem and that looked like a umask, at least at 2:00 AM when I was pretty burnt out.  

I followed instructions off the NVidia site for that screen setup, and it works fine - as root.  It compensates OK, and it's about all I can do because the NV card has no PCI sub address to hang another driver instance on.  My Dell at work has an ATI card with ports at 1:0:0 and 1:0:1 and that has to have two screens defined. 

Apparently Twinview works a different way - just enabling the option informs the card of the second monitor, but I'll bet they still treat it as one wide screen under the hood somewhere.

I think this thing is an X problem now.  I found this error when I tried to run startx from the command line as the non-root user:

"X: client 2 rejected from local host"

It has another one in the xorg log:

error opening security policy file /etc/X11/xserver/SecurityPolicy

So, it looks like the non-root user gets only one physical screen.  I'll go see if there is a forum for this.

---

