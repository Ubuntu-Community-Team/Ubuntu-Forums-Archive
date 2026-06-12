---
title: "Intermittent problem with onboard audio"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by soze on 2007-04-13
Edgy 2.6.17-11
I have 3 audio devices: Mobo Audio (VIA 8237), Logitech USB headset and a MobilePre USB pre-amp.

Everything used to work fine, however in the past two weeks or so 80% of the time when I reboot, the on-board audio device does not present itself (i.e. I only have the two USB audio devices available).

I get the following line in /var/log/syslog :

```
VIA 82xx Audio: probe of 0000:00:11.5 failed with error -12
```

If I keep re-booting and retrying, eventually it works.

...and yes, the onboard audio is turned on in my BIOS.

Any thoughts?
(I'm leaning towards the theory that my mobo audio hw is circling the drain)

---

### Post by soze on 2007-04-17
One more thing...
it seems that if the two USB audio devices are unplugged during a reboot, then the mobo audio works fine.

Any ideas?

---

### Post by soze on 2007-04-19
Nothing?

---

