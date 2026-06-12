---
title: "TV: Error tvtime and Hauppauge HVR1600"
date: 2010-06-07
forum: Multimedia Software
---

### Post by oregonbob on 2010-06-07
I would like to get a simple but complete tv viewer for Ubuntu 10.04 64bit, a Hauppauge HVR1600 or HDHomerun tuner (I have both). VLC works OK but I have to run another program to change channels and then restart VLC, which is a pain.

I am trying tvtime, but it just quits with the following error output and I wondered if anyone else got it working (or a similar program).

---------------------

# tvtime -v
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /root/.tvtime/tvtime.xml
cpuinfo: CPU AMD Phenom(tm) 9750 Quad-Core Processor, family 15, model 2, stepping 3.
cpuinfo: CPU measured at 2411.196MHz.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 10706000
xfullscreen: Using XINERAMA for dual-head information.
xfullscreen: Pixels are square.
xfullscreen: Number of displays is 1.
xfullscreen: Head 0 at 0,0 with size 1680x1050.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is Metacity and is EWMH compliant.
xcommon: You are using metacity.  Disabling aspect ratio hints
xcommon: since most deployed versions of metacity are still broken.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 286: NV17 Video Texture.
speedycode: Using MMXEXT optimized functions.
station: Adding frequency table us-broadcast, all channels active
videoinput: Using video4linux2 driver 'cx18', card 'Hauppauge HVR-1600' (bus PCI:0000:01:0a.0).
videoinput: Version is 66048, capabilities 1030051.
videoinput: Maximum input width: 720 pixels.
videoinput: Card failed to allocate capture buffers: Invalid argument
Segmentation fault
------------------------------
Any thoughts or another program to recommend? MythTV is overkill and not very good. It demands fullscreen, etc. I would just like to popup a window for viewing TV while working.

---

### Post by saedelaere on 2010-07-16
> **oregonbob said:**
> I would like to get a simple but complete tv viewer for Ubuntu 10.04 64bit, a Hauppauge HVR1600 or HDHomerun tuner (I have both). VLC works OK but I have to run another program to change channels and then restart VLC, which is a pain.

I am trying tvtime, but it just quits with the following error output and I wondered if anyone else got it working (or a similar program).

---------------------

# tvtime -v
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /root/.tvtime/tvtime.xml
cpuinfo: CPU AMD Phenom(tm) 9750 Quad-Core Processor, family 15, model 2, stepping 3.
cpuinfo: CPU measured at 2411.196MHz.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 10706000
xfullscreen: Using XINERAMA for dual-head information.
xfullscreen: Pixels are square.
xfullscreen: Number of displays is 1.
xfullscreen: Head 0 at 0,0 with size 1680x1050.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is Metacity and is EWMH compliant.
xcommon: You are using metacity.  Disabling aspect ratio hints
xcommon: since most deployed versions of metacity are still broken.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 286: NV17 Video Texture.
speedycode: Using MMXEXT optimized functions.
station: Adding frequency table us-broadcast, all channels active
videoinput: Using video4linux2 driver 'cx18', card 'Hauppauge HVR-1600' (bus PCI:0000:01:0a.0).
videoinput: Version is 66048, capabilities 1030051.
videoinput: Maximum input width: 720 pixels.
videoinput: Card failed to allocate capture buffers: Invalid argument
Segmentation fault
------------------------------
Any thoughts or another program to recommend? MythTV is overkill and not very good. It demands fullscreen, etc. I would just like to popup a window for viewing TV while working.

[TV-Viewer]("http://tv-viewer.sourceforge.net/") supports watching analog TV. If you get segfaults on Ubuntu 64bit when you try to start the application have a look at this [howto]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Howto#Replacing_included_Tcl.2FTk_packages_with_ActiveTcl")

Regards

---

