---
title: "Mouse stutters every 10 seconds"
date: 2010-09-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by DodgeV83 on 2010-09-20
Every 10 seconds the mouse on my Dell Studio XPS 13 stutters.  This happens with the touchpad and an external mouse.

To reproduce, I move my mouse in circles until I notice the stutter (for about half a second), hit the stop watch, and it will happen again at exactly 10 seconds from that point.

Anyone else seeing this?

---

### Post by teachop on 2010-09-20
I also have a thread in this forum for this issue, at least it sounds the same.  I put in a Launchpad bug #630299 on it.  Please read that and see if it sounds the same to you.

---

### Post by antiram on 2010-09-20
i had this with the power_method=dynpm power management for a r600 radeon card. 

no stutter with this settings:
echo profile > /sys/class/drm/card0/device/power_method
echo low > /sys/class/drm/card0/device/power_profile

---

### Post by NightwishFan on 2010-09-20
Yes it probably is something to do with the timer tick or a 'regular event' of your graphics card.

---

### Post by zika on 2010-09-20
Do You have unclutter installed...?

---

