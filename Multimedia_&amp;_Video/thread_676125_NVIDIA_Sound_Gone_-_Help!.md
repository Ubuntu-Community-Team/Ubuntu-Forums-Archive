---
title: "NVIDIA Sound Gone - Help!"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by oolunchbox on 2008-01-23
I've lost sound in Kubuntu Gutsy. I was having problems running compiz so I upgraded to the newest video drivers from Nvidia's website and upon reboot I was sent into an endless loop of logging in and being kicked back out. When I installed the drivers I forgot to uninstall the old ones first, so I went through and uninstalled all of the Nvidia drivwers, logged in using the nv driver and re-enabeled the nvidia driver using the restricted drivers manager. I finally got everything working (so i thought) only to discover that I have lost my sound. I've tried downloading the nforce drivers from Nvidia's website but those do not install. 

lspci -v
returns:
```
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81f2
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```
I'm running an Asus CROSSHAIR motherboard on Kubuntu Gutsy. I'd prefer not to reinstall if I can avoid it. I've also tried the steps outlined in the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is") thread with no luck. Any advice?

---

### Post by oolunchbox on 2008-01-23
Bump

---

