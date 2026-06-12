---
title: "Potential radeon drm oops......"
date: 2010-06-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by seeker5528 on 2010-06-02
I had issues with the radeon driver, don't necessarily expect it to be wide spread, in particular since this started for me before the weekend and I don't see a lot of screaming. 

But in case somebody else runs into it, if I can change to a VT when the problem starts I see messages like:

 Jun 2 12:03:49 ubuntu kernel: [ 578.361780] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(9).
Jun 2 12:03:49 ubuntu kernel: [ 578.361789] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !

Some times followed by a message indicating a reset will be attempted.

Bug # [588940](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/588940)

Later, Seeker

---

