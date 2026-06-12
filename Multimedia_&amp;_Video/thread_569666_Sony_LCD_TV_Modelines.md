---
title: "Sony LCD TV Modelines"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by Plebster on 2007-10-07
Hi,

I'm really struggling to set up the modeline on my ubuntu  mythtv fronted for my Sony KDL32V2500 lcd TV. I have tried numerous setting and have had no joy.  I have feisty fawn installed on an old Toshiba A2 laptop which has an Intel 855GM integrated graphics card. I have installed 915 resolution drivers but still no mater what I only get 1024 x 768!!

Here is my xorg.conf, as you can see i've tried loads of differebt modelines:

```

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
         Identifier "SonyBravia"
         HorizSync 47.7
         VertRefresh 84.72
         #ModeLine "1360x768" 171.200 1360 1430 1542 1792 768 771 777 795 +hsync +vsync
         #ModeLine "1360x768" 85.500 1360 1424 1536 1792 768 771 777 795 +Hsync +Vsync
         #ModeLine "1360x768" 85.500 1360 1430 1542 1792 768 771 777 795 +hsync +vsync
         #ModeLine "1280x768" 79.500 1280 1350 1478 1664 768 771 778 798 -hsync +vsync
         Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795 -Hsync +Vsync
EndSection

```

I have connected my XP laptop to the screen and managed to get the native resolution of 1360 x768. Whilst in Windows I have run MonInfo the details are:

```

Monitor
  Windows description......... Sony Monitor
  Manufacturer description.... SONY TV
  Manufacturer................ Sony
  ————————————————————————————
  Plug and Play ID............ SNYA500
  Serial number............... n/a
  EDID data source............ I2C bus (real-time)
  ————————————————————————————
  Manufacture date............ 2005, ISO week 42
  EDID revision............... 1.3
  Display type and signal..... Analog 0.700,0.300 (1.0V p-p)
  Sync input support.......... Separate
  Screen size................. n/a
  Power management............ n/a

Color characteristics
  Display gamma............... 2.20
  Red chromaticity............ Rx 0.645 - Ry 0.335
  Green chromaticity.......... Gx 0.265 - Gy 0.585
  Blue chromaticity........... Bx 0.140 - By 0.065
  White point (default)....... Wx 0.282 - Wy 0.284

Timing characteristics
  VESA GTF support............ Not supported
  Horizontal scan range....... 30-49kHz
  Vertical scan range......... 57-63Hz
  Video bandwidth............. 90MHz
  Extension blocks............ n/a
  Timing recommendation #1.... 1360x768 at 60Hz
      Modeline................ "1360x768" 85.500 1360 1430 1542 1792 768 771 777 795 +hsync +vsync
  Timing recommendation #2.... 1280x768 at 60Hz
      Modeline................ "1280x768" 79.500 1280 1350 1478 1664 768 771 778 798 -hsync +vsync

Standard timings supported
   640 x  480 at  60Hz - IBM VGA
   640 x  480 at  60Hz - VESA
   720 x  400 at  70Hz - IBM VGA
   800 x  600 at  60Hz - VESA
  1024 x  768 at  60Hz - VESA
  1280 x  768 at  60Hz - Sony
  1360 x  768 at  60Hz - Sony

Raw EDID base
  00: 00 FF FF FF FF FF FF 00  4D D9 00 A5 01 01 01 01 
  10: 2A 0F 01 03 08 00 00 78  0A 3F F7 A5 55 43 95 23 
  20: 10 48 48 A1 08 00 31 40  45 40 61 40 01 01 01 01 
  30: 01 01 01 01 01 01 66 21  50 B0 51 00 1B 30 46 70 
  40: 36 00 00 00 00 00 00 1E  0E 1F 00 80 51 00 1E 30 
  50: 46 80 37 00 00 00 00 00  00 1C 00 00 00 FD 00 39 
  60: 3F 1E 31 09 00 0A 20 20  20 20 20 20 00 00 00 FC 
  70: 00 53 4F 4E 59 20 54 56  0A 20 20 20 20 20 00 79 

Display adapter
  Adapter description......... Auxiliary port
  Adapter device ID........... 0x27A68086
  Display settings............ n/a

User/computer information
  Registered user name........ 
  Registered organization..... n/a
  Network user name........... Jim
  Network computer name....... LAPDOG-SMURF
  Windows version ............ Windows XP
  Windows build .............. 5.01.2600 Service Pack 2
  Installation date .......... 5/1/2007 12:00:00 PM

```

and powerstrip gave the following:

```

PowerStrip timing parameters:
1360x768=1360,70,112,250,768,3,6,18,171200,512

Generic timing details for 1360x768:
HFP=70 HSW=112 HBP=250 kHz=96 VFP=3 VSW=6 VBP=18 Hz=120

VESA detailed timing:
PClk=171.20 H.Active=1360 H.Blank=432 H.Offset=54 HSW=112 V.Active=768 V.Blank=27 V.Offset=3 VSW=6

Linux modeline parameters:
"1360x768" 171.200 1360 1430 1542 1792 768 771 777 795 +hsync +vsync

```

Any help would be greatly aprpreciated!!

Cheers,

Jim

---

