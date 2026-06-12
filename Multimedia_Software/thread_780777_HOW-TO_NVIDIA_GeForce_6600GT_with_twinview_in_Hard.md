---
title: "HOW-TO: NVIDIA GeForce 6600GT with twinview in Hardy Heron"
date: 2008-05-03
forum: Multimedia Software
---

### Post by MatthewAPeters on 2008-05-03
I finally got it working!  

I promised someone I would share the how-to.

Since I suggest printing it because much of it is done in the command terminal, I am attaching as a text file.

I am also including my xorg.conf, which you can use and hack to your heart's content, but I offer here with the wfm caveate: it worked for me, what else do you want?

Just a heads-up, the solution DOES use Envy, so unfortunately it will be easy.  This solutions is specifically for the NVIDIA GeForce 6600GT card.  It may work for other NVIDIA cards if they are between 2 and 5 years old - but I can only vouch for my card.  Also, this has taken a couple of days to figure out, so I am somewhere between tired and wired.  You will have to put up with my sense of humor - don't worry, its PG13.  

If you have been struggling to get your video card working like it used to, and this how-to doesn't work for you, I will be cross-linking other threads and/or bugs I have tripped over on the way here - maybe someone else will uncover something along the way.  Stick with it, and everyone know what you figure out.  It's good karma.

Thanks to those that helped me get it working - you know who you are - enjoy what remains of your weekend!


These are other threads or bugs that I have tripped over while trying to get my system back to normal.  Most appear to be directly related.  Others are only slightly tangential.

