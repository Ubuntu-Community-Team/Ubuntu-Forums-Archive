---
title: "Do HDTV's not function like LCD computer monitors?"
date: 2009-12-06
forum: Multimedia Software
---

### Post by second.exodous on 2009-12-06
I can't get my HDTV to work on my Ubuntu box.  I want to move it back and fourth between my LCD monitor in my computer room and then out to my living room and hook it up to my 23" HDTV through HDMI to watch files.

I've seen lots of how-tos to set up my xorg.conf to include it's maximum resolution of 1366x768 but none that tell me to configure my computer to use both since I switch between the two.

I put this ModeLine in my xorg.conf file:

```
Section "Monitor"
        #DisplaySize      530   300     # mm
        Identifier   "Monitor0"
        VendorName   "GSM"
        ModelName    "W2453"
        HorizSync    30.0 - 83.0
        VertRefresh  56.0 - 61.0
        ModeLine     "1366x768" 85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection
```

However, I don't get that option in my 'Display Preferences' in the gnome gui.  Am I doing something wrong?  Every howto I've looked at has the scenario that the person wants to set up the box to work just on the HDTV and not two displays.  Like I said before, I want to move it from computer room that has an LCD of 1920x1080 to my living room with a HDTV with 1366x768 and back again.

Any help?

Edit:  I forgot to mention the only resolution I get on my HDTV when I plug in my computer through HDMI is a 4:3 aspect ratio, 800x600.

EDIT:  Well, I don't have time right this second, family is coming over, but [randr](http://www.phoronix.com/scan.php?page=article&item=927&num=1) looks promising since I can't get xorg.conf configure correctly.  I think the problem may be that my HDTV, a 32" Polaroid FLM-323B, doesn't send the correct data to my computer.  If that is the case I don't see randr helping me much, but I'll try tonight.

---

### Post by airborne180 on 2009-12-06
I'm no ubuntu guru, and I've been battling similar stuff... it seems that the LCD TV doesn't provide EDID information (at least mine didn't) on available resolutions, like a monitor would.  I was able to get the various resolution options available by adding a Screen section to my xorg.conf:
 
Section "Screen"
Identifier "Default Screen"
Monitor "Monitor0"
Device "Configured Video Device"
DefaultDepth 24
Option "AddARGBGLXVisuals" "True"
Option "MetaModes" "1360x768_60.00"
EndSection

It was my impression that the "MetaModes" option did the trick.  Good luck!

---

