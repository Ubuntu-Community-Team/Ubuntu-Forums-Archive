---
title: "Nightmares On Nvidia Quadro FX370 wouldnt Install drivers"
date: 2009-03-01
forum: Multimedia Software
---

### Post by Blk_Knight on 2009-03-01
Is anyone out there going through the madness I'm going through or have gone through a similar experience, cause I've just about had it!

I run an Athlon AMD 64 X2 Dual Core Processor 3600+ which came with an onboard Nvidia Geforce 650 Le video card. I wanted to run the 3D application but first I had to get my video card installed because my Ubuntu 8.04 would not recognize my video card and when I  tried putting it in use through system admin hardware and rebooted it wouldn't boot up. It forced me into an 800x600 resolution. So I went to the Nvidia site to get the drivers for it and it told me to repeat my prior hardware installation and run sh NVIDIA-Linux-x86_64-180.29-pkg2.run  from the directory where I downloaded it that did not change the result... I got a message stating:

ERROR: this .run file is intended for the
Linux-x86_64 platform, but you appear to be
running on Linux-x86.  Aborting installation.

At this time I got frustrated and posted a note in this forum. Someone suggested I get the 8.10 version because the driver allegedly thought I was running a 32 bit linux and not a 64 bit. So I did and tried it again nothing changed. My boot up loader sucks at this point I hate the fact that I'm now scrolling down so many linux version to get to the image that I am, and should be using, setting up this thingy has taken up my second weekend and I decided that this sunday I must put an end to it! 

So I thought well, I'll cough out the dough and go out and buy another video card that said anything linux on the box, which turned out to be an adventure on its own... I ended up with another Nvidia from frys an Nvidia Quadro Fx370 because on the case it said it supported windows XP, Vista and or Linux. I thought great for $149.00 maybe my problems would finally come to an end... I get home install the hardware try to load the drivers from CD just to find out there was no specific Nvidia driver for linux on the disk. So again I go to the Nvidia site and its got the very same driver it recommended I download earlier while I was dingly with the Nvidia 650 Le onboard card, NVIDIA-Linux-x86_64-180.29-pkg2.run it was still on my system so I did it agaiiin, and for the life of me I couldn't believe what happened, first I got a blank screen on several occasions and when I forced myself through the sea of darkness, I ended up with the same 800x600 resolution. 

When I look at my etc/X11/xorg file now it looks like this:

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option	"AddARGBGLXVisuals"	"True"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
=======================================================

The irony is that it doesn't even recognize my Dell Monitor.. Huh!
now this is the xorg file that ends in .conf I have about 15 of these xorg files going from the .conf to .conf0 all the way to .conf7 several .conf_backup, .conf_distribution upgrade, and failsafes and I have a feeling the more I keep trying the more crazy .confcrazies its just going to keep creating...

when I look at my /var/log/Xorg.0.log file I get this:

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux the1eon 2.6.20-17-generic #2 SMP Wed Aug 20 16:47:34 UTC 2008 i68
6
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar  1 21:07:21 2009
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
============================================================

Now so aparrently its loading the xorg.conf.failsafe whenever I try to force my way through by installing the Nvidia graphics card through the System-Hardware where it actually shows my Nvidia cards. (Actually two version a 173 version and a recommended 177 version) I tried the recomended version, and got the black screen tried the other version and it wouldn't boot it just force me into the failsafe .conf which is where I'm running now with an 800x600 res. 

I was hoping to install the video card driver so that I can take advantage of my 3d capabilities on them but this is proving to be far more than I expected! When I run a glxinfo command I get this:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
2 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault
=================================================

I have read multiply links of other peoples problems, checked multiple times on google for solutions, my hope is fading faster than I can stay awake... One of the people I met in Frys strongly recommended going with Slackware or Gentoo but I thought Id give Ubuntu one last try: can anybody out there help me with a solution to this crisis... Is it impossible to install a 3d nvidia graphic card to any of the Ubuntu versions out there... What's going on!!!

---

