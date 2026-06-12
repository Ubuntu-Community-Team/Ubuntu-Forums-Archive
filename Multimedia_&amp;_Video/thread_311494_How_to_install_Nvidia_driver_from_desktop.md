---
title: "How to install Nvidia driver from desktop"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by DapperMe17 on 2006-12-02
Hi

I have an Nvidia graphic card driver that was downloaded to my desktop.

It is a run file, how do I install it from the desktop?

Thanks much!

---

### Post by taurus on 2006-12-03
Why not install it from a repos!!!

```
sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```

---

