---
title: "Can't get dual head to work on ATI after Jaunty update June 22"
date: 2009-06-25
forum: Multimedia Software
---

### Post by drdan14 on 2009-06-25
After performing the package updates on June 22, dual monitor setup stopped functioning correctly. Now, my computer boots with my two monitors mirrored, and I can't figure out how to extend them back into my Big Desktop configuration. I tried to fix the problem by installing the latest version of ATI's Catalyst drivers (9.6), which allowed me to boot, but I can't get back my big desktop.

My xorg.conf looks like this:
```

Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[5]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "amdcccle-Monitor[5]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    Option        "EnableMonitor" "crt1,lvds,tv,tmds1,crt2,tmds2,cv,tmds2i"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[5]-0"
    Driver      "fglrx"
    BusID       "PCI:5:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
    SubSection "Display"
        Virtual   2560 1024
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[5]-0"
    Device     "amdcccle-Device[5]-0"
    Monitor    "amdcccle-Monitor[5]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

Here are the updates installed on June 22, from Synaptic history. Before these updates, my video drivers were working fine:
```

Commit Log for Mon Jun 22 11:34:25 2009


Upgraded the following packages:
app-install-data-commercial (11.9.04) to 11.9.04.2
app-install-data-partner (11.9.04) to 11.9.04.2
compiz (1:0.8.2-0ubuntu8) to 1:0.8.2-0ubuntu8.1
compiz-core (1:0.8.2-0ubuntu8) to 1:0.8.2-0ubuntu8.1
compiz-gnome (1:0.8.2-0ubuntu8) to 1:0.8.2-0ubuntu8.1
compiz-plugins (1:0.8.2-0ubuntu8) to 1:0.8.2-0ubuntu8.1
compiz-wrapper (1:0.8.2-0ubuntu8) to 1:0.8.2-0ubuntu8.1
dvipdfmx (1:20080607-1) to 1:20080607-1ubuntu1
file (4.26-2ubuntu3) to 4.26-2ubuntu4
gstreamer0.10-esd (0.10.14-1) to 0.10.14-1ubuntu0.1
gstreamer0.10-plugins-good (0.10.14-1) to 0.10.14-1ubuntu0.1
gstreamer0.10-plugins-good-dbg (0.10.14-1) to 0.10.14-1ubuntu0.1
gstreamer0.10-pulseaudio (0.10.14-1) to 0.10.14-1ubuntu0.1
hal (0.5.12~rc1+git20090403-0ubuntu2) to 0.5.12~rc1+git20090403-0ubuntu3
libdecoration0 (1:0.8.2-0ubuntu8) to 1:0.8.2-0ubuntu8.1
libhal-storage1 (0.5.12~rc1+git20090403-0ubuntu2) to 0.5.12~rc1+git20090403-0ubuntu3
libhal1 (0.5.12~rc1+git20090403-0ubuntu2) to 0.5.12~rc1+git20090403-0ubuntu3
libmagic1 (4.26-2ubuntu3) to 4.26-2ubuntu4
linux-generic (2.6.28.11.15) to 2.6.28.13.17
linux-headers-generic (2.6.28.11.15) to 2.6.28.13.17
linux-image-generic (2.6.28.11.15) to 2.6.28.13.17
linux-libc-dev (2.6.28-11.42) to 2.6.28-13.44
linux-restricted-modules-common (2.6.28-11.15) to 2.6.28-13.17
linux-restricted-modules-generic (2.6.28.11.15) to 2.6.28.13.17
python-cupshelpers (1.1.3+git20090218-0ubuntu19.1) to 1.1.3+git20090218-0ubuntu19.2
system-config-printer-common (1.1.3+git20090218-0ubuntu19.1) to 1.1.3+git20090218-0ubuntu19.2
system-config-printer-gnome (1.1.3+git20090218-0ubuntu19.1) to 1.1.3+git20090218-0ubuntu19.2
tzdata (2009f-0ubuntu1) to 2009j-0ubuntu0.9.04
tzdata-java (2009f-0ubuntu1) to 2009j-0ubuntu0.9.04
xserver-xorg-video-intel (2:2.6.3-0ubuntu9) to 2:2.6.3-0ubuntu9.3

