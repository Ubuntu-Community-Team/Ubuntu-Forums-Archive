---
title: "OGG OGV Video in Maverick Meerkat 10.10"
date: 2010-10-27
forum: Multimedia Software
---

### Post by MathUHenry on 2010-10-27
With the install of Maverick Meerkat 10.10 Desktop Edition, I lost the ability to play OGG .ogv video files. When I downgrade to Lucid, it works fine in any player. Is anyone else having this problem?

Using a Dell Inspiron Mini 10 netbook.

Regards,

MathUHenry

---

### Post by sgarman on 2010-11-02
You need to install the 'liboggplay1' package.

```
sudo apt-get install liboggplay1
```

Even still, I have an odd issue playing some large (> 400 MB) .ogv videos, where Totem won't start playing them automatically, but if I move the progress slider around, the video will seek to the correct spot and I can play it from there.

HTH,

Scott

---

### Post by MathUHenry on 2011-02-27
Thank you Scott.

---

### Post by no2498 on 2011-02-27
scott try installing smplayer
i know its part on totem but it works better

---

