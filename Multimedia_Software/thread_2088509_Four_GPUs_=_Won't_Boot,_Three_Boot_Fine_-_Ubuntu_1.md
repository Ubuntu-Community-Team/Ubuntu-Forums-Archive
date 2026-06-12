---
title: "Four GPUs = Won't Boot, Three Boot Fine - Ubuntu 11.10 64-bit"
date: 2012-11-26
forum: Multimedia Software
---

### Post by n8n8 on 2012-11-26
Hi All,

I'm running a Tyan S8225 motherboard and 4 GTX295 GPUs.   The system is dual boot 64-bit Windows 7/Ubuntu 11.10, and Windows recognizes all the  cards just fine.  Ubuntu won't do anything after grub boot selection  when there are 4 GPUs present, but will boot fine after removing one of  them.  Sometimes it goes to a blinking cursor, sometimes it goes to a greyish-black screen (monitor not off)

I also have an Aspeed integrated graphics interface (that  I'd love to drive display with, while using all the GPUs for  computation) but can't seem to get the nVidia cards to show up if I give  it (the integrated graphics) preference in the BIOS.

I've disabled the nouveau driver and installed the CUDA drivers...

I've  tried booting to into single user mode, but it won't even do that if  there are 4 (really 8 i.e. /dev/nvidia0 - /dev/nvidia8 ) gpu cards present.

If anyone has any ideas on how to solve this so that all the GPUs are recognized and the system boots, I'd love to hear them!

Thanks!

---

