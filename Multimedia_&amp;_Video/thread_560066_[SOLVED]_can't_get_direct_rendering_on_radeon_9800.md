---
title: "[SOLVED] can't get direct rendering on radeon 9800 (open source driver)"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by jai_mantravadi on 2007-09-25
I've got a Radeon 9800 SE, which according to the documentation (Open source driver howto) has partial Accelerated 3D support. I have followed all of the Howto instructions, including the troubleshooting steps, and I still get a "no" on direct rendering under glxinfo. I have TRIED and TRIED and TRIED to install the closed-source driver, but all I ever get is either a mesa driver (the open source driver), or a blank text-mode screen with a blinking cursor on the top when I start KDE.
If I can get AIGLX/DRI working under the open source driver, I'd be pretty happy with that because I just want to run Compiz fusion.
Please help! I want my 3d Accelerated desktop :'(
My system is:
AMD Athlon 3200+
1.5 GB of Ram
250 GB hard drive  (SATA)
Kubuntu Fiesty
ATI Radeon 9800 SE
Gigabyte K8NSNXP (Nforce 3 250 mobo)
Creative Labs Audigy 2 ZS Platinum

I *really* like Ubuntu, and I want to keep using it when I upgrade to a new system in the coming months (thinking a Athlon 64 X2 6000+ with an ATI graps card)
Any help would definately be appreciated!
Jai

---

### Post by w4ett on 2007-09-25
Have you been running the flgrx drivers for that card??? If so do:

```
sudo apt-get remove fglrx
```

then restart X

---

### Post by jai_mantravadi on 2007-09-26
I've added/removed the fglrx drivers before, but they won't load. The drivers I'm using are the mesa drivers. When I first wrote this, I was just using the mesa drivers and I'd already unloaded the fglrx drivers (a while ago). After writing this I attempted (once again) to load the fglrx drivers using envy, and they still won't load. Point is, I really don't care which fglrx or ati just so long as I can get my 3D accelaration to work. If I can get both to work, I'll put the open source ones in.
Thanks.

---

### Post by jai_mantravadi on 2007-09-28
I guess I should ask if anyone has any ideas for getting direct rendering to work with the open source ATI driver? I really want a 3-D enhanced desktop, and from everything I gather, the open-sauce driver supports my card (at least partially) for 3-D acceleration. I've tried everything in the HOWTO. Should I include my xorg.conf for debugging? Thanks in advance!

---

### Post by CowzRule on 2007-09-28
I've had great success with the open source drivers with my ATI X800 Pro agp card in the computer I used to have. I did a search for my previous posts to find the settings I had in my xorg.conf and the following is what I had that worked great:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
[Color=Red]	Driver		"radeon"
	Option	   "DRI" "Enable"
	Option          "AGPMode" "8"
	Option          "ColorTiling" "on"	
	Option          "AccelMethod" "XAA"
	Option          "EnablePageFlip" "on"
	Option	   "XAANoOffScreenPixMaps"
	Option	   "RenderAccel" "true"[/color]
	BusID		"PCI:1:0:0"
EndSection
``````
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"stylus" "SendCoreEvents"
	InputDevice	"cursor" "SendCoreEvents"
	InputDevice	"eraser" "SendCoreEvents"
[color=red]	Option		"AIGLX" "true"[/color]
EndSection
```The following goes at the bottom of the file```
[color=red]Section "Extensions"
  Option "Composite" "Enable"
