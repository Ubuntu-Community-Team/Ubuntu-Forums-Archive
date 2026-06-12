---
title: "IBM xSeries 100 + integrated chipset ATI ES1000"
date: 2008-05-23
forum: Multimedia Software
---

### Post by Marcus Aurelius Severus on 2008-05-23
Hello everybody,

My computer is a IBM xSeries 100 with integrated graphic chipset ATI ES1000.

I have a wide LCD screen (under Windows, resolution is 1680x1050). It is a Samsung SynchMaster 225BW.

I installed last Ubuntu 8.04 LTS and the display is very ugly.

I guess it's because Ubuntu doesn't recognize the ATI ES1000 chipset. The "driver" line in xorg.conf is the standard "vesa"

I looked for drivers in the ATI website. I didn't even find any mention of the ES1000 ! I also looked for drivers in the IBM website. And... Yes ! There are drivers ! For Windows XP.... :'(

I tried the generic ATI driver, I installed xorg-driver-fglrx, I read several forums, included this one. I filled xorg.conf with hundreds of different parameters, and I still bear this ugly appearance.

Does anybody can help ?
Thanks a lot :)

---

### Post by josir on 2008-05-24
Hi Marcus, I have the same problem with the same server (IBM x3200) and Ubuntu 8.04 Server Edition. With vesa, it works fine but I would like to use the proper ati driver. 

I found this bug on Lauchpad but it seems to be solved.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/86072](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/86072)

When I issue an "lspci", it shows:

0a:04.0 VGA compatible controller: ATI Technologies Inc ES1000 (rev 02)

Is your config has the same string?

If you find any solution, let me know. If I find first, I will post to you :)

Josir Gomes

---

### Post by Marcus Aurelius Severus on 2008-05-26
Yes, it is the same string :)
Good luck to solve this problem :)

I've looked in vain for errors in /var/log/Xorg.0.log... 

```
*root@administrateur:/etc/X11#* **grep EE /var/log/Xorg.0.log**
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
*root@administrateur:/etc/X11#* **grep WW /var/log/Xorg.0.log**
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Configured Mouse: No Device specified, looking for one...
```


Just in case, here is my xorg.conf...

```
# xorg.conf (X.Org X Window System server configuration file)
#
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"oss"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"ES1000"
	Boardname	"vesa"
	Busid		"PCI:0A:4:0"
	Driver		"ati"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 225BW (Analog)"
	Horizsync	30.0 - 81.0
	Vertrefresh	56.0 - 75.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ES1000"
	Monitor		"Configured Monitor"
	Defaultdepth	16
	SubSection "Display"
		Depth	16
		Modes	"1680x1050@60"	"1920x1200@60"	"1600x1024@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
		Virtual "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes	"1680x1050@60"	"1920x1200@60"	"1600x1024@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
		Virtual "1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
	Load		"dbe"
	Load		"extmod"
	Load		"type1"
	Load		"freetype" 
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by leech on 2008-06-09
This is a regression of the ATI driver.

It semi worked on Suse 10.0, but is horribly broken in every distribution I've tried Fedora 9, Suse 10.3, 11.0, Ubuntu 8.04, and Kubuntu 8.04.  Debian Etch seems to have worked on it as well, at least the graphical installer, but that's because it uses Framebuffer.

On Suse 10.0 it has crashed X, then would not load again until I changed the driver to Vesa.

The specific reason it's ugly is because Vesa does not do 1680x1050 (as far as I know), and on an LCD, if you're not in your native resolution, it's butt ugly.

I'd be really happy if we could either fix this issue of having a black screen on the ES1000 driver, or even if I could set Vesa by default during the install (there probably is a way to do this, but I haven't yet had the time look into that.)

Leech

---

### Post by Crass Spektakel on 2008-06-10
Hi, this is a "me too" report but with some success and insight.

I am using an IBM 3650 system (don't ask for more details, I have only seen it for a couple of minutes before lockign the airconditioned cabinet) which is using "01:06.0 VGA compatible controller: ATI Technologies Inc ES1000 (rev 02)".

XOrg using the ati driver on its own recognizes it but uses bad settings, resulting in a black screen. All other ATI-drivers are NOT supporting ES1000 which is a rather strange rework of very old hardware for embedded systems: [Wikipedia]("http://http://en.wikipedia.org/wiki/ATI_Rage#RAGE_XL") and [AMD]("http://ati.amd.com/products/server/es1000/index.html") - if you actually did get a picture with the autodetected ES1000 let me know.

But there is limited hope:

Use VESA drivers. At least I get 1024x768 in decent quality. But if I use 1280x1024 then the screen is horribly distorted, just like randomly placed pixels. VESA only support a small number of fixed resolutions and 1280x1024 actually is part of the list but still doesn't work which means the VESA-Bios of the ES1000 is badly bugged. I might add that Ubuntu also chokes on a rather old and simple chipset like the S3-Virge so no points for Gfx support to ubuntu. #-o

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
        Option          "XkbVariant"    "nodeadkeys"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "vesa"
        Busid           "PCI:1:6:0"
        Driver          "vesa"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1280x1024"
        Horizsync       31.5-64.0
        Vertrefresh     56.0 - 65.0
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        Defaultdepth    16
        SubSection "Display"
                Virtual 1024 768
                Depth   16
                Modes "1024x768@60"     "800x600@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection
Section "ServerFlags"
EndSection

```

---

