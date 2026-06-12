---
title: "support for non power two textures miss error"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by weekendli on 2007-02-03
After I start my beryl aiglx, I got following error and gnome frozen. Basically the error msg is "non power of two textures missing"

The situation here is my video card is ati radeon 7500 mobility, and the xorg driver currently using is "ati". 

Do you know what goes wrong in my configuration? Or any chance I can get beryl working on my laptop. 

Thank you.

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x5b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing

---------------------------------------------------------------------------------------------------------
#############################################
# xorg.conf
#############################################
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        Load    "dbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
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
        Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by Dieg oTrazzi on 2007-02-04
I am in the same situoation. 1 week ago I was able to run Beryl with no problem, and now I keep ketting this error: 

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing

What happent ? and how can I go back to that fantastic Beryl ? 

here is amy xorg.config, I have a Mobility radeon X300 running on a dell 6000


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
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
	Option	    "XkbVariant" "alt-intl"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

---

### Post by mythic on 2007-02-04
Same problem for me, I have an ati X800 with fglrx, ran XGL + beryl fine until about a week or 2 ago and it suddenly stopped working with the same error.  I've tried reinstalling the gfx drivers as well as beryl, changing the XGL script and tinkering with xorg.conf but to no avail :(

---

### Post by weekendli on 2007-02-05
My beryl working again since I reinstall the system. There're something I don't know. I'm using aiglx + beryl. It seems xgl + aiglx have some problem install together even all xgl packages was removed later. Therefore, I installed aiglx + beryl on a clean system, here we go, it work! 

I'm not sure this can help on your xgl.

---

### Post by Drakonim on 2007-02-07
FYI:
This seems to be a problem with the OpenGL libraries in some way, (or in the way I'm loading them)

If you can get beryl to "pass" on everything except for:

***Checking for non power of two texture support : failed***

try this command inside an XGL session:

*LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl*

wobbly windows ahoy!

[well, it worked for me anyway ;-)]

I guess I'll head into /usr/lib and start mucking about with my libGL* files again...

---

### Post by paxindustria on 2007-02-07
Hi, 

I also had this same problem. Beryl worked like a champ, it auto updated and then broke, I've tried everything short of reinstalling the OS at this point, which I may do. Though I may take a fine tooth comb and try removing all traces of AIGLX (Beryl worked well for me on my t60p with XGL)

-Pax

---

### Post by nquery on 2007-02-08
> **Drakonim said:**
> FYI:
This seems to be a problem with the OpenGL libraries in some way, (or in the way I'm loading them)

If you can get beryl to "pass" on everything except for:

***Checking for non power of two texture support : failed***

try this command inside an XGL session:

*LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl*

wobbly windows ahoy!

[well, it worked for me anyway ;-)]

I guess I'll head into /usr/lib and start mucking about with my libGL* files again...

this let me load up beryl, but when i tried to turn on beryl-manager, it went back to GNOME. and typing letters is really slow, as in, i type a letter, and it shows up on screen a few seconds later

---

