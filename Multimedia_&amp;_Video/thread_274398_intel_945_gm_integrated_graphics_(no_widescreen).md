---
title: "intel 945 gm integrated graphics (no widescreen)"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by ncab23 on 2006-10-09
I just installed ubuntu, and everything is running smoothly, but I cannot figure out how to up to resolution to widescreen. Currently it is set at 1024x768, and that is the highest one available to me. I have seen other posts about the intel 915, but nothing for my situation. Any help is appreciated. Thanks.

---

### Post by az on 2006-10-09
You need a tool called 915 resolution.

andy@andy-desktop:~$ apt-cache show 915resolution
Package: 915resolution
Priority: extra
Section: universe/x11
Installed-Size: 124
Maintainer: Steffen Joeris <steffen.joeris@skolelinux.de>
Architecture: i386
Version: 0.5-1ubuntu6
Replaces: 855resolution
Provides: 855resolution
Depends: libc6 (>= 2.3.4-1)
Recommends: vbetool (>= 0.6-1)
Conflicts: 855resolution
Filename: pool/universe/9/915resolution/915resolution_0.5-1ubuntu6_i386.deb
Size: 14268
MD5sum: f4904f186f5698460983b9d401fc2c6e
Description: resolution modify tool for Intel graphic chipset
 915resolution is a tool to modify the video BIOS of the 800
 and 900 series Intel graphics chipsets. This includes the 845G,
 855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
 This modification is necessary to allow the display of certain
 graphics resolutions for an Xorg or XFree86 graphics server.
 .
 915resolution's modifications of the BIOS are transient.
 There is no risk of permanent modification of the BIOS.
 This also means that 915resolution must be run every time the
 computer boots inorder for it's changes to take effect.
 If you want to automatically set the resolution on each boot
 and before X is launched, see /usr/share/doc/915resolution/README.Debian
 for information about configuring the provided initscript.
 .
 Web site: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu




I beleive that this is a limitation in the intel graphic chipset.  I don't think it is able to autodetect your non-standard resolution and so you must do it "by hand"

Installing that package and reading the documentation should not be terribly hard.  Basically, you tell it that one of the preset resolutions is your desired resolution and then switch to it.  You then make it do that every time you boot.  It is a few minutes of extra work on the command line.

---

### Post by ncab23 on 2006-10-09
So i got 915resolution, and am following the readme, but as i try to view the video modes through the bios list, I get the following message:

"
Intel 800/900 Series VBIOS Hack : version 0.5.2

Unable to obtain the proper IO permissions: Operation not permitted
"

Is there any way around this?

---

### Post by az on 2006-10-09
> **ncab23 said:**
> So i got 915resolution, and am following the readme, but as i try to view the video modes through the bios list, I get the following message:

"
Intel 800/900 Series VBIOS Hack : version 0.5.2

Unable to obtain the proper IO permissions: Operation not permitted
"

Is there any way around this?

Are you using sudo?

---

### Post by ncab23 on 2006-10-09
no i wasnt, stupid mistake, thanks for all your help its working fine now

---

### Post by JarkkoN on 2006-10-13
Thanks for the advice. I also installed the 915resolution, modified the /etc/default/915resolution to 1280x800, and executed /etc/init.d/915resolution start. However, there is no change in the resolution. The patch confirms the change when executed and also in booting. The screen stays 1028x768, even if the 945G chipset is there and the 3022WTMi laptop screen could do 1280x800. Did I miss something?

---

### Post by JarkkoN on 2006-10-13
The file /etc/X11/xorg.conf defines the "Intel Corporation Mobile Graphics Controller" and i810 driver. The SubSection for Display includes only the resolutions (1280x800 and 1600x1200). Still no change to the resolution on display, which stays in 1024x768. 

What next? How to get higher resolution?

---