EndSection
```[/color]
The items in red are what I had to change or add.
Give these settings a try and post back if they worked or not.
Also post your xorg.conf so others can see what you got.
Oh yea, open /var/log/Xorg.0.log in gedit. It might show you what the problem might be. Look for lines beginning with (WW) and (EE) and refer to you video settings.

---

### Post by jai_mantravadi on 2007-10-02
Cowzrule, Thanks for the info... but, no dice. I tried copying your xorg.conf sections (replacing the ones I had before), but I still can't get any direct rendering! Please help! I'm attaching my xorg.conf and xorg.0.log if anyone feels like helping out a newbie Ubuntu user (not new to computers/*nux, but haven't run linux as my main operating system before). This is one of the main reasons I can't fully recommend linux to my friends. I'd love to try and get some games (older, known to work with Linux) up and running direct or under wine/crossover/cedega, but if I can't get direct rendering, then there's not much point in trying.  Any ideas? One big point I forgot to add last time is that I'm running the 64 bit version of Ubuntu (fiesty), but I hadn't thought I saw people having trouble with direct rendering specifically because of that.

lspci | grep ATI
```

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
```

xorg.conf:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	Option 		"AIGLX" "true"
	Identifier     "Default Layout"
	Screen 		"Default Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option      "Buttons"  "12"
	Option	    "ZAxisMapping" "4 5 6 7 8 9"
	Option	    "ButtonMapping" "1 2 3 10 11 12"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 80.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Radeon 9800"
	Driver	"ati"
	#Driver		"radeon"
	Option	  	 "DRI" "Enable"
	Option          "AGPMode" "8"
	Option          "ColorTiling" "on"	
	Option          "AccelMethod" "XAA"
	Option          "EnablePageFlip" "on"
	Option	   "XAANoOffScreenPixMaps"
	Option	   "RenderAccel" "true"
	 Option          "ColorTiling"    "on"
        Option          "EnablePageFlip" "true" #only works with accelmethod "XAA"
        Option          "AccelDFS"       "true" #seemed to speed things up using EXA acceleration
        Option          "TripleBuffer"   "true" #This *might* help if you use something like Beryl and have slow video playback.
        Option          "DynamicClocks"  "on"   #This is for laptop users, it saves energy when in battery mode.

        Option          "DMAForXv"       "true" #This can speed up movie playback but can in rare cases case instability
        Option          "GARTSize"       "64"   #This is the size of the "GART" that xorg will use.
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Radeon 9800"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

xorg.0.log is attached (there's warnings, and Direct rendering is disabled, but I don't understand why/what to do about them).

Thanks!
Jai

P.S. BTW, I've been through both HOWTO's for the open and closed-source drivers, all the troubleshooting info, and tried ENVY to try and get fglrx working, still only the mesa driver. Also, I've been searching the forums, and still haven't found anything (hence the newb post).

---

### Post by CowzRule on 2007-10-03
I went through your xorg.conf and changed it to what, hopefully, should give you 3d.
Since you said you tried installing the FGLRX divers, I'd try running```
sudo dpkg-reconfigure -phigh xserver-xorg
```in the terminal. When it's finished, copy the file I posted into the right place and reboot. 
Good luck.

---

### Post by jai_mantravadi on 2007-10-03
CowzRule,
Thanks for the help, but... no dice *again* (not your fault). *sigh* When I ran the reconfigure, I just selected the defaults, but the graphics driver was listed as "ati". I scrolled down to "radeon", but there wan't an entry there (I'm presuming that they're both the same driver since the community HowTO actually uses "ati" in its device section. After that, I copied your xorg.conf in the right place (/etc/X11), and restarted using ctrl-alt-f12. After that, since I didn't see direct rendering, I rebooted, and still didn't see direct rendering as a result of glxinfo.
Thanks for all the help, but I guess I'll have to wait until I upgrade (which should be in the next couple of months). I'm sticking with AMD/ATI because AMD just released their specs to the open source community, so we should be seeing a stable driver on the linux side in the next few months for the later generation ATI cards.
I did check the log (xorg.0.log), and now I get an error I didn't get before
```

(II) RADEON(0): [drm] DRM interface version 1.3
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0x1f000000
(II) RADEON(0): [drm] mapped SAREA 0x1f000000 to 0x2b9447815000
(II) RADEON(0): [drm] framebuffer handle = 0xe0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(WW) RADEON(0): [agp] AGP not available
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(II) RADEON(0): [agp] You may want to make sure the agpgart kernel module

