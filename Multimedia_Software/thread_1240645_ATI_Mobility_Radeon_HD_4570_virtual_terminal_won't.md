---
title: "ATI Mobility Radeon HD 4570 virtual terminal won't work after suspend with radeon drv"
date: 2009-08-14
forum: Multimedia Software
---

### Post by narnie on 2009-08-14
I have a laptop with the above card. First problem is using the proprietary driver fglrx. Suspend and hibernate (mission critical things for me with this laptop) go to sleep, but don't ever fully wake up. It just stays with the desktop background and never finishes resuming. I switched back to the open source radeon (actually inactivating proprietary driver broke the system resulting in the need to do a complete reinstall) and it will suspend and hibernate ok.

Unfortunately, when I tried to control-alt F1 or whichever to get to a virtual terminal, I get colored blocks that flash repeatedly instead of the terminal screen (it works normally from a fresh boot).

Is there a more "polite" way to wake up the radeon driver or kick it into a reload as if I'd just started the boot but keep programs in tact? I'm doubting it, but thot I'd ask. Any other advise on settings in xorg.conf or in the suspend.sh/resume.sh scripts to make it play nicer?

I really miss the eye candy from not using the fglrx driver, so if there are any ideas on how to fix that with suspend/resume, it would be even better. Not sure if there are any settings withing xorg.conf for this driver that may make the proprietary behave better. (I can ssh into the machine in it's frozen state and copied the kern.log, dmesg.log, and pm.suspend log)

I thought ATI open sourced their drivers, so I was thinking it would be a better bet it would work for 3D even if using the radeon driver so I got this laptop instead of the one with an "old faithful" intel integrated. Now I have a nice card, but no 3D/compositing :(

With thanks,
Narnie

---

