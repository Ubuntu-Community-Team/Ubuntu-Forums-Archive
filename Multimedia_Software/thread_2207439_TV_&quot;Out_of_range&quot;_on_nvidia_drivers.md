---
title: "TV: &quot;Out of range&quot; on nvidia drivers"
date: 2014-02-23
forum: Multimedia Software
---

### Post by aso824 on 2014-02-23
Hi,
I'm using Ubuntu 13.10 with Nvidia 319.60 driver (binary installer). My graphic card is 8600GT.
I'm trying to configure TV - Sony Bravia KDL-26B40xx - to work with this graphic card. Current, I have connected it with HDMI cable (DVI->HDMI conventer, ATI brand), also tried on VGA cable. TV says "Out of range". I tried all resolutions and modes, changed display mode in TV... without results.

HDMI cable is correct, because I connected it to my laptop with Debian 8 and Intel graphic, and works like a charm. 
What can be a problem? I will try Windows tomorrow to check conventer and graphic card port, but I think it's driver problem.

Thanks for help,
aso

**SOLVED**
I booted computer with HDMI only but on second DVI port and works good.
Probably problem is in NVIDIA graphic card, it can send correct HDMI signal only on one DVI port. 
I still have issues with 1080i signal, but on 1360x768 it works great.

---

