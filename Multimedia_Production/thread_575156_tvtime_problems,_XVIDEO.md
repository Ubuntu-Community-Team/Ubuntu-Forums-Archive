---
title: "tvtime problems, XVIDEO"
date: 2007-10-13
forum: Multimedia Production
---

### Post by wiscados on 2007-10-13
I have used tvtime on the same computer, with the same TV-tuner card and same version of Ubuntu. But after a reinstall I did some time ago, it doesn't work. I have tried to fix it, but I have not been able to do it.

output of 'tvtime -v'
```
$ tvtime -v
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/wiscados/.tvtime/tvtime.xml
cpuinfo: CPU Intel(R) Pentium(R) 4 CPU 2.80GHz, family 15, model 2, stepping 9.
cpuinfo: CPU measured at 2799.738MHz.
tvtime: Cannot set priority to -10: Permission denied.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 70200000
xfullscreen: Single-head detected, pixel aspect will be calculated.
xfullscreen: Pixel aspect ratio on the primary head is: 453/464 == 0.98.
xfullscreen: Using the XFree86-VidModeExtension to calculate fullscreen size.
xfullscreen: Fullscreen to 0,0 with size 1024x768.
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
**xvoutput: No XVIDEO port found which supports YUY2 images.**

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

```

I noticed it said permission denied on the 7th line, so I tried running it with 'sudo' but it's pretty much the same:
```
$ sudo tvtime -v
Password:
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/wiscados/.tvtime/tvtime.xml
cpuinfo: CPU Intel(R) Pentium(R) 4 CPU 2.80GHz, family 15, model 2, stepping 9.
cpuinfo: CPU measured at 2799.690MHz.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 70200000
xfullscreen: Single-head detected, pixel aspect will be calculated.
xfullscreen: Pixel aspect ratio on the primary head is: 453/464 == 0.98.
xfullscreen: Using the XFree86-VidModeExtension to calculate fullscreen size.
xfullscreen: Fullscreen to 0,0 with size 1024x768.
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
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

```

---

### Post by Jaxilian on 2008-06-10
I got same issues

---

### Post by Jaxilian on 2008-06-24
bump

---

