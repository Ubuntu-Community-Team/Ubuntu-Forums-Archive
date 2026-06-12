---
title: "Intel video driver"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by Fadsjeik on 2007-08-13
Hi

This weekend I tried the intel driver xserver-xorg-video-intel instead of xserver-xorg-video-i810 for my 915GM intel graphics card on my Dell laptop (D610). However I was not able to log in with my own username. The log in screen starts as usual, but when I try to login, X fails to start and I see a couple of flickering black screens that take me back the login screen after a couple of seconds. I looked around the ubuntu forums and found two possible remedies. One is obviously to uninstall the new driver and reinstall the old one (which is what I did in the end). The second was to add a new user. To my surprise I could login and start X with this new user! However I would like to use my old user profile with the new intel driver, because I spent a bunch of time setting up this profile. Does anyone know how to do this? It might be a long shot, but I noticed that the fonts at the login screen are different with the different drivers. From the ubuntu forums I found that more people have this problem.

Any help is greatly appreciated.

P.s. Does the intel driver allow for a bigger allocation of (shared) video memory. Currently 8mb is allocated to video memory, but I have 1Gb of memory, so I want to allocate a bigger portion of that to the video memory. I couldn't find any way to this (BIOS doesn't allow any tweaking and specifying the amount of video ram in xorg.conf doesn't work), so my hope was that the intel driver might do the trick. Is this the case, or is there an other way to increase the video ram with the i810 driver?

---

### Post by cwelch on 2007-08-20
How'd you un/reinstall the driver? I fouled mine up. Video works now, can log in, but desktop-effect and stuff don't work. Think that might be it. Thanks!

---

### Post by Fadsjeik on 2007-08-21
Hey,

re-installing can be done via the packet manager. Select xserver-xorg-video-i810, this will automatically deselect the intel driver. From the command line type

```
sudo apt-get install xserver-xorg-video-i810
```

This will also automatically uninstall the intel driver and install the i810 driver.

Good luck!

---

### Post by jordanmthomas on 2007-08-21
from the i810 manpage:
> By default 8 Megabytes of system memory are used for graphics. For the 830M and later, the default is 8 Megabytes when DRI is not enabled and 32 Megabytes with DRI is enabled. This amount may be changed with the VideoRam entry in the config file Device section. It may be set to any reasonable value up to 64MB for older chipsets or 128MB for newer chipets. It is advisable to check the XFree86 log file to check if any features have been disabled because of insufficient video memory. In particular, DRI support or tiling mode may be disabled with insufficient video memory. Either of these being disabled will reduce performance for 3D applications. Note however, that increasing this value too much will reduce the amount of system memory available for other applications.

So, you'd just open up your /etc/X11/xorg.conf, go to your graphics card section, and add a line like this in the proper Device section:
```
VideoRam 32768
```
(this would be 32 MB -- put it in kilobytes)

Here's my section from ArchLinux (I am using intel driver, but i810 should work...just use i810 instead of intel on the driver line)
```
Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "ColorKey"                  # <i>
        #Option     "CacheLines"                # <i>
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "DRI"                       # [<bool>]
        #Option     "NoDDC"                     # [<bool>]
        #Option     "ShowCache"                 # [<bool>]
        #Option     "XvMCSurfaces"              # <i>
        #Option     "PageFlip"                  # [<bool>]
        Identifier  "i915 card"
        [COLOR="Red"]VideoRAM  131072  #gives me 128 megs[/COLOR]
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "Mobile 915GM/GMS/910GML Express Graphics Controller"
        BusID       "PCI:0:2:0"
EndSection

```
(more options are listed, but I have them commented out and just use the defaults)


hope this helps some.

---