### Post by garethc on 2006-12-16
If you're like me, you'll never work out how to get a 1280x800 resolution. And I researched the problem to death & tried everything. That was 2 months ago: no one was able to help me and I gave up on Ubuntu until its next release because of this problem. Hopefully things have, uh, progressed and I hope you find a way -- if you do, let me know how you did it! [email]formless.form@gmail.com[/email]

Dell Inspiron 6400 / Intel 945GM chipset / GMA950 integrated graphics

---

### Post by wait- on 2006-12-28
I don't know how much this will help, I'm much in the same boat as you are, but I *did* notice that changing the following section in my xorg.conf file by commenting out all the resolutions in my xorg.conf file seemed to allow the screen resolution switcher to do some of it's own analysis and added some options to the System->Preferences->Screen Resolution dialog

 ```

	SubSection "Display"
		Depth		24
		Modes		**#**"1024x768" "800x600" "640x480"
	EndSubSection

```
Of course always back up your xorg.conf file before making changes just in case 

Hope that helps

---

### Post by CalvinChile on 2006-12-28
Hi,

I have also an Inspiron6400 with i945 running Edgy.  For me the resolution 1280x800 is working fine. I include here some of the setup files.

more 915resolution
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=5c
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1280
YRESO=800
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32
======================
sudo 915resolution -l
Password:
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 32 bits/pixel

=================
xorg.conf

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
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  FontPath "/usr/share/fonts/X11/misc"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "dri"
  load "v4l"
  load "dbe"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
  option "XkbOptions" "lv3:ralt_switch"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
  option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  option "SendCoreEvents" "true"
  option "Device" "/dev/psaux"
  option "Protocol" "auto-dev"
  option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/wacom"# Change to
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/wacom"# Change to
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/wacom"# Change to
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "Device"
  identifier "Intel Corporation Mobile Integrated Graphics Controller"
  boardname "Intel 915"
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
  vendorname "Intel"
  Option  "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Dell"
  modelname "Dell 1505FP (Digital)"
  HorizSync 30.0-61.0
  VertRefresh 56.0-76.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Intel Corporation Mobile Integrated Graphics Controller"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1440 900
    modes "1440x900@60" "1280x800@60" "1280x768@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "device" #
  identifier "device1"
  boardname "Intel 915"
  busid "PCI:0:2:0"
  driver "i810"
  screen 1
  vendorname "Intel"
EndSection
Section "screen" #
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
  SubSection "Display"
    depth 24
    modes "640x480@60"
  EndSubSection
EndSection
Section "monitor" #
  identifier "monitor1"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by joel_gil on 2007-01-14
hello all.
 I do have been able to install 915res. and got the ideal 1280x800 working (this as well on an Inspiron 6400 i945 video). problem is, that every time I restart the configuration goes back to 1024x768.
](*,) 
For all who haven't even been able to configure it to 1280x800 follow the instructions from this site: [http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/](http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/) the instructions are quite easy and simple to follow.  At that site they also say how to save the config each boot, but i dont get it to work.

So in few words what i need it someone to tell me how to save the configuration each time i boot. Which file is it that i have to modify, etc.

This is kinda anoyin for all hehe, it would b easier with windows.

---

### Post by joseff on 2007-01-15
joel, I have the EXACT same problem.  

I have a 2-year old Acer with intel 855.  On every restart the screen goes back to 1024x768.  I tried logging in and doing 915resolution -l and the 1280x800 mode is there.  Same with the xorg.conf.  But it simply is *not* in the System->Preferences->Screen resolution

However, if I Ctrl-Alt-Backspace, the gdm login screen will come up in 1280x800.  Eh?  Do I really have to Ctrl-Alt-Backspace everytime the computer restarts? ](*,) 

In dapper I never even touched the /etc/default/915resolution config file.  I simply installed 915resolution and ta-da, it went to 1280x800 automagically.  Could this be an issue with Upstart?

My sorta fix this time around is to simply suspend the computer instead of shutting down.  Dapper couldn't put my computer to sleep but Edgy sleep works like a charm.

---

### Post by joel_gil on 2007-01-15
actually this is the 2nd time i intall ubuntu, but the 1st on my own.

