---
title: "Dual-monitor, dual video card setup guide"
date: 2006-10-16
forum: Multimedia &amp; Video
---

### Post by Rich@CMU on 2006-10-16
I am new to Ubuntu and fairly new to Linux in general.  Over the last 2-3 weeks, I have spent over 15 painful hours wading my way through the many, many how-tos on the Ubuntu forums instructing users how to get dual monitors working.  There was a lot of good information and I learned quite a tremendous amount in the process (particularly from the extensive how-to at: [http://www.ubuntuforums.org/showthread.php?t=221174)](http://www.ubuntuforums.org/showthread.php?t=221174)).

Unfortunately, none of these how-tos was able to guide me to working dual monitors.  I wish I could say that I have some unusual set up, but I have two identical 17-inch Samsung SyncMaster 170N LCDs and two nVidia video cards.

Anyway, I have finally gotten it working (yee haw!) and would like to share my solution in case it might come in handy for other people who are new to this sort of thing.  Although this is really long, it is actually really simple... I'm just trying to spell everything out so there is as little confusion as possible (I was a very confused lad reading through many of the how-tos).   :-)

First, as almost every other how-to on the subject wisely instructs, **backup your [COLOR="Red"][/COLOR]/etc/X11/xorg.conf** file. ```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
``` My understanding is that xorg.conf is a configuration file that X Windows checks when it loads to figure out how to set up the windowing environment, including mouse, keyboard and monitor interaction.  Anyway, back it up because you're going to be making a lot of changes to it and if something goes wrong (and it certainly did for me -- many, many times :-)), you can get things back to how they were before by restoring xorg.conf and restarting X Windows.  For instance, if X Windows is not starting and you're stuck at a command prompt, do this: ```
sudo mv /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
startx
```

Now for the fun part.  

Almost all of the how-to docs on the forums run you through lots of specific details on how to set up xorg.conf for dual monitors.  You're not going to completely get out of that, but X Windows actually knows how to do most o fthe hard part for you.

You're going to run "X -configure", but it won't run while you're running X windows, so you'll have to exit out of it.  In most Linuxes, you would just use CTRL-ALT-BACKSPACE to shutdown X Windows and get to a full screen command prompt.  However, Ubuntu seems to automatically reload X Windows after about 10 seconds, so that isn't going to work for us.  Instead, reboot Ubuntu, but when you get to the GRUB boot menu, choose Ubuntu "recovery mode".  This will boot Ubuntu to a command prompt and will not start X Windows.  (Note: please chime in with a simpler way to shut down X Windows without it restarting automatically). 

Now run: ```
X -configure
``` This X Windows command detects your video cards and monitors and creates a (mostly) appropriate xorg.conf file and places it at /root/xorg.conf.new.  When you run this command, the screen will probably go blank for a second, then most likely spit out a warning about not being able to detect your mouse or keyboard... we'll fix this in a minute.

Now reboot your system by typing "reboot".  Choose the normal Ubuntu option from GRUB this time.

Now we're going to edit the xorg.conf file that X Windows just created for us. We're going to copy over some of the stuff from our current xorg.conf, so you'll need to have both of them open. I use gedit to edit my files below, but feel free to use whatever text editor you like.  

Open a terminal and type: ```
gedit /etc/X11/xorg.conf
```
You should see something like:
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
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:1:7:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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
```

Now, open another terminal and type ```
sudo gedit /root/xorg.conf.new
``` 
You need to edit this file, so don't forget to use 'sudo'.  This file should look something like this:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
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
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "record"
	Load  "xtrap"
	Load  "freetype"
	Load  "type1"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/mouse"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  340   270	# mm
	Identifier   "Monitor0"
	VendorName   "SAM"
	ModelName    "SyncMaster"
 ### Comment all HorizSync and VertSync values to use DDC:
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	#DisplaySize	  340   270	# mm
	Identifier   "Monitor1"
	VendorName   "SAM"
	ModelName    "SyncMaster"
 ### Comment all HorizSync and VertSync values to use DDC:
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV11 [GeForce2 MX/MX 400]"
	BusID       "PCI:1:7:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
	Identifier  "Card1"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV18 [GeForce4 MX - nForce GPU]"
	BusID       "PCI:3:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```

The first thing I recommend you do is replace the mouse and keyboard sections in the new file with the corresponding sections from the old xorg.conf.  This will ensure that they'll continue to work the way they used to and won't cause any issue for X Windows.  In my case this means I need to remove:
```
Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/mouse"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection
``` 
and replace it with: 
```
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```
Next, make sure that the ServerLayout section of the new xorg.conf reflects these changes.  In my case, I need to change:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	[B]InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"[/B]
EndSection
``` to
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	[B]InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
[/B]EndSection
```

Notice that all I did was copy those lines over from the old xorg.conf file.  If there were other devices listed in the "ServerLayout" section of your old xorg.conf, copy them over as well.

Now take a look at the "Files" and "Module" sections.  Copy over any lines that are not present in the new file, but be sure not to leave any duplicates.  Your old xorg.conf may also have additional Sections for other devices.  Copy those over as well.

Save your changes.

Open a termial and type > sudo mv /root/xorg.conf.new /etc/X11/xorg.conf

If everything above was done carefully, you should now be able to restart X Windows and see both screens.  Hit CTRL-ALT-BACKSPACE to exit X Windows.   X Windows should restart automatically in about 10 seconds, but if it doesn't type "startx".  

After you log on, you should see two desktops.  If for any reason you encounter an error and X Windows won't start, type the following to restore your original xorg.conf file and restore X Windows:```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
startx
```  Hopefully, it doesn't come to that, but if it does, try the procedure again double checking for typographical errors or skipped steps.

After you get this working, if you'd like to be able to drag windows between your two screens and use a single shared task bar, you'll need to add the following to the end of your xorg.conf:
```
Section "ServerFlags"
  Option    "Xinerama" "enable"
EndSection
```

Finally, I just want to say that I realize this undoubtedly won't work for everyone on all different setups, but hopefully it will be a breakthrough for some and at least a help to others.  The real breakthrough for me in getting this to work was stumbling across "X -configure" and just giving it a try.  Ironically, we can thank the following how-to on Gentoo's wiki for this: [http://gentoo-wiki.com/HOWTO_Dual_Monitors#Setting_up_Two_Graphics_Cards](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Setting_up_Two_Graphics_Cards)

Good luck and if this helps you, let me know. :-)

---

### Post by NeilBlanchard on 2007-04-12
Hello,

Are these instructions still appropriate?  I would sure love it to have the ability to just turn on a second monitor, and have it work...

---

