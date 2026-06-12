---
title: "Re: Wiki on ATI Cards"
date: 2008-12-30
forum: Multimedia Software
---

### Post by 2evisual on 2008-12-30
Here is the page link
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
This is from this original link below

[http://wiki.ubuntulinux.org/BinaryDriverHowto](http://wiki.ubuntulinux.org/BinaryDriverHowto)
This page says if you have an older card than
the 9500 go to the Radeon Driver page above

The question I have is
there is a note here that says
For these cards you must use the "fglrx" driver.
is my AIW 9000 RV250 supported by the "fglrx" driver
As the below is a little confusing.
I've put in Bold where the specific line is.

"Will It Work On Your Card?

Check first your graphic card name and chipset:

$ lspci -nn | grep VGA

It should report something like this for your graphics card:

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]

Unsupported

You are currently not able to use the "radeon" driver for the following cards and derivatives:

None known.

**For these cards you must use the "fglrx" driver.**

2D modesetting only

HD 3xxx / R600 based cards
HD 4xxx / R700 based cards

Accelerated 3D support (r300, r400 and r500 series)

All these cards and derivatives have good 3D acceleration support

9500 / R300 based cards
9600 / rv350 or rv360 based cards
9700 / R300 based cards
9800 / R350 or R360 based cards
X300 / rv370 based cards
X600 / rv380 based cards
X700 / rv410 based cards
X800 / R420 or R423 or R430 or R480 based cards
X850 / R480 or R481 based cards
X1050 / rv370 based cards
X1300 / R515 based cards
X1600 / R530 based cards
X1800 / R520 based cards
X1900 / R580 based cards
Xpress 200 / RS480 IGP
Xpress 200 / RS482 IGP for Intel
Xpress 200M / RS482 IGP
Xpress 1100 / RS482 IGP
Xpress 1150 / RS485 IGP
Xpress 1200 / AMD 690V / RS690C IGP
Xpress 1200 / AMD M690V / RS690MC IGP
Xpress 1250 / AMD 690G / RS690 IGP
Xpress 1250 / AMD M690 / RS690M IGP
Xpress 1250 / AMD 690G / RS600 IGP for Intel
Xpress 1270 / AMD M690T / RS690T IGP

If you have an Xpress chip and you are not using Ubuntu 8.10 or later see RadeonXpress for instructions on how to enable 3D support and desktop effects.

Full 3D support (r100 and r200 series)

All these cards and derivatives have full 3D acceleration support

7000 / rv100 based cards
7200 / R100 based cards
7500 / rv200 based cards
8X00 / R200 based cards
9000 / rv250 based cards
9100 / R200 based cards
9200 / rv280 based cards "

---

### Post by Benanov on 2009-04-09
I've had the FLOSS radeon driver work for an R300 card but I lost DRI/DRM recently.

Is that's what this is referring to?

---