Installed the following packages:
linux-headers-2.6.28-13 (2.6.28-13.44)
linux-headers-2.6.28-13-generic (2.6.28-13.44)
linux-image-2.6.28-13-generic (2.6.28-13.44)
linux-restricted-modules-2.6.28-13-generic (2.6.28-13.17)

```

* When I disable "mirror screens" and enable "side by side" monitors in gnome-display-properties (either as superuser or not) ([http://www.stanford.edu/~dgolden1/misc/ubuntu/xorg_display_pref_side_by_side.png](http://www.stanford.edu/~dgolden1/misc/ubuntu/xorg_display_pref_side_by_side.png)) and reboot, nothing happens. My monitors are still mirrored.

* When I enable "side by side" monitors in Catalyst Control Center, it makes one of my monitors really tiny ([http://www.stanford.edu/~dgolden1/misc/ubuntu/xorg_display_ccc_small_monitor.png](http://www.stanford.edu/~dgolden1/misc/ubuntu/xorg_display_ccc_small_monitor.png)). When I reboot, one monitor is indeed set to a very low resolution, and some sort of "faux" big desktop is enabled, where I can't drag windows across monitors, and each monitor has its own set of workspaces and what not. I can increase the resolution after booting, but it's still the wrong kind of big desktop.

* When I enable Xinerama in Catalyst Control Center and reboot, I never make it to the login screen; my right monitor is dark (but on) and my left monitor stays in standby mode. No keypresses (CTRL+ALT+BKSPACE, CTRL+ALT+F4,F5,F6) do anything, and I need a hard reset.

* When I run "aticonfig --initial=dual-head", I get to the "faux" big desktop, where again I can't drag stuff across monitors. However, the monitor resolutions are correct.

I tried booting with the previous kernel, but got the same problems.

I have an ATI Radeon HD 2600 card with 512 MB memory and two DVI outputs, Ubuntu 9.04, X.Org X Server 1.6.0.

Can anyone give me a hand with this?

Thank you!
Dan

---

### Post by drdan14 on 2009-06-25
Update: I tried disabling RandR 1.2 as per the instructions in this post:

[http://ubuntuforums.org/showthread.php?t=1137576](http://ubuntuforums.org/showthread.php?t=1137576)

This allowed me to use Xinerama, but at the expense of Compiz, which refuses to start with this message:

```
$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No composite extension
Xlib:  extension "RANDR" missing on display ":0.0".
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

---

### Post by markbuntu on 2009-06-25
In xorg.conf Section "SeverLayout" add this

Option "AIGLX" "on"


This will turn on the AIGLX compositer so compiz should work

---

### Post by drdan14 on 2009-06-25
No, luck. Compiz refuses to start with a similar message:

```
$ compiz --replace &
[1] 5177
Checking for Xgl: [dgolden@dualcoredan ~]$ not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No composite extension
Xlib:  extension "RANDR" missing on display ":0.0".
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

My xorg.conf file now looks like this (with xinerama on and compiz not working):
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
	Option         "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "Capabilities" "0x00000800"
	Option	    "EnableRandR12" "false"
	Option	    "PairModes" "0x0+0x0"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:5:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

I also get errors saying > Xlib:  extension "RANDR" missing on display ":0.0". when I start GUI programs from the terminal, such as gedit, although the programs seem to load fine anyway.

Thanks for the help!
Dan

---

### Post by gradinaruvasile on 2009-06-25
Have u tried booting with the 11 kernel? Does it work that way?

---

### Post by drdan14 on 2009-06-25
Yeah, I tried with the 11 kernel, but it doesn't change anything. compiz --replace gives the same output as with the 13 kernel.

---

### Post by drdan14 on 2009-06-26
Another update:

Here's an exerpt from my Xorg.0.log. There seem to be some problems with AIGLX:

```

