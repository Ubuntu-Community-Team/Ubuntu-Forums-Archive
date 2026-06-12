---
title: "nforce3 and ati again, now on edgy...."
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by alanrr_sr on 2006-12-10
Hi,

I am trying to get fglrx over a nforce3 chipset, but I got no success.
Some time ago I downgrade my bios to get my ati 9550 working on my motherboard, but this is not a option anymore :(

Kernel and driver have changed from 6.04, but the error is the same:
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP

I have no success trying to load modules by hand, using internal agpgart module or not, and MS Windows trick works yet....



Anyone with a new solution, or everyone using a nforce3 chipset can have fglrx driver working (with rendering)???

References:
6.10 completely up to date...
bios 1011
motherboard asus k8n (nforce3 chipset)
Windows trick: after boot in windows and reboot in linux, the driver works 100% fine
lsmod points fglrx not using amd64_agp  (with option UseInternalAGPGART setting no). fglrx tries to use agpgart directly...
Reference Threads:
[http://www.ubuntuforums.org/showthread.php?t=143855](http://www.ubuntuforums.org/showthread.php?t=143855)
[http://www.ubuntuforums.org/showthread.php?t=122874](http://www.ubuntuforums.org/showthread.php?t=122874)

Thx

---

### Post by Drachen on 2006-12-19
Hi!

I got the same problem but with an Asus A9250 (ATI 9250).

I was able to put the 3D working with the ATI Driver ( open-source driver) but everything was very slow. So I tried (again) the fglrx driver and I followed every tutorial in the internet and I think that the problem is with tha AGP modules.

Any help? Please :confused:

---

### Post by alanrr_sr on 2006-12-31
Hi,

No solution yet.... i believe itis a AGP module problem too... but I am not smart enough too look/find a way to fix that...

For now, one important lesson...ATI no more, too much work, and I can not believe then anymore

---

