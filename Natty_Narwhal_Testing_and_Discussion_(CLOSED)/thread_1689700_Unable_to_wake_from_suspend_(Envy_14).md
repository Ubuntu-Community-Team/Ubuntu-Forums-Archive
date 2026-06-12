---
title: "Unable to wake from suspend (Envy 14)"
date: 2011-02-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by afoglia on 2011-02-17
Ever since I upgraded to natty on Sunday, my computer has been unable to wake from a suspend.

When I try to wake it the screen stays off, and I'm left with no choice but to manually reboot it.  My computer is an Envy 14, and I'm using the integrated graphics.  This is a regression from natty which had no display problems[*] when using the integrated graphics.  One other, possibly related issue, the discrete card is no longer turned off, despite having "echo OFF > /sys/kernel/debug/vgaswitcheroo/switch" in my /etc/rc.local.


[*] There was one problem, where the screen started at minimum brightness, but that was easily fixed.

I did find a blog post from someone in September claiming this was caused by the screensaver.  I shut off the screensaver in KDE, but that had no obvious effect on the awake.

---

### Post by cariboo on 2011-02-17
Right now you are using the open source drivers, I would suggest you wait until the AMD/ATI devs come up with a new driver that supports the new Xorg. Testing development versions with ATI graphics is always problematical until new ATI/AMD drivers are released, which usually come out about the the time the RC is released.

You may also have noticed that the devs have removed hibernate from the menu for this release.

---

### Post by afoglia on 2011-02-17
> **cariboo907 said:**
> Right now you are using the open source drivers, I would suggest you wait until the AMD/ATI devs come up with a new driver that supports the new Xorg. Testing development versions with ATI graphics is always problematical until new ATI/AMD drivers are released, which usually come out about the the time the RC is released.

I'd almost believe that except (a) I'm 99.9% sure I did not install the proprietary drivers under maverick, and did not have even one-hundredth the video problems I now have, and (b) I'm using the integrated (Intel) graphics, and not the discrete (ATI) graphics.

> **cariboo907 said:**
> You may also have noticed that the devs have removed hibernate from the menu for this release.

Not in Kubuntu, they haven't.

---

### Post by cariboo on 2011-02-17
What Intel graphics chipset does your system have? My Compaq netbook runs the 945 chipset, and suspend works the way it should here.

---

### Post by afoglia on 2011-02-17
> **cariboo907 said:**
> What Intel graphics chipset does your system have? My Compaq netbook runs the 945 chipset, and suspend works the way it should here.
I have an Envy 14, with a Core i5 450-M.  lspci just says "00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)".  hardinfo does tell me what the kernel module is: i915.

---

