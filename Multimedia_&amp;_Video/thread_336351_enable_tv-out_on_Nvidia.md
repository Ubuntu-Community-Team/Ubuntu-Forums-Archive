---
title: "enable tv-out on Nvidia"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by Ampsonic on 2007-01-11
I have finally successfully gotten MythTV working on my system! Horray!

Now I just need to get TV out working. 

I've got an Nvidia Geforce4 Ti 4200 in the system, and it's operating on whatever the default driver edgy installs for it. 

I saw a couple of tv out guides, but it seems that they are for expanding the desktop, where as I want to mirror the desktop onto the tv. 

If someone could just point me in the right direction it would be great


Thanks!
Nick

---

### Post by Ampsonic on 2007-01-11
Alright! Been working on this since my post, I installed the real nvidia drivers, then installed NVTV. I have some tv output, but it isn't in color. Working on different settings in NVTV to get it to work, but it's annoying because the wrong settings make it impossible to get to everything on the desktop. Will post my results later.

---

### Post by Ampsonic on 2007-01-11
Still can't get it to output in color....out via svideo and tried every preset availble, all is in black and white. Any ideas?

---

### Post by Ampsonic on 2007-01-11
anyone have any idea? Any help would be greatly appreciated.

---

### Post by kingcharles1666 on 2007-01-15
perhaps setting pal to ntsc or vice versa?

---

### Post by o0splitpaw0o on 2007-01-15
> **Ampsonic said:**
> Still can't get it to output in color....out via svideo and tried every preset availble, all is in black and white. Any ideas?

The Nvidia port doesn't use a standard 4 pin adapter. If you bought it new, it usually comes with a 5 pin adapter that converts to svideo. I know that sounds very retarded, because of the fact that many ALREADY HAVE S-Video port on them!! 

I keep many at my store just because it's a frustrating mistake. They cost less than 1.00 to 50 cents at most places. I'd check out [http://www.svideo.com/leadtek6pin.html](http://www.svideo.com/leadtek6pin.html) This place has many more. compare amount of pins on the agp adapter to the svideo you want.

---

### Post by edward4130 on 2007-01-17
I am having much the same luck.  I have the mythtv system up and running recording things and doing it's thing all while a Ubuntu framework... I love it!!!  Now the Nvidia TV out on my 7600GTS is not working at any output resolution.

When I try to install the Nvidia drivers from the repository It says there is a conflict and I need to remove current software first... Of course it does not specify what software it is.. :) I have yet to go into command line and try to install it the apt-get way as I don't know the exact driver and file URL repositories.  _can anyone give a lead?  It appears this is common but I did not find any How -to's yet.

-Edward

---

### Post by edward4130 on 2007-01-18
can anyone post what they got done to get NVTV to work  I installed it but nothing happens when I open it.  Also still no TV out.... No Nvidia driver will load since I apparantly have a conflict... 

Can anyone tell me how to remove the conflict... that may get me unstuck and put in the Nvidia driver?

-Edward

---

### Post by fenian on 2007-01-19
I could never get NVTV to work.I use seperate x screens to view mythtv,dvds,etc...,to do this You need to edit your xorg.conf file to use twin view or seperate x screens.This wiki tells how to do both

[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)

I personally like seperate x screens because it allows me to watch tv on one screen while continuing to work on the other.Be sure to backup your original xorg.conf file just in case.
If after folllowing the intructions x fails to boot and leaves you at a command prompt
login with username and pass then type
 sudo dpkg-reconfigure -phigh xserver-xorg 
then
ctrl+alt+backspace.

---

### Post by edward4130 on 2007-01-20
well this could be the reason that I dont have tv-out .. I dont even have this xorg thing.  and not a directory in /etc/ that is  "x11".  I'm on the hunt to load it but it is not showing up in the apt manager,  any extra guidance will be appreciated as I have only a few hours to get this running before the wife sends me out to work on HONEY-DO'S

-Edward

---

### Post by fenian on 2007-01-20
In a terminal type
sudo gedit /etc/X11/xorg.conf
note that the  X in X11 is capitalized.This should bring up a text file which you can edit.

---

### Post by fenian on 2007-01-20
Sorry I missed your post about the nvidia driver not working correctly.You can use the envy script to remove and reinstall your nvidia drivers get it here
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
after doing this you will still need to edit your xorg.conf for tvout.

---

