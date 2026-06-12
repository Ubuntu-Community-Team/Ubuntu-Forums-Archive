---
title: "Displaycal and Monaco Optix XR (DTP94)"
date: 2016-09-22
forum: Multimedia Software
---

### Post by TimGS on 2016-09-22
Hi,

I have a secondhand DTP94 with which I am trying to use displaycal.

Following instructions found on the web I have the following:

```
tim@dougal:~$ dispcal -yl -P 0.25,0.5,1 -v -qm -t 5500 -b 80 -g 2.2 -o /home/tim/Desktop/ArgyllCMS
Setting up the instrument
 Instrument Type:  DTP94
 Serial Number:    103682
 Boot version:     D929
 Software version: DB06
Place instrument on test window.
Hit Esc or Q to give up, any other key to continue:
Display type is 'l'
Target white = 5500.000000 degrees kelvin Daylight spectrum
Target white brightness = 80.000000 cd/m^2
Target black brightness = native brightness
Target advertised gamma = 2.200000

Display adjustment menu:
Press 1 .. 7
1) Black level (CRT: Offset/Brightness)
**2) White point (Color temperature, R,G,B, Gain/Contrast)**
3) White level (CRT: Gain/Contrast, LCD: Brightness/Backlight)
4) Black point (R,G,B, Offset/Brightness)
5) Check all
6) Measure and set ambient for viewing condition adjustment
7) Continue on to calibration
8) Exit
Doing some initial measurements
**Red   = XYZ   0.00   0.00   0.00**
Green = XYZ   0.00  50.62   0.00
Blue  = XYZ   0.00   0.00  38.17
White = XYZ  25.08 108.33  52.09

Adjust R,G & B gain to get target x,y. Press space when done.
   Target Br 80.00, x 0.3325 , y 0.3475 

```

I am having difficulty getting the measured values anywhere near the targets. Brightness is easy, but the colour balance not so. I am wondering about the highlighted initial measurements - should Red be all zeros? Could I have something wrong with my secondhand DTP94 or perhaps a software problem?

thanks,
-- Tim.

---