```

any other tricks? Should I know what DRM means (I'm assuming it doesn't mean digital rights management). I didn't have this in my previously posted error log. Does the order of listing of the modules affect the outcome in xorg.conf? Thanks!
Jai

---

### Post by jai_mantravadi on 2007-10-07
Bump..
Am I doing something wrong or does the open-source driver not support my card for 3-D acceleration? Why does the log show that it can't load AGP after the changes to the xorg.conf from before? I can't seem to understand this, and I think I'm reasonably computer savvy (not necessarily linux savvy). Thanks!

---

### Post by Stemp on 2007-10-18
```
(WW) RADEON(0): [agp] AGP not available
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
```

i guess you have a problem with your agp driver.

Could you give us the output of this command ? 

```
$ lsmod | grep agp
```

Then in the system menu, try to look at the infos about of your agp devices (in hardware infos)

---

### Post by jai_mantravadi on 2007-10-19
lsmod | grep agp - doesn't result in anything. Not sure what you mean by the system infos. It does detect  the card, and using the other settings for xorg.conf (see first couple of posts in the thread), it *does* load the agp but not the DRI. I guess there's something in the settings from the first xorg.conf I posted to the second? Any reason this difference would stop it from loading agp?

---

### Post by Stemp on 2007-10-19
For me, and I may be wrong... It is not loading the right agp driver.
And it has nothing to do with your xorg configuration.

By example my agp driver is sis_agp, and in hardware infos i can see :
SiS AGP Port (virtual PCI-to-PCI bridge)

---

### Post by jai_mantravadi on 2007-10-22
Stemp,
Thanks for the suggestion, I did some digging, and found that AGP wasn't loading via dmesg. I was getting "agpgart: No usable aperture found", and needed to up the aperture in the bios. However, I still cannot get direct rendering to work...

i'm using Kubuntu 64 (now Gutsy) which may be why I'm not sure exactly where to look (if you're using gnome, the menus are different). When I pull up the system settings, it gives me the following:
```

