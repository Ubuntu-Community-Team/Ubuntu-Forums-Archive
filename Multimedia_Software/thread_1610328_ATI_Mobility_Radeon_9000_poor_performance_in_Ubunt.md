---
title: "ATI Mobility Radeon 9000 poor performance in Ubuntu 10.10 Maverick"
date: 2010-10-31
forum: Multimedia Software
---

### Post by aks_ on 2010-10-31
Hi all,

I'm on an oldish laptop, HP Pavilion zv5000, 3.0 ghz cpu, ~1gb memory, with an ATI Mobility Radeon 9000 video card. I just migrated to Ubuntu Maverick after a windows trojan fiasco. Everything is great except for the video performance. The default gui is slow and loads the cpu quite a bit, scrolling is choppy, flash movies lag. I've heard that installing the fglrx ATI proprietary drivers may fix this, but there is a problem. According to thinkwiki ([http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_9000](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_9000)) the latest fglrx version to support the Mobility Radeon 9000 is 8.28.8. But this version won't even install on Maverick, and even if it did it apparently does not support kernels newer than 2.6.17. I have two questions:

1. What might be some ways to improve visual performance with this card in Ubuntu Maverick?

2. When it comes to fglrx 8.28.8, is there a way to force it to install and work under Maverick? What gives me hope is a patch posted by zasf a few years back that forces the drivers to install under Dapper with kernel >= 2.6.17 ([http://ubuntuforums.org/showthread.php?t=240892](http://ubuntuforums.org/showthread.php?t=240892)). But the patch doesn't apply to later releases. Does anyone know how something similar might be done under Maverick?

Thanks,

Alex

---

### Post by ajgreeny on 2010-10-31
I am a bit surprised that you find the performance of maverick on that graphic card so slow, though I accept that it is never going to be a real racer, but then it wasn't with Windows XP either.

As for a different driver, I'm afraid you have no choice; as you say the ATI Proprietary drivers do not support that card any more.

I have an Acer Travelmate with the same card and find it perfectly acceptable with maverick, though I could not run lucid as it overheated very badly, and karmic was very slow unless I ran at 16 bit colour.  I am therefore very pleased with the performance of this laptop with maverick; it is a great improvement on the last two ubuntu versions.

PS:  This machine only has a Celeron D 330 cpu, and 512 MB ram, some of which is shared, but nevertheless it runs very well for such a low spec laptop.  I wonder therefore if your slow performance is a result of some other hardware incompatibility, or is perhaps because of your very high expectations for such a low spec gpu.

---

### Post by Yellow Pasque on 2010-10-31
You might want to post /var/log/Xorg.0.log and maybe output of:
```
export LIBGL_DEBUG=verbose; glxinfo
```

> When it comes to fglrx 8.28.8, is there a way to force it to install and work under Maverick?
No. That's a dead-end.

---

### Post by aks_ on 2010-11-01
Thanks for the quick responses. ajgreeny, I agree with you that the performance is very acceptable, much better than I remember it being with Hardy. My most immediate point of comparison is Windows XP though, and Maverick doesn't do as well, especially when it comes to playing flash and other movies, which were very smooth in Windows. Here things are choppy, frames drop, etc.

Temüjin, thanks, I've attached the files.

---

