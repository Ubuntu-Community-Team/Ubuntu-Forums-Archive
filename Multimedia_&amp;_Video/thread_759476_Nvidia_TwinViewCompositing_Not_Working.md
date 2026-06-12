---
title: "Nvidia TwinView/Compositing Not Working"
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by HyperHacker on 2008-04-19
[edit] (title was: Neither of my video cards work!) Got the Nvidia working; see below.

I've tried to install Xubuntu with two different graphic cards now and neither work. I have 2 LCD monitors, 1680x1050 DVI on the left and 1280x1024 VGA on the right.

First I tried with my ATI Radeon 9550. It installed fine but I could only do 1280x1024 (same image on both screens) with no hardware acceleration and no 3D. I tried both the proprietary ATI driver and fglrx, and managed a few different result, all without hardware acceleration:
1) Both screens working, but no way to move windows from the screen they appeared on.
2) Both screens working, but much graphic corruption. The mouse cursor would become a large (maybe 100x100px) square of random pixels from the left screen when on the right, terminal windows on the right would draw on both screens, and windows would randomly be drawn with the contents of other windows, even ones that had been closed.
3) Same as 2 but using software rendering for the cursor which left crud all over the screen.

After fiddling with it for about 12 hours I gave up and bought an Nvidia Geforce 6200 OC, and it's even worse. It booted up in "low graphics mode" with the Vesa driver. I switched it to the nv driver and rebooted. With the nv driver the left screen shows a bunch of garbage and the right shows an out-of-range error. Even the terminal is corrupted garbage. Everything still responds but I can't see f-all. I had to revert to the vesa driver in recovery mode.

I did "sudo apt-get install nvidia-glx" and got this:
> Reading package lists...
Building dependency tree...
Reading state information...
Suggested packages:
  nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/4493kB of archives.
After unpacking, 13.7MB of additional disk space will be used.
(Reading database ... 90814 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1%3a1.0.9639+2.6.22.4-14.10_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.10_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.10_i386.deb


Even the live CD doesn't boot on this card. It's even crazier, instead of a screen full of garbage, it's two screens full of animated moving randomly cycling garbage like something out of a movie.

I'd really like to get one of these cards working, preferrably the ATI so I can return the new card (moving to a free OS shouldn't cost $120 <_<). Naturally this all works fine in Windows, so nothing wrong with the hardware. With the popularity of these brands I would really hope at least *one* of them has decent support and works well; I really would have expected both to work out of the box.

---

