---
title: "Last Night's Updates Killed Video..."
date: 2009-07-08
forum: Multimedia Software
---

### Post by kulturloseramerikaner on 2009-07-08
Last night I ran through the normal update, in which the latest kernel headers and whatnot where installed for the 2.6.24-24 kernel that Hardy is still using.  Today when I started, I got an error message in which X was asking me for my monitor settings and insisting that I use the Vesa driver even though I'm running a GeForce 8800 GTS; it also failed to find my NIC and there were other driver-related issues as well, only the soundcard worked.  I rebooted into recovery mode, ran the repair X option, and got back in.  The internet works now as well, and it found the proper resolution for my widescreen monitor, but it still will not apply the proper driver for the nVidea card and has therefore prevented me from running my Compiz and Emerald.  A quick glance in Synaptic doesn't show me anything that relates to nVidea, and I can't find the option to apply restricted drivers in the Hardware Drivers section in the System menu.  I should know how to fix this, but haven't had to deal with it in a while.  No, going into desktop effects from the appearance menu did not help.  Any help would be greatly appreciated.
Update:
Although I forced update manager to run to see if there was a bug found and corrected for yesterday's updates, it didn't find anything new for today.  For some reason, the automatic update daemon did find another header update.  I applied it, and had to reboot.  After logging back in, I tried hardware manager again on a hunch and sure enough, the latest nVidea driver was there for download.   After installing and restarting again, I was able to apply advanced desktop effects, which immediately reapplied my Emerald theme.  I manually apply the desktop cube setting for Compiz, but now everything seems to be back.

---