Line 24: (**) Option "AIGLX" "on"
Lines 1059-1222: (WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/X11R6/lib64/modules/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(WW) AIGLX: 3D driver claims to not support visual 0x8a
(WW) AIGLX: 3D driver claims to not support visual 0x8b
(WW) AIGLX: 3D driver claims to not support visual 0x8c
(WW) AIGLX: 3D driver claims to not support visual 0x8d
(WW) AIGLX: 3D driver claims to not support visual 0x8e
(WW) AIGLX: 3D driver claims to not support visual 0x8f
(WW) AIGLX: 3D driver claims to not support visual 0x90
(WW) AIGLX: 3D driver claims to not support visual 0x91
(WW) AIGLX: 3D driver claims to not support visual 0x92
(WW) AIGLX: 3D driver claims to not support visual 0x93
(WW) AIGLX: 3D driver claims to not support visual 0x94
(WW) AIGLX: 3D driver claims to not support visual 0x95
(WW) AIGLX: 3D driver claims to not support visual 0x96
(WW) AIGLX: 3D driver claims to not support visual 0x97
(WW) AIGLX: 3D driver claims to not support visual 0x98
(WW) AIGLX: 3D driver claims to not support visual 0x99
(WW) AIGLX: 3D driver claims to not support visual 0x9a
(WW) AIGLX: 3D driver claims to not support visual 0x9b
(WW) AIGLX: 3D driver claims to not support visual 0x9c
(WW) AIGLX: 3D driver claims to not support visual 0x9d
(WW) AIGLX: 3D driver claims to not support visual 0x9e
(WW) AIGLX: 3D driver claims to not support visual 0x9f
(WW) AIGLX: 3D driver claims to not support visual 0xa0
(WW) AIGLX: 3D driver claims to not support visual 0xa1
(WW) AIGLX: 3D driver claims to not support visual 0xa2
(WW) AIGLX: 3D driver claims to not support visual 0xa3
(WW) AIGLX: 3D driver claims to not support visual 0xa4
(WW) AIGLX: 3D driver claims to not support visual 0xa5
(WW) AIGLX: 3D driver claims to not support visual 0xa6
(WW) AIGLX: 3D driver claims to not support visual 0xa7
(WW) AIGLX: 3D driver claims to not support visual 0xa8
(WW) AIGLX: 3D driver claims to not support visual 0xa9
(WW) AIGLX: 3D driver claims to not support visual 0xaa
(WW) AIGLX: 3D driver claims to not support visual 0xab
(WW) AIGLX: 3D driver claims to not support visual 0xac
(WW) AIGLX: 3D driver claims to not support visual 0xad
(WW) AIGLX: 3D driver claims to not support visual 0xae
(WW) AIGLX: 3D driver claims to not support visual 0xaf
(WW) AIGLX: 3D driver claims to not support visual 0xb0
(WW) AIGLX: 3D driver claims to not support visual 0xb1
(WW) AIGLX: 3D driver claims to not support visual 0xb2
(WW) AIGLX: 3D driver claims to not support visual 0xb3
(WW) AIGLX: 3D driver claims to not support visual 0xb4
(WW) AIGLX: 3D driver claims to not support visual 0xb5
(WW) AIGLX: 3D driver claims to not support visual 0xb6
(WW) AIGLX: 3D driver claims to not support visual 0xb7
(WW) AIGLX: 3D driver claims to not support visual 0xb8
(WW) AIGLX: 3D driver claims to not support visual 0xb9
(WW) AIGLX: 3D driver claims to not support visual 0xba
(WW) AIGLX: 3D driver claims to not support visual 0xbb
(WW) AIGLX: 3D driver claims to not support visual 0xbc
(WW) AIGLX: 3D driver claims to not support visual 0xbd
(WW) AIGLX: 3D driver claims to not support visual 0xbe
(WW) AIGLX: 3D driver claims to not support visual 0xbf
(WW) AIGLX: 3D driver claims to not support visual 0xc0
(WW) AIGLX: 3D driver claims to not support visual 0xc1
(WW) AIGLX: 3D driver claims to not support visual 0xc2
(WW) AIGLX: 3D driver claims to not support visual 0xc3
(WW) AIGLX: 3D driver claims to not support visual 0xc4
(WW) AIGLX: 3D driver claims to not support visual 0xc5
(WW) AIGLX: 3D driver claims to not support visual 0xc6
(WW) AIGLX: 3D driver claims to not support visual 0xc7
(WW) AIGLX: 3D driver claims to not support visual 0xc8
(WW) AIGLX: 3D driver claims to not support visual 0xc9
(WW) AIGLX: 3D driver claims to not support visual 0xca
(WW) AIGLX: 3D driver claims to not support visual 0xcb
(WW) AIGLX: 3D driver claims to not support visual 0xcc
(WW) AIGLX: 3D driver claims to not support visual 0xcd
(WW) AIGLX: 3D driver claims to not support visual 0xce
(WW) AIGLX: 3D driver claims to not support visual 0xcf
(WW) AIGLX: 3D driver claims to not support visual 0xd0
(WW) AIGLX: 3D driver claims to not support visual 0xd1
(WW) AIGLX: 3D driver claims to not support visual 0xd2
(WW) AIGLX: 3D driver claims to not support visual 0xd3
(WW) AIGLX: 3D driver claims to not support visual 0xd4
(WW) AIGLX: 3D driver claims to not support visual 0xd5
(WW) AIGLX: 3D driver claims to not support visual 0xd6
(WW) AIGLX: 3D driver claims to not support visual 0xd7
(WW) AIGLX: 3D driver claims to not support visual 0xd8
(WW) AIGLX: 3D driver claims to not support visual 0xd9
(II) AIGLX: Loaded and initialized /usr/X11R6/lib64/modules/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 1

```

Is this maybe a known problem with the Catalyst 9.6 drivers? Should I try reverting to Catalyst 9.5?

Thanks,
Dan

---

### Post by drdan14 on 2009-06-26
I finally got compiz working again. The trick? Revert to the Catalyst 9.4 drivers, acquired from the ATI web site.

Here's my current xorg.conf with Compiz and Big Desktop **finally working**:

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:5:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	SubSection "Display"
		Virtual   2560 1024
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

But note that compiz-check fails, with the same error as when I was using the 9.6 ATI drivers and compiz wasn't working, despite the fact that compiz is actually working with the 9.4 drivers:

```
 compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV630 [Radeon HD 2600 Series]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

Thanks for everyone's help. Boo for ATI's 9.6 driver release!

Dan

---

### Post by rsea on 2009-07-02
Hey Dan,

I had the exactly same problem as you do and I've managed to get ATI drivers 9.6 with big screen, compiz and dtop=horizontal by disabling RandR 1.2 using the link you posted [above]("http://ubuntuforums.org/showpost.php?p=7170485&postcount=2"). 

First I've installed ati drivers, then I run "aticonfig --initial=dual-head", after "aticonfig --dtop=horizontal" then I edited amdpcsdb and xorg.conf to disable xrandr and restarted the X (just logged off and logged in again). 

With X running (with one monitor off I suppose) I opened a terminal and ran "sudo amdcccle" (Catalyst Control Center) to configure the graphics, on the forth option (something like 'video manager' I use another lang) you enable the second monitor as "big desktop at left/right of monitor 1" and then set the minor configurations. 

After this, enable the compiz using the Preferences->Appearance->Visual Effects and checking Extra. It should work fine except by the transparency, so restart the system and you will be working with all features you want together!

I hope works with you and everyone else who are in this situation!

Ubuntu :guitar:

Good luck and may the Force be with you,
Rodolfo.

---

### Post by helliewm on 2009-10-11
I have an ATI 4850 Card using fglrx. 2 VGA monitors with resolutions of 1680 1050 and 1440 900. I followed the instruction in this thread. I now have the resolution correct across the 2 monitors. However amdcccle-ATI Catalyst Control is only detecting one monitor and they are mirroring each other.
System, preferences, display dpes not work (which I expected having following the instruction is this thread) so cannot turn off mirrored monitors that way.

How can I turn off mirroring and why is Amdccle-Ati Catalyst Control only picking up one monitor?

Xinerama is grayed out in ATI Catalyst Control.

Helen

Ps I am using Karmic and install ed fglrx drivers by Karmic Hardware Drivers

---

