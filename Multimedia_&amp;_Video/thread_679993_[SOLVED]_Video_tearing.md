---
title: "[SOLVED] Video tearing"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by Tails9 on 2008-01-27
Hi,

I've got the same problem as many people here, and therefore I read many topics regarding this issue, but they weren't able to solve it. My screen is tearing when playing back video.

I recently purchased a new monitor, a Samsung SyncMaster (o, the irony) 245b, with a refresh rate of 75Hz.

I've enabled vSync in compiz, and turned the refresh rate up to 200.
I also ran the xserver reconfiguring thing in a terminal.

My videocard is a Nvidia 7900GS, and It uses he nvidia driver.
I would like to try nvidia-settings, but when I run it, it says "You do not appear to be using the NVIDIA X driver." etc. This may be because I have nvidia-glx-new installed, which gets uninstalled when I reinstall nvidia-settings, and the other way around.

I've also tried this:[http://ubuntuforums.org/archive/index.php/t-76387.html](http://ubuntuforums.org/archive/index.php/t-76387.html), but it didn't help completely. After this procedure, it's able to use a 67Hz refresh, instead of 54.

Here's the concerning xorg.conf part:

```
Section "Device"
	Identifier	"nVidia Corporation G71 [GeForce 7900 GS]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster245b"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
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
```

Could anyone help me with this?

---

### Post by Tails9 on 2008-02-08
*Bump*

---

### Post by erginemr on 2008-02-08
Hello,

Can you please try this one, if you haven't already:

