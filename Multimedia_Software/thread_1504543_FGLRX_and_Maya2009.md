---
title: "FGLRX and Maya2009"
date: 2010-06-08
forum: Multimedia Software
---

### Post by elf128 on 2010-06-08
Hi,
I use Maya for linux under kubuntu starts from 2007 with a different hardware.

Last half of year i use my notebook Acer 8920G.
It has ATI Radeon hd3650 with 512RAM. OK, I know, it's not a powerfull workstation, but it's enought for my purposes.

Everything was fine under kubuntu 9.04 and 9.10. Until i make upgrade from 9.10 to 10.04
After that, i have fatal error on the star of maya:
```
/usr/autodesk/maya2009-x64/bin$ ./maya

maya encountered a fatal error

Signal: 11 (Unknown Signal)

```

As i know, that mean, that there was a problem with video while start of maya.
I try different versions of Catalist, but the problem remain the same.

BTW, here is result of fglrxinfo:
```
/usr/autodesk/maya2009-x64/bin$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 3650
OpenGL version string: 3.2.9756 Compatibility Profile Context

```
Any other 3D software work fine: Shake, Google Earth some custom application. I still have an issue with performance while resize of windows with desktop effects turned on, but it's old issue.

IT'S VERY INTERESTING, that if i remove fglrx and setup open-source radeon driver, Maya work and desktop effects work fine, but there is no power-save options and i have a lot of performance issue. Hi quality render in Maya viewports and Shake run slow as hell.
As for me, power save is very important because it's notebook. With open-source driver it work like a heater ( 70C on Video while temperature of CPU less then 40C ) and without charger i'm out of battery after 30 minutes.

So, the question is, what i miss and how can i check why Maya cann't run with FGLRX.

---

