---
title: "AAO A110 Netbook accelerated graphics drivers for Ubuntu 13.10??"
date: 2014-01-14
forum: Multimedia Software
---

### Post by TNFrank on 2014-01-14
So where can I find some Intel Accelerated Graphic Drivers for my Acer Aspire One ZG5 A110 to bump the video graphics memory up from it's current 8MB to the 244MB that I read about?  Thanks.

---

### Post by TNFrank on 2014-01-15
Ok, just in case ya'll don't understand what I'm looking for here's a link to the article I read about upgrading the Acer Aspire One.
[http://www.virtualsecrets.com/acer-aspire-one-netbook.html](http://www.virtualsecrets.com/acer-aspire-one-netbook.html)
Scroll down about half way and you'll find this:
"I was not impressed with the 8MB  integrated graphics card memory size.  That proved to be a short-lived  problem...after I installed the** Intel Graphics Media Accelerator Driver  for Mobile (Mobile Intel 945 Express Chipset Family) - driver version  6.14.10.4926 - the available graphics memory went from 8MB to 224MB!**   That is what I like to see."
This is what I'm looking for only for Linux(i.e. Ubuntu) and not Windows. Anyone?

---

### Post by sireangelus on 2014-01-16
First, there are no driver to install. All linux intel graphics driver are open source only and are a deep integrated part of the stack, from the kernel to mesa; I'd say that to update those with latest and gratest( and probably betas) software is of medium difficulty, but very hard to fix in case problem arises. Lucky for you, the ram you seek is already there; The driver/bios(not sure which) automatically increases or decreases the amount of ram the gpu can use depending on the case, from a 8mb minimum (or you wouldn't be able to see the bios splash screen/grub/whatever loading bootloard you have) to the standard 40-50 normally required to do the job in case of a compositing window manager, up to those 224 should a program ever require them.

---

### Post by TNFrank on 2014-01-23
So basically what you're saying is that the amount of RAM used for video is automatic depending on the needs of the system. That's good to know. Thanks for the info.

---

### Post by Yellow Pasque on 2014-01-23
Intel calls it DVMT (Dynamic video memory technology): [https://en.wikipedia.org/wiki/DVMT](https://en.wikipedia.org/wiki/DVMT)

Please mark thread solved.

---

