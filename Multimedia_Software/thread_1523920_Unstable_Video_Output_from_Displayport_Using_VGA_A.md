---
title: "Unstable Video Output from Displayport Using VGA Adapter"
date: 2010-07-04
forum: Multimedia Software
---

### Post by mrfuzzemz on 2010-07-04
I'm getting a very unstable video response from a Dell Studio 14z laptop via a displayport to VGA(standard DB-15) connection. I have a StarTech DP2VGA adapter and, while it connects, the picture flashes black for a few seconds multiple times a minute.

I'm using Lucid 10.04 64-bit and had the same issues with previous editions of Ubuntu. I don't seem to have this problem in Windows 7, so I rule out it being a hardware issue.

System:
Nvidia Geforce 9400m G using the latest NVidia drivers, 256.35 (previous versions had the same problem)

Any help is appreciated and I'm willing to post any output that may provide more insight.

Thanks

EDIT: I've noticed that during the configuration activating the DP->VGA attached display, the following is deposited in /var/log/Xorg.0.log:

> (II) Jul 04 12:58:18 NVIDIA(0): Setting mode
(II) Jul 04 12:58:18 NVIDIA(0):     "DFP-0:nvidia-auto-select@1600x900+1680+0,DFP-3:1680x1050_60@1680x1050+0+0"
(WW) Jul 04 12:58:19 NVIDIA(GPU-0): Acer AL2216W (DFP-3): Failed to set DisplayPort power state
(WW) Jul 04 13:07:00 NVIDIA(GPU-0): Acer AL2216W (DFP-3): Failed to set DisplayPort power state

---

