---
title: "X Error of failed request when using xcalib and defining second monitor"
date: 2008-12-12
forum: Multimedia Software
---

### Post by sombertattoo on 2008-12-12
Mods: Please move, edit title, etc until I fit in the right place.

Hardware: Asus Nvidia 9800GT Ultimate, Twin Samsung 206BW

Software: Ubuntu Intrepid Ibex 64, Nvidia drivers 177.82, Monitors hooked up with TrueView enabled

Problem: I'm looking to set monitor .icm profiles to my monitors. I have a .icm profile for my monitors and using xcalib, I set my primary monitor (monitor #0) to use it using command ```
xcalib -s 0 226BW.icm

```That worked successfully. Then I tried again with ```
xcalib -s 1 226BW.icm
``` for the second monitor which failed with this error message: 

```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  19 (XF86VidModeGetGammaRampSize)
  Value in failed request:  0x17
  Serial number of failed request:  8
  Current serial number in output stream:  8

```

Any helpful hints around this? I'm wondering, with TrueView enabled, does xcalib only see 1 monitor? But no detectable color profile is applied on the second screen so I doubt that is the case.

---

### Post by 5hamar on 2011-08-26
> **sombertattoo said:**
> Mods: Please move, edit title, etc until I fit in the right place.

Hardware: Asus Nvidia 9800GT Ultimate, Twin Samsung 206BW

Software: Ubuntu Intrepid Ibex 64, Nvidia drivers 177.82, Monitors hooked up with TrueView enabled

Problem: I'm looking to set monitor .icm profiles to my monitors. I have a .icm profile for my monitors and using xcalib, I set my primary monitor (monitor #0) to use it using command ```
xcalib -s 0 226BW.icm

```That worked successfully. Then I tried again with ```
xcalib -s 1 226BW.icm
``` for the second monitor which failed with this error message: 

```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  19 (XF86VidModeGetGammaRampSize)
  Value in failed request:  0x17
  Serial number of failed request:  8
  Current serial number in output stream:  8

```Any helpful hints around this? I'm wondering, with TrueView enabled, does xcalib only see 1 monitor? But no detectable color profile is applied on the second screen so I doubt that is the case.
-------------------------------------------------------------------------------------------------------
You probably sorted it out but for future generations - syntax: xcalib -s screen-1 /path/to/your/icc-profile , should do the job

---

