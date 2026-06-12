---
title: "[SOLVED] 2 version of java how to i uninstall the old one"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by scraghty604 on 2008-04-09
so apprently i have 1.4 and java6 

im not sure what file name i am lookgin for under synaptics so if someone coulde tell me that or the code neeeded in terminal  thanxs

---

### Post by warp99 on 2008-04-10
Open the package manager Synaptic and look for the package "Blackdown Java" remove it from the system. Then open a terminal and enter the following:

```
sudo update-alternatives --config java
```

Make sure that 'java-6-sun' is the default, if not change it.

---

