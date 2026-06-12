---
title: "ATI Radeon &amp; Dual-Head"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kiz64 on 2010-09-08
Under 10.04, I had a relatively nice desktop that span two monitors, using the fglrx driver and an aticonfig configured xorg.conf

Having upgraded the system (Intel Core2 cpu; 3G Ram; ATI Radeon  HD 2400 graphics card; 200G HDD) to 10.10, I'm having major issues with X

I have the following display packages installed:
xserver-xorg-video-ati 1:6.13.1.1ubuntu5
xserver-xorg-video-radeon 1:6.13.1.1ubuntu5
fglrx 2:8.723.1-0ubuntu4
xorg-driver-fglrx 2:8.723.1-0ubuntu4

If I boot with the 2.6.35-20-generic kernel, the system tries to launch X, but segfaults & drops back to a console.
If I boot with the 2.6.32-24-generic kernel, I can get X, but dual-head is eluding me.

The best I have managed is with the xorg.conf below, which gives me two desktops... but no way to get to the second display!

```
Section "ServerLayout"
    Identifier     "X.org Configured"
        Screen  "screen0"
        Screen  "screen1" RightOf "screen0"
#        Option "Xinerama"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
  # All modules load automatically
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      380   300    # mm
    Identifier   "Monitor0"
    VendorName   "DELL"
    ModelName    "DELL 1908FP"
    HorizSync    31.0 - 83.0
    VertRefresh  56.0 - 76.0
    Option        "DPMS"
EndSection
Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "BEN-Q"
    Option        "DPMS" "true"
EndSection

Section "Device"
        Option     "SWcursor" "true"              # [<bool>]
    Identifier  "Card0"
    Driver      "radeon"
    BusID       "PCI:1:0:0"
        Screen      0
EndSection

Section "Device"
        Option     "SWcursor" "true"              # [<bool>]
    Identifier  "Card1"
    Driver      "radeon"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```This, however, produces a couple of errors (full log file at [http://lucas.ucs.ed.ac.uk/Xorg.0.log]("http://http://lucas.ucs.ed.ac.uk/Xorg.0.log")) :
```

[    36.229] (==) ServerLayout "X.org Configured"
[    36.229] (**) |-->Screen "Screen0" (0)
[    36.229] (**) |   |-->Monitor "Monitor0"
[    36.229] (**) |   |-->Device "Card0"
[    36.229] (**) |-->Screen "Screen1" (1)
[    36.229] (**) |   |-->Monitor "Monitor1"
[    36.229] (**) |   |-->Device "Card1"
[    36.229] (EE) Screen screen0 doesn't exist: deleting placement

``````

[    36.457] (WW) RADEON(1): Direct Rendering Disabled -- Zaphod Dual-head confi
guration is not working with DRI at present.
Please use the xrandr 1.2 if you want Dual-head with DRI.

```Any suggestions how I can get dual-head going? (it doesn't need to be dri/accelerated/3d.... just more screen real-estate for programming in ;-) )

---

### Post by ranch hand on 2010-09-08
Your box sounds awfully similar to mine (see sig).  I have never really had much luck with fglrx.

Since 9.04 there has been a driver at the ATI site that does support the HD 2400 Pro.  Doesn't blow my skirt up but it does work, at least in 9.04.

I use the OSS drivers.  They work better in 2d than fglrx.

The drivers from xorg.edgers are even better.
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

I do not use dual monitors but I am sure that the OSS drivers will do it for  you.

---

### Post by meborc on 2010-09-08
there have been many threads on this.. like - [http://ubuntuforums.org/showthread.php?t=1561685](http://ubuntuforums.org/showthread.php?t=1561685)

the proprietary drivers are broken as they don't support the new version of x server that is in MM

if you really need closed-source, either go back to LL or wait until october-november (or whenever the ATI guys release a catalyst that supports the new x server)

As i understand, catalyst guys usually support/test their drivers on stable linux distro releases, so before 10.10 there really is little hope

---

### Post by kiz64 on 2010-09-08
> there have been many threads on this.. like - [http://ubuntuforums.org/showthread.php?t=1561685](http://ubuntuforums.org/showthread.php?t=1561685)

I saw that.... but it descended into an open verses closed drivers

> 
if you really need closed-source, either go back to LL or wait until october-november (or whenever the ATI guys release a catalyst that supports the new x server)

I don't.... I'd just like to get back to my 2560x1024 real-estate for coding :)

> As i understand, catalyst guys usually support/test their drivers on stable linux distro releases, so before 10.10 there really is little hope
Yah - I reckoned that the proprietary drivers would be in this state... 8-)

---

### Post by meborc on 2010-09-09
> **kiz64 said:**
> I saw that.... but it descended into an open verses closed drivers
...

sorry, the "using the fglrx driver" gave me the impression that you are trying to get it working on MM :)

---

