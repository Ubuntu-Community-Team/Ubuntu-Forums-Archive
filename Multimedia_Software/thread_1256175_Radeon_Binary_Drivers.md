---
title: "Radeon Binary Drivers"
date: 2009-09-02
forum: Multimedia Software
---

### Post by rogueleader12345 on 2009-09-02
I have a Radeon X1900 GT and when I tried to install the binary drivers in Ubuntu, it crashed both times. So I decided to load Kubuntu up on my flash drive, and my sound works great now (I had been having problems in Ubuntu before) so I figured let's try the video card. What drivers, specifically, should I install, or is it possible to use the Catalyst Center in Jaunty? I would like to be able to use the desktop effects, but cannot without the drivers, at least I think that's why. If that's not the reason, please feel free to enlighten me. Thanks!

---

### Post by tgalati4 on 2009-09-02
You have to regress to Intrepid or Hardy to use the Catalyst driver with your older ATI card.  Jaunty uses a new xorg version.  AMD/ATI only provides a Jaunty-compatible Catalyst driver for newer cards.  Yours is not one of them.

---

### Post by SniperSlap on 2009-09-02
> **tgalati4 said:**
> You have to regress to Intrepid or Hardy to use the Catalyst driver with your older ATI card.  Jaunty uses a new xorg version.  AMD/ATI only provides a Jaunty-compatible Catalyst driver for newer cards.  Yours is not one of them.

What do the poor suckers with ATI cards do to get 3D instead?  I was poking around with radeonhd and came up empty handed.

I have a work machine that I'd like to get going with 3D.

---

### Post by tgalati4 on 2009-09-03
Send an email to AMD/ATI and tell them your problem.  The open source drivers are getting better.  It may take a year or so to get decent 3D acceleration on older cards with the open drivers.

Downgrading to Intrepid is not so bad.  If there are newer packages that you need, you can always manually compile them.

---

### Post by Yellow Pasque on 2009-09-03
> **SniperSlap said:**
> What do the poor suckers with ATI cards do to get 3D instead?
Man, you don't want to know: [http://ubuntuforums.org/showthread.php?t=1257453](http://ubuntuforums.org/showthread.php?t=1257453)

---

### Post by tgalati4 on 2009-09-04
Thanks for the link.  I think I will give it a shot and test the performance.

---

