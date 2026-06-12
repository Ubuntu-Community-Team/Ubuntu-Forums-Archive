---
title: "Any way to choose default monitor with nVidia drivers?"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by endlesssnowfall on 2006-08-31
It's a rather complicated problem to describe, but bear with me.  To start off, I'm running a 7600 GT with dual DVI ports, one connected to a larger digital LCD, and one connected to a smaller analog LCD.  

Before I installed the nVidia drivers, my larger digital LCD was the main display, with the other monitor displaying garbled artifacts.  After I installed the drivers, my larger monitor turned off, and my smaller monitor became the one being used.

It doesn't matter which port the monitors are plugged into, the smaller monitor is always the main one, unless I unplug it of course.  Is there any settings I could use to force it to use my larger monitor?

**Edit (problem fixed): **It turns out that the nvidia driver uses any analog CRTs by default, so I have to add the this option in the device section of xorg.conf:
```
Option        "UseDisplayDevice" "DFP"
```

---

