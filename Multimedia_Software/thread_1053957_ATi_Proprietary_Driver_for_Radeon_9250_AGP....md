---
title: "ATi Proprietary Driver for Radeon 9250 AGP..."
date: 2009-01-29
forum: Multimedia Software
---

### Post by Izobalax on 2009-01-29
Hi...

I have an ATi Radeon 9250 AGP graphics card. I've been looking to see if the better-performing proprietary drivers include this card model. Searching the web gives me conflicting answers. So I come to you. 

I installed Envyng and installed the proprietary drivers through that, but after restarting that killed my xorg and I had to remove all the changes. 

Is it possible for me to do this, and what's a safe way of installing the proprietary drivers?

/izo\

---

### Post by Izobalax on 2009-02-01
Bump?

/izo\

---

### Post by Izobalax on 2009-02-02
Anyone, please? :(

/izo\

---

### Post by bluerags on 2009-02-03
hello Izo

I ran across problems with my ATI 9250 with Ubuntu as well, so I'll just share my experience here.

first, i tried to install the proprietary driver too, and came to these results:
the proprietary driver doesn't support the 9250 cards anymore. These two pages will confirm that:
[http://www.phoronix.com/forums/showthread.php?p=52840](http://www.phoronix.com/forums/showthread.php?p=52840)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
that driver was only made up to Xorg 6.8.
if you try to download the driver on the ATI site and select linux and a 9250 card, this is what you'll get:
[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)
(some version from Aug 2008 )
if, in the same place, you look for the driver for an older 9500, you will see that there is a driver from jan. 29th 2009 with Xorg 7.4 support.
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)
so if you REALLY want to use the proprietary driver, you can downgrade your Xorg, but i've seen many places where they advise you not to do that.

your better option seems to be using the Xorg radeon driver. There's an nice manual here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
and they say:
"Full 3D support (r100 and r200 series)
All these cards and derivatives have full 3D acceleration support 
7000 / rv100 based cards
7200 / R100 based cards
7500 / rv200 based cards
8X00 / R200 based cards
9000 / rv250 based cards
9100 / R200 based cards
9200 / rv280 based cards
"
(your 9250 is a rv280pro, so it should work)

I did the installation more or less the way they tell you on that page, except that i didn't do an xorg.conf file. I simply moved that file, since it's beeing deprecated and I wanted to see what the system would do without it. result: everything got detected nice and smooth, i have openGL acceleration and all the nifty sexy compiz desktop animations.

hope this helps

rags

---

