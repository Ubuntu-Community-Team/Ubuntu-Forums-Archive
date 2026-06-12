---
title: "[SOLVED] Cannot get Nvidia drivers to work."
date: 2008-08-28
forum: Multimedia Software
---

### Post by davethewave83 on 2008-08-28
Hello!
I have an Nvidia Geforce 4 MX 420, I installed the nvidia-glx-legacy then tried nvidia-settings, when I get into nvidia-settings it says it does not appear that I am using the Nvidia X drivers and to type nvidia-xconfig.. so I do, but it says command not found so I sudo apt-get install nvidia-xconfig and it says it's going to remove my nvidia-glx-legacy drivers but I do not want it to because then what will it configure? 

I have been trying for days to get the nvidia drivers working, if anyone can help me out it'd be much appreciated. I've been to other forums and guides and either nothing happens, or the screen goes blank and I have to dpkg-reconfigure xserver-xorg just to get video back again. 

Thanks!

---

### Post by davethewave83 on 2008-08-28
OK I got them to work by using Envy,however, now my screen is slightly offset to the left about an inch, to the right of that is an inch of blackness, and my screen resolutions cannot go beyond 800x600 whereas I used to be running 1024x768. Can anyone help with fixing the resolution? I imagine it has something to do with my xorg.conf (my xorg.conf lists 1024x768 as a possible screen resolution under the screen area) 

I tried manually setting it in nvidia-settings by manually settig "panning" to 1024x768 but that did not work. Any ideas? 

Thanks!:)

---

### Post by djRobbieF on 2008-08-28
Edit:  I just re-read your question and realized I misunderstood.  Sorry  ;)

---

### Post by overdrank on 2008-08-28
> **davethewave83 said:**
> OK I got them to work by using Envy,however, now my screen is slightly offset to the left about an inch, to the right of that is an inch of blackness, and my screen resolutions cannot go beyond 800x600 whereas I used to be running 1024x768. Can anyone help with fixing the resolution? I imagine it has something to do with my xorg.conf (my xorg.conf lists 1024x768 as a possible screen resolution under the screen area) 

I tried manually setting it in nvidia-settings by manually settig "panning" to 1024x768 but that did not work. Any ideas? 

Thanks!:)

Hi and you may try what PmDematagoda suggest here
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)
```
Do this:-
1) Open a modules file for editing with:-
Code:

sudo nano /etc/default/linux-restricted-modules-common

2) Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"

and save the file.

Then reboot the PC and see if the Nvidia driver now works.
```
And then use the nvidia-settings but I do not believe you will need to use panning.

---

