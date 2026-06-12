---
title: "Asus G73 JW Subwoofer not detected in Sound preference."
date: 2010-12-16
forum: Multimedia Software
---

### Post by Mobidoy on 2010-12-16
I have an asus G73 JW laptop and when I look at all the profiles under material tab, there is not one that includes the .1 of the subwoofer, I have stereo, 4.0 surround but no .1 .... 

When I play music no boom boom :) :D comes out of the sub... 

Any fix ?

---

### Post by Mobidoy on 2010-12-17
Any other owner of G73 JW can test that please ?

---

### Post by delca85 on 2010-12-22
which device have you chosen for audio output? HDA Nvidia Digital Stereo (HDMI) o the other one?
Have you solved the problem with Powermizer makes screen flickering?

---

### Post by Mobidoy on 2010-12-23
For sound device, it is the other one.... looks like the sound chip does not have a driver....

```
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)

```

```
cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC259

```

For the flickering, no, it has not been solved yet.... Something to do with Nvidia drivers. I am using the latest and the problem still exist.

---

### Post by delca85 on 2010-12-23
Ok. Thank you very much!

---

### Post by mrdonaldpurple on 2011-01-27
Any luck on getting the sub to work?

---

### Post by Mobidoy on 2011-01-28
There is a patch that is included in kernel 2.6-37 so, it will work soon :)

---

### Post by misreckoning on 2011-02-02
Have you had any luck? Kernels on ppa are 2.6.35, so I guess it is not going to be so soon... any simple way to apply the patch to earlier kernels, or perhaps try backports of alsa?

EDIT: upgrade to natty? [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc7-natty/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc7-natty/CHANGES)

---

### Post by lidex on 2011-02-02
> **misreckoning said:**
> Have you had any luck? Kernels on ppa are 2.6.35, so I guess it is not going to be so soon... any simple way to apply the patch to earlier kernels, or perhaps try backports of alsa?

EDIT: upgrade to natty? [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc7-natty/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc7-natty/CHANGES)

That may not be the best advice. Natty is currently in alpha (and fairly unstable) and any number of things can break. If you want to try an upstream kernel go here:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by misreckoning on 2011-02-03
There we have 2.6.37 rc1 and rc2 for maverick, others are for natty. We need the rc7. Anyways, who cares about subwoofer, lets just wait for 11.04. Simplest solution.

Thanks for warning me!

---

