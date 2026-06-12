---
title: "How To: Configure ATI Radeon HD 4650"
date: 2010-04-01
forum: Multimedia Software
---

### Post by mole84 on 2010-04-01
I recently decided to upgrade my old desktop instead of buying a new one. I figured I would go ahead and max out the specs on the motherboard while I was at it. I had a standard AGP slot and the best graphics card I could find for AGP was the Radeon HD 4650 (AGP 1GB GDDR2). So I ordered the parts and went on my merry way.

I installed the card and did a fresh install of 9.10, hoping to max perform my "new" system. The card was acting kinda fishy on the live boot and I had to reboot a few times before it magically worked. I got installed etc and when I booted it worked, but it turned out performance was painful. When using Firefox the delay when scrolling down the screen was literally unbearable. No problem right, I used the restricted drivers app to go ahead and install the ATI drivers hoping that it would auto-magically fix things.

System booted but once I logged in the screen would just fill with freezing and garbage so it was impossible to get anything done. 

I did some research and basically it seems as though there are three main options for drivers with X and ati cards in ubuntu.

[LIST=1]
[*]radeon: the default driver that was running originally
[*]radeonhd: another open source driver 
[*]fglrx: the proprietary ATI driver
[/LIST]

I experimented with all three options but this is what ended up being my solution. 

Download your ATI driver using this site: [AMD Graphics Drivers & Software]("http://support.amd.com/us/gpudownload/Pages/index.aspx") 
Just select Linux in the OS Select column.

You should end up with something like this, ```
ati-driver-installer-10-3-x86.x86_64.run
``` downloaded to your computer.

Now we need to shut down X and run some terminal commands. Open up a terminal from Applications > Accessories > Terminal

[COLOR="Red"]If you are following along here you need to print the tutorial because this will kill your screen to the terminal[/COLOR]

This will shut down X so we can modify X's settings.
```
sudo stop gdm
``` 
Browse to the downloaded file. ie
```
cd /home/user/Downloads/
```
Make the file executable
```
chmod +x ati-driver-installer-10-3-x86.x86_64.run
```
Launch the file
```
sudo ./ati-driver-installer-10-3-x86.x86_64.run
```
Now just follow through the installer. Once the installer is finished we need to setup the driver.
```
aticonfig --initial
```
This should set up a new xorg.conf file in your /etc/X11/ folder. Browser to the X11 folder.
```
cd /etc/X11
```
Now is the critical part, we need to modify some of the directives in the xorg.conf file to make things work better. We will use a terminal text editor which can be kinda tricky, but find a tutorial on vi or nano if you need help.
```
sudo vi xorg.conf
```
Browse down to where it says ```
Section "Device"
``` and find the line for Option "DRI" and make it read ```
Option "DRI" "true"
```
Then scroll down to the bottom of the file and we will add a new section that reads like this
```

Section "Extensions"
	Option "Composite" "Disable"
	Option "OpenGLOverlay" "1"
EndSection
```
Now save and close the file. Make sure your changes saved by double checking the file```
vi xorg.conf
``` re-close the file and now we are ready to go.
```
sudo start gdm
```
Hopefully everything will come up just fine, if it locks up, try a reboot.
Here is my final xorg.conf file.
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
	Load  "record"
	Load  "dri"
	Load  "extmod"
	Load  "dbe"
	Load  "dri2"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "SPT"
	ModelName    "X7S-NAGA II"
	HorizSync    24.0 - 80.0
	VertRefresh  50.0 - 75.0
	Option	    "DPMS"
	#DisplaySize	  340   270	# mm
EndSection

