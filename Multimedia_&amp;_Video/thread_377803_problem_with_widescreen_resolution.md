---
title: "problem with widescreen resolution"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by vbdanl on 2007-03-06
Hi. I have a emachine with replaced motherboard.  [mobo]("http://www.biostar-usa.com/mbdetails.asp?model=p4m80-m4") is P4M800.  on board graphics are VIA Technology S3 Unichrome Pro.  I am trying to get new 19" Proview PL926wbi monitor to use 1440x900 resolution.
I have tried installing this [http://www.viaarena.com/default.aspx?PageID=420&OSID=44&CatID=3200&SubCatID=150](http://www.viaarena.com/default.aspx?PageID=420&OSID=44&CatID=3200&SubCatID=150) driver, but still don't get display option for 1440x900 resolution.  I have added it and others to the xorg.conf file.  
I get frequent lockups since changing to this new driver (uses via instead of vesa) in xorg.conf.
The screen basically looks like a regular 17" monitor stretched out to fit on a 19" widescreen, which basically sucks.  The fonts are harder to read and images worse than with old 17".
I see lots of posts for nvidea cards, but I don't have one.  I was wondering if anyone has been able to get a widescreen to display correctly using on board video setup?  and if so, what does your xorg.conf look like, and what drivers did you install?  thanks.

---

### Post by punx45 on 2007-03-06
I have the same VIA chipset on my computer running myth on Fedora 5 on which I have a 22" widescreen display.  in this case I selected to install the driver during install.   

here are the pertinent sections from my xorg.conf

```
Section "Monitor"

 ### Comment all HorizSync and VertSync values to use DDC:
 ### Comment all HorizSync and VertSync values to use DDC:
 ### Comment all HorizSync and VertSync values to use DDC:
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "VG2230wm"
        DisplaySize  470        300
 ### Comment all HorizSync and VertSync values to use DDC:
        HorizSync    30.0 - 82.0
        VertRefresh  50.0 - 75.0
        Option      "dpms"
EndSection

Section "Device"
        Identifier  "Videocard0"
        Driver      "via"
        VendorName  "Videocard vendor"
        BoardName   "VIA Technologies, Inc. Unknown device 3344"
EndSection

Section "Device"
        Identifier  "Videocard0"
        Driver      "via"
        VendorName  "Videocard vendor"
        BoardName   "VIA Technologies, Inc. Unknown device 3344"
EndSection


Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes    "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1680x1050" "1280x800"
        EndSubSection
EndSection

Section "DRI"
        Group        0
        Mode         0666
EndSection

```

if you were having trouble installing the driver, there appears to be a VIA package available through aptitude.   here is the info for that too.

it isnt installed by default so you might have to install it with ```
sudo apt-get install <packagename>
```

```
geoff@toaster:~$ aptitude show xserver-xorg-driver-via
Package: xserver-xorg-driver-via
State: installed
Automatically installed: no
Version: 1:0.1.33.2-0ubuntu4
Priority: optional
Section: x11
Maintainer: Daniel Stone <daniel.stone@ubuntu.com>
Uncompressed Size: 389k
Depends: libc6 (>= 2.3.4-1), libdrm2, xserver-xorg-core (>= 1:0.99.0-1)
Replaces: xserver-xorg (< 6.8.2-35)
Provides: xserver-xorg-driver
Description: X.Org X server -- VIA display driver
 This driver for the X.Org X server (see xserver-xorg for a further description)
 provides support for VIA/S3 CLE266/KM400/K8M800/UniChrome cards, which are
 frequently found in low-form-factor VIA motherboards, and in some laptops.

 This driver also contains support for XvMC, the XVideo Motion Compensation
 extension.  XvMC modules are provided in /usr/lib.

 More information about X.Org can be found at: <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>

 This module can be found as the module 'driver/xf86-video-via' at
 :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg

```

and of course, after installing drivers or changing xorg.conf you will need to restart X either with 'CTRL+ALT+Backspace'

or by switching to a fullscreen terminal with 'Alt+F1'   login, type 'sudo /etc/init.d/gdm restart' and then go back to gnome by 'Alt+F7'

---