### Post by Giannis68 on 2008-08-28
**Download** - [NVIDIA-Linux-x86-96.43.07-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/96.43.07/NVIDIA-Linux-x86-96.43.07-pkg1.run")
[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.07/NVIDIA-Linux-x86-96.43.07-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.07/NVIDIA-Linux-x86-96.43.07-pkg1.run)

before you start remove an nvidia driver with Synaptic package manager
open terminal
cd /etc/init.d
delete any nvidia file (script)
reboot your pc
press Alt+Ctrl+F1
sudo gdm stop
and install new nvidia drivers
edit xorg.conf from /etc/X11
Section "Device"
    Identifier    "nVidia Corporation"
    Driver        "[COLOR=Red]nvidia[/COLOR]"
save and reboot

---

### Post by davethewave83 on 2008-08-29
Hmm well I'll give those suggestions a try but just to let you know of a strange phenomenon:

When I enable display 2 the driver works fine on that display, the problem is that the login screen is off display 2 and on display 1 which will not operate as my LCD, but if I set display 2 as display 1 it still acts the same way... 

it seems for some reason the reason the screen is blank is because it's trying to run on an invalid screen perhaps, not sure what to make of this :confused: I am tired, I will give the other ideas a go

---

### Post by davethewave83 on 2008-08-29
The problem with the screen being blank is that the xorg.conf requires ```
Option		"UseDisplayDevice"  "DFP"
``` in the screen area but still no good
my xorg.conf contains this for my video:

```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Toshiba"
	Modelname	"Toshiba DP782M, Equium 17-inch Monitor"
	Horizsync	30.0-82.0
	Vertrefresh	50.0-160.0
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
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	Option		"UseDisplayDevice"  "DFP"
	SubSection "Display"
		Depth	24
		Modes		"1280x960@75"	"1400x1050@60"	"1280x1024@60"	"1400x1050@75"	"1280x960@60"	"1600x1200@65"	"1280x1024@75"	"1600x1200@60"	"1152x864@75"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
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
```

but I have no options to set the screen to 1024x768, it is stuck on 800x600 running the Nvidia drivers, I really wish there were an "over ride" feature, and the screen has an inch of blackness to the right :( anyone ever get this to work? Seems like these settings should all check out to me, not sure what could be limiting the resolution

---

### Post by davethewave83 on 2008-08-29
It appears this problem is fairly popular [http://www.ubuntux.org/ubuntu-8-04-screen-resolution-limited-with-nvidia-geforce2-mx-400](http://www.ubuntux.org/ubuntu-8-04-screen-resolution-limited-with-nvidia-geforce2-mx-400) 

without the drivers I can get 1024x768 but with the drivers I get a max of 800x600, or a "virtual" setting of 1024x768 but in "virtual" mode the screen scrolls and it's ugly. 

How can I get a genuine 1024x768? *goes insane from doing this forever*

I am guessing that it has something to do with my monitor choice in displayconfig-gtk, but I've picked quite a few of them and always they end up with problematic resolutions. How can one determine which setting is the correct one to obtain 1024x768?

---

### Post by Giannis68 on 2008-08-30
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

if you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:
[INDENT][FONT=Courier New]* development tools like *make* and *gcc* are installed
* the *linux-headers* package matching the installed Linux kernel is installed
* the *pkg-config* and *xserver-xorg-dev* packages are installed
* [COLOR=Red]the *nvidia-glx* package has been uninstalled with the *--purge* option and the files [/COLOR][FONT=Courier New][COLOR=Red]/etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel[/COLOR][/FONT][COLOR=Red] do not exist[/COLOR][/FONT][/INDENT]If you use Ubuntu, please also ensure that the *linux-restricted-modules* or *linux-restricted-modules-common* packages have been uninstalled. Alternatively, you can edit the [FONT=Courier New]/etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common[/FONT] configuration file and disable the NVIDIA *linux-restricted* kernel modules (*nvidia*, *nvidia_legacy*) via:
[INDENT][FONT=Courier New]DISABLED_MODULES="nv nvidia_new"[/FONT][/INDENT]Additionally,** delete** the following file if it exists:[INDENT][B][FONT=Courier New][COLOR=Black]/lib/linux-restricted-modules/.nvidia_new_installed
[/COLOR][/FONT][FONT=Courier New][COLOR=Black][FONT=Courier New]/etc/init.d/nvidia-glx[/FONT][/COLOR][/FONT][COLOR=Black]
[/COLOR][FONT=Courier New][COLOR=Black][FONT=Courier New]/etc/init.d/nvidia-kernel[/FONT][/COLOR][/FONT][/B]
[FONT=Courier New]
before delete this files i was the same problem only 800x600



[/FONT][/INDENT]

---

### Post by davethewave83 on 2008-08-30
Thanks for the reply, I uninstalled everything relating to Nvidia drivers as well as what you have put there for the removal of the restricted drivers. As soon as I removed the restricted drivers it then disabled my internet as I require a restricted driver to run my wireless. I re-installed the restricted drivers after connecting via ethernet and made sure the nvidia driver was disabled. Then I did an invoke-rc.d gdm stop, sh NVIDIA-Linux-x86-96.43.07-pkg1.run which gave me a warning on some nvidia.ko file that could not be found, but eventually said it installed successfully.

After restart X failed to load the driver and asked me to reconfigure, so I reconfigured for a toshiba 15" monitor using nvidia drivers, said ok. The gdm came up in low graphics mode so I reboot, and it asked me to reconfigure again *loop* 

so now I am stuck with several choices,

I can re-install Ubuntu to fix my driver problem as I have no idea how to fix this manually, then run the nvidia driver in 800x600 and "get used" to it.

I can run without any drivers and get 1024x768 but be limited in programs that I can run.

I can re-install WindowsXP and have everything I require under the expense of losing all my current data and having to run window$ :(

I believe one should be able to sh NVIDIA-Linux-x86-96.43.07-pkg1.run reboot and have it "just work" or have an override to force 1024x768, I do not understand this issue with 800x600, why does it choose that resolution?

---

### Post by Giannis68 on 2008-08-31
[http://ubuntuforums.org/showthread.php?t=862203](http://ubuntuforums.org/showthread.php?t=862203)
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by davethewave83 on 2008-08-31
> **Giannis68 said:**
> [http://ubuntuforums.org/showthread.php?t=862203](http://ubuntuforums.org/showthread.php?t=862203)
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

Thank you for the reply, the first one is what I have been doing and is not working.. the problem is not that I do not know how to install the drivers, but it is that once installed correctly they only allow a max resolution of 800x600 and I would like 1024x768. I do not know what the second one is for, there is no information on it there that I can find and I am unable to post the problem there as they require a non-free email account to sign up which I do not possess :(

Edit*
It may be that I have a defective EDID, and I need to set the resolutions manually adding an option to disable EDID in the xorg file, I will experiment with this option.

---

### Post by davethewave83 on 2008-08-31
After disabling EDID in the xorg.conf, I now have a split screen with 60% of the screen on top, 40% on the bottom, and the image "wraps" it also has a large black area to the right. I assume this means my monitor resolutions are not set correctly in the xorg, but I do not know what to set them to that would work.

---

### Post by davethewave83 on 2008-09-01
It would appear no one has ever had this problem and that no one is able to help me solve it here, or on any other forums as well so I am probably going to be forced to return to XP for the time being :(

If anyone uses a laptop with an nvidia video card and have not had any problems please let me know the brand and model.. I would like to look into a new laptop as I believe it is a problem with the mx 420 more than it is a problem with ubuntu. 

Thanks.

---

### Post by davethewave83 on 2008-09-01
nevermind solution solved by reading [http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391) 

it required a hex hack.:guitar:

---

