---
title: "[SOLVED] Nvidia restricted driver resolution stuck at 1920x1200"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by psichron on 2007-11-19
System Information:
Ubuntu Gutsy
Dell Vostro 1700
17" WUXGA 1920x1200
Geforce 8600m

The problem:
After enabling the restricted nvidia drivers, the resolution is stuck at 1920x1200. There are no options to lower the screen resolution. Manually editing xorg.conf, or selecting a generic LCD, results in a black screen.

Solution:
Edit xorg.conf
In your "Screen" section make sure there is a SubSection called "Display" , listing all the modes you want to be able to use:
```
SubSection "Display"
		Modes	"1024x768" "1280x960"
EndSubSection
```

Next you need to add the modelines for each of the listed modes in the "Display" SubSection, to your "Monitor" section.
To generate the modelines, visit [http://www.bohne-lang.de/spec/linux/modeline/]("http://www.bohne-lang.de/spec/linux/modeline/"), select the resolution you want to generate, and enter a "Vertical Frequence in Hz" of **59**. Click Calculate under Modeline Tool 1.

Add the generated modelines at the bottom of the "Monitor" Section in your xorg.conf:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     59.0
    # V-freq: 59.00 Hz  // h-freq: 46.98 KHz
    Modeline "1024x768" 59.38  1024 1056 1128 1264   768  768  770  796 
    Modeline "1280x960" 98.23  1280 1336 1456 1672   960  960  962  995 
EndSection
```

Restart X11/gdm (logout), and open the resolution changer tool again. You should now have more resolutions to choose from.

---

