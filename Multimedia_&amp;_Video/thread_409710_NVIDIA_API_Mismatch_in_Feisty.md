---
title: "NVIDIA API Mismatch in Feisty"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by flipside17 on 2007-04-14
Hello all,

I just did an upgrade to Feisty from Edgy. I've had no problems at all with NVIDIA graphics drivers in Edgy. After I installed the driver in Feisty, I can't get in to X. When I view a detailed output, it says that I have kernel module version 1.0-7184 and I have driver version 1.0-9755. However, the output of 
```
dpkg-query -l | grep nvidia
```
says: 

```
ii nvidia-glx-new 1.0.9755+2.6.20.5-15.20
ii nvidia-kernel-common 20051028+1ubuntu7
ii nvidia-new-kernel-source 1.0.9755+2.6.20.5-15.20

```

They don't look mismatched to me. 
What should I do?

---

### Post by old_geekster on 2007-04-15
I get much the same output to the query that you get, with one exception.  I have nVidia driver 1.0-9631.  This appears to be the latest for Feisty.

I suggest that you run the following: sudo apt-get install nvidia-glx.  This should install the latest drivers and may correct your problem.

---

### Post by flipside17 on 2007-04-16
I got it working with 9755 in feisty. I edited my /etc/default/linux-restricted-modules-common file and disabled "nv". This ended up working with no problem.

---

