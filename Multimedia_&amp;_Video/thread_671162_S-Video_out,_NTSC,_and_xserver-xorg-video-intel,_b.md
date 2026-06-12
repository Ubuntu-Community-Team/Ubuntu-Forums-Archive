---
title: "S-Video out, NTSC, and xserver-xorg-video-intel, b&amp;w output"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by beowulf573 on 2008-01-18
I've been trying to get TV Out working on my laptop via the s-video connector to my NTSC tv.  The picture is sharp but I've only in black and white.  From searching the forums and the web I see others have experienced this problem, but most seem to involve the video card defaulting to a NTSC mode and being connect to a PAL tv.

I'm using a Lenovo 3000 N100 laptop, running Gutsy and xserver-xorg-video-intel.  lspci shows the controller to be "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)"  The laptop has a seven pin connector, the tv a four pin.  I've tried two different four pin cables, four pin to composite cable, and a seven pin to the composite cable.  The four pin cables both show a b&w images, the composible images are heavily distorted and b&w.

I've tried booting with the tv connected and on, and then connecting while the laptop was running.  I've tried using xrandr to set the mode to NTSC and various display modes, all work but only in b&w.

I noticed that xorg.conf doesn't have an entry for the tv as a monitor by default, so I've tried adding one, but now no image appears on the tv.  The log indicates that there are no modes available because all the vrefreshes are out of range.  I've tried googling different NTSC compatible modelines but I haven't found any that work.  It's been a few years since I've hacked on a X11 config file, I'm not even certain that's required any more.  I've also added the TVStandard -> NTSC and TVOutFormat SVIDEO options to the tv monitor entry.

Does anyone have any suggestions on anything else to try?  Does anyone have any known good modelines I can try?  I've run out of ideas.

Thanks.

---

