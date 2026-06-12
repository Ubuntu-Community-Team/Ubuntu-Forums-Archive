---
title: "gnome-control-center displays says laptop for single desktop monitor"
date: 2013-06-08
forum: Multimedia Software
---

### Post by genterminl on 2013-06-08
I just upgraded to 12.04, and then switched to a newer, higher resolution monitor.  In trying to install a color profile for it, I noticed that the Displays section of gnome-control-panel identifies the monitor as "laptop" with no apparent way to change it.  So far, all the similar posts and bugs I have found were related to using fglrx and dual monitors.  (I don't know if it really affects anything else, but it's certainly disconcerting.)

My video is an on-board SiS 730S, using the sis driver, with the sisfb kernel module installed.  The montor is a Hyundai X224W.

Actually, I have two problems, and I don't know if they are related or not.  The xorg driver seems to see the DDC and EDID information from the monitor correctly, but then throws out all the higher resolution modelines, such as "SIS(0): Not using driver mode "1680x1050" (bad mode clock/interlace/doublescan)".  I can get 1280x1024, but nothing higher, even though I know the monitor can do 1680x1050, and I'm pretty sure the driver can also, especially since there is no second output.  (I found a page on the sis driver which implies some resolutions may not be available even for the primary monitor, depending on the configuration of the secondary output.)
[EDIT:  Rereading [http://www.winischhofer.net/linuxsispart1.shtml#notbabble](http://www.winischhofer.net/linuxsispart1.shtml#notbabble) shows that the higher resolutions are NOT available.  The card can do SOME higher resolutions, but no wide ones that this monitor is capable of, so I'll probably have to find another video card.]

In addition, I had a great deal of trouble in the Color section of g-c-c to import a color profile for the monitor.  Originally, that screen only showed one printer profile.  However, lots of attempts finally got it to show "Unknown Chassis Manufacture - default" for the monitor, and it imported the color profile.   "default" also happens to be the name of the monitor shown by xrandr.

Any suggestions regarding why "laptop" shows up or how to get full resolution would be appreciated.  Even pointers as to which "fine manual" to read.

---

