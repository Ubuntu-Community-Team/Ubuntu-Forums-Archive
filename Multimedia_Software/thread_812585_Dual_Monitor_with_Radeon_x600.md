---
title: "Dual Monitor with Radeon x600"
date: 2008-05-30
forum: Multimedia Software
---

### Post by rphilli5 on 2008-05-30
I am running into difficulty setting up dual monitors in 8.04 and was hoping someone had some advice.  I have an ATI Radeon Mobility x600 and I'm using the fglrx driver.  I have two monitors with the same resolution and would like to have a normal dual monitor setup.  

The monitor resolution setting app states "unknown" for the monitors.  Following some posts I installed the ATI Catalyst Control Center, which recognizes the monitors correctly.  The monitors will work in single mode or clone, but I can not get them to work in a normal dual monitor manner.

Any ideas?

---

### Post by seapahn on 2008-06-03
Have you run 'sudo aticonfig --initial=dual-head' to get a basic /etc/X11/xorg.conf file started for you?

---

