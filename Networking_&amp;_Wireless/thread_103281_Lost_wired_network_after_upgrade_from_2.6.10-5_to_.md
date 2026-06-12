---
title: "Lost wired network after upgrade from 2.6.10-5 to 2.6.10-6"
date: 2005-12-13
forum: Networking &amp; Wireless
---

### Post by sorceror171 on 2005-12-13
I performed an upgrade sometime late last week (sorry I can't be more precise, I think it ws Friday, but things were pretty hectic around here). Among other things, it installed a new kernel (2.6.10-6-k7-smp). After this, the system would hang for a while on boot while starting networking. Once booted, only the loopback interface is present. Other functions seem normal.

I tried reenabling the previous kernel (2.6.10-5-k7-smp) and booted into it (uname -a confirmed the kernel version) but still, no network. The boot messages via dmesg for both kernels look similar, with the e100 module loading apparently normally. No obvious problems in /var/log/messages, either.

I'm using Windows on the same machine to post this, so I'm pretty sure it's not a hardware issue. Any suggestions on where I should look to diagnose this problem?

---

