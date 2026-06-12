---
title: "Custom Modelines Screen Not Centred"
date: 2010-03-09
forum: Multimedia Software
---

### Post by kempy1000 on 2010-03-09
Hello,

I can not get my screen to center on the monitor. The only hint of a solution I can find is modelines. I have tried a few custom ones but none have moved the screen at all.

I am using the radeon driver on an ATI X1550.

Does anyone have any idea how I can move the image on the screen?

(My screen wont let me move and save the image using its built in controls and I think its edid is corrupt maybe? xvidtune wont run and get-edid fails)

xorg.conf
```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "extmod"
        Load  "dbe"
        Load  "record"
        Load  "dri"
        Load  "dri2"
        Load  "glx"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Panasonic"
        ModelName    "TH-42PA20"
        HorizSync     15-110
        VertRefresh    48-120
        Modeline "640x480@60" 24.11 640 672 760 792 480 490 495 505
EndSection

Section "Device"
        Option     "AGPFastWrite"               "True"
        Option     "RenderAccel"                "True"
        Identifier  "Card0"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "RV516 [Radeon X1300/X1550 Series]"
        BusID       "PCI:5:0:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Depth     24
                Modes   "640x480@60"
        EndSubSection
EndSection

```


Thank you for any help

Chris

---

### Post by efflandt on 2010-03-10
Normally Ubuntu 9.10 has no xorg.conf by default.  Are you using default modules or did you install something else ATI specific?

From the manual it looks like the native resolution of your display is 852x480 @ 60 Hz

**gtf 852 480 60** yields:

# 848x480 @ 60.00 Hz (GTF) hsync: 29.82 kHz; pclk: 31.49 MHz
  Modeline "848x480_60.00"  31.49  848 864 952 1056  480 481 484 497  -HSync +Vsync

If I try **cvt 852 480** I end up with:

# 856x480 59.68 Hz (CVT) hsync: 29.84 kHz; pclk: 31.75 MHz
Modeline "856x480_60.00"   31.75  856 880 960 1064  480 483 493 500 -hsync +vsync

That ends up with extra horizontal pixels.  So **cvt 848 480** ends up:

# 848x480 59.66 Hz (CVT) hsync: 29.83 kHz; pclk: 31.50 MHz
Modeline "848x480_60.00"   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync

When you run **xrandr** does your video show up as DVI-0 or VGA-0 (mine shows up as DVI-0, but not sure if it shows up as VGA-0 when using vga)?  Substituting whatever it is for DVI-0 below, I would try:

```
xrandr --newmode "848x480_60.00"  31.49  848 864 952 1056  480 481 484 497  -HSync +Vsync
xrandr --addmode DVI-0 848x480_60.00
xrandr --output DVI-0 --mode 848x480_60.00
```or one of the other modelines above and see if any of those look decent.  Note that xrandr is temporary, so if you do not know how to clear a mode, just log out of X and log back in.

But I am not certain how to plug that into xorg.conf, because I have none.  I only need to set special video modes when my laptop uses an external display, and for that I use xrandr commands in a script with a desktop launcher to double-click run the one I need.

---

### Post by kempy1000 on 2010-03-10
> **efflandt said:**
> Normally Ubuntu 9.10 has no xorg.conf by default.  Are you using default modules or did you install something else ATI specific?


If I remove xorg.conf and restart X the screen is exactly the same (off-centre). I am just using the radeon driver nothing else. The offical ATI driver doesn't support my card. Unless I downgrade to Hardy.

> **efflandt said:**
> 
```
xrandr --newmode "848x480_60.00"  31.49  848 864 952 1056  480 481 484 497  -HSync +Vsync
xrandr --addmode DVI-0 848x480_60.00
xrandr --output DVI-0 --mode 848x480_60.00
```
This moved the screen slightly down and left but not a great extent. (Swapped DVI-0 for VGA-0)

xrandr sees my output as VGA-0.

Thanks for the help.

---

### Post by kempy1000 on 2010-03-10
Thanks for the help I have now fixed my problem!

My perfect modeline is
```

xrandr --newmode "848x480_60.00" 34.18 848 872 936 1072 480 481 484 516 -HSync +Vsync

```

I used these two articles mainly:
[http://www.epanorama.net/documents/vga2rgb/timings.html](http://www.epanorama.net/documents/vga2rgb/timings.html)
[http://www.arachnoid.com/modelines/](http://www.arachnoid.com/modelines/)

Both very very helpful!

Chris

---

