---
title: "Viewsonic VA2226w under 8.4"
date: 2008-12-31
forum: Multimedia Software
---

### Post by arohanui on 2008-12-31
I've just updated 7.10 to 8.4 and weirdly, my display is having issues.  It can't find the drivers for my Viewsonic VA2226w widescreen monitor, which is weird, since it was working just fine before I updated.

And my googlefu is failing me, I can't find the linux drivers for the VA2226w anywhere.

Can anybody help me?

(Apologies if this should have been posted on Hardware instead, please let me know.)

Thanks

---

### Post by arohanui on 2008-12-31
Bump.

Anyone?

---

### Post by huwnet on 2008-12-31
I assume this is a monitor? While you can get monitor profiles they probably won't fix the problem.

Are you sure it isn't an issue with the graphics card? Or perhaps the resolution or refresh rate isn't supported by the monitor?

---

### Post by arohanui on 2008-12-31
No, the monitor isn't listed on the available screens when I try to configure it, even though many other Viewsonic models are, and I am using the resolution and refresh rates that I was using successfully before the Ubuntu version update.

And the graphics card information is correct.

---

### Post by arohanui on 2009-01-02
Success! I added the following into xorg.conf:

```
  Monitor         "VA2226w-11"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
```

Yay screen real estate!

---

### Post by arohanui on 2009-01-10
I'm not sure what I did (perhaps it was updating my nvidia drivers?), but my screen resolution fix has ceased to work.  I can only select from a default list of resolutions at System>Preferences>Screen Resolution:
1280x1024, 1024x768, 800x600, or 640x480.  I'm currently running 1024x768 (which is at least the correct aspect ratio), but it should be in 1600x1050.

My /etc/X11/xorg.conf file:
```
Section "Monitor"
        Identifier      "Configured Monitor"
        VendorName      "ViewSonic"
        ModelName       "VA2226w"
        HorizSync       30.0 - 82.0
        VertRefresh     50.0 - 75.0
        Option         "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection      "Display"
                Depth   24
                Modes   "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```

---

