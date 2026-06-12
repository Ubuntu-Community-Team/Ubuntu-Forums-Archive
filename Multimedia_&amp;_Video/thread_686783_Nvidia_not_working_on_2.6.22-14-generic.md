---
title: "Nvidia not working on 2.6.22-14-generic"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by twyt88 on 2008-02-03
Hi all, 

I've seen a few post about how using 2.6.22-14-generic kernel and drivers breaks nvidia drivers, however none of the solutions seems to make sense.

My problem is as follows:

- Nvidia don't work on 2.6.22-14-generic, but works on 2.6.22-14-386
- Cannot compile lirc on 2.6.22-14-386 because of a bug with the lirc package, so I can't get my remote control going. I was told that 2.6.22-14-generic has the standard lirc packaged pre-compiled.

During my investigations, I've found that the /lib/modules for 2.6.22-14-386 has the following modules:

./2.6.22-14-386/kernel/drivers/char/agp/nvidia-agp.ko
./2.6.22-14-386/kernel/drivers/video/nvidia
./2.6.22-14-386/kernel/drivers/video/nvidia/nvidiafb.ko
./2.6.22-14-386/volatile/nvidia_new.ko
./2.6.22-14-386/volatile/nvidia_legacy.ko
./2.6.22-14-386/volatile/nvidia.ko


However 2.6.22-14-generic only has:

./2.6.22-14-generic/kernel/drivers/char/agp/nvidia-agp.ko
./2.6.22-14-generic/kernel/drivers/video/nvidia
./2.6.22-14-generic/kernel/drivers/video/nvidia/nvidiafb.ko


You might think that I am missing the linux restrictied kernel for 2.6.22-14-generic, but:

@starbuck:/lib/modules$ dpkg -l | grep linux-restricted
ii  linux-restricted-modules                   2.6.22.14.21                            Generic Linux restricted modules.
ii  linux-restricted-modules-generic           2.6.22.14.21                            Restricted Linux modules for generic kernels

So what else am I missing?


Thanks for your help!

TT

---

### Post by twyt88 on 2008-02-05
SUCCESS!!!

Resolved by apt-get install --reinstall on the restricted package .. that worked

But now my sound is not working .. oh well .. another post then

I guess number one rule, reinstall package just in case.

TT

---

### Post by Castaa on 2008-02-06
> **twyt88 said:**
> SUCCESS!!!

Resolved by apt-get install --reinstall on the restricted package .. that worked

But now my sound is not working .. oh well .. another post then

I guess number one rule, reinstall package just in case.

TT

Congrats!

What is the specific "apt-get install --reinstall"  package name?

Thanks.

---

### Post by twyt88 on 2008-02-07
Hi Castaa,

(as root) apt-get install --reinstall linux-restricted-modules-2.6.22-14-generic

For some reason the update on that package wasn't done properly. There were no errors or logs.

---

