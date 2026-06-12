---
title: "nVidia Install Problem"
date: 2005-12-14
forum: Multimedia &amp; Video
---

### Post by engti on 2005-12-14
hi,

I managed to logon using the vesa driver into my ubuntu, which it wasn't doing earlier.
Now I have the nvidia driver installer on my desktop, and I used terminal to run it using sudo.
It tells me that something called "ld" is missing.
Is this the universe/multiverse thing, cos i think i enabled those.

I also cannot access my ntfs partitions, cause somebody named "root" has the permission. i cant access it, or mount it or unmount it. Nothing, nada.



Help, if i have to go through another installation manual, i'll drown. :D 

Thanks a lot.

My system spec is:
AMD 3000+
Asus A8-NE
nVidia 6600 PCIe
200 GB Hdd
1gb RAM

---

### Post by daller on 2005-12-14
Have you installed "nvidia-glx"?

Ran "sudo nvidia-glx-config enable"?

---