### Post by edward4130 on 2007-01-20
I am editing the xorg.conf file directly, but having some difficulty.  First I killed it entirely now I seem to to be editing it and nothing is workeing even after a restart.  I had to go to safemode and copy the backup back in to work again.. he he at least I made a backup before I broke it.

-Edward

---

### Post by fenian on 2007-01-20
In the screens section of your xorg.conf file where it says Option "ConnectedMonitor" try Option "UseDisplayDevice"

---

### Post by edward4130 on 2007-01-20
Can anyone please post to me the Monitors section of this file I am really getting tired of all of the restarting and I can't find a Clear example!!

Just the monitors / ATV -out part.. I shoudl be able to get alll the peices.

-Edward

---

### Post by fenian on 2007-01-20
Here is my xorg.conf file...

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Dec 15 10:12:14 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0       "Screen0"
    Screen 1       "Screen1" rightof "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "Monitor" #CRT
        HorizSync       50.0-180.0
        VertRefresh     31.0-180.0
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier "Television" #TV
        HorizSync 30-50
        VertRefresh 60
EndSection

Section "Device"
        Identifier      "Device0"
        Driver          "nvidia"
        Screen 0
        Option  "NoLogo"        "true"
        Option  "RenderAccel"   "true"
        BusID   "PCI:01:00:0"
EndSection

Section "Device"
        Identifier      "Device1"
        Driver "nvidia"
        Screen 1
        BusID   "PCI:01:00:0"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "Monitor"
        DefaultDepth    24
        Option  "UseDisplayDevice" "CRT"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "Television"
        DefaultDepth    24
        Option  "TVOutFormat" "COMPOSITE"
        Option  "TVStandard" "NTSC-M"
        Option  "UseDisplayDevice" "TV"
        SubSection "Display"
                Depth 24
                Modes "640x480"
        EndSubSection
EndSection


Section "Extensions"
    Option         "Composite" "Enable"
EndSection


would you please post yours so I can troubleshoot.

---

### Post by edward4130 on 2007-01-20
Here is my original file that works at least what i thought was important:

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"M19W"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"M19W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

##### This is the section that will not work.. so much that I hav to restart in safe mode and return to the original.  Man this is really getting old.. I have put in 3 hours and still back at square one.. hope one of you guys can point me in the right direction.  I'm not really wanting to use both my 19 widescreen and the TV soon as the tv works without blowing up i will only use it as it is intended to be a PVR and entertainment station.

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"M19W"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"M19W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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


######thanks !! -Edward

---

### Post by fenian on 2007-01-20
If you only want to use the tv you could try disconnecting the monitor and having the tv as the only thing plugged into the video card.I'm not sure if this would work but it's worth a shot.

---

### Post by edward4130 on 2007-01-20
My F'ing god,   NOTHING  in my building of teh system and using all flavors of linux have i EVER had this much freaking issues...... 

I just want the TV out to work... it has it on the freaking card... Ive spent no less than 6 hours jacking with it today adn more than 30 restarts, because every time the xserver hits a problem it locks up and I have to restart in safe mode... twice I have had to wait for it to check the disks because of 30 mounts without journaling..


AHHHHHHH!!!!  ( I needed to let that out ) 

-Edward

any help will be appreciated as i'm really not getting why it won't just use the freaking tv out because if f'ing does on startup and shutdown as well as durring safemode....  Is that a hint for the ones that beat this thing in the past!!

---

### Post by edward4130 on 2007-01-20
No Monitor... tried that. TV only is just nothing to see and if I use the onboard vidieo out for the monitor I get the same issues.

---

### Post by fenian on 2007-01-20
In the device section where it says Driver 'nv" this need to say Driver "nvidia" .If you haven,t installed the nvidia drivers you'll need to do that using this guide
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
if you have already done this change that line to Driver "nvidia" and try with just the tv hooked up.

---

### Post by crumbum on 2007-01-26
I just got twin view working but my tv is coming out in black and white.  The screen res on my monitor is different as well it says its 1024 x768 witch is what I have always had it set for but everything is much larger looks like crap

---

### Post by graabein on 2007-01-26
I wish there was a good GUI for setting xorg.conf in the next Ubuntu [-o< 
Especially tv-out. I've tried sporadically since Warty but no go.

---

### Post by edward4130 on 2007-01-26
I'm back on this project tonight and Saturday, It will work, and thanks for the points in the right directions.  I love this Distro, lots of participation!  Wish old SGI IRIX was like this, I would have spent many less hours working through stuff.

-Edward

---

### Post by Crakie on 2007-01-26
I had a lot of trouble getting TV-out to work on my 7600GT. Here's a couple of things I learned:

1) My TV was showing both COMPOSITE and SVIDEO in black and white. I had to use a piece of wire to connect two pins together in the TV-out adapter on my videocard. Now in XP everything was ok, but still... no picture in Linux.

