---
title: "How can I add a letterboxed or stretched non-native resolution to my laptop?"
date: 2014-12-11
forum: Multimedia Software
---

### Post by JunCTionS on 2014-12-11
I want to give an Inkscape/Sozi presentation and go online for a quick demo with an external VGA display behind my back. I have a Latitude E6530 and when I run xrand I get:
```

LVDS-0 connected primary 1600x900+1920+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1600x900       60.1*+   40.0  

```

So only one mode is available for the primary and the VGA display doesn't match it. Now, I don't care about my screen being stretched or letterboxed as long as I can sort of see and control what is on the VGA display.

I looked around and found a couple of possible solutions:
[https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions)
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

So I try this:
```

cvt 1024 768
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode LVDS-0 1024x768_60.00

```

(That newmode line being the output of cvt)

But then I get the error:

```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  37
  Current serial number in output stream:  38

```

I've tried with the other resolutions available on the VGA output but with no luck. And can't seem to find how to get valid parameters other than those given out by cvt.
The Displays GUI settings have the mirror option greyed out, but I can sort of kludged them into being one within the other, but it is hard to keep track of which area of my screen is on the external display.

Any idea what I could do?

---

