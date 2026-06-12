---
title: "RR/LFE and RL/C swap, how to fix?"
date: 2008-10-22
forum: Multimedia Software
---

### Post by gorman on 2008-10-22
Hi, my problem is that the rear left and center channel are swapped, as well as the rear right and LFE.
I have created an asound.conf file in /etc with this content:```
pcm.ch51 {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0   1
    ttable.1.1   1
    ttable.2.4   1
    ttable.3.5   1
    ttable.4.2   1
    ttable.5.3   1
}

pcm.!default      pcm.ch51
```I rebooted but nothing changed, when I used speaker-test -Dplug:surround51 -c6 -twav to check.

I'm pretty sure that the above table is the right one to swap channels, but maybe I have the syntax wrong for making the change the default.

---

### Post by b055man on 2009-05-06
> **gorman said:**
> I rebooted but nothing changed, when I used speaker-test -Dplug:surround51 -c6 -twav to check.

Your config look fine and I guess the only problem is the speaker-test call - instead of specifying the alsa device (*surround51*), you should rely on the default you've just configured.
```

speaker-test -c6 -twav

```or```

speaker-test -Dch51 -c6 -twav

```Hope that helps,
A.

---

