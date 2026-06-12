---
title: "Screen resolution and S3 GammaChrome Driver"
date: 2010-10-04
forum: Multimedia Software
---

### Post by liantze on 2010-10-04
(I'm posting this without much hope, but still...)

I've just installed Ubuntu 10.04 on an old laptop, the Fujitsu Lifebook S7025. Tech specs are [here]("http://www.fujitsu.com/downloads/COMP/fpcap/notebooks/previous/factsheet_s7025.pdf").

The problem: the dreaded graphics-card-not-detected-properly-hence-low-resolution woe. I tried adding "Virtual 1280 960"</code> to my (minimal) xorg.conf shown below:

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 1280 960 
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection
```


I was then able to set a resolution of 1280 x 960 (0Hz refresh rate?). But then the screen gets too big for the physical monitor, where I have to move the mouse down to access the lower part of the screen, and can't access the far right part at all.

```

$ lspci | grep VGA
01:00.0 VGA compatible controller: S3 Inc. Device 8e13 (rev 03)

```

but the VESA driver is in effect (from /var/log/Xorg.0.log).

After reading various posts on the Internet, I reckon my best bet is to track down a proper driver for my graphics card. According to the Lifebook's specs sheet, the graphics card is S3 Graphics™ GammaChrome XM18™ ULP MPM-64 with dedicated 64MB video memory, PCI Express® X 16. The S3 website lists only Linux drivers for Chrome 40/00/500 cards only, but who knows, maybe someone here has a GammaChrome driver? (fingers crossed? please?)

---

