---
title: "Uninstall ATI Proprietary fglrx and install Open fglrx"
date: 2008-05-06
forum: Multimedia Software
---

### Post by PoopyTheJ on 2008-05-06
How do I uninstall the proprietary ATI drivers and install the open source fglrx drivers instead? I'm wondering this because when I attempt to switch users my system locks up and this is supposedly a known bug with ATI's drivers. it would be really nice to have my programs like deluge continue to run while my wife uses the PC. Like really nice, that is pretty much the only thing stopping me from switching totally to ubuntu, as I can do this with windows just fine. So if there's a workaround for the user switching thing other than switching to the Open source fglrx drivers let me know, otherwise I'd just like to try the Open source fglrx drivers.
I used Envy to install the ATI drivers, I'm running an ATI 3850HD, and am a real noob at ubuntu. Any advise, suggestions, rude remarks?

---

### Post by amohanty on 2008-05-06
umm... fglrx are the propietery ones and the ati driver-set are the oss ones. Which ones are you using??

AM

---

### Post by jocko on 2008-05-06
There is no "open fglrx" driver. fglrx is the name of ATI's proprietary driver.
I don't think there are any open drivers that support 3d acceleration using that card, but the [radeonhd]("http://www.phoronix.com/scan.php?page=article&item=843&num=1") driver may support 2d acceleration.

---

### Post by PoopyTheJ on 2008-05-06
Ahhh, ok thanks for the clarification. I am using the restricted fglrx driver. So is the xf86-video-radeonhd driver talked about on that link the same as the xserver-xorg-video-radeonhd driver in synaptic? In either case how do I go about uninstalling my current driver and installing the new driver? Is there anything special I would need to do? I'm running Compiz, and Gutsy Gibbon. Would I just uninstall using envy and then choose that driver from synaptic? Or uninstall and download and compile the radeonHD driver from source if it's different? Thanks for the help, my ignorance was hanging out for public display there. :lolflag:

---

### Post by jocko on 2008-05-06
Try the one in the repo first. Uninstall fglrx and install the radeonhd driver using synaptic.
 I have never tried the radeonhd driver, so I don't know what more steps are required to get it working.
At least you will need to reconfigure xorg by running this in a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
And then reboot.

If you're lucky it will work after that as xorg should be able to detect the driver and configure itself properly, but to be sure I advice you to try searching the forums to see if there are any better instructions.
If you're unlucky you may end up not being able to start up xorg, so do some research before you try anything.

---

### Post by PoopyTheJ on 2008-05-07
So uninstall fglrx, install the radeonhd driver from synaptic and the reconfigure xorg, then reboot? No reboot steps in between there right? And I'll go searching around the forums as well.

---

### Post by PoopyTheJ on 2008-05-09
ok so I tried to install the RadeonHD driver following the directions from here [http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1) and like every other driver I've tried I get no love. When I use envy to install my video drivers  ONLY the 8.3 version works! it recognizes my monitor will support up to 2048x1600, and I have 3d acceleration 24bit color all the whistles. When I try any other driver through envy, or any driver not through envy, when I boot up I get an error that Ubuntu is running in low resolution mode, I cannot choose anything higher than 800x600 in resolutions and when I manually try to choose a different monitor all I get for output is garbage. When I try to play Scorched3d I get this error
The Scorched3d process terminated due to configuration errors.
Display : ERROR: Failed to set video mode.
Error Message: Couldn't find matching GLX visual
----------------------------
Requested Display Mode:-
Driver=x11
Resolution=640x480x0 (windowed)
DepthBuffer=24
DoubleBuffer=On
ColorComponentSize=0

So not knowing anything about Linux or Ubuntu it looks like X is falling back to the failsafe xorg.conf file and ignorinig my nicely setup xorg.conf. I'm attaching my xorg.conf file for reference as well. Any help would be immensly appreciated!

Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"radeonhd"
	Busid		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Option 		"TexturedVideo" "off"
EndSection

Section "Monitor"
	Identifier	"G225f"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"G225f"
	Defaultdepth	24
	SubSection "Display"
		Modes		"2048x1536"	"1920x1440"	"1792x1344"	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

Section "Extensions"
Option "Composite" "Off"
EndSection

Section "ServerFlags"
Option "AIGLX" "Off"
EndSection

---

### Post by jocko on 2008-05-09
> **PoopyTheJ said:**
> When I try to play Scorched3d I get this error

Do you get that error even with fglrx working?
As I said in my first post, radeonhd will not give 3d acceleration. If you want to be able to play games you need 3d, so you need to use fglrx.
If you use Hardy, stay with the one that works (catalyst 8.3) which is also the same as the one in the repos.
If you still use gutsy, you could try the version in the repos instead of using envy.

---

### Post by rannsaicher on 2008-05-09
Have a look at this for starters
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a)
Note that a fresh install of ubuntu will use the ati driver ( package xserver-xorg-video-ati  in synaptic package manager.) this is the default setup.
The proprietary ATI driver fglrx is available in the repository.(package xorg-driver-fglrx, and also needs the kernel module which is in the package linux-restricted-modules-generic to be loaded)
Later versions than have been packaged are available from the ati drivers site. There is now an installer file to download and run, which will create the kernel, driver and control packages for you to install.
 Note "restricted" refers to the fact that these packages contain "non open source" or restricted code. 
there is no need to deinstall the ati driver when moving to the fglrx driver.

A key change when moving to fglrx from the "ate" driver is to find the device section in /etc/X11/xorg.conf with driver "ati" and change this to driver "fglrx". Backing out is easy, just deinstall the fglrx packages, change fglrx back to ati in the xorg.conf file and reboot.

Note I was running Gutsy with the ATI 8.443 fglrx driver on 9600Xt card( from ati site) . On upgrade to Hardy I have been unable to get any fglrx driver ( package version or ati site sourced version to work. I have had to fall back to using the ati driver. It appears the hardy has introduced major issues for ATI card users.

---

### Post by PoopyTheJ on 2008-05-10
I can do without 3d really, I just want compiz to work and I want user switching to work. The only driver I can get to work is the fglrx driver, but I don;t have user switching with it, machine just freezes at a black screen when I try. tbh thats about the only thing keeping me from using ubuntu exclusively, asI don;t game that much UT2k4 mostly, which works with Linux. So if I could get fglrx to work with user switching I'd be in heaven. ;) And I fixed that apparently I had to uninstall the radeonHD drivers to switch back to fglrx by running make uninstall in the radeonhd directory as it just would not play nice, I may try again at a later date, we'll see. And the Open ATI driver doesn't support my card afaik.

---

### Post by jocko on 2008-05-11
> **PoopyTheJ said:**
> [COLOR=Red]I can do without 3d really, I just want compiz to work[/COLOR] and I want user switching to work.

There's absolutely no way you can get compiz working without 3d acceleration.

---

### Post by PoopyTheJ on 2008-05-12
ahhh, ok, then I can probably even do without Compiz, user switching is much more important to me. I really and truly just want USer switching to work, I still have my windows install for games, so I can do without compiz for now, until the radeonhd drivers reach maturity

---