Cross posts: 
[dual monitor issue]("http://ubuntuforums.org/showthread.php?t=774245") 
[Bug #220374 in linux-restricted-modules-2.6.24 ]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/220374")
[nvidia 6600 not supported]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/219101")
[Nidia 6600GT Drivers, never getting the right resolutions, only when booting in safe mode]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/211387")
[Dual Monitors Working, can't drag windows between them]("http://ubuntuforums.org/showthread.php?p=4874036#post4874036")
[nvidia legacy and screen resolution]("http://ubuntuforums.org/showthread.php?p=4874082#post4874082")
[Did you have problems getting the proprietary Nvidia drivers going in Hardy?]("http://ubuntuforums.org/showthread.php?p=4874114#post4874114")
[Nvidia driver problems]("http://ubuntuforums.org/showthread.php?p=4874131#post4874131")

---

### Post by Chester87 on 2008-05-04
Maybe u did it the same way as i did it, but this is how i did it. After a fresh install off Ubuntu 8.04.

First install all the drivers using the Hardware Drivers under System>Administration>Hardware Drivers. It will ask you to reboot, just reboot.

Then install EnvyNG for Ubuntu 8.04, which u can find here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

After a successful installation of EnvyNG, run it. There you can click which card u have, Nvidia in this case. And check the automatic hardware recognition thing.

This will install all the things u need for NVidia to run properly. After your done installing go to System>Administration>Nvidia X Server Settings. You **[SIZE="4"]dont[/SIZE]** even get this error when you start up X Server > You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server This is where u can change all the resolutions and monitor depth etc. In here click on X Server Display Configuration. Adjust your second monitor so it has the right resolution and is on the left or right of your original one.

In my case (I have two 19" Acer AL1922 monitors) i configured it with separate x screen and enabled Xinerama. The moment you click apply it asks you to reboot, DONT reboot. Because everytime that you reboot it will forget your configuration. Instead save to X Configuration File. And save the file on your desktop.

Open the file and copy the complete content. Then open your Terminal. And type ```
sudo gedit /etc/X11/xorg.conf
``` There you can delete all the stuff that there is standing there and paste the content off the other file there. Save the file and reboot. And your done you got two working monitors. 

And in my setup I even rotated 1 monitor. All working really fine now. Even when you maximize one window it wont take both monitors but it will stick on just the monitor that you maximized it on.

If you want to rotate an monitor like in my setup. At these who lines:
```
Option "RandRRotation" "On"
Option "Rotate" "CCW"
```
Where CCW stands for Counter Clock Wise. If you want to rotate is Clock Wise just change it to CW.

I'm sorry if my English isn't that good, hope that people understand what i wrote :D

---

### Post by process91 on 2008-05-22
This still does not work for me. I followed the "default" or "suggested" Ubuntu procedure first, by installing the NVIDIA driver via the restricted driver manager. Then I uninstalled it and followed the procedure outlined in the HowTo here. It simply does not work. No error message, nothing. I start X and I get a frozen black screen.

---

### Post by MatthewAPeters on 2008-05-23
> **process91 said:**
> This still does not work for me. I followed the "default" or "suggested" Ubuntu procedure first, by installing the NVIDIA driver via the restricted driver manager. Then I uninstalled it and followed the procedure outlined in the HowTo here. It simply does not work. No error message, nothing. I start X and I get a frozen black screen.
Are you using the new-legacy drivers?  Out of curriosity, are you using the GeForce 6600GT card, or something a little different?  I have asked around for a list of cards supported by the various packages, but haven't found a comprehensive list that would definitively identify which driver package is right for each card.

---

### Post by process91 on 2008-05-23
I am using the NVidia GeForce 6600GT. I tried out each driver and I have gotten the same result. I first installed the newest driver using the Restricted Driver Manager, then I uninstalled that completely and installed the "new legacy" driver with EnvyNG, and then I uninstalled that completely and installed the "legacy" driver. All resulted in a frozen black screen.

As another note, I actually reformatted this computer because of this issue. I was using Gutsy (7.10) and upon restart (after an automatic update) I was getting this frozen black screen. I thought my xorg.conf had been corrupted or something had happened to cause the error, but everything was set up correctly.

I have installed both Hardy and Gutsy on the machine now with the same results, it is my opinion that this driver package is broken in the newest updates.

---

### Post by MatthewAPeters on 2008-05-23
> **process91 said:**
> I am using the NVidia GeForce 6600GT. I tried out each driver and I have gotten the same result. I first installed the newest driver using the Restricted Driver Manager, then I uninstalled that completely and installed the "new legacy" driver with EnvyNG, and then I uninstalled that completely and installed the "legacy" driver. All resulted in a frozen black screen.

As another note, I actually reformatted this computer because of this issue. I was using Gutsy (7.10) and upon restart (after an automatic update) I was getting this frozen black screen. I thought my xorg.conf had been corrupted or something had happened to cause the error, but everything was set up correctly.

I have installed both Hardy and Gutsy on the machine now with the same results, it is my opinion that this driver package is broken in the newest updates.
Have you looked at or updated any of the related cases that I cross-link to in my how-to?


Bug #220374 in linux-restricted-modules-2.6.24 

or

nvidia 6600 not supported - [https://bugs.launchpad.net/bugs/219101](https://bugs.launchpad.net/bugs/219101)

The bug # 219101 was just promoted from Medium to High importance.  If you have not contributed your experiences there, please do - you may help the search for the solution or benefit from the case's findings.

I wish that my how-to had spawned from personal knowledge of how gdm and nvidia work, and not from finally hacking it to work - perhaps you can appeal directly to  some of the folks who work alot with the driver packages - I received help from them in putting together my how-to, I think it is very supportive community.

Wish I had more

Good luck - and please update this thread with your findings!

Matt

---

### Post by zeezam on 2008-09-10
I'm running twinview on two Dell 2007FP screens with 1600x1200 in resolution.
Drivers and everything seems to work fine but I have huge lag on my screensaver and when I browse in firefox.

Any common problems?

---

### Post by MatthewAPeters on 2008-09-11
> **zeezam said:**
> I'm running twinview on two Dell 2007FP screens with 1600x1200 in resolution.
Drivers and everything seems to work fine but I have huge lag on my screensaver and when I browse in firefox.

Any common problems?

Not here.  Lags could be from several causes, though.  Not enough RAM could result in swapping.  Too many processes consuming the RAM you do have can do the same.  Is there a reason you believe this lag is tied to the video driver or hardware?

---

### Post by zeezam on 2008-09-11
> **MatthewAPeters said:**
> Not here.  Lags could be from several causes, though.  Not enough RAM could result in swapping.  Too many processes consuming the RAM you do have can do the same.  Is there a reason you believe this lag is tied to the video driver or hardware?

Okey, I guess no because I have a AMD Athlon G4 CPU and 4GB RAM.
If I run glxgears in preview it's very smothly but when I open it in fullscreen huge lag appears.

Here is my xorg.conf
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
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
    Option         "XkbLayout" "se"
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
    ModelName      "DELL 2007FP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 2007FP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
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
    BoardName      "GeForce 6600"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"

	# Removed Option "TwinView" "1"
	# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1600+0"
	# Removed Option "TwinView" "0"
	# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
	# Removed Option "TwinViewXineramaInfoOrder" "CRT-0"
	# Removed Option "TwinViewXineramaInfoOrder" "DFP-0"
	# Removed Option "metamodes" "CRT: nvidia-auto-select +1600+0, DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1600+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by hooby3dfx on 2008-09-28
I just installed Hardy on my desktop with an AGP 6600GT.

This thread seemed to be pretty relevant to my issue, which is that no matter what I do I can't set my resolution to anything above 1024x768!!
I followed the instructions on this page and had no success.  I can't believe this is causing me trouble!

My xorg.conf is a mess at this point, but I think it should give me the option to set my display to 1280x1024.  I'm using a Samsung SyncMaster 710N LCD display.  
Using either the "Screen Resolution" menu or displayconfig-gtk, I am sometimes able to "set my monitor" to 1280x1024, but it just makes a panning setup within 1024x768.  Setting the res in nvidia-settings is the only thing that will work, but 1280x1024 never appears in the menu.  
Any suggestions?
Heres my xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Jan 22 19:53:46 PST 2008


Section "ServerLayout"
	Identifier	"Layout0"
  screen 0 "Screen0" 0 0
	Inputdevice	"Keyboard0"	"CoreKeyboard"
	Inputdevice	"Mouse0"	"CorePointer"
EndSection

Section "Files"
	Rgbpath		"/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
	Load		"extmod"
	Load		"type1"
	Load		"freetype"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	
	# generated from default
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"Protocol"	"auto"
	Option		"Device"	"/dev/psaux"
	Option		"Emulate3Buttons"	"no"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	
	# generated from default
	Identifier	"Keyboard0"
	Driver		"kbd"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 710N/177N/CX711N/CX701N"
	Horizsync	30-81
	Vertrefresh	56-85
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Device"
	Identifier	"Device0"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Device0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"UseEdidFreqs"	"false"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1024x768@60"	"1152x864@75"	"1024x768@70"	"1280x1024@75"	"1024x768@75"	"1280x960@60"	"1024x768@85"	"1280x1024@60"	"832x624@75"	"1280x960@75"	"800x600@60"	"1400x1050@60"	"800x600@85"	"1600x1200@65"	"800x600@75"	"1600x1200@60"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "ServerFlags"
EndSection
```
Also, the refresh rate always appears wrong, like 50,51,53khz.
Thanks.

Oh, and my login screen is way too high a resolution, and panned inside a 1024x768 display which doesn't pan (fixed at the top left). 
Also, I started getting the nvidia splash at startup which didn't happen before.

EDIT
Oh, and its plugged in via VGA.  
I'm wondering if I should do something with xrandr...?

FINAL EDIT:
This ended up actually being a problem with the EDID of my monitor!!!  It was putting out corrupted data.
For people with a similar problem, I recommend using the CustomEDID option in your xorg.conf, and point to a file with a backup of your monitors legit edid.

---