[http://ubuntuforums.org/showthread.php?t=624498&highlight=tearing](http://ubuntuforums.org/showthread.php?t=624498&highlight=tearing)

---

### Post by Tails9 on 2008-02-08
Haven't seen that one before, but it didn't help. Still tearing.
But thanks.

---

### Post by erginemr on 2008-02-09
I am also using an NVIDIA card (GeForce 4 MX) and a Samsung SyncMaster 763MB (CRT) monitor. In spite of the ominous message "You do not appear to be using the NVIDIA X driver.", if you can use Compiz, then you are using a binary NVIDIA driver. You can also check it with:
```
glxinfo | grep -i direct
```
which should report: "direct rendering: yes"
The applet "screens and graphics" in Ubuntu menu is buggy. It reports my refresh rate as ~50 MHz, whereas my actual refresh rate is 75 MHz.

I can also advise you to take a copy of your currect xorg.conf file and reconfigure it with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I have attached my xorg.conf file as an example...

---

### Post by ollebolle on 2008-02-10
Thank you so much erginemr!

I was googling around, and found this tread, and it solved my tearing problems! :cool:

Direct rendering was on, and this line solved my problem:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Thank you so much! :p  No more tearing!

---

### Post by Tails9 on 2008-02-10
> **erginemr said:**
> I am also using an NVIDIA card (GeForce 4 MX) and a Samsung SyncMaster 763MB (CRT) monitor. In spite of the ominous message "You do not appear to be using the NVIDIA X driver.", if you can use Compiz, then you are using a binary NVIDIA driver. You can also check it with:
```
glxinfo | grep -i direct
```
which should report: "direct rendering: yes"


I didn't expect it, but this is what mine says: "```
glxinfo | grep -i direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```
".

---

### Post by Tails9 on 2008-02-10
**Update**: I tried the 'sudo dpkg-reconfigure -phigh xserver-xorg' and restarted the X server.
My screen went black. I tried CTRL+ALT+F1, and I get thick lines of all colours of the rainbow, flickering.
Im now on XP restoring the xorg.conf backup.

I attached the xorg.conf that came out of the  'sudo dpkg-reconfigure -phigh xserver-xorg' command.

[edit] the attachmant manager thinks my xorg.conf text is invalid, so I'll post it in a codeblock.

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"alt-intl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G71 [GeForce 7900 GS]"
	Driver		"nv"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G71 [GeForce 7900 GS]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1200" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

---

### Post by Tails9 on 2008-02-12
*Shameless Bump* 

(is there a rule regarding bumping threads?)

---

### Post by erginemr on 2008-02-12
Don't worry! Bump as you like! :lolflag:

In the mean time, please try:
```
sudo dpkg-reconfigure xserver-xorg
```
which will ask you a couple of questions, as compared to the former command where everything was automatically configured. Try to stick to the default / suggested settings.

I will also be working on it...

For one, the "xorg.conf" file you have posted seems missing in parts to me. I have to go back home and check it.

What is more troubling is the fact that you do not happen to have NVidia binary driver installed. You need to purge-remove the "nvidia-glx-new" and "nvidia-settings" packages and reinstall "nvidia-glx-new" only. Did you mess with Envy or NVidia web site to install the driver from the "NVIDIA-*.run" installer package? If not, pray stay away from them and stick to the Synaptic repositories if possible, because they will cause compatibility issues with your kernel sooner or later. 

To put it in another way: What did you install and how did you install it?

More later...

---

### Post by erginemr on 2008-02-12
Nothing ground-breaking, but here is my xorg.conf file for a comparison:
```
# xorg.conf (xorg X Window System server configuration file)
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

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "tr"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV17 [GeForce4 MX 440]"
    Driver         "nvidia"
    # Option       "MetaModes" "1024x768"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV17 [GeForce4 MX 440]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Option         "XvmcUsesTextures" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_75" "800x600_75" "640x480_75"
    EndSubSection
EndSection
```
that had also been created by "dpkg-reconfigure". Obviosly, my previous assessment regarding a deficient config file was false, as your config file seems to have all essential parts included.

I have two more questions:

1- Regarding this remark of yours: *"I've enabled vSync in compiz, and turned the refresh rate up to 200."* Did you bring this setting, whatever it is, back to its default value?

2- What is the native resolution of your monitor? Or what resolution are you trying to achieve? 1920x1200 maybe, according to:
[http://www.trustedreviews.com/displays/review/2007/08/23/Samsung-SyncMaster-245B-24in-Monitor/p1]](http://www.trustedreviews.com/displays/review/2007/08/23/Samsung-SyncMaster-245B-24in-Monitor/p1])

---

### Post by Tails9 on 2008-02-12
I used Envy. I'll try what you suggested tomorrow.

Should it be possible to use nvidia-settings after that?

---

### Post by erginemr on 2008-02-12
I remember having used nvidia-settings without installing it explicitly. If my memory serves me correct, I think it comes with the binary driver package. It is not hard to find out; you can just try running nvidia-settings from Alf+F2.

And if you are happy with the current state of your desktop now, I'd say take a backup your xorg.conf file while you can and leave it here. You don't need to tinker anymore if everything works as it should.

---

### Post by Tails9 on 2008-02-13
> **erginemr said:**
> Obviosly, my previous assessment regarding a deficient config file was false, as your config file seems to have all essential parts included.


That might be, but the generated config I last posted crashed my system. (Or crashed X, I don;t know)

---

### Post by Tails9 on 2008-02-14
Well, I did what you suggested, purged everything, reinstalled nvidia-glx-new, ran the dpkg command, but it's still not working. Nvidia-settings still does not work and it's still isung indirect rendering. Strange.

---

### Post by erginemr on 2008-02-14
:( Sorry, I have no other tricks up in my sleeve, except maybe to boot an Ubuntu Live CD and try to copy its xorg.conf file from there. (But this is sugested in the assumption that you still have rainbow colors. If you have got your screen back but no 3D -this was also a question, have you?-, then please disregard this one.)

It seems as if somehow you card is not detected by the system as an eligible NVidia drive...

---

### Post by Tails9 on 2008-02-14
I guess I have to refine my search and look for topics regarding indirect rendering.

Thanks for your help though :)

---

### Post by erginemr on 2008-02-14
You are welcome, but I am sorry that it didn't work.

On a final note, you don't have this line:
```
Section "Module"
    Load "glx"
EndSection
```

which is responsible from "glx" (3D). We may have bulls-eye here!.. See my xorg.conf file.

There should also be an other command line config tool:
```
sudo nvidia-xconfig
```
which should be installed in your system inside the "nvidia-glx-new" packages. Please try it. too.

If these do not work either, I hope you will find the solution somewhere else, soon.

---

### Post by Tails9 on 2008-02-14
I was just looking at it!

I added it to my xorg, and I will restart after I've finished my Age of Empires 2 experiment ;)

Thanks

---

### Post by Tails9 on 2008-02-15
I think i've found my problem. It's XGL. ("But you never told you used XGL!": didn't know it was important)

>  Re: After trying XGL/AILX -- How many live without it?
I tried XGL + compiz - and don't use it anymore!

Why?

As it disables DRI (direct rendering) for normal applications it is simply not useable on a normal system:
No 3-D acceleration (which I need for Bridge Construction Set [yeah!] + Planet Penguin Racer),
No good smooth Fullscreen Video Playback.

---

### Post by Tails9 on 2008-03-02
I Removed XGL, recompiled the kernel and excluded NvidiaFB (framebuffer) support.

I have direct rendering now!
I'll test the video tearing next.

---

### Post by Tails9 on 2008-03-02
And the videotearing is gone! thanks to direct rendering.

---