2) In Linux, I only got Twinview to work. I can forget about separate X screens.

3) For Twinview to work, the option "ConnectedMonitor" "CRT, TV" was required in the device section of xorg.conf

4) The resolution going to the TV had to be 800x600 or less. 

Using the Twinview method in the Nvidia TV-out wiki of Ubuntu with these additional notes, things should work for people with a similar card.

---

### Post by crazedgremlin on 2007-01-29
run through this and choose nvidia as the driver:
```
sudo dpkg-reconfigure xserver-xorg
```

add all of this [SIZE="1"](just below BusID in Section "Device")[/SIZE]:
```
	Option		"TwinView"	"1"
	Option		"SecondMonitorHorizSync"	"30-50"
	Option		"SecondMonitorVertRefresh"	"60"
	Option		"TwinViewOrientation"		"Clone"
	Option		"TVStandard"	"NTSC-M"
	Option		"TVOutFormat"	"SVIDEO"
	Option		"TVOverScan"	"0.6"
	Option		"ConnectedMonitor"	"CRT, TV"
	Option		"NoLogo"
```



that worked for me...good luck and don't forget that first command (dpkg-reconfigure) in case this doesn't work for you

---

### Post by edward4130 on 2007-01-29
Thanks Guys!  All is working.

---

### Post by graabein on 2007-01-31
I am also working on it, trying multiple X screens with nVidia GeForce GT6600. I have one monitor set up on CRT-1 and the television on TV-0. I get text and boot splash on the television but it turns blue when I get into GDM. Where do I go from here? 

Does this mean I have tv-out if I just set the correct resolution and refresh rate? I have it at 640x480 and a 30-50 and 60 right now... I'm following the [NvidiaTVOut wiki]("https://help.ubuntu.com/community/NvidiaTVOut").

And if I get multiple X screens to work how do I know? Is the telly going to show my desktop wallpaper or something? I'm kind of new to this but hopefully I will learn. 

#-o


Btw I checked the Xorg.0.log and it looks okay as far as I can tell.

---

