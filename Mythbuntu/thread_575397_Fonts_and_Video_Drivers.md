---
title: "Fonts and Video Drivers"
date: 2007-10-14
forum: Mythbuntu
---

### Post by ickyb0d on 2007-10-14
Hardware :
Processor: P4 3.2 Ghz
Memory: 1GB RAM
Storage: Seagate 250GB
Video: Onboard - Intel 82915G/GV/910GL

Greetings,  I'm no stranger to mythtv or ubuntu (been running both for almost a year now), but I've encountered a problem i've never seen before.  I was previously running MythTV under Ubuntu 6.10 with little problems - I've currently installed the latest version of Mythbuntu.

During the installer the xorg.conf uses "vesa" for the video device.  This is what I'm currently using and it provides a useable desktop.  This produces very small fonts (almost unreadable) and somewhat choppy video playback.  The related entries in the xorg.conf is something similar to:

```

Section "Device"
        Identifier      "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Driver          "vesa"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x720"
        EndSubSection
EndSection

```



Now using these next section(s) in the xorg.conf, i get insanely huge fonts, but the video play back is MUCH smoother.

```
Section "Device"
        Identifier      "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

```


I've found that setting the actual resolution in the "Screen" portion doesn't really help, and in fact can sometimes result in an unsupported display mode for my monitor (which i should probably mention is a Polaroid FLM-3232 HDTV).  But the obvious change between the two conf files is "vesa" vs. "intel".  I assume using the generic driver results in the choppy playback, and using the intel one - which is correct for my onboard video - results in the better playback.  

The one thing i can't figure out, is' what's up with the font size differences.  I've installed everything from the default repos relating to freetype fonts, but that doesn't seem to help.  Has anyone had this same problem? or does anyone have any insight into this?  I really don't think it has anything to do with interpreting the resolution since the icons and everything else in mythtv seems ok - just the fonts are big for some reason.

I couldn't get screenshots working when i've had a large font.  So I've attached some photos for reference.  On the login screen you can see the huge font in the small textbox, and you can see the huge fonts on the menu as well.  Any help or insight into this would be greatly appreciated!

---

### Post by laga on 2007-10-14
Wow, that's indeed insanely huge.

Here's what I guess: your HDTV set is outputting invalid/insane information regarding its DPI or size. I'd assume that "vesa" can't read EDID information while the intel driver can do that.

Can you grep /var/log/Xorg.0.log for "DPI"? Also, is your system up to date? In the latest packages, we hardcode the DPI setting to 100 because MythTV requires that for proper operation. That might help improve your situation.

---

### Post by mjezell on 2007-10-14
I had the same problem running a Nvidia card and came across this fix on the myth user mail list 

Try this in your xorg.conf  if you have a nvidia card in the video card section
Option      "UseEdidDpi"   "FALSE"
Option      "DPI"          "96 x 96"

This corrected my font sizes but I'm not quit sure how this lines up with the 100x100 DPI required by Myth to run properly.  Hope it helps.

---

### Post by ickyb0d on 2007-10-14
Laga - 

Grep'ing that file for DPI gives me the following...

```

cat /var/log/Xorg.0.log |grep DPI
(**) intel(0): DPI set to (45, 81)

```

Mjezel -

Unfotunately, adding those options to the device section (or the other two sections for that matter), didn't help.  Maybe these are options that are only relevant to nVidia cards?  Thanks though, the help is much appreciated!

I know the edid stuff with the polaroid tv's has been a hassle in the past.  And quite honestly i'm not really sure how I had this working before, maybe i'll have to search some of my old threads and see if I actually did solve it before, or if it was some fluke.

---

### Post by laga on 2007-10-14
Is your system up to date?

---

### Post by ickyb0d on 2007-10-14
> **laga said:**
> Is your system up to date?



ah! sorry, yes.  I installed the 7.10 Mythbuntu beta from the website, and have so far run apt-get update, apt-get dist-upgrade as well as apt-get upgrade.  The problem remained the same across both the beta and the RC releases.

---

### Post by ickyb0d on 2007-10-22
well, to put some closure on this, i ended up buying a [new video card]("http://www.xfxforce.com/web/viewFeature.jspa?featureId=1094899") (nVidia GeForce 7600 GS - i needed one anyways) and this proves to be a bit more customizable than my onboard intel one.  Using what mjezell posted, i was able to get the fonts to show up correctly using the nVidia card.

---

