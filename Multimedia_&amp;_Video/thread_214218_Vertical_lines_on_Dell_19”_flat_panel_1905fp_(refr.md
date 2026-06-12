---
title: "Vertical lines on Dell 19” flat panel 1905fp (refresh rate problem?) – Ubuntu 6.06"
date: 2006-07-12
forum: Multimedia &amp; Video
---

### Post by TangleWeb on 2006-07-12
I did a clean install of Ubuntu Dapper Drake 6.06 on an older Compaq DeskPro ENL PIII 800 MHz with 512mb of RAM & an Intel 82815 integrated graphics controller.  It is connected to a 19” Dell UltraSharp 1905fp flat panel.  The install went perfectly, with all hardware detected.  It came up at 1280 x 1024 resolution, the default for this display.

The problem is that there are vertical lines through the picture every 2 inches or so, that “flicker”.  Sort of like the vertical refresh is off.  I have tried 75 Hz & 60 Hz, the 2 available choices at this resolution.

The monitor has connections for both analog or DVI, but the PC only has analog out.

If I change the resolution to 1024 x 768, it looks great at 75, 70, 0r 60 Hz.  No lines at all.

I installed this same version of Ubuntu on an identical system at home, connected to an older 19” Gateway CRT monitor & it defaulted to 1280 x 1024 & the picture is perfect.

A co-worker who is considerably more experienced with Linux than I said that there is a way to “tweak” the vertical refresh rate. I don’t know where to do this, or what settings to try.  I would sure appreciate any help!

~Dave

---

### Post by Paerez on 2006-07-12
can your post your xorg.conf file? That has the refresh rates in it. You can run Gedit and open "/etc/X11/xorg.conf" then copy and paste it here. Then we can try messing with the refresh rates.

---

### Post by TangleWeb on 2006-07-12
> **Paerez said:**
> can your post your xorg.conf file? That has the refresh rates in it. You can run Gedit and open "/etc/X11/xorg.conf" then copy and paste it here. Then we can try messing with the refresh rates.Excellent!  Thank you!

I am on a different PC at the moment.  I will be back to the Ubuntu box later today.  I was in the "xorg.conf" file a little earlier (made a backup first), I haven't changed anything, but I only see color depth & resolution mentioned.  Anyway, I'll post it a little later.

The specs of the 1905fp say Horizontal: 31-80kHz
Vertical: 56-75Hz, but not specifically what is recommended at the native 1280 x 1024 setting.  I posted a question in the Dell User Community Forums to get this information.

~Dave

---

### Post by Paerez on 2006-07-12
You can include the sync rates if you want, here is my section for the monitor as an example:
```
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor 1600x1200"
        HorizSync    31.5 - 94.0
        VertRefresh  50.0 - 90.0
        Option      "dpms"
EndSection
```

That should show you how to put in your ranges.

---

### Post by TangleWeb on 2006-07-12
> **Paerez said:**
> You can include the sync rates if you want, here is my section for the monitor as an example:
```
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor 1600x1200"
        HorizSync    31.5 - 94.0
        VertRefresh  50.0 - 90.0
        Option      "dpms"
EndSection
```

That should show you how to put in your ranges.That is EXACTLY what I needed.  Thank you!

I'll post my xorg.conf file & edit it as listed a little later.

~Dave

---

