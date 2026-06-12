---
title: "[SOLVED] :banghead: Dual Monitor Intel 915"
date: 2008-08-15
forum: Multimedia Software
---

### Post by SabreWolfy on 2008-08-15
Any help would be greatly appreciated. I'm running Ubuntu 8.04 on an Acer Travelmate laptop, which has a 15" LCD screen at 1400 x 1050 resolution. I have an Intel 915GM screen card, which uses the Intel i810 drivers. I think Ubuntu is great and I love using it and I have no intention of returning to Windows. Sometimes, however, Ubuntu drives me crazy!

A friend recently plugged an external CRT monitor onto his W*ndows V*sta HP laptop. The desktop was extended onto the monitor. No problem. No hassles. It just worked.

I tried the same thing with my Ubuntu laptop. Needless to say, I've spent most of the week trying to get dual monitors to work. They just won't. I get corrupted displays, no display, incorrect resolutions, corrupted panels, etc...

I've searched these forums and tried suggestions, I've tried guides from thinkwiki and from intellinuxgraphics. I've edited my xorg.conf. I've booted off an Intrepid Alpha 4 LiveCD. I've stood on my head. I've whistled through my eyebrows. It just will not work. Cloning sort of works, but I want an extended desktop.

The best I managed to get was a "sort of" extended desktop, but the panels on the LCD appeared in the wrong position and I could not return the LCD to a resolution of 1400 x 1050 -- it would only go to 1280 x 1024. I tried using *xrandr*, *grandr* and *displayconfig-gtk*. I also tried the monitor resolution tool in Ubuntu. Sometimes I go errors about needing to increase the virutal screen size. Editing xorg.conf to do that resulted in a corrupted display. Passing the appropriate parameter to xrandr returned an error.

Is this just [some|another] thing that Ubuntu / GNU Linux "can't" do? My friends chuckle happily that this is just "another win for W*ndows". I've "wasted" a week on this. It took my friend all of 5 seconds to plug the CRT monitor onto his laptop and extend the desktop.

Suggestions?

---

### Post by SabreWolfy on 2008-08-15
After further searching, I have found [this]("http://ubuntuforums.org/showthread.php?p=5506057") post. The xorg.conf file from this post (modified to adjust the resolution to match my LCD) *almost* works on my system! The only problem is that the "main" desktop is on the CRT and the extended desktop is on the LCD. Moving these in grandr does nothing. Maybe some further editing of xorg.conf...

The desktop wallpaper does not appear correctly though -- it seems to appear split over both desktops. I have seen mention of this in another post before. I don't think that there is a solution to this though...?

[Edit: Selecting a wallpaper which matches the size of the left monitor and selecting TILED sort of works. Otherwise, edit the wallpaper and increase the canvas size and optionally paste in another image into the additional space. Effectively, the wallpaper should be the size of the "virtual" desktop in order to avoid it stretching across both desktops.]

Compiz appears to have disabled itself too, after I installed the xorg.conf file I mentioned previously.

[Edit: Attempting to enable Compiz results in a message saying that it could not be enabled. I think this may be a limitation of the actual screen card? Intel 915GM.]

[Edit: Indeed, it seems that Compiz cannot be enabled on the Intel 915 when using dual monitors with a combined "virtual" resolution of more than 2048x2048. See [here]("http://ubuntuforums.org/showpost.php?p=3842393&postcount=13").]

[Edit: A great script called *Compiz-Check* is detailed [here]("http://ubuntuforums.org/showthread.php?t=799070").]

---

### Post by Jdm111 on 2008-11-08
I have the same problem, here was the output for compiz check
Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz.

---

### Post by SabreWolfy on 2008-11-09
When using dual monitors, a virtual screen resolution is established, which is the sum of the resolutions of the two screens. So, for example, my laptop had (the motherboard has since died :() a resolution of 1400 x 1050 and the external 22" LCD has a resolution of 1680 x 1050. The total resolution is therefore 1400+1680 x 1050. There is a limit to the size of the "screen" which the Intel 915GM cards can manage with Compiz enabled, and it is less that the example above. I no longer use dual monitor, but when I did, Compiz was disabled. I presume that newer or more powerful cards are able to use Compiz effects at high virtual resolutions.

---

