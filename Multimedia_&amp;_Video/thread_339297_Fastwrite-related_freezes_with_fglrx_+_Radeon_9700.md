---
title: "Fastwrite-related freezes with fglrx + Radeon 9700 Pro"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by mcwitt on 2007-01-15
I am experiencing frequent random freezes when using the fglrx driver, which seem to occur more frequently when doing direct rendering. I have had the same problem in Windows, which seems to be related to problems in the fast-write support of my motherboard (Intel E7205-based). In that case, disabling fast writes on the driver control panel fixed the problem. 

I have googled far and wide, but have been unable to figure out how to disable fast-writes with fglrx. Following instructions on [http://www.rage3d.com/board/showthread.php?t=33793288](http://www.rage3d.com/board/showthread.php?t=33793288), I tried to disable FW via AGPMasks in my xorg.conf, but to no avail (dmesg | grep AGPCommand still shows the FW bit enabled and I still get the crashes).

The agpgart module seems to interfere with fglrx's internal AGPGART, not allowing it to load and thus not disabling FW. I have tried blacklisting agpgart and intel_agp, but agpgart is loaded anyway, and a message from fglrx says that internal AGP is not supported in the 2.6 kernel.

I have been fighting this problem for a long time and would greatly appreciate any suggestions.

card: ATI Radeon 9700 Pro
fglrx version: 8.28.8
kernel version: 2.6.17-10-generic

---

