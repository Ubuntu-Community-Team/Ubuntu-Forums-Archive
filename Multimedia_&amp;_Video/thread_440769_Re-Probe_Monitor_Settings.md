---
title: "Re-Probe Monitor Settings"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by LakeWind on 2007-05-11
I just bought a new wide screen LCD monitor and was wondering how to re-probe the monitor so that it is recognized properly by Ubuntu?

I dual boot between OpenSuse 10.2 and Ubuntu Feisty Fawn, it's very easy with OpenSuse (sax2 -r). Actually with OpenSuse I didn't even have to do that though. It was automatically recognized as soon as I booted up (plug and play). Unfortunately this is not so with my installation of Ubuntu though.

I'm hoping someone can help me out here please.

Thanks!
:confused:

---

### Post by taurus on 2007-05-11
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by LakeWind on 2007-05-12
> **taurus said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That did it. Thanks very much!!

:)

---

