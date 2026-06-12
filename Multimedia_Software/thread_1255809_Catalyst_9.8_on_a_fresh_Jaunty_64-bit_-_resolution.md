---
title: "Catalyst 9.8 on a fresh Jaunty 64-bit - resolution problem"
date: 2009-09-01
forum: Multimedia Software
---

### Post by kubusiowaty on 2009-09-01
Hi there,

I'm writing this because I couldn't find any information about my problem on google / ubuntuforums so I've decided to post some information in hope that it will help someone.

Couple of hours ago, I've finished re-installing Ubuntu 9.04 and I had a lot of problems with getting Catalyst 9.8 (fglrx) driver to work with my LCD display's native resolution (1440x900).

Setting the HorizSync, VertRefresh, modelines for this resolution didn't help.

When I tried to change resolution from **Administration->Screen** I've noticed that 1280x800 and 1440x900 resolutions aren't there but instead I've had a nice pack of unsupported ones (like 1440x1050 or 1600x1200).

Gladfully I've found the solution (not an elegant one but it works).

In the Catalyst 9.7 setting the HorizSync and VertRefresh was enough to solve the problem.
So I've reverted to 9.7, set the proper values in xorg.conf, rebooted, set the resolution to the desired one.

Then I've made new packages for Catalyst 9.8 and upgraded the driver (without removing the previous one).

After another reboot the resolutions where working as expected with the new driver.

**Edit:** Seems that this was an driver error. I've just removed (totally using purge) the 9.8 drivers and installed fresh Catalyst 9.9.
The problem is gone.

---

