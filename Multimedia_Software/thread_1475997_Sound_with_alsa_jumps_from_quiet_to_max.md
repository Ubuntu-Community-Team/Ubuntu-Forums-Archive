---
title: "Sound with alsa jumps from quiet to max"
date: 2010-05-07
forum: Multimedia Software
---

### Post by Apex9 on 2010-05-07
When I increase the volume on my computer (from silent) it only has 3 levels: really quiet, still quiet, and max volume. 

So when I press volume up 3 times, it's already maxed out, even though there are supposed to be 15 more volume levels. Continuing to increase the volume beyond the 3rd level has no effect, even the the volume bar is not full.

I'm using alsa version 1.0.22.

When I go into alsamixer I see that going from silent to Volume 1, PCM volume jumps from 0 to 98, Front volume jumps from 0 to 60. Master stays at 0. When I volume up again, PCM stays at 98 and Front jumps to 88. Master again stays at 0. I volume up one more time to reach max volume. Front jumps from 88 to 100 and Master volume finally goes from 0 to 6.

Further volume increases move Master up in regular increments of around 10 or so, but have no effect on the actual volume.

Anyone have any idea what could be causing this?

---

### Post by nimu on 2010-05-22
I don't have any idea about the cause of this bug, but I have the same problem. I've reported a [bug]("https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/581830") on launchpad and hopefully someone will find a solution :)

---

### Post by kid1000002000 on 2012-01-15
Same problem in 11.10; don't forget to subscribe to this bug.
[https://bugs.launchpad.net/ubuntu/+s...on/+bug/871133]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/871133")

---

