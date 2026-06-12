---
title: "nForce S3 Resume results in loss of ethernet connectivity"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by Signal64 on 2008-12-17
I have a couple of the new nVidia 730i based motherboards and one in particular is giving me issues with ethernet after a resume from sleep (S3).

The board in question is a Gigabyte E7AUM-DS2H.
If you resume from sleep the ethernet device shows that it is up and available but the media connection becomes unavailable.

In either 8.10 or WinXP you loose your DHCP IP address and hardcoding it doesn't help.
To correct the problem you have to shutdown, pull the power, and cold start it. A normal shutdown/restart isn't enough.

It seems a register get's set on power down, but not reset on power up.

With the same setup (OS and drivers) on an ASUS P5N7A-VM 730i board this isn't an issue.

There's some confusion on the Gigabyte as the specs lists an Realtek 8211CL as it's ethernet device.
That is just a media converter and not a device that uses a driver. 
The ethernet functions and device is on the nForce chipset (same as other nforce chipsets).  

Just to be sure, lspci -nn doesn't show it and no realtek driver is loaded.  

I suspect this is a BIOS issue as it happens in both OS's on the Gigabyte and not on the ASUS board.
Contacting Gigabyte hasn't yeilded anything yet.

Does this issue sound familiar to anyone?
Is there anyway to help prove to Gigabyte it is indeed something that could be addressed with a BIOS fix?  DSDT?

---

### Post by Signal64 on 2008-12-25
Could really use some help diagnosing this as I'm stuck in Gigabyte's level 1 support hell.

---

### Post by hickop on 2008-12-25
Sounds like I have the same problem on my abit an-m2 equipped with Gigabit LAN chipset, as I reported here: [http://ubuntuforums.org/showthread.php?t=971007](http://ubuntuforums.org/showthread.php?t=971007)

EDIT : tried installing another Ethernet LAN card and putting off the on-board one, and now network is working when resuming from suspend.

---

### Post by nikolko on 2009-02-28
Hi, 

are there any updates on this topic? Did you managed to solve the problem or still looking for a solution? I faced with same question...

---

