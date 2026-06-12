---
title: "Different DPI for multiple monitors"
date: 2008-06-25
forum: Multimedia Software
---

### Post by zehnra on 2008-06-25
I'm running Ubuntu Hardy on a lenovo T61p with an external monitor connected via docking station (VGA, not DVI...not sure if that's a problem yet or not).  The monitor's native resolution is 1920x1200...which at 96 DPI is TINY.  The external monitor is 1280x1024.  In my xorg.conf file I have:

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Laptop LCD"
    VendorName     "Unknown"
    ModelName      "LEN"
    HorizSync       60.8 - 73.0
    VertRefresh     50.0 - 60.0
    Option         "DPMS"
    Option         "DPI"   "128 x 128"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "External LCD"
    VendorName     "Unknown"
    ModelName      "LEN L171p"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
    Option         "DPI"   "96 x 96"
EndSection
```

running [FONT="Courier New"]xdpyinfo | grep resolution[/FONT] returns:
```
resolution:    128x128 dots per inch
resolution:    96x96 dots per inch
```

However, the two monitors are not using these DPI settings.  Gnome is overriding them both.  The DPI being used is pulled from [FONT="Courier New"]Appearance Preferences[/FONT] (System --> Preferences --> Appearance) under the Fonts tab and the Details submenu.  That is currently set to 96 DPI, as anything else is just huge on the 1280 monitor.

Does anyone have an idea on how to set individual DPI resolutions per monitor that actually works?

---

### Post by Oscaruzzo on 2010-06-08
Bump :confused:

---

### Post by NTL2009 on 2010-06-12
I am also interested in this. I've got my eMachines EM725 laptop loaded with Lucid now, and before I buy an external monitor I want to know if I need to be concerned about matching resolutions or DPI. It does seem the Appearance preferences are global.

---

