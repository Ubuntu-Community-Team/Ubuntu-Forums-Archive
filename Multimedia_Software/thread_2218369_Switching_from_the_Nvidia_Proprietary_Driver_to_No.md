---
title: "Switching from the Nvidia Proprietary Driver to Nouveau in 14.04"
date: 2014-04-20
forum: Multimedia Software
---

### Post by kmand on 2014-04-20
I've been using the proprietary Nvidia driver and thought I would like to give Nouveau a try in 14.04. How do I switch?

By the way my motivation is that my desktop keeps getting hung, and it takes a reinstall of Nvidia to free it.  The hangs seem correlated to Mesa updates that I keep getting. I wonder if Nouveau will work better.

My only use of either is for VDPAU support for video media.

---

### Post by monkeybrain20122 on 2014-04-20
If you have not removed or blacklisted your nouveau driver as some outdated tutorials instructed (or in other distros) then just uninstall the Nvidia driver and remove xorg.conf and reboot. Worked for me last time (13.10)

P.s. vdpau doesn't work in nouveau.

---