### Post by Dieg oTrazzi on 2007-02-08
I had to reformat agaon and then I ainstalled AIGLX , but everything was much more slow, and espetially things like Google earth and 3D sw were not working no more. 
So I now reinstalled everything one last time with FGLRX support, and I promised my self not to use beryl no more ( at least until I will find a good way to use it ). :(

---

### Post by Drakonim on 2007-02-08
> **nquery said:**
> this let me load up beryl, but when i tried to turn on beryl-manager, it went back to GNOME. and typing letters is really slow, as in, i type a letter, and it shows up on screen a few seconds later

This probably means one of 4 things:

1. you don't have the fglrx kernel module loaded 
2. the fglrx driver version in out of sync with the kernel module version
3. you aren't running fglrx as the driver for your Xgl session
4. you aren't running Xgl

please post the output of the following commands:
(you **_don't_** have to sudo or be root, but do pay attention to capitalization please) 

*ps awx |grep X*

*lspci |grep VGA*

*uname -a*

*dpkg --list |grep restricted-modules*

*modinfo fglrx*  

*fglrxinfo|grep version*

*grep Composite /etc/X11/xorg.conf*

*grep AIGLX /etc/X11/xorg.conf*

*grep Proprietary /var/log/Xorg.0.log*

---

### Post by rod.naph on 2007-02-08
i'm having the same problem on edgy with an ati mobility x1400 card, beryl used to work fine for me to until a few days ago,  here's the output of the commands you asked for.

~> ps awx |grep X
 4195 ?        SL     0:22 /usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-HuZTLM
 4213 tty7     SLs+   0:03 /usr/bin/Xorg vt7 -auth /tmp/.Xgl-auth-vTM7R5 -nolisten tcp :93 -terminate
 4921 ?        S      0:00 kio_file [kdeinit] file /home/rod/.kde/socket-dread/klaunchera6cJ2b.slave-socket /home/rod/.kde/socket-dread/kdesktopTXVWwb.slave-socket
 5643 pts/1    R+     0:00 grep X

~> lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7145

~> uname -a
Linux dread 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

~> dpkg --list |grep restricted-modules
ii  linux-restricted-modules-2.6.17-10-generic 2.6.17.7-10.1                 Non-free Linux 2.6.17 modules on x86_64 gene
ii  linux-restricted-modules-common            2.6.17.7-11.1                 Non-free Linux 2.6.17 modules helper script
ii  linux-restricted-modules-generic           2.6.17.10                     Restricted Linux modules for generic kernels

~> modinfo fglrx
filename:       /lib/modules/2.6.17-10-generic/volatile/fglrx.ko
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        agpgart
author:         Fire GL - ATI Research GmbH, Germany
description:    ATI Fire GL
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
parm:           firegl:charp

~> fglrxinfo|grep version
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
OpenGL version string: 1.2 (2.0.6011 (8.28.8))

~> grep Composite /etc/X11/xorg.conf
        Option "Composite" "false"

~> grep AIGLX /etc/X11/xorg.conf

~> grep Proprietary /var/log/Xorg.0.log
(II) ATI Proprietary Linux Driver Version Identifier:8.28.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.28g1                
(II) ATI Proprietary Linux Driver Build Date: Aug 17 2006 09:28:12
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.28.1.1.2.3-driver-lnx-x86-x86_64-287161

~>   

hope it can shed some light on the problem.

---

### Post by barbe-et-hache on 2007-02-09
thanks to Drakonim, I can ave beryl working and manage the properties with beryl-manager. I'm using this script to start beryl :

#!/bin/sh
beryl-manager
sleep 1 
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl

---

### Post by bornakke on 2007-02-10
FInaly! Wasn't using the fglrx drivers, but installed it and used the script above. Fixed the problem. :) 

However system seem a little more unstable than before, and using glxinfo or fglrxinfo makes the Computer lock down. Does anybody know a way to fix the problem for other drivers than fglrx? or  when a "complete" solution will be around?

---

### Post by twisterss on 2007-02-11
> **barbe-et-hache said:**
> thanks to Drakonim, I can ave beryl working and manage the properties with beryl-manager. I'm using this script to start beryl :

#!/bin/sh
beryl-manager
sleep 1 
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl

I had the same problem and it works for me too, but it's strange :
in beryl manager, metacity is selected.
I hope this problem will be fixed...:)

---

### Post by Drakonim on 2007-02-14
> **rod.naph said:**
> i'm having the same problem on edgy with an ati mobility x1400 card, beryl used to work fine for me to until a few days ago,  here's the output of the commands you asked for.

~> ps awx |grep X
 4195 ?        SL     0:22 /usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-HuZTLM
 4213 tty7     SLs+   0:03 /usr/bin/Xorg vt7 -auth /tmp/.Xgl-auth-vTM7R5 -nolisten tcp :93 -terminate
 4921 ?        S      0:00 kio_file [kdeinit] file /home/rod/.kde/socket-dread/klaunchera6cJ2b.slave-socket /home/rod/.kde/socket-dread/kdesktopTXVWwb.slave-socket
 5643 pts/1    R+     0:00 grep X

~> lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7145

~> uname -a
Linux dread 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

~> dpkg --list |grep restricted-modules
ii  linux-restricted-modules-2.6.17-10-generic 2.6.17.7-10.1                 Non-free Linux 2.6.17 modules on x86_64 gene
ii  linux-restricted-modules-common            2.6.17.7-11.1                 Non-free Linux 2.6.17 modules helper script
ii  linux-restricted-modules-generic           2.6.17.10                     Restricted Linux modules for generic kernels

~> modinfo fglrx
filename:       /lib/modules/2.6.17-10-generic/volatile/fglrx.ko
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        agpgart
author:         Fire GL - ATI Research GmbH, Germany
description:    ATI Fire GL
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
parm:           firegl:charp

~> fglrxinfo|grep version
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
OpenGL version string: 1.2 (2.0.6011 (8.28.8))

~> grep Composite /etc/X11/xorg.conf
        Option "Composite" "false"

~> grep AIGLX /etc/X11/xorg.conf

~> grep Proprietary /var/log/Xorg.0.log
(II) ATI Proprietary Linux Driver Version Identifier:8.28.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.28g1                
(II) ATI Proprietary Linux Driver Build Date: Aug 17 2006 09:28:12
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.28.1.1.2.3-driver-lnx-x86-x86_64-287161

~>   

hope it can shed some light on the problem.

Sorry for the delay rod.naph, I was on vaca for the first time in years... \\:D/ 

The major differences I can detect in your case are two fold:

1.  very old versions (albeit matching) of ATI drivers / kernel module
2.  x86_64 architecture

Unfortunately, I have all Intel based machines, but I would bet a dollar installing the newer 8.33 series of drivers would make a difference.
Keep in mind, installing the new drivers outside of the standard packaging channels can really muck things up, so if you don't feel 100% confident (or you can't spare the time for a re-install) don't try this at home!

