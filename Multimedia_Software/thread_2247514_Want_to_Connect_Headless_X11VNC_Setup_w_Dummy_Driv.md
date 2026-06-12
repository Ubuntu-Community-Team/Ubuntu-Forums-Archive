---
title: "Want to Connect Headless X11VNC Setup w/ Dummy Driver to HDMI Monitor"
date: 2014-10-08
forum: Multimedia Software
---

### Post by ben115 on 2014-10-08
I have an i5 system running Ubuntu 12.04lts 32bit OS that I'm using as a headless x11vnc server and I want to be able to have the option of connecting to an HDMI monitor as well.

It uses the xserver-xorg-video-dummy driver and I created an upstart job so X11vnc starts before I login to the system.

When I try to connect to it with an HDMI monitor, I have no success.  If I trying booting up with the HDMI monitor plugged in, I'm connected at boot and can see the system post, but the HDMI connection kicks out right before the login screen appears, which is right around the time x11vnc starts up.  And when I try to connect to the HDMI monitor after I've logged in via x11vnc, I can't connect to it at all.

Here is my /etc/X11/xorg.conf file:
```
Section "Device"    Identifier  "Configured Video Device"
    Driver      "dummy"
    VideoRam 10000
EndSection


Section "Monitor"
    Identifier  "Configured Monitor"
    HorizSync 5.0 - 1000.0
    VertRefresh 5.0 - 200.0
#    Modeline "1280x800" 24.15 1280 1312 1400 1432 800 819 822 841
    Modeline "1280x800" 83.46 1280 1344 1480 1680 800 801 804 828
EndSection


Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    DefaultDepth 24
    SubSection "Display"
    Depth 24
    Modes "1280x800"
#    Virtual 1680 1050
    EndSubSection
EndSection
```

Any ideas would be greatly appreciated.

Thanks

---

