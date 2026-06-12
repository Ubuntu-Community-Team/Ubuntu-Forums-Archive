---
title: "ATI Open Source Driver TV-out"
date: 2008-06-22
forum: Multimedia Software
---

### Post by fort1 on 2008-06-22
I have a laptop with an ATI card and the open source driver.
It is connected to a television set via S-video.

The laptop has a wide screen (16x9), the tv is 4x3, PAL, 50 Hz.

To get a picture on the tv in Windows, one key-press (Fn+F4) is sufficient.
It seems, that in UBUNTU everything must be done by hand.

1.Changing NTSC to PAL,
2.Changing 60Hz to 50Hz,
3.Changing screen dimensions 16x9 &#8594; 4x3.

I wonder if anybody has developed a script doing all that ? :confused:
It would be ideal having 2 scripts: TV On and TV Off.....

Thanks....

---

### Post by fort1 on 2009-05-18
Ok, it is very simple in UBUNTU 9.04 using the new open source ATI driver!
I wrote 2 scripts and linked them with two launcher buttons on the desktop.

TV ON
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600 --rate 50
xvattr -a XV_CRTC -v 1

TV OFF
xvattr -a XV_CRTC -v 0
xrandr --output S-video --off

You may need installation of "xvattr" - no sweat, it is in UBUNTU repositories. I have a PAL TV and the S-Video output seems to be PAL by default. Otherwise xrandr handles the tv standatd as well.

---

