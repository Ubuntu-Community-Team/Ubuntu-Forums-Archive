---
title: "Broadcom 4312 very slow connection speed"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by prolefeedprocessor on 2010-10-14
I'm using UNR 10.04 (Lucid Lynx) on a Lenovo IdeaPad S10-2.
The wireless adapter is:
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
(Dell 1395, according to Broadcom's list)

I occasionally start out with acceptable speeds when connecting to my router, but then within minutes (usually within seconds) the rate will inevitably drop from 54 Mb/s to 11 Mb/s to 2 Mb/s to 1 Mb/s (according to "Connection Information").  No matter how patient I am, pages seem to be loading even slower than 1 Mb/s.  Whatever the actual speed may specifically be, it is utterly unusable.

Right now I am using the "Broadcom STA Wireless Driver" ("wl"), but I've tried everything under the sun, all with the same abysmal bitrate problem.
I tried the other proprietary Broadcom driver from the Hardware Drivers list, "Broadcom B43 Wireless Driver" ("fwcutter", which presumably works in conjunction with the already-present "b43").
I tried the original XP drivers using ndiswrapper. I've tried installing the STA driver using the tar ball and instructions from the Broadcom site (that one just plain didn't work).
And I should mention that, of course, the default open source drivers that come with Ubuntu were useless (couldn't even detect networks).

I reformatted before trying each new driver, just to be sure.
Each time, in addition to following instructions when available:
I always blacklisted ssb and whatever other drivers I wasn't trying at the time.
I disabled and re-enabled wireless (both through the status bar and through terminal with ifdown and ifup).
I disabled power management on the device.
I restarted the computer (and then always made sure stubborn ssb remained blacklisted at boot, rmmod'ed it if it decided to load up anyway).
I even fiddled with the router's transmission rate, but that just made the connection never connect for some reason. I also tried switching to G-only from B/G, but that had no effect.
I also fiddled with the the adapter's rate using iwconfig, and while that made Connection Information indicate the rate I forced, I still suffered extremely slow speeds and eventually got disconnected, so that didn't actually *do* anything.

At this point, I'm considering taking the adapter to a Tibetan monk for exorcism.

Wired ethernet connection (also controlled by a Broadcom device) to the same router works perfectly, but being bound to a wall defeats the purpose of having a netbook.

The router is Linksys WRT54G using Tomato 1.28 firmware, although I think that's probably irrelevant because no other device has ever had an issue like this when connecting to my router.

I haven't actually been able to test this on other wireless networks (I tried at my school and failed, but that indicates nothing because my school's wifi is always problematic anyway).

This problem did not occur under the original XP OEM (the driver for which I used with ndiswrapper), although it did occur when I briefly tried Windows 7.  It also occurred when I tried UNR 9.10 Karmic and 10.10 Maverick.

I hope that was a thorough explanation of the problem and all the stuff I already tried.  Please let me know if there is anything else you need to know.  This is driving me crazy because I know the solution is probably something really stupid-simple.  Whoever can help me solve this will remain my hero indefinitely.

Thanks!

---

### Post by Brownout on 2010-10-14
Do you get consistent speeds while on battery and on AC power?

---

### Post by prolefeedprocessor on 2010-10-14
None whatsoever. I usually have it on AC power, but the same problem occurred from battery power as well.

---

### Post by ersiner on 2010-10-14
Same here. It worked fine in 10.04.

---

### Post by prolefeedprocessor on 2010-10-14
> **ersiner said:**
> Same here. It worked fine in 10.04.

I'm using 10.04 and experiencing the problem. What did you do to get it working in 10.04?

---

### Post by ersiner on 2010-10-14
> **prolefeedprocessor said:**
> I'm using 10.04 and experiencing the problem. What did you do to get it working in 10.04?

Nothing really. I was working fine with 10.04 from the first day. A few days ago I have reinstalled my machine with 10.10 and I started having this problem.

---

### Post by prolefeedprocessor on 2010-10-14
Which driver are you using in 10.04? The built-in one or one of the proprietary ones?

---

### Post by ersiner on 2010-10-14
> **prolefeedprocessor said:**
> Which driver are you using in 10.04? The built-in one or one of the proprietary ones?

wl, the one which Ubuntu suggested me to install.

---

### Post by prolefeedprocessor on 2010-10-14
I just confirmed this on another wireless network. Definitely nothing to do with my router.

---

### Post by solnyshok on 2010-11-01
I have Broadcom 4727 (802.11bgn) and have similar simptoms on Meerkat Desktop amd64. I use

sudo iwconfig eth1 rate 54Mb

that keeps speed at 54Mbps until reboot. I however, cannot find any way to go higher than that, to achieve N speeds. Funny, because, I am actually connecting on N, I checked it by putting router to "N only" mode.

---

