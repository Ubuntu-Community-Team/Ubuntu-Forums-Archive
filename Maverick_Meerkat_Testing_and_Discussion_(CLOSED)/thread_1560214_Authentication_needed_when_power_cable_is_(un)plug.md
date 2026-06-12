---
title: "Authentication needed when power cable is (un)plugged"
date: 2010-08-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by bprins on 2010-08-24
Hi,

When I unplug my power cord, I have to enter the root password in order to enable set the brightness to a lower/higher level.

Since I don't have that problem in Lucid I get the feeling this might be a bug. 

Any ideas?

Bas

---

### Post by cariboo on 2010-08-24
It is a bug. When I pull the plug on my netbook, it just works, no authentication needed.

---

### Post by bprins on 2010-08-24
Something worth to file at bugzilla or is it too trivial?

---

### Post by Mr. Picklesworth on 2010-08-24
Try filing downstream first. Chances are this is an issue with our PolicyKit setup.

---

### Post by mc4man on 2010-08-24
This is what you may be seeing? - at least here it doesn't actually affect ability to change brightness -  can be cancelled if desired (twice

Certainly is unintended behaviour I'd think (the need to auth.

---

### Post by coffeecat on 2010-08-24
> **mc4man said:**
> This is what you may be seeing? - at least here it doesn't actually affect ability to change brightness -  can be cancelled if desired (twice


This is what I started seeing on my Acer laptop this morning after the updates. I hadn't seen it before. I could still adjust the brightness with the Fn key combination.

---

### Post by bprins on 2010-08-25
Same for me. after updates this popped up. Also have an acer.

---

### Post by woodbj on 2010-08-25
Maybe it has something to do with the latest update to gnome-power-manager

> gnome-power-manager (2.31.90-0ubuntu4) maverick; urgency=low

  * Fix LP: #615047 - asks for root permission to do 
    gnome-power-backlight-helper --get-max-brightness. Clean the distributed 
    policy file from the source tree before building so we install a policy
    file with the correct pkexec path
    - add debian/patches/15_distclean.patch
    - update debian/patches/series

 -- Chris Coulson   Tue, 24 Aug 2010 10:59:30 +0100

[http://www.ubuntuupdates.org/packages/show/214170](http://www.ubuntuupdates.org/packages/show/214170)

---

