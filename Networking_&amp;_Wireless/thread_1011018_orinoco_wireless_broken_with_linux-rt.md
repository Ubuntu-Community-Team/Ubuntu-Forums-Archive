---
title: "orinoco wireless broken with linux-rt"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by ninjabob7 on 2008-12-14
I'm trying to install the linux-rt kernel so I can record audio, but I've been having a few problems. First there was the NVIDIA problem. I installed the kernel headers so that I could fix it, and it mysteriously fixed itself. Whatever.
Now the problem is my wireless. It appears to work - the settings are fine - but the ping time to my router is around 8000 ms (not a typo). I tried to do ifdown and ifup, but ifdown hangs until ^C and ifup hangs despite ^C. I'm using the orinoco_pci driver, which is loaded and works fine under the generic kernel, and I use ifup and ifdown to configure it. In addition, I'm on an amd64 system, which could further complicate the issue.

---