Section "Device"

	### Available Driver options are:-
	### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
	### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
	### [arg]: arg optional
	#Option     "NoAccel"            	# [<bool>]
	#Option     "SWcursor"           	# [<bool>]
	#Option     "Dac6Bit"            	# [<bool>]
	#Option     "Dac8Bit"            	# [<bool>]
	#Option     "BusType"            	# [<str>]
	#Option     "CPPIOMode"          	# [<bool>]
	#Option     "CPusecTimeout"      	# <i>
	#Option     "AGPMode"            	# <i>
	#Option     "AGPFastWrite"       	# [<bool>]
	#Option     "AGPSize"            	# <i>
	#Option     "GARTSize"           	# <i>
	#Option     "RingSize"           	# <i>
	#Option     "BufferSize"         	# <i>
	#Option     "EnableDepthMoves"   	# [<bool>]
	#Option     "EnablePageFlip"     	# [<bool>]
	#Option     "NoBackBuffer"       	# [<bool>]
	#Option     "DMAForXv"           	# [<bool>]
	#Option     "FBTexPercent"       	# <i>
	#Option     "DepthBits"          	# <i>
	#Option     "PCIAPERSize"        	# <i>
	#Option     "AccelDFS"           	# [<bool>]
	#Option     "IgnoreEDID"         	# [<bool>]
	#Option     "DisplayPriority"    	# [<str>]
	#Option     "PanelSize"          	# [<str>]
	#Option     "ForceMinDotClock"   	# <freq>
	#Option     "ColorTiling"        	# [<bool>]
	#Option     "VideoKey"           	# <i>
	#Option     "RageTheatreCrystal" 	# <i>
	#Option     "RageTheatreTunerPort" 	# <i>
	#Option     "RageTheatreCompositePort" 	# <i>
	#Option     "RageTheatreSVideoPort" 	# <i>
	#Option     "TunerType"          	# <i>
	#Option     "RageTheatreMicrocPath" 	# <str>
	#Option     "RageTheatreMicrocType" 	# <str>
	#Option     "ScalerWidth"        	# <i>
	#Option     "RenderAccel"        	# [<bool>]
	#Option     "SubPixelOrder"      	# [<str>]
	#Option     "ShowCache"          	# [<bool>]
	#Option     "ClockGating"        	# [<bool>]
	#Option     "VGAAccess"          	# [<bool>]
	#Option     "ReverseDDC"         	# [<bool>]
	#Option     "LVDSProbePLL"       	# [<bool>]
	#Option     "AccelMethod"        	# <str>
	#Option     "ConnectorTable"     	# <str>
	#Option     "DefaultConnectorTable" 	# [<bool>]
	#Option     "DefaultTMDSPLL"     	# [<bool>]
	#Option     "TVDACLoadDetect"    	# [<bool>]
	#Option     "ForceTVOut"         	# [<bool>]
	#Option     "TVStandard"         	# <str>
	#Option     "IgnoreLidStatus"    	# [<bool>]
	#Option     "DefaultTVDACAdj"    	# [<bool>]
	#Option     "Int10"              	# [<bool>]
	#Option     "EXAVSync"           	# [<bool>]
	#Option     "ATOMTVOut"          	# [<bool>]
	#Option     "R4xxATOM"           	# [<bool>]
	#Option     "ForceLowPowerMode"  	# [<bool>]
	#Option     "DynamicPM"          	# [<bool>]
	Identifier  "Card0"
	Driver      "fglrx"
	VendorName  "ATI Technologies Inc"
	BoardName   "HD 4650"
	Option	    "DRI" "true"        	# [<bool>]
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth     24
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

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option "Composite" "Disable"
	Option "OpenGLOverlay" "1"
