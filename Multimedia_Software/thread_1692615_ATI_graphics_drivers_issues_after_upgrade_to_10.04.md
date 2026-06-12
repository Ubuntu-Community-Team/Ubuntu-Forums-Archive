---
title: "ATI graphics drivers issues after upgrade to 10.04"
date: 2011-02-21
forum: Multimedia Software
---

### Post by kburn on 2011-02-21
Hi All,

I recently upgraded from 9.04 to 10.04 and unfortunately, my setup has regressed significantly.  My setup is used as my main HTPC, so after upgrading to 10.04 (which had issues with fglrx upgrades btw), I try to open XBMC and get the following message:

XBMC needs hardware accelerated OpenGL rendering.
Install an appropriate graphics driver.

Previous to the upgrade, everything was working fine with the Catalyst drivers.  After some searching around, am I correct in understanding that the fglrx proprietary ATI drivers are no longer supported in 10.04 and that the open source drivers don't support 3D rendering?

Currently I'm using a gigabyte AMD motherboard with an on-board ATI HD4200 chip:


01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]


I tried removing and installing the fglrx drivers in synaptic to no avail (the install of the fglrx drivers fails).  Before I go digging any deeper and spending any more time on this, I want to see if anyone knows whether I can even use the fglrx drivers any longer now that I'm on 10.04 or whether there's another way to get 3D rendering working.

BTW, I opened jockey-gtk and it's telling me the ATI driver isn't activated.  Tried activating and get a "jockey-gtk SystemError: installArchives() failed ati" error.  

If anyone has any info on whether or not it's possible to restore my system to a working state with my current HW and new 10.04 OS, it would be greatly appreciated.  At this point I'm contemplating grabbing a cheap nvidia card from somewhere, although I'd like to save the $40 or so as long as it's not going to take me another few days to figure this out. =P

Thanks,

k

---