....
<bootdata>[   44.253521] agpgart: Detected AGP bridge 0</bootdata>
<bootdata>[   44.253527] agpgart: Setting up Nforce3 AGP.</bootdata>
<bootdata>[   44.268615] agpgart: AGP aperture is 256M @ 0xd0000000</bootdata>
<bootdata>[   44.947634] Linux agpgart interface v0.102 (c) Dave Jones</bootdata>
...
  <property class="info" subclass="linux" name="driver" type="string">agpgart-amd64</property>
 <xlogdata>(II) RADEON(0): [agp] Mode 0x1f00420a [AGP 0x10de/0x00e1; Card 0x1002/0x4e48]</xlogdata>
 <xlogdata>(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001</xlogdata>
 <xlogdata>(II) RADEON(0): [agp] ring handle = 0xd0000000</xlogdata>
 <xlogdata>(II) RADEON(0): [agp] Ring mapped at 0x2ab22e5e4000</xlogdata>
 <xlogdata>(II) RADEON(0): [agp] ring read ptr handle = 0xd0101000</xlogdata>
 <xlogdata>(II) RADEON(0): [agp] Ring read ptr mapped at 0x2ab22e6e5000</xlogdata>
 <xlogdata>(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xd0102000</xlogdata>
 <xlogdata>(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0x2ab22e6e6000</xlogdata>
 <xlogdata>(II) RADEON(0): [agp] GART texture map handle = 0xd0302000</xlogdata>
 <xlogdata>(II) RADEON(0): [agp] GART Texture map mapped at 0x2ab22e8e6000</xlogdata>
 <bootdata>[   44.253521] agpgart: Detected AGP bridge 0</bootdata>
 <bootdata>[   44.253527] agpgart: Setting up Nforce3 AGP.</bootdata>
 <bootdata>[   44.268615] agpgart: AGP aperture is 256M @ 0xd0000000</bootdata>
 <bootdata>[   44.947634] Linux agpgart interface v0.102 (c) Dave Jones</bootdata>
vijay@forefront:~$ cat kdevice.txt | grep render
 <xlogdata>(II) RADEON(0): Direct rendering enabled</xlogdata>
vijay@forefront:~$ cat kdevice.txt | grep radeon
 <xlogdata>(II) LoadModule: "radeon"</xlogdata>
 <xlogdata>(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so</xlogdata>
 <xlogdata>(II) Module radeon: vendor="X.Org Foundation"</xlogdata>
 <xlogdata>(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon</xlogdata>
 <xlogdata>(II) Loading sub module "radeon"</xlogdata>
 <xlogdata>(II) LoadModule: "radeon"</xlogdata>
 <xlogdata>(II) Reloading /usr/lib/xorg/modules/drivers//radeon_drv.so</xlogdata>
 <xlogdata>(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"</xlogdata>

...

```

So... if AGP is loading at boot (according to dmesg), and according to the Xorg.0.log I've got DRI loading (see also above), and according to glxinfo the driver is:
```

OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x TCL
OpenGL version string: 1.3 Mesa 7.0.1

```
and not the "indirect driver", then WHY does glxinfo | grep render give:
```

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

Also, can anyone tell me why there's no difference in the output between the two commandlines
```

$glxinfo 

```

..and..
```

$LIBGL_DEBUG=verobse  glxinfo

```

I'm at a loss here as to why I can't get direct rendering to work according to glxinfo but according to the log files, everything is now loading fine. 

Please help! I want my 3D accelerated desktop! :) Thanks!
Jai

---

### Post by Stemp on 2007-10-23
Do you have a copy of your first xorg.conf ? 
It will be good to try it now.
My new (well Gutsy's one) xorg.conf is quite different from my Feisty file.

By example my "Device" Section is now only this :
```
Section "Device"
        Identifier      "ATI Technologies Inc RV350 AP [Radeon 9600]"
        Boardname       "ati"
        Busid           "PCI:1:0:0"
        Driver          "ati"
        Screen  0
        Option          "MergedFB"      "off"
EndSection
```

and "Module" :
```
Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection
```

Not anymore AIGLX=true or Extensions Section

---

### Post by criskat777 on 2007-11-08
I have a 9600 pro and the only way that i could get compiz+AWN+all the toys oddly enuff was with the original drivers that were loaded when i did a fresh install. i had tried every dang how to u can think of and at the end all i hade to do was use synaptic to get compiz manager and some other packages that are on a how to in here somewhere. just serch for a how to install compiz with original open source drivers and u will get it working believe me i have one of the lest supported ati cards 9600 pro and yes i have the worse one as well a craptop with the unsupported 9000 chips:(

---

### Post by jai_mantravadi on 2007-11-13
I tried loading compiz-manager, and I've been through the howto's on both compiz and the open-source radeon driver. So I bascially gave up because it was more headache than it was worth. I was trying to do it without a fresh install.
Now after trying to reconfigure my MOUSE of all things, I even broke what ATI functionality I had.
more on that [here]("http://ubuntuforums.org/showthread.php?p=3764438").

I *really* wanted to keep the old install... not having to reinstall every so often was on of the *many* (good) reasons to switch to ubuntu

---

### Post by jai_mantravadi on 2007-11-23
OK... now that I've tried a fresh install off the gutsy DVD (took a couple of coasters to figure out my CD media was a bad batch), Direct rendering was working with the open-source driver out-of-the box. Compi Fusion took about 2 minutes to install, and even less time to get working. Haven't tried fglrx yet, but I'm not sure that's worth it since I'm upgrading the hardware in a few days :). Thanks to everyone who tried to help me get the [open and closed source] drivers working. Sorry for the frustration. I never did figure out why direct rendering wasn't working, (or how installing a new mouse driver can screw up a graphics card even after reversing the instructions completely).
Jai

---