Last time i was with a guy who knew pretty well how to get atoun linux, and fixed the problem by editin a boot file, but i have lost contact with this person and cant remember which file was it.

So i am certain theres a way to fix it, i just dont know how to :-?

---

### Post by joseff on 2007-01-16
I've tried deleting all modes from xorg.conf, leaving only 1280x800 and the computer STILL starts at 1024x768.

The only way to switch to 1280x800 is to restart gdm, either by Ctrl-Alt-Bksp or /etc/init.d/gdm restart.  It seems gdm simply disregards the x settings?  I'm not familiar with it at all.  Where else do I need to look?  gdm.conf?  gdm.conf-custom?

Any help?  Pretty please?

---

### Post by joseff on 2007-01-16
WOOOHOOOO I did it!

This works ONLY if you're in a situation like myself: you can switch to widescreen after restarting gdm, but on reboot the display reverts to 1024x768.  Therefore: you MUST have widescreen running first.  Read the tutorials on this.

DISCLAIMER: THIS MAY SERIOUSLY SCREW YOUR SYSTEM!!! FOLLOW AT YOUR OWN RISK!!!

Now that aside, have a look at the /etc/rc5.d/ directory, you have:
```
S13gdm
S20915resolution
```

Which means that gdm is started before 915resolution.  We'll have to change that.  First remove the symlinks to 915resolution from runlevels 2,3,4,5
```
sudo update-rc.d -f 915resolution remove
```

Then we'll move up 915resolution to... say, 12.
```
sudo update-rc.d 915resolution defaults 12
```

You should have widescreen on your next reboot. :)

---

### Post by joel_gil on 2007-01-16
i want to try it... but the 'this will screw up ur sytem' is kidna holdin me back.... hehe


could u tell me whats up with that? :-?

---

### Post by joseff on 2007-01-16
Just my standard disclaimer... maybe it should read a less scary "Your mileage may vary, if you mess up your laptop it's not my fault" :D

if for some reason something goes totally wrong, just remove the 915resolution symlinks from init:

```
sudo update-rc.d -f 915resolution remove
```

and you'll be back in square one, no harm done.

Same disclaimer applies here: YMMV, MESS UP YOUR LAPTOP AT YOUR OWN RISK!

---

### Post by joel_gil on 2007-01-17
there is no 'S20915resolution' in any of my rc.d folders =S

dammit!!! i dont want to spend 2 years doin ctrl.alt.bs!!!  >_<

---

### Post by joel_gil on 2007-01-17
I GOT IT FINALLY!!!!
But not hoe joseff said it.

well lets start by the beginnin... i follow ALL the steps in here: [http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/](http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/) 

(read it so u can understand what am i talkin about next.)

but for some reason my etc/init.d/bootmisc.sh was different from the normal so thats why i didnt got it to work before, but at the end of the comments i mentioned my problem and this is how the end of the bootmisc.sh should look like in any ubuntu:

----------------------------------------------
 echo "Usage: $0 start|stop" >&2
exit 3
;;
esac
/usr/sbin/915resolution 5a 1680 1050 32
: exit 0
-----------------------------------------------
(well in dell inspiron 6400 is was '915resolution 54 1280 800', but it goes accordin on how u configured de 915res...)

and thats it! no messin with the xorg.conf or rc.d folders, nothin, just one simple line before the 'exit' on bootmisc.sh so no 'under ur own risk' hehehe 

GOOD LUCK EVERYONE:p 

btw, i had this problem specifically cus my bootmisc.sh had been modyfied before, turns out that for everyone else they just follow step by step on the link above and that was it. so the solution is there for sure ;)

---

### Post by joseff on 2007-01-17
Basically both methods make sure 915resolution gets executed before gdm.  Congrats joel.

About the S20915resolution, I got it because I installed 915resolution from the deb available from the geocities page.  If you install the ubuntu version maybe you get another number instead of 20 in S##915resolution.

---

