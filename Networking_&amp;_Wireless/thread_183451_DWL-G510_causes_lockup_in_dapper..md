---
title: "DWL-G510 causes lockup in dapper."
date: 2006-05-28
forum: Networking &amp; Wireless
---

### Post by jono.carnie on 2006-05-28
Hi all,

I've been playing around with wifi cards on a dapper install.
The first one I tried was giving me too much grief, a belkin usb one (fd7050b).
So off I went and got a Dlink one, figuring a pci one would so much simpler.
DWL-G510 ver c1 the box says.


I already had the rt2570 and rt2500 drivers loaded up, and didn't think to unload them.  So I plugged in the card and booted up, the system gets to the point of starting the desktop and then freezes.  Not a total lockup, as the mouse responds.
I can also get into a terminal (ctl-alt-f1), most commands seem to work there, like lsmod and lspci etc.  But even this eventually stops responding.

So I took the card out and unloded the modules, modprobe -r rtxxxxx, rebooted and checked modules were no longer there.
plugged card back in, and hey-presto. it locks up exactly at the same place.

lspci reports it as a unknown RT device.

I booted up via the dapper live disk, and it finds the card ok. the driver loaded is the rt61.
I don't get a network link as I'm using wpa on the router and ubuntu seems to only support wep at the moment.

So my question is, what do i have to do to get this card recognised in the dapper install?
Am I going about it the right way installing the card?
I know the manual with the card says install all drivers before plugging in the card??


Oh yeah, it's installed on the Shuttle.
Help anyone?

JC

---

### Post by jono.carnie on 2006-05-28
well now that was a bit of an anti-climax.
Seems the solution was right under my nose all the time.

Using the following;
The "ndiswrapper" method

This method consists in the following commands (replace "driver" below with the name of the Windows XP driver):
# ndiswrapper -i driver.inf
# ndiswrapper -l
(to ensure that the driver is loaded and the hardware detected)
# modprobe ndiswrapper
# iwconfig wlan0
(to ensure that the interface is available)

from [http://www.wlanfr.net/contenus.php?id=182](http://www.wlanfr.net/contenus.php?id=182)
worked a charm...
the bit that i think is important is the driver is actually the rt73, not the rt25xx for my usb key.

had a sneaky look in the xp install and that's what it was using.

All good now, rebooted and still working.

JC

---

