---
title: "Cannot install icc profiles generated with displayCal."
date: 2019-02-25
forum: Multimedia Software
---

### Post by cunfusu on 2019-02-25
I've recently bought a device to calibrate my displays. I've managed to generate profiles for my displays but I cannot install them using displayCal.
I get the error:
'colord: Querying for profile [id of the profile] returned no results for 20 secs'
I actually get this error only when installing the profiles for external monitor..
But anyway it does not look like the profile is installed if I query colord using colordmgr

I suspect that there is something wrong with colord because I cannot find devices  and seems that the only profiles available are the default ones

```
&#10140;  ~ colormgr get-profiles | grep Filename  
Filename:      /usr/share/color/icc/colord/AdobeRGB1998.icc
Filename:      /usr/share/color/icc/colord/AppleRGB.icc
Filename:      /usr/share/color/icc/colord/BestRGB.icc
Filename:      /usr/share/color/icc/colord/BetaRGB.icc
Filename:      /usr/share/color/icc/colord/Bluish.icc
Filename:      /usr/share/color/icc/colord/BruceRGB.icc
Filename:      /usr/share/color/icc/colord/CIE-RGB.icc
Filename:      /usr/share/color/icc/colord/ColorMatchRGB.icc
Filename:      /usr/share/color/icc/colord/Crayons.icc
Filename:      /usr/share/color/icc/colord/DonRGB4.icc
Filename:      /usr/share/color/icc/colord/ECI-RGBv1.icc
Filename:      /usr/share/color/icc/colord/ECI-RGBv2.icc
Filename:      /usr/share/color/icc/colord/EktaSpacePS5.icc
Filename:      /usr/share/color/icc/colord/Gamma5000K.icc
Filename:      /usr/share/color/icc/colord/Gamma5500K.icc
Filename:      /usr/share/color/icc/colord/Gamma6500K.icc
Filename:      /usr/share/color/icc/colord/NTSC-RGB.icc
Filename:      /usr/share/color/icc/colord/PAL-RGB.icc
Filename:      /usr/share/color/icc/colord/ProPhotoRGB.icc
Filename:      /usr/share/color/icc/colord/SMPTE-C-RGB.icc
Filename:      /usr/share/color/icc/colord/SwappedRedAndGreen.icc
Filename:      /usr/share/color/icc/colord/WideGamutRGB.icc
Filename:      /usr/share/color/icc/colord/sRGB.icc
Filename:      /usr/share/color/icc/colord/x11-colors.icc
&#10140;  ~ colormgr get-devices
&#10140;  ~
```
Is it expected that I do not get a list of devices from colord?
Is this caused by the fact that I do not use kde or gnome?


this is the ubuntu version I'm running:
originally it was a kubuntu but now I use i3wm

```
&#10140;  ~ uname -a            
Linux bestia 4.15.0-45-generic #48~16.04.1-Ubuntu SMP Tue Jan 29 18:03:48 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

I've also tried the diagnostic util provided by darktable and this is what I get.

```
&#10140;  ~ darktable-cmstest   
darktable-cmstest version 2.4.4
this executable was built with colord support enabled
darktable itself was built with colord support enabled

couldn't locate primary CRTC!
CRTC for screen 0 CRTC 2 has no mode or no output, skipping

LVDS-1    the X atom and colord returned different profiles
    X atom:    _ICC_PROFILE (1401600 bytes)
        description: LP125WH2-SLB3 #1 2019-02-23 14-40 2.2 F-S XYZLUT+MTX
    colord:    "(none)"
        description: (file not found)

DP-2    the X atom and colord returned different profiles
    X atom:    _ICC_PROFILE_1 (740580 bytes)
        description: LT2223pwC #2 2018-08-29 13-09 2.2 F-S XYZLUT+MTX
    colord:    "(none)"
        description: (file not found)

Better check your system setup
 - some monitors reported different profiles
You may experience inconsistent color rendition between color managed applications
&#10140;  ~ 

```

---

