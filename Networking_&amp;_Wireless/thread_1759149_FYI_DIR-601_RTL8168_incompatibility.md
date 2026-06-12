---
title: "FYI: DIR-601 RTL8168 incompatibility"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by celem on 2011-05-15
FYI - I am posting this to help anyone with a similar problem.

I finally resolved a compatibility issue between the D-Link DIR-601 router and the Realtek RTL8111/8168B NIC. My system has worked great for its two-year life until I swapped out the motherboard to a MSI 770T-C35 e/w a Realtek RTL8111/8165B Ethernet controller. The Internet had VERY slow connect times - 15 to 20 seconds, frequently with timeouts. A retry would usually result in an instant load. I went to Realtek and installed their latest Linux r8168 driver and followed both their instructions and those at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/208012]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/208012") to no avail - the problem remained. Mind you, another Ubuntu computer connected to the same router had no such problems - it was unique to the combination of D-Link DIR-601 router and Realtek RTL8111/8168B NIC.

Finally, I went to the D-Link site and downloaded the latest firmware, version 1.02NA. My current version was 1.00NA.

Upgrading the D-Link DIR-601 router resolved my problem. I don't know if the r8168 Realtek driver had any impact or not - I am not going to reinstall the old r8169 driver.

---

