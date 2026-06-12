---
title: "Zotac Zbox (Intel GMA3150) HDMI to TV overscanning"
date: 2011-08-13
forum: Multimedia Software
---

### Post by 320i on 2011-08-13
Hello,

I am not sure what to do about my problem so I am making a post. I will point out that I am kind of new to linux, but I understand the basics of command line operation and such, which is why i didnt post this in the beginners forum.

I bought a Zotaz Zbox SD-ID12-U, linked below, and am having annoying troubles with the HDMI connection to my TV.
[http://www.zotacusa.com/zotac-zbox-zboxsd-id12-u-intel-atom-d525-1-8-ghz-dual-core-mini-pc.html](http://www.zotacusa.com/zotac-zbox-zboxsd-id12-u-intel-atom-d525-1-8-ghz-dual-core-mini-pc.html)

I have installed Ubuntu 11.04 via USB DVD player -- everything seems to be working except for this.

The issue is that through HDMI at 720p it over-scans about 20 pixels on all four sides of the tv screen. In the "Monitor Preferences" it lists only 3 resolution options, all of which have the same overscan issue:
[I]1280x720(16:9)
800x600 (4:3)
640:480(4:3)[/I]

The device has an Intel GMA 3150 on it and when I run "lspci | grep VGA" the output is:

*00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)*

This problem does not exist when I use a VGA cable, which scales the screen properly for a variety of resolutions. I prefer to use HDMI so I would like to resolve this issue.

I have looked through the forums but am kind of overwhelmed with this stuff and really dont know where to begin.

Please help, I will try to comply with instructions.

---

### Post by BicyclerBoy on 2011-08-13
By default most TVs overscan on HDMI input.
Some TVs behave inconsistently with different HDMI inputs.

VGA (Dsub15) is treated as PC input so no overscan.

Best solution is to search your TV setup menu to :
turn off overscan
set just-scan
set PC input mode.

You may have to select "professional mode" or some other silly consumer electronics marketing term.

Failing all that, most video drivers allow for overscan compensation.
Your driver is likely intel i915 or i965.

---

### Post by 320i on 2011-08-13
Unfortunately my TV is extremely simplistic and does not have any settings like that, I looked and checked the manual - I think it needs to be done on the computer side.

For reference I have other computers that do 720p and 1080p fine with this TV (Win7 and Nvidia based though).

Not sure what driver I have exactly, but this is what I found in my /var/log/Xorg.0.log file (another thread described this as the place to find the driver):

[SIZE="1"] [    11.485] 	ABI class: X.Org Video Driver, version 10.0
[    11.485] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge[/SIZE]

Also the file mentions its using Chipset: "Pineview G" -- not sure if this helps. Forgive me if I am looking in the completely wrong place.

If this is the wrong driver, how do I update it?

---

### Post by 320i on 2011-08-13
I should clarify that ~20 pixels on all sides can not be seen on the screen... they are cut off. Sorry for the ambiguous description earlier.

---

### Post by BicyclerBoy on 2011-08-14
Could try something like..

to find out your screen name. VGA DVI1 LVDS1 etc 
xrandr -q
then
xrandr --output DVI1 --set BOTTOM 37 --set RIGHT 46 --set TOP 36 --set LEFT 54

mess about with the numbers to see if it works..

---

### Post by 320i on 2011-08-14
xrandr -q outputs:


[SIZE="1"]Screen 0: minimum 320 x 200, current 1280 x 720, maximum 4096 x 4096
LVDS1 connected 1280x720+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x720       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
[/SIZE]

xrandr --output LVDS1 --set BOTTOM 37 --set RIGHT 46 --set TOP 36 --set LEFT 54 results in:

[SIZE="1"]X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  27
  Current serial number in output stream:  27[/SIZE]

not sure what it means - I tried fiddling around a bit, when I change the LVDS1 to some other name it gives a different error mode, when i try setting individual attributes its the same error mode as shown above

---

