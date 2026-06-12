---
title: "AD1988B center channel volume too low"
date: 2009-05-16
forum: Multimedia Software
---

### Post by maheshasolkar on 2009-05-16
Greetings!

I am trying to setup 5.1 channel surround sound with the on-board audio of Asus P5K-E / Wifi AP motherboard. The audio chip on this motherboard is Analog Devices AD1988B. I am using speakers (2-front, 2-rear and a center - no subwoofer) from an old AIWA music system.

By setting default-sample-channel to 6 in /etc/pulse/daemon.conf, I've reached a point where I can hear test sounds from all the 5 speakers. I tested this with:

```
  % speaker-test -c 6 -l1 -twav
```

My problem is, the volume on the center speaker is really low. I've tried to set volumes to max in gnome-volume-control and alsamixer. But it hasn't helped.

I am wondering if the on board audio hardware is powerful enough to driver the speakers directly. Although the front-left and front-right speakers sound pretty good.

Anyone having similar problems? Any ideas?

---

### Post by xeth on 2009-07-24
i have the same board and the same problem

---

