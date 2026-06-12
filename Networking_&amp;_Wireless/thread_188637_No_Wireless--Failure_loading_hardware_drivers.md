---
title: "No Wireless--Failure loading hardware drivers"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by jdjacobs on 2006-06-04
I was using Breezy with no problem.  However, after many of installs of Dapper, the same problem:  no wireless.  iwconfig did not show that the orinoco driver was loaded for my Dell C400 laptop.  Moreover, iwconfig shows two wireless interfaces:  wifi0 and eth1.  (Breezy showed only eth1)

I also noted on boot that there is a failure loading hardware devices on boot.  I select the first, second and last two listed failures:

4294693:624000 wifi0 Beacon interval setting to 100 failed
4294693:627000 wifi0 period setting to 3 failed
     .
     .
     .
     .
udevd-event [3061]: wait_for_sysfs: wiating for \            '/sys/devices/platform/i8042/serio0/serio2/bus/ failed
4294693:714000 input TPPS/2 IBM Track Point as /class/input/input3 failed

Any clue how to fix this?

Thanks,

Jim

---

### Post by TheSqueak on 2006-06-12
I'm getting a similar problem with my linksys wireless card.

Bootup freezes for a **very** long time and drops out of the nice boot up screen to a message of

"udevd-event[3431]: wait_for_sysfs: waiting for 'sys/devices/platform/i82365.0/bus' failed"

It does then eventually resume booting and everything seems to work alright (I can get ra0 up and see the wireless networks, but I don't currently use it) , but it's really annoying to have to wait so long to boot.

Any ideas?

---