EndSection
```

---

### Post by dlh1 on 2010-04-23
Works for me, thanks.

---

### Post by dawhistler on 2010-04-24
What kind of resolution are you capable of getting?
I could only make to something like 1300X700

---

### Post by LanceSandino on 2010-05-25
Hi.

Someone posted your post in my thread here ->
[http://ubuntuforums.org/showthread.php?p=9359750#post9359750](http://ubuntuforums.org/showthread.php?p=9359750#post9359750)

and I thought i'd give it a try.

It did not work at all :S

Do you recommend doing anything else?

---

### Post by mole84 on 2010-09-01
Since 10.04 a fresh install of ubuntu will allow you HD4650 to work just find. I found that sometimes my card would still lag up after a few days of being up. 

I found the solution for this is to enable the 

```
Option "AGPMode" "1"
```

In your xorg.conf file. You will also notice that in 10.04 there is no xorg.conf file by default because the new X prefers not to have one. To force X to generate a xorg.conf file drop to a root shell and use
```
sudo stop gdm
```
```
Xorg -configure
```

This will create a new xorg.conf file in your home directory, so copy that to /etc/X11/xorg.conf to make it the actual xorg.conf.

```
sudo cp xorg.conf.new /etc/X11/xorg.conf
``` 
Then open that file with a 

```
gksudo gedit /etc/X11/xorg.conf
``` 
and scroll down until you find the AGPMode option, enable it by removing the # and adding "1" at the end.

---

### Post by SeePU on 2010-09-01
I find that peculiar and somewhat annoying...

I mean the part about a video driver problem that requires you to create an xorg file.  Why aren't these devs working together in this situation?  If they are going to change to a new system (HAL/XORG etc.?), why not work with the video card brand manufacturers or something?  

They are designing the system to not use an xorg.conf file but because the drivers are inefficient and buggy, we have to create an xorg config file to deal with it?!?  I sure hope that this situation can be fixed soon.  Then one has to deal with what should be part of the xorg config file since the detection of the card/drivers is not good enough or that the issues/bugs persist even though the detection is working?  

I am wondering if the problem exists with Nvidia cards, too, though.

---

### Post by diegofrafer on 2011-01-06
In the ATI webpage if I search a driver for hd4650 agp don't appear option for linux. 

Are the same drivers the 10.3 version PCI-E and the AGP?

I have a ati hd4650 agp and ubuntu 10.04 and I have a problem with the drivers download. With the xorg radeon drivers the image is cropped in HDMI.

Anyone with proprietary drivers installed for ati hd4650 apg?

Thanks.

---

### Post by TG12 on 2011-01-11
I think I followed some guides here before but I solved it, I posted a guide here for those who are having problems.
[http://ubuntuforums.org/showthread.php?t=1664919](http://ubuntuforums.org/showthread.php?t=1664919)

---

### Post by Browser_ice on 2011-06-11
I have followed the instructions in this link to configure my xorg.conf with my Saphyr HD4650 1gb AGP card and the result is that my graphic is lagging (flash, scrolling in Firefox, moving windows around, ...). Can someone help me to configure it ?

> lspci | grep AGP
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
01:00.0 VGA compatible controller: ATI Technologies Inc RV730 Pro AGP [Radeon HD 4600 Series]

> dmesg|grep drm
[    0.000000] Linux version 2.6.32-32-generic (buildd@roseapple) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 (Ubuntu 2.6.32-32.62-generic 2.6.32.38+drm33.16)


> glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15

> dpkg -l | grep glx
ii  libgl1-mesa-glx     7.7.1-1ubuntu3       A free implementation of the OpenGL API -- G
ii  libglitz-glx1       0.5.6-1build1        Glitz OpenGL library GLX backend

dpkg -l | grep fglrx
ii  fglrx               2:8.723.1-0ubuntu5   Video driver for the ATI graphics accelerato
ii  fglrx-amdcccle      2:8.723.1-0ubuntu5   Catalyst Control Center for the ATI graphics
ii  fglrx-modaliases    2:8.723.1-0ubuntu5   Identifiers supported by the ATI graphics dr


[PHP]Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen         "Screen0" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "record"
	Load  "dri"
	Load  "extmod"
	Load  "dbe"
	Load  "dri2"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Compaq"
	ModelName    "Compaq S700 Color Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
	ModeLine     "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
	ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine     "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	#Option	    "DPMS"
EndSection

Section "Device"

	### Available Driver options are:-
	### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
	### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
	### [arg]: arg optional
	#Option     "NoAccel"            	# [<bool>]
	#Option     "SWcursor"           	# [<bool>]
	#Option     "Dac6Bit"            	# [<bool>]
	#Option     "Dac8Bit"            	# [<bool>]
	#Option     "BusType"            	# [<str>]
	#Option     "CPPIOMode"          	# [<bool>]
	#Option     "CPusecTimeout"      	# <i>
	#Option     "AGPMode"            	# <i>
	#Option     "AGPFastWrite"       	# [<bool>]
	#Option     "AGPSize"            	# <i>
	#Option     "GARTSize"           	# <i>
	#Option     "RingSize"           	# <i>
	#Option     "BufferSize"         	# <i>
	#Option     "EnableDepthMoves"   	# [<bool>]
	#Option     "EnablePageFlip"     	# [<bool>]
	#Option     "NoBackBuffer"       	# [<bool>]
	#Option     "DMAForXv"           	# [<bool>]
	#Option     "FBTexPercent"       	# <i>
	#Option     "DepthBits"          	# <i>
	#Option     "PCIAPERSize"        	# <i>
	#Option     "AccelDFS"           	# [<bool>]
	#Option     "IgnoreEDID"         	# [<bool>]
	#Option     "DisplayPriority"    	# [<str>]
	#Option     "PanelSize"          	# [<str>]
	#Option     "ForceMinDotClock"   	# <freq>
	#Option     "ColorTiling"        	# [<bool>]
	#Option     "VideoKey"           	# <i>
	#Option     "RageTheatreCrystal" 	# <i>
	#Option     "RageTheatreTunerPort" 	# <i>
	#Option     "RageTheatreCompositePort" 	# <i>
	#Option     "RageTheatreSVideoPort" 	# <i>
	#Option     "TunerType"          	# <i>
	#Option     "RageTheatreMicrocPath" 	# <str>
	#Option     "RageTheatreMicrocType" 	# <str>
	#Option     "ScalerWidth"        	# <i>
	#Option     "RenderAccel"        	# [<bool>]
	#Option     "SubPixelOrder"      	# [<str>]
	#Option     "ShowCache"          	# [<bool>]
	#Option     "ClockGating"        	# [<bool>]
	#Option     "VGAAccess"          	# [<bool>]
	#Option     "ReverseDDC"         	# [<bool>]
	#Option     "LVDSProbePLL"       	# [<bool>]
	#Option     "AccelMethod"        	# <str>
	#Option     "ConnectorTable"     	# <str>
	#Option     "DefaultConnectorTable" 	# [<bool>]
	#Option     "DefaultTMDSPLL"     	# [<bool>]
	#Option     "TVDACLoadDetect"    	# [<bool>]
	#Option     "ForceTVOut"         	# [<bool>]
	#Option     "TVStandard"         	# <str>
	#Option     "IgnoreLidStatus"    	# [<bool>]
	#Option     "DefaultTVDACAdj"    	# [<bool>]
	#Option     "Int10"              	# [<bool>]
	#Option     "EXAVSync"           	# [<bool>]
	#Option     "ATOMTVOut"          	# [<bool>]
	#Option     "R4xxATOM"           	# [<bool>]
	#Option     "ForceLowPowerMode"  	# [<bool>]
	#Option     "DynamicPM"          	# [<bool>]
	Identifier  "Card0"
	Driver      "fglrx"
	VendorName  "ATI Technologies Inc"
	BoardName   "HD 4650"
	#Option	    "NoAccel" "true"           	# [<bool>]
	Option	    "DRI" "true"        	# [<bool>]
	#Option	    "AGPMode" "8"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Virtual   1400 1050
		Depth     24
		Modes    "1280x1024@60" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "800x600@60" "800x600@85" "800x600@75" "640x480@85" "640x480@75" "640x480@60"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
	Option	    "OpenGLOverlay" "1"
EndSection
[/PHP]

---

### Post by biker3 on 2011-09-28
Do you have now problems with IRQ like [this bug in Debian]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=628080") with the same card?:(

---

### Post by jamie.nicholson on 2012-05-15
Upgrading Lucid to the latest xorg seems to have introduced all manner of trouble with this card (slow cutting/flicker and lines) - had these for about 6 months there. Is anyone else using a updated Lucid system with the latest Xorg and this card with no troubles?

I've tried numerous times to reconfigure and followed the guides but no luck yet my next option will be to downgrade xorg and try again. Also tried Maverick and Unity but no luck too.

The interesting part is that there were a lot of annoying whack vertical and horizontal lines being introduced. Running it in low graphics mode for a couple of days seems to have fixed the issue which is rather amusing and I found out the open source drivers drive the card real hard which is perhaps why the lines appeared.

---