### Post by graabein on 2007-02-01
Here's my Xorg.0.log if anyone cares:

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.17-6-686 i686
Current Operating System: Linux barbosa 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 20 16:00:49 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "photon20visi"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc105"
(**) XKB: model: "pc105"
(**) Option "XkbLayout" "no"
(**) XKB: layout: "no"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1462,7880 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1462,7880 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1462,7880 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1462,7880 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1462,7880 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1462,7880 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 1462,7880 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1462,7880 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1462,0080 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,00f1 card 10b0,0a21 rev a2 class 03,00,00 hdr 00
(II) PCI: 02:02:0: chip 1033,00f2 card 1033,00ce rev 01 class 0c,00,10 hdr 00
(II) PCI: 02:0b:0: chip 10ec,8139 card 1462,788c rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000d (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf3d00000 - 0xf7dfffff (0x4100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd3c00000 - 0xf3bfffff (0x20000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf7e00000 - 0xf7efffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] rev 162, Mem @ 0xf6000000/24, 0xe0000000/28, 0xf5000000/24, BIOS @ 0xf7de0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf7efef00 - 0xf7efefff (0x100) MX[B]
	[1] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[2] -1	0	0xf7fff900 - 0xf7fff9ff (0x100) MX[B]
	[3] -1	0	0xf7fffa00 - 0xf7fffbff (0x200) MX[B]
	[4] -1	0	0x50100000 - 0x501003ff (0x400) MX[B]
	[5] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[8] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[10] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[12] -1	0	0x0000c400 - 0x0000c43f (0x40) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[14] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[24] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf7efef00 - 0xf7efefff (0x100) MX[B]
	[1] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[2] -1	0	0xf7fff900 - 0xf7fff9ff (0x100) MX[B]
	[3] -1	0	0xf7fffa00 - 0xf7fffbff (0x200) MX[B]
	[4] -1	0	0x50100000 - 0x501003ff (0x400) MX[B]
	[5] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[8] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[10] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[12] -1	0	0x0000c400 - 0x0000c43f (0x40) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[14] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[24] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf7efef00 - 0xf7efefff (0x100) MX[B]
	[5] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[6] -1	0	0xf7fff900 - 0xf7fff9ff (0x100) MX[B]
	[7] -1	0	0xf7fffa00 - 0xf7fffbff (0x200) MX[B]
	[8] -1	0	0x50100000 - 0x501003ff (0x400) MX[B]
	[9] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[12] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[14] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c43f (0x40) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[20] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[30] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "keyboard"
(II) Loading /usr/lib/xorg/modules/input/keyboard_drv.so
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf7efef00 - 0xf7efefff (0x100) MX[B]
	[5] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[6] -1	0	0xf7fff900 - 0xf7fff9ff (0x100) MX[B]
	[7] -1	0	0xf7fffa00 - 0xf7fffbff (0x200) MX[B]
	[8] -1	0	0x50100000 - 0x501003ff (0x400) MX[B]
	[9] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[12] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[14] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c43f (0x40) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[20] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[30] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf7efef00 - 0xf7efefff (0x100) MX[B]
	[5] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[6] -1	0	0xf7fff900 - 0xf7fff9ff (0x100) MX[B]
	[7] -1	0	0xf7fffa00 - 0xf7fffbff (0x200) MX[B]
	[8] -1	0	0x50100000 - 0x501003ff (0x400) MX[B]
	[9] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[12] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[14] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c43f (0x40) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[23] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[28] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[31] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[32] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[33] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 GT at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.36.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 GT at PCI:1:0:0:
(--) NVIDIA(0):     LAC photon20vision2 (CRT-1)
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): LAC photon20vision2 (CRT-1): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xf7efef00 - 0xf7efefff (0x100) MX[B]
	[8] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[9] -1	0	0xf7fff900 - 0xf7fff9ff (0x100) MX[B]
	[10] -1	0	0xf7fffa00 - 0xf7fffbff (0x200) MX[B]
	[11] -1	0	0x50100000 - 0x501003ff (0x400) MX[B]
	[12] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[13] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[14] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[15] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c43f (0x40) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[26] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[32] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[33] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[34] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[35] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[36] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "no"
(**) Generic Keyboard: XkbLayout: "no"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element unix/:7100, removing from list!
```

---

### Post by fenian on 2007-02-02
Yes if you get seperate x screens going television will display your wallpaper and a top and bottom panel.Please post your xorg.conf file if you're having problems.

---

### Post by graabein on 2007-02-05
Here is my xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "ServerLayout"
    Identifier     "Basic Layout"
    Screen 0 	   "screen0"
    Screen 1       "screen1" rightof "screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

			# local font server
	# if the local font server has problems, we can fall back on these
        # paths to defoma fonts
    FontPath        "unix/:7100"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/lib/X11/fonts/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/lib/X11/fonts/cyrillic"
    FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/lib/X11/fonts/Type1"
    FontPath        "/usr/share/fonts/X11/CID"
    FontPath        "/usr/lib/X11/fonts/CID"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/lib/X11/fonts/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/usr/lib/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
	#Load	"dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "keyboard"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "no"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier	"Monitor"
    	#Identifier     "photon20visi"
    	HorizSync       30.0 - 80.0
    	VertRefresh     56.0 - 85.0
    	Option         "DPMS"
EndSection

Section "Monitor"
	Identifier	"Television"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Device"
	Identifier	"device0"
	#Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nvidia"
	Screen 		0
        Option  	"NoLogo"	"true"
        Option  	"RenderAccel"	"true"
        BusID   	"PCI:01:00:0"
EndSection

Section "Device"
	Identifier	"device1"
	Driver		"nvidia"
        Screen 		1
        BusID   	"PCI:01:00:0"
EndSection

Section "Screen"
    Identifier     "screen0"
    #Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
    Device	   "device0"
    Monitor	   "Monitor"
    #Monitor        "photon20visi"
    DefaultDepth    24
    Option	   "ConnectedMonitor"	"CRT-1"
    Option         "NoLogo"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1600x1200" "1600x1200" "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1600x1200" "1600x1200" "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1600x1200" "1600x1200" "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1600x1200" "1600x1200" "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1600x1200" "1600x1200" "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1600x1200" "1600x1200" "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"Television"
	DefaultDepth	24
	Option		"TVOutFormat"		"SVIDEO"
	Option		"TVStandard"		"PAL-G"
	Option		"ConnectedMonitor"	"TV-0"
	SubSection "Display"
		Depth 24
		Modes "640x480"
	EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by fenian on 2007-02-05
First make sure you have the latest nvidia drivers (9746) if you don' already have themyou can get them by using envy...

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
 
You will need to use the script to remove all old nvidia drivers first and then use it to install the new ones.

After you have the new drivers installed type in a terminal

> gksudo /usr/bin/nvidia-settings

This will bring up the nvidia setiings window enable both monitors using separate X screen (or twinview if you prefer that) with appropriate resolutions then click the save x configuration button and exit.Restart X (ctrl+alt+backspace) login and you should have tvout.

---

### Post by graabein on 2007-02-08
Well that broke X. I downloaded and installed **envy** deb and logged out of X as it said to. Then I uninstalled and installed then nvidia driver. I got some error messages about not finding X server when I ran **nvidia-settings**. 

I'm at work now so please tell me what logs and error messages to look for when I get back home. I did not have time to look at this last night.

---

### Post by graabein on 2007-02-08
I'm at home now. Any takers?

:popcorn:

---

### Post by fenian on 2007-02-08
Were you able to log into X after you installed the drivers?

---

### Post by graabein on 2007-02-08
No. I get a blue text-based page with the following message: 

*Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?*

I hit <yes> and get:

```
GDM: Xserver not found: /usr/bin/Xgl :0 :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM.
```

Suggestions?

---

### Post by fenian on 2007-02-08
Somehow the drivers didn't install correctly.I would go through the envy install steps again.Be sure not to run nvidia-settings until you are logged back into X.The envy script should end by restarting X automatically.

---

### Post by graabein on 2007-02-08
OK it said uninstallation of drivers was complete. Then I install again. -- Is the on screen text logged to envy.log file btw? -- I answer <yes> for automatically configure xorg.conf. I also answer <yes> to starting xserver... 

It says the same thing as it did in my previous post. And before the blue screen with that message it says: **sudo: /etc/init.d/kdm: command not found**.



Edit: I'm off to bed. I'll send a mail to the creator of envy tomorrow.

---

### Post by graabein on 2007-02-09
I'm going to read through the [support thread]("http://www.ubuntuforums.org/showthread.php?t=281823") here on the forums before I do anything further...

:-#

---

### Post by FrancoNero on 2007-02-09
> **fenian said:**
> 

[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut).

there should be a GUI (or system controls option) for this. after all, it's supposed to be linux for human beings ;-)
it's things like this that keep lots of people from converting to linux....

---

### Post by crazedgremlin on 2007-02-17
> **graabein said:**
> OK it said uninstallation of drivers was complete. Then I install again. -- Is the on screen text logged to envy.log file btw? -- I answer <yes> for automatically configure xorg.conf. I also answer <yes> to starting xserver... 

It says the same thing as it did in my previous post. And before the blue screen with that message it says: **sudo: /etc/init.d/kdm: command not found**.



Edit: I'm off to bed. I'll send a mail to the creator of envy tomorrow.

um...aren't you running gdm?  Why is it going to kdm?  that's weird

---

### Post by graabein on 2007-02-28
> **crazedgremlin said:**
> um...aren't you running gdm?  Why is it going to kdm?  that's weird

Yeah I know... Can't understand where it gets kdm from... When i reconfigure X to use vesa :shock: I get back to gdm and into X but it's low resolution and painfully slow. Any idea how to fix this kdm/gdm thing?

---

### Post by crazedgremlin on 2007-02-28
I think a
```
sudo dpkg-reconfigure ubuntu-desktop
```
might work...didn't try it out...

---

### Post by graabein on 2007-03-01
Now we're getting somewhere! It said **ubuntu-desktop not installed** so I did and reconfigured X. It still won't launch GDM. I get the same error message as before upon restart but now I have **nvidia** driver and a manually set *xorg.conf* with screen resolution to 1600x1200 so I can use it as I did before. 

Any suggestions where to look to identify the error? I checked **Synaptic** and it says that GDM is installed.

---

### Post by crazedgremlin on 2007-03-01
this is super weird.   what you're saying is you did```
sudo apt-get install ubuntu-desktop
```

if gdm doesn't launch:
1) press ctrl+alt+f1 to go to a console
2) login
3) type ```
sudo '/etc/init.d/gdm start'
```

---

### Post by graabein on 2007-03-01
Sure I'm sure. Already got newest version it says. When I start gdm by hand I get the same result. So I logon in text mode and startx. Then it's all fine. 

BTW I got tv-out now. YAHOOO! Been a long time coming! Doing **gksudo /usr/bin/nvidia-settings** got me a nice config app to set it up. Running two X screens now. Still have to tune screen1 to fit the telly and fix Freevo a bit...



Screen1 is a bit off on the telly. Can I adjust this in the xorg.conf file? I want it a bit up and to the right.

---

### Post by denis_std on 2007-03-19
Hello guys! 

I got a question. I have the following setup: 

TV: 

german CRT -> PAL-B or PAL-G

graphics card: 

> 
AOpen Nvidia 5200FX

          o GPU Takt: 200MHz
          o Speicher Takt: 400MHz
          o AGP-Modus max.: 8x
          o Arbeitsspeicher: 128MB
          o Hardware Monitoring: NEIN
          o Anschlüsse: 1x TV-OUT  S-Video, 
          o Steckplatz: AGP
          o Speicherzugriffszeit: 5 ns
          o Chipsatz: nVidia GeForce FX5200
          o Grafikspeichertyp: DDR
          o Auflösung: 2048 x 1536 
          o Unterstützung: DirectX  9.0  

drivers:

nvidia driver installed via the envy script: 1.0-9746

here is my xorg.conf:

[http://www.ubuntuusers.de/paste/8436/](http://www.ubuntuusers.de/paste/8436/)

my problem:

I get no picture at all at the tv.
If I use the nvidia gui from the driver to setup the tvout, twin view works fine but the colors on the tv are only black and white. 
Under Windows XP I get a colored picture with the same hardware setup.

Before I tried to add the following options to get it working but it failed as well. I only get a picture at the tv in black and white.

These were the options I added: 

> Option "TwinView" "true"
Option "TwinViewOrientation" "Clone"
Option "TVOutFormat" "COMPOSITE"
Option "TVStandard" "NTSC-M"
Option "SecondMonitorHorizSync" "30-50"
Option "SecondMonitorVertRefresh" "60"
Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;    512x384,512x384"
Option "ConnectedMonitor" "CRT,TV"

I'm really frustrated now. What's my fault? 

I'm looking forward for your answers!

Regards, Denis

Würde mich über Hilfe sehr freuen! 

Gruß Denis

---

### Post by denis_std on 2007-03-19
*Push*

---

### Post by kingmob on 2007-04-19
Same problem as the guy above me, though i am using SVIDEO. This works fine in windows, but here i only have B&W :(.

Also, does anyone know how you can run different users on the different x-screens? Preferably i'd like them both to automatically login, but both as a different user, automatically starting mythtv on the TV. I've got a seperate set of mouse and keyboard and should be setup too probably.

---

### Post by laurbalaur on 2007-04-19
Hy. I have the same problem. Here's my xorg:

[PHP]# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Nov  1 19:47:17 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 MX 440]"
    Driver         "nvidia"
    Option "TwinView"
    Option "TwinViewOrientation" "Clone"
    Option "SecondMonitorHorizSync"     "30-50"
    Option "SecondMonitorVertRefresh"   "60"
    Option "MetaModes" "1024x768, 1024x768; 800x600, 800x600; 640x480, 640x480;"
    Option "TVStandard" "PAL-G"
    Option "TVOverScan"	"0.6"
    Option "TVOutFormat" "SVIDEO"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 MX 440]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
EndSection

Section "Extensions"
    Option         "SVIDEO" "Enable"
EndSection

[/PHP]

---

### Post by Blyzzard on 2007-04-19
I've been struggling almost non-stop now for about 4 days to get my tv-out to work.

All i have is Ubuntu 6.06 Dapper and i've tried most (if not all) of the suggestions i could find here.

i've tried this: 
[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut) 
and i've tried this:
[http://doc.gwos.org/index.php/Nvidia_easy_tv_out](http://doc.gwos.org/index.php/Nvidia_easy_tv_out)

I have tweaked, fiddled, mauled, hacked and done what i'm sure is illegal in about 20 countries to the xorg.conf file.

my hardware i hear you ask?

AMD motherboard (semperon 2600) and a nvidia 5200.

I used to run XP on that machine and the tv-out worked (i'm sorry to say). so i know the connection is good. I've completely killed one installation of Dapper and had to re-install from scratch.

i've tried installing nvidia drivers and that causes more problems tahn it's worth.

If you've read this far, thanks, this isn't a rant, it's a plea for help.

I've been beating my head on my desk and i've lost sleep over this, i REALLY don't want to go back to XP but if i can't get the tv-out working on it, i'll be forced to :( 

Some stuff comes through on my screen from boot-up... pictures:

This is what i see while it's booting:
 [IMG]http://www.blyzz.com/ubuntu/00.jpg[/IMG]

And this is what i see while i'm logged on:
 [IMG]http://www.blyzz.com/ubuntu/01.jpg[/IMG]

If i set the background to a dark colour, my tv becomes very dark, and then if i move a window (with a light coloured titlebar) around i can see that, what's being displayed on my tv is the top few pixels on the screen.

So it's not quite a clone of my desktop, but closer to a clone than to a dual-view type setup.

the closest i've come to seeing this work is that other people have posted that they have got it to work, unfortunately, i'm still in the dark (pls excuse the pun).

Also: If you know what my problem is and decide to help: please pretend i'm a complete idiot and let me know what to do step for step. I'm still very new to the whole non-microsoft environment, and only partially acquainted with the terminal

Thanks

Blyzz

---

### Post by laurbalaur on 2007-04-20
Sorry, my mistake. I used COMPOSITE and it worked.

---

### Post by Blyzzard on 2007-04-23
Anyone got any suggestions for me while i still have some hair left?

---

### Post by crazedgremlin on 2007-04-23
have you tried my solution on page 3?
First make sure you have nvidia-glx installed (or nvidia-glx-legacy...whatever's appropriate for your card)
Second, do what I said on [page three]("http://ubuntuforums.org/showthread.php?t=336351&page=3")
you can skip the first part if you've already set nvidia as the driver.

---

### Post by ahardy66 on 2007-04-26
Just read this thread and have to jump on it, hopefully it's still fresh. 

I've got the colour problem - just black and white. I picked up a £20 cable that's tv-out to scart, and I thought this one should do the job, so i was disappointed to read that people are laying the blame for the lack of colour on the cable. 

This cable that I've got has no instructions or manual with it, but it is high quality and it even has a switch on the scart plug, although I have no idea what the switch does. 

What I'm asking is, does nobody have any experience of the black and white problem that isn't caused by cable issues? It will be my third attempt to buy cables if I have to get another one!

I'm in the UK so I might even have to order it from the States, which will take an age and all for what something I'm not sure about at all!

Thanks!

---

### Post by kingmob on 2007-04-27
Well i am 100% sure it isn't a cable issue in my case, but a driver issue with nvidia. I have it working in a weird way in windows, with svideo to composite converters, because my TV doesn't take svideo. 
The thing is however, if i'd had gotten a proper cable from nvidia, it wouldn't have that big a problem, since i would have had acces to all the pins. Now all i have is a lousy 9pin to svideo. And it is precisely this that seems broken, where the colour channel is broadcast over the wrong pin. 
The switch on your scart most likely switches between composite and svideo and that can make the difference between colour and B&W.

I have it seen reported that component out is also somewhat bugged on some cards, at least mine (6600GT), where one channel is broadcast over the composite pin :|.

If they'd just used standard connectors, instead of these weird 9-pins for which i can't get a cable anywhere, all would have been fine :(. Sadly ATI does something similar |(But ofcourse slightly different).

---

### Post by ahardy66 on 2007-04-28
I've got a 9-pin on my galaxy zalman 7950gt and it looks like the 'pro 7 pin' that they've got pictures of on [www.svideo.com](www.svideo.com) - is that the same with yours?

---

### Post by osxdude on 2007-04-28
My nVidia card came with one of those S-Video to Compsite adapters; you actually have to change a special setting to get color. It is inside the nVidia's Advanced display properities. (on the Windows platform.)


Jus' wanted to give my part.

---

### Post by kingmob on 2007-04-29
The problem is that it is not an svideo to composite adapter, but simply a "strange 9-pin connector"-to-composite adapter. It looks like svideo, but it is not the same.
The pro-7 thing looks a lot like the same thing, but then for Ati i believe.

Also, this might be a problem, but because tv-out is so different for every single damn card it seems, there can be a whole lot of different causes to your problems. However, if svideo works on windows but not on ubuntu, i think we can safely say that the driver is bugged. To me it looks like you should fall back to composite if you have problems with svideo. But the sad thing is i never received that adapter with my card :(

---