[go download the new ATI drivers, and run the package maker extention to the install script for your OS revision.  a great WIKI on how to do this is available @ [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) I reccomend method 2 for you. ]

Hope it helps!

---

### Post by Newbinator on 2007-06-24
> **Drakonim said:**
> FYI:
This seems to be a problem with the OpenGL libraries in some way, (or in the way I'm loading them)

If you can get beryl to "pass" on everything except for:

***Checking for non power of two texture support : failed***

try this command inside an XGL session:

*LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl*

wobbly windows ahoy!

[well, it worked for me anyway ;-)]

I guess I'll head into /usr/lib and start mucking about with my libGL* files again...

Beautiful! This worked! However, how do I now add this LD_PRELOAD command on startup? Please remember that I am very new to Linux. Thanks for any help I can get.

Cheers!

---

### Post by Newbinator on 2007-06-24
> **Newbinator said:**
> Beautiful! This worked! However, how do I now add this LD_PRELOAD command on startup? Please remember that I am very new to Linux. Thanks for any help I can get.

Cheers!

I noticed that the terminal spits out the following after executing that line of code. Does any part of this code tell me what is wrong or what I need to do to fix this?

[B]root@pipo-laptop:/home/pipo# LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension            : passed (v0.3)
Checking for XDamage extension               : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

/usr/bin/beryl: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Reloading options
/usr/bin/beryl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/beryl: Plugin 'dbus':initDisplay failed
/usr/bin/beryl: Couldn't activate plugin 'dbus'
Couldn't initialise dbus. This should not happen!
[/B]

---

### Post by drfreakynutz on 2007-08-17
OK, so this thread is old, but I am running into the exact problems listed here, so if anyone can help it would be great.  Basically I have beryl running when I execute the command recommended here:  LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl

However, when I execute this command my window frames go away so I can no longer move, maximize or minimize the window without right clicking the icon for that window in the bottom task bar.  If I try to run the beryl manager command before executing the above command my top and bottom task bars go away and the frames of my windows dissappear.  I don't have the beryl gem in my top task bar either.  Any help would be greatly appreciated, I'm very noob with linux so any suggestions will probably need to assume little to no knowledge.  thanks in advance.  Here's the info:


nick@logopolis:~$ ps awx |grep X
 5044 tty7     Ss+    0:28 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 6775 pts/0    R+     0:00 grep X
nick@logopolis:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
nick@logopolis:~$ uname -a
Linux logopolis 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686 GNU/Linux
nick@logopolis:~$ dpkg --list |grep restricted-modules
ii  linux-restricted-modules-2.6.15-26-386 2.6.15.11-4                            Non-free Linux 2.6.15 modules on 386
ii  linux-restricted-modules-2.6.15-28-386 2.6.15.12-28.2                         Non-free Linux 2.6.15 modules on 386
ii  linux-restricted-modules-2.6.17-12-386 2.6.17.8-12.3                          Non-free Linux 2.6.17 modules on 386
ii  linux-restricted-modules-2.6.20-16-386 2.6.20.5-16.29                         Non-free Linux 2.6.20 modules on 386
ii  linux-restricted-modules-386           2.6.20.16.28.1                         Restricted Linux modules on 386.
ii  linux-restricted-modules-common        2.6.20.5-16.29                         Non-free Linux 2.6.20 modules helper script
nick@logopolis:~$ modinfo fglrx
filename:       /lib/modules/2.6.20-16-386/volatile/fglrx.ko
depends:        agpgart
vermagic:       2.6.20-16-386 mod_unload 486 
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany
parm:           firegl:charp
nick@logopolis:~$ grep Composite /etc/X11/xorg.conf
        Option "Composite" "Enable"
nick@logopolis:~$ grep AIGLX /etc/X11/xorg.conf
nick@logopolis:~$ grep Proprietary /var/log/Xorg.0.log



**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0



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

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "dbe"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82945G/GZ Integrated Graphics Controll
er"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "DELL E197FP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82945G/GZ Integrated Graphics Controll
er"
        Monitor         "DELL E197FP"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x
400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x
400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x
400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x
400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x
400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x
400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by d90 on 2007-08-26
> **Drakonim said:**
> FYI:
This seems to be a problem with the OpenGL libraries in some way, (or in the way I'm loading them)

If you can get beryl to "pass" on everything except for:

***Checking for non power of two texture support : failed***

try this command inside an XGL session:

*LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl*

wobbly windows ahoy!

[well, it worked for me anyway ;-)]

I guess I'll head into /usr/lib and start mucking about with my libGL* files again...


thanks bro. you rulez

---

