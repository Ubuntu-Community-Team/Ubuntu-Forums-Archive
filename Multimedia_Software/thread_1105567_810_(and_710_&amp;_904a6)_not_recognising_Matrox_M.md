---
title: "810 (and 710 &amp; 904a6) not recognising Matrox Millennium II"
date: 2009-03-24
forum: Multimedia Software
---

### Post by gheil on 2009-03-24
NB:

i tried the non-install features for 710 and 810.

The result is THE SAME for 810 ... But WORKS ie is non-aliasing) for 710 at 1024x768@85Hz (has no option for the higher rez's as recognized by XP3, so 710 still does not recognize all the capabilities of this card)

--

Hi

i have a Matrox Millennium II which is not recognized by Jackelope...(904a6) This (very old (~'95) with Tyan Trinity MB and Matrox Millennium II video) was recognized just fine by and installed with WinXP.

The symptoms i am having is it aliases a window or control panel all over. It also does not use the allowable displays (such as are used fine in XP eg 1280x1024@32b) The highest resolution allowed (13xxx768) goes off screen...

i found this entry and tried to follow it. [https://answers.launchpad.net/ubuntu/+source/yelp/+question/5121](https://answers.launchpad.net/ubuntu/+source/yelp/+question/5121) Every time i rebooted the only successful option was to do automatic reconfiguration which wiped xorg.conf out. i tried resetting xorg.conf, with the latest attempt below.

Any other suggestions? Even VESA would be better...

--

Section "Device"
	Identifier "Matrox Graphics, Inc. MGA G400"
	Driver ¨mga¨
	BusID ¨PCI:1:0:0¨
	Option ¨OldDmaInit¨ ¨True¨
EndSection

Section "Monitor"
	Identifier "Samsung 990DF"
	ModelName "990DF"
	Option ¨DPMS¨
	HorizSync 28-80
	VertRefresh 48-75
EndSection

Section "Screen"
	Identifier "Samsung 990DF"
	Monitor "Configured Monitor"
	Device "Configured Video Device"
EndSection

---

### Post by gheil on 2009-03-25
OK.
Given at least 710 does not break too badly ... if i install that, what do i need to AVOID when i upgrade in place, to keep video working? i wish a newer version would work, hate to be ALWAYS watching out.

---

### Post by gheil on 2009-03-26
OK.
Given at least 710 does not break too badly ... if i install that, what do i need to AVOID when i upgrade in place, to keep video working? i wish a newer version would work, hate to be ALWAYS watching out. It would be good too if some version of Ubuntu actually recognized that card, or there was a way to coerce the system...

--

lspci reports:

00:08.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2164W [Millennium II]

How does one coerce this, correct determination, to a non-aliased, correct screen resolution, usage?

--

Looking at Xorg.0.log:

This may be why it fails

[ 1.925900] (WW) MGA(0): Unable to probe memory amount due to hardware bug. Assuming 4096 KB...

(the device actually has 32MB of memory)

[ 2.559260] (WW) MGA(0): Shrinking virtual size estimate from 2048x1536 to 1360x768
[ 2.559551] (--) MGA(0): Has SDRAM
[ 2.559679] (--) MGA(0): Virtual size is 1360x768 (pitch 1376)
[ 2.559759] (**) MGA(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz...

1360x768 IS the highest but is way oout of whack wrt the monitors aspect capabilities. The 4MB may be causing the aliasing...

[ 2.986848] (II) MGA(0): Using MGA 2164W ILOAD video
[ 2.986915] (II) MGA(0): This is an experimental driver and may not work on your machine....

Perhaps But what does and how do i install it?

---

### Post by gheil on 2009-03-27
Is there anymore i can do to diagnose the problem?

i did get an ISA Stealth card at the Goodwill, but it turned out to be a dud. The MB can take either ISA or PCI boards. So far though i am stuck with trying to make the PCI MMatrox solution work - besides it is a good card and i am used to it;-)

---

