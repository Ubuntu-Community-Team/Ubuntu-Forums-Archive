---
title: "VIA EPIA-SP 8000 with Netgear WG311v3 and NDISWRAPPER"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by dorkxer on 2009-06-18
Hi,

I have been struggling with trying to get my Netgear WG311v3 running under Ubuntu 9.04 with ndiswrapper  on my mini-itx VIA EPIA-SP 8000. I have the win32 drivers installed and ndiswrapper -l says that the device is present. Upon running "sudo modprobe ndiswrapper" kern.log shows that the device has been found and setup, but then the system hangs. If I sit at TTY1 I can see bug messages that the CPU has been stuck for 61 seconds. 

I have tried changing BIOS settings for IRQs and have had no success. Has anyone successfully gotten this wireless card to work on an EPIA-SP or does anyone have any ides for me to try?

I appreciate the support in advance.

---

