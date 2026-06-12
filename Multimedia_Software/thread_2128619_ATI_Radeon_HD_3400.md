---
title: "ATI Radeon HD 3400"
date: 2013-03-23
forum: Multimedia Software
---

### Post by Deadly Eyez on 2013-03-23
Have i just started using ubuntu so sorry if my question seems stupid.
I installed ubuntu 12.10 and everything works fine on my laptop except the loud noise and heat problem. 
Now i asked around and everyone suggested that one of my drivers is not properly set so i checked and found out that under graphics I have Driver = Unknown. 
Now i tried to look around for a driver to radeon hd 3400 and found one in AMD website downloaded installed then rebooted. 
My screen went really large and i couldn't see the icons bar to the left. 
after a 5 hours trying to fix it i purged (Delete?) the driver and ubuntu started working but still driver unknown. 
Any idea what i have to do to fix this please?
Someone already told me that 12.04 and on don't support for radeon hd 3400 but is there a solution to the overheat and noise problem?

---

### Post by QIII on 2013-03-23
*Moved to** Mulitmedia & Video***



Hello and welcome!

The problem is not that Ubuntu does not support your card, but rather that the ATI driver for that card will not work with Ubuntu versions after 12.04.2.

The HD 2xxx to HD 4xxx cards have been put in a "legacy branch" by AMD.  The legacy driver will not work with X Server 1.13 and beyond.  12.10 uses X Server 1.13.

You can still use the card, of course, but you will have to do so with the default open source Radeon driver, which was installed when you installed Ubuntu -- and is used again when you remove the ATI driver.

If heat and battery life are a problem, you can use jupiter.

[This]("http://ubuntuguide.net/install-jupiter-applet-in-ubuntu-12-04-12-10") gives a pretty good run down on installing it.

Best wishes!

---

### Post by bazsound on 2013-03-23
it is possible to install the legacy driver, theres a ppa that you have to add to your system that will downgrade the x server to 1.12.2 (newest version that suppers the legacy drivers) and then then you can install fglrx-legacy.

search for fglrx-legacy ubuntu 12.10 and you should find instructions

---

### Post by QIII on 2013-03-23
I recommend strongly against that, actually.  It leaves you with a patched kernel, a downgraded X Server and a dead-end driver.

The future consequences of moving forward with such a system cannot be predicted.

The open source Radeon driver will provide more than adequate performance for the vast majority of users.

---

