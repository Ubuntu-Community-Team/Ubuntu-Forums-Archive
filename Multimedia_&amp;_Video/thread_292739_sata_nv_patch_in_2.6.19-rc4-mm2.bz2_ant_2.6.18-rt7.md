---
title: "sata_nv patch in 2.6.19-rc4-mm2.bz2 ant 2.6.18-rt7"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by floogy on 2006-11-04
Hi, how can I get a patched kernel with realtime Preemtion and a working sata_nv with adma support?

Is everything I need already in 2.6.19-rc4-mm2.bz2 ??

I'm not sure about that :-(


[http://lwn.net/Articles/203532/](http://lwn.net/Articles/203532/)
[2.6.19-rc4-mm2:linux/kernel/hrtimer.c]("http://www.kernel.org/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fpeople%2Fakpm%2Fpatches%2F2.6%2F2.6.19-rc4%2F2.6.19-rc4-mm2%2F2.6.19-rc4-mm2.bz2;z=2205")
[2.6.19-rc4-mm2:devel/Documentation/hrtimer/highres.txt]("http://www.kernel.org/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fpeople%2Fakpm%2Fpatches%2F2.6%2F2.6.19-rc4%2F2.6.19-rc4-mm2%2F2.6.19-rc4-mm2.bz2;z=30")
[2.6.19-rc4-mm2:linux-2.6.19-rc4/Documentation/hrtimers.txt]("http://www.kernel.org/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fpeople%2Fakpm%2Fpatches%2F2.6%2F2.6.19-rc4%2F2.6.19-rc4-mm2%2F2.6.19-rc4-mm2.bz2;z=33")

[ 2.6.19-rc4-mm2:linux/drivers/ata/sata-nv.c]("http://www.kernel.org/diff/diffview.cgi?file=%2Fpub%2Flinux%2Fkernel%2Fpeople%2Fakpm%2Fpatches%2F2.6%2F2.6.19-rc4%2F2.6.19-rc4-mm2%2F2.6.19-rc4-mm2.bz2;z=555")

[http://www.linuxsymposium.org/2006/linuxsymposium_procv1.pdf](http://www.linuxsymposium.org/2006/linuxsymposium_procv1.pdf)
[http://tglx.de/projects/hrtimers/ols2006-hrtimers.pdf](http://tglx.de/projects/hrtimers/ols2006-hrtimers.pdf)

---

### Post by damu on 2006-11-07
I have a kind of similar question. I decided to go for the easy option for the kernel on my new install of Ubuntu 64 bits. After installing edgy, I upadted my sources list to feisty and updated to kernel 2.6.19. 
I had better results for audio with the stock kernel of dapper or edgy (2.6.17). It's been mentionned though that from kernel 2.6.18 onwards, the rt optimization would already be implemented. Is it really the case?

---

