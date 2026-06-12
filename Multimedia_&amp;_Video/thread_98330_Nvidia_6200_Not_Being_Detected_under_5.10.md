---
title: "Nvidia 6200 Not Being Detected under 5.10"
date: 2005-12-03
forum: Multimedia &amp; Video
---

### Post by seanigan on 2005-12-03
After installing my card is listed in the xorg.conf file as Unknown Nvidia Card.

I installed through synaptic the NVidia drivers, and now I see the splash screen but my xorg config file still has Unknown Nvidia Card.

---

### Post by mo_x on 2005-12-03
If everything is working ok I wouldn't worry about it. You can try the following to see the driver identifies the card correctly:
```
cat /var/log/Xorg.0.log | grep 6200
```
It gives me this output:
```
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce 6200 TurboCache(TM)
(II) NVIDIA(1): NVIDIA GPU detected as: GeForce 6200 TurboCache(TM)
```

---

