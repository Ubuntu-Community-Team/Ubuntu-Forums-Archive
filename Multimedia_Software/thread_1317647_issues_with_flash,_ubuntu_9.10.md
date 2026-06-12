---
title: "issues with flash, ubuntu 9.10"
date: 2009-11-06
forum: Multimedia Software
---

### Post by vood on 2009-11-06
i am still relatively new to Ubuntu, i am running 9.10 on my laptop. i was running 9.04 before and had some issues with watching videos in hulu but i was able to fix that now now since i up graded i've had some new problems. i start a hulu video it will start to play but i wont be able to control any of the controls, such as full screen, pop out. i have the same problem with mega videos so i assume it is a flash issue does any one know how i can fix this?

---

### Post by lovinglinux on 2009-11-06
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by vor_lord on 2009-11-07
I have the same issue on youtube -- videos play, but I can't push buttons (though I can move the slider).  lovinglinux's suggestion didn't work for me.

---

### Post by mckemie on 2009-11-07
I upgraded from 9.04 to 9.10 a few days ago and just discovered flash doesn't work in Firefox.  No controls, no nothing.  I noticed my flashblock addon disappeared in the upgrade; I re-installed it and now have the flashblock icon in flash areas.  Clicking on those icons yields nothing.  I think I'm running 32 bit; here is my kernel:  vmlinuz-2.6.31-14-generic

This is running on a 2mhz, 1gig fairly new laptop sold as an emachine.

Correction, I apparently am running 64 bit:
root@emachine:/proc# uname -a
Linux emachine 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

This, apparently, was a known bug in the release candidate, but remains unaddressed in the release:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/434050?comments=all](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/434050?comments=all)

---

### Post by vood on 2009-11-07
i looked at this and it was informational but i don't think it has a way to fix this problem. i already tied to re-install the plug-ins and still not luck. Im running 64 bit and i don't have 'flashplugin-nonfree' installed

> **lovinglinux said:**
> See **Solution** [*[COLOR=Red]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004").

---

### Post by mckemie on 2009-11-13
A work around (that works for me) is posted at the launchpad link above and here:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/434050?comments=all](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/434050?comments=all)

---

