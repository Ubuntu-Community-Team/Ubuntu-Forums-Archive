---
title: "nvidia kernel module"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by tristan.buckmaster on 2007-04-20
Hi I installed the nvidia-glx-new package on feisty and then realised it did not support my geforce2-mx card, so I re-installed nvidia-glx, but now my nvidia kernel module will not load (I believe it is trying to load the nvidia_new module).  I have tried reinstalling the restricted kernel module patches, although that did not help.

---

### Post by tristan.buckmaster on 2007-04-20
If I type modprobe nvidia when using the nv drivers instead of the nvidia driver I get

Not loading nvidia_new module; not used in /etc/X11/xorg.conf

suggesting it is still trying to load the nvidia_new module, instead of the nvidia module.  Any ideas how to fix this?

---

### Post by nellistc on 2007-04-21
Try running

```
sudo depmod -a

```
This fixed the module problem with nvidia_new.ko and nvidia.ko for me.

---

### Post by bouncingmolar on 2007-10-08
> **nellistc said:**
> Try running

```
sudo depmod -a

```
This fixed the module problem with nvidia_new.ko and nvidia.ko for me.

That fix for the initial problem didn't do anything for me.

---

### Post by nick_h on 2007-10-08
Uninstalling nvidia-glx-new can leave a configuration file in /lib/linux-restricted-modules which will need deleting.

---

