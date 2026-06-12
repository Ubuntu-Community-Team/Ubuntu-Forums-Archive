---
title: "TV monitor through HDMI"
date: 2009-01-24
forum: Multimedia Software
---

### Post by AlexH76 on 2009-01-24
I'm on 8.10 (laptop) Attached laptop to tv monitor through HDMI. The 'configure display settings' recognized the monitor. I picked a resolution for the tv monitor, then it said that it "detected that the virtual resolution must be set in the config in order to apply the settings". I let it do that automatically, however I got still "no signal" on the tv screen. 

I modified xorg.conf. Now when I enable the tv monitor by choosing a resolution (after connecting the cable) it 'goes' to my laptop screen, making it really wide so I can't even see my panels. 

It seems that is does not really 'output' to the tv monitor. Below is my xorg.conf. Anyone can tell me what to modify/add so that I can use the external monitor?

[FONT="Courier New"][SIZE="2"]# devices

Section "Device"
  Identifier	"intel"
  Driver	"intel"
  Screen	0
EndSection

Section "Device"
  Identifier	"intel"
  Driver	"intel"
  Screen	1
EndSection

# monitors

Section "Monitor"
  Identifier	"Laptop Monitor"
EndSection

Section "Monitor"
  Identifier	"LG TV Monitor"
EndSection

# screens

Section "Screen"
  Identifier	"Laptop Screen"
  Device	"intel"
  Monitor	"Laptop Monitor"
  SubSection "Display"
    Virtual	2880 900
  EndSubSection
EndSection

Section "Screen"
  Identifier	"TV Screen"
  Device	"intel"
  Monitor	"LG TV Monitor"
  SubSection "Display"
    Virtual	2880 900
  EndSubSection
EndSection[/SIZE][/FONT]

---

### Post by AlexH76 on 2009-01-24
xrandr output shows monitor through hdmi is detected. What is wrong in xorg.conf??

[FONT="Courier New"][SIZE="2"]Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1440 x 1440
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis) 367mm x 229mm
   1440x900       60.0*+
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-1 connected (normal left inverted right x axis y axis)
   1360x768       59.8 +   59.8
/*snip  
[/SIZE][/FONT]

---

### Post by AlexH76 on 2009-01-24
A new xorg.conf below, however still the same: as soon as I select a resolution for the external monitor, this takes effect on the laptop monitor, and the external (tv) monitor still says "no signal"

[FONT="Courier New"][SIZE="2"]

Section	"Device"
  Identifier	"intel"
  Driver	"intel"
  Option	"monitor-LVDS"		"Monitor1"
  Option	"monitor-HDMI-1"	"Monitor2"
EndSection

Section	"Monitor"
  Identifier	"Monitor1"
EndSection

Section "Monitor"
  Identifier	"Monitor2"
  Option	"LeftOf" "Monitor1" 
  Option	"Enable" "true"
EndSection

Section	"Screen"
  Identifier	"Default Screen"
  Device	"Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller"
  Monitor	"Monitor1"
  SubSection	"Display"
	Virtual	2880 900
  EndSubSection
EndSection
[/SIZE][/FONT]

---

### Post by AlexH76 on 2009-01-24
Ahhh, well... it was just the 'Virtual' mode.. External monitor is capable of 16:9, so the right Virtual would be 2800 900.. that solved it for me.

---