### Post by ryanhaigh on 2008-04-19
You are having issues with installing the nvidia-glx driver (by the way I think you should be using nvidia-glx-new, check restricted-driver-manager in system>admin and see what it recommends) because there are files left from the ati fglrx driver. Doing the following MAY remove the files (can't remember from when I replaced my ati card with the nvidia)
```
sudo apt-get remove --purge xorg-driver-flgrx
```

Then reinstall the nvidia driver.

If that doesn't work you might try removing the files mentioned manually using
```
sudo rm /usr/lib/libGL.so.1
sudo rm /usr/lib/flgrx/libGL.so1.xlibmesa
```

I would have to recommend sticking with nvidia for your graphics card ati driver support is just not as good under linux. I would however still return your card if it cost you $120, 6200 cards are ~$55 AUD here, so unless your really need your dualscreens right now I would say return the card, use a single display with your ati card for the moment and get another card somewhere cheaper/online.

---

### Post by HyperHacker on 2008-04-20
Nope.
```
$ sudo apt-get remove --purge xorg-driver-flgrx
Package xorg-driver-fglrx is not installed, so not removed
```
I removed the files manually but I still get the error. Even stranger is it's complaining about /usr/lib/fglrx/libGL.so[COLOR="Red"].1[/COLOR].xlibmesa - which doesn't exist - rather than /usr/lib/fglrx/libGL.so[COLOR="Red"]1[/COLOR].xlibmesa which I removed like you said. I tried purging and reinstalling xorg-xserver, no difference.

---

### Post by HyperHacker on 2008-04-21
Well I gave up and formatted and reinstalled, I guess the ATI drivers broke something. It's working now, but I can't get TwinView to work. I have two monitors:
Left: 1680x1050 LCD connected to DVI
Right: 1280x1024 LCD connected to VGA
If I try to set them up through Screens and Graphics, no matter what I select, I end up with the left screen showing the right half, and both at 1280x1024. So far I've managed this by editing xorg.conf (and nvidia-xconfig, which seemed to just reorder things and blindly overwrite my backup copy :rolleyes: ):
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007

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
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Composite" "Disable"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
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
    Identifier     "Generic Monitor"
    HorizSync       31.0 - 92.0
    VertRefresh     55.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"

#	Boardname	"nv"
    Identifier     "GeForce 6200 OC"
    Driver         "nvidia"
EndSection

Section "Screen"
 #     
    Identifier     "Default Screen"
    Device         "GeForce 6200 OC"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TwinView" "true"
    Option         "MetaModes" "1680x1050 , 1280x1024 ;"
    Option         "TwinViewOrientation" "rightof"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050@75" "1920x1200@60" "1680x1050@60" "1600x1024@60" "1440x900@60" "1440x900@75" "1280x800@60" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
    EndSubSection
EndSection


```With this I have only the left monitor, at 1280x1024. Just about any change I try to make makes it revert to the Vesa driver, "low graphics mode", all that fun stuff.

[edit: compositing is actually on and working, even though that *Option         "Composite" "Disable"* line is there. O_o Now if it continues working with the other monitor enabled...]

---

### Post by ryanhaigh on 2008-04-21
I use nvidia-settings to configure my displays (I have the same setup as you), you will need to run it with admin privilliges to save to xorg.conf so press alt-f2 to bring up the run dialog and then enter gksudo nvidia-settings, enter your password, configure your monitors, click apply to test, and save to xorg.conf when your happy.

---

### Post by HyperHacker on 2008-04-21
My God, it works! Thanks a lot!

It's not quite perfect though; when I maximize a window, it stretches across both screens (as do the panels). Can that be prevented? It's kind of a problem with the panel since I have dead space at the bottom of the right screen (1050 vs 1024 height) so some of the panel is unreachable. Also in Windows, I had the taskbar at the right side of the left screen, which worked very well. (Windows would simply be dragged right under it, but maximized ones wouldn't occupy the same space.) With this setup there doesn't seem to be a way to do that. I guess I could get used to having it on the left but if there's a way to put it on the right that would be totally awesome. :D (These panels don't work very well vertical, but I hope to figure a way to fix that. Anyone who still uses Windows, I highly recommend a vertical taskbar, it really rocks.)

Heh, even the password prompt from gksudo pops up in the middle of the workspace rather than the middle of the screen. I guess the way to fix that would be to use separate X screens instead of TwinView, but then how do I move windows between them?

---

### Post by ryanhaigh on 2008-04-21
I have heard people having the same issue but it never did that for me using twinview, the panels were always on the left screen. I remember something about metamodes being a possible fix. Have you restarted X since you saved the changes? I can't find the thread where I had discussed this with others but you might have more luck, it may even have been on someones blog.

I have attatched my dualscreen xorg.conf, I haven't looked at it for a while so it may be messy after using nvidia-settings more than a few times. Hope it helps.

edit: found it, although the person in question just went back to xinerama

---

### Post by HyperHacker on 2008-04-21
Well I played with the settings some more, tried the separate X screens and sure enough that made it so I couldn't move windows between screens. Unfortunately it also did something strange, now it's convinced the right monitor is the "main" screen rather than the left one, so things like the login screen show up on it. This actually seems to be a good thing as Xfce now sees two monitors, so the maximize/password prompt/panel issues no longer appear (I can choose which monitor for the panels, etc) and I can still drag between monitors normally.

It's working quite nicely this way (though I have yet to try anything 3D, so no idea how performance is really), but these panels really do not like being vertical. I have one at the right like I did in Windows now, but maximized windows go right under it and it overlaps the one at the top. >_< That seems to be the only glitch though.

I'll post my xorg.conf in case anyone else is trying to do this, but unless I find 3D isn't working or something, I'd say this is fine besides the vertical panels. Only glitch is when asked to choose a monitor for something to display on, the buttons are backward from how the screens are arranged, but oh well.

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007
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
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Composite" "Disable"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
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
    Identifier     "Generic Monitor"
    HorizSync       31.0 - 92.0
    VertRefresh     55.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEC 90GX2"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LG L226WA"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"

#	Boardname	"nv"
    Identifier     "GeForce 6200 OC"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

 #     
    Identifier     "Default Screen"
    Device         "GeForce 6200 OC"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TwinView" "true"
    Option         "MetaModes" "1680x1050 , 1280x1024 ;"
    Option         "TwinViewOrientation" "rightof"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050@75" "1920x1200@60" "1680x1050@60" "1600x1024@60" "1440x900@60" "1440x900@75" "1280x800@60" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: 1280x1024 +1680+0, DFP: 1680x1050 +0+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT: 1280x1024 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1280x1024 +1680+0, DFP: 1680x1050 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1680x1050 +0+0"
EndSection


```
I could probably tweak it to make the left screen be #0 again, but I need to go to bed, and knowing me that seemingly simple task will take all damn night. :p

[edit] I just stuck a 3D program running under WINE between the two monitors and turned it translucent and it ran with only a slight performance loss. Putting it entirely on one monitor it runs full speed. I'd say it works. :D

...Or not, the screen savers aren't working. :( In preview, they only cover one monitor, and sitting idle, they just don't start at all, nothing happens.

---

