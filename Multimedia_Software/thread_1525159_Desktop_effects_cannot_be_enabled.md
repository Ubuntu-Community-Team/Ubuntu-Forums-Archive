---
title: "Desktop effects cannot be enabled?"
date: 2010-07-06
forum: Multimedia Software
---

### Post by fred2028 on 2010-07-06
I have an HP Proliant DL380 G6 server (relatively new), and I can't enable desktop effects. I'd think even a recent integrated GPU would be able to do this right? Why can't I do it?

---

### Post by dabl on 2010-07-06
You need to be using a video driver that supports 3D.

---

### Post by fred2028 on 2010-07-06
> **dabl said:**
> You need to be using a video driver that supports 3D.
I currently have no HW drivers installed (proprietary). How do I install a 3D-capable one?:

---

### Post by Yellow Pasque on 2010-07-06
You need to know what video device you have first:
```
sudo lshw -C video
```

---

### Post by fred2028 on 2010-07-06
> **Temüjin said:**
> You need to know what video device you have first:
```
sudo lshw -C video
```
It says:
```
*-display UNCLAIMED
description: VGA compatible controller
product: ES1000
vendor: ATI Technologies Inc
physical id: 3
bus info: pci@0000:01:03.0
version: 02
width: 32 bits
clock: 33 MHz
capabilities: pm bus_master cap_list
configuration: latency=64 mingnt=8
resources: ... too lazy to type
```
What command do I use to install the optimal video card driver?

---

