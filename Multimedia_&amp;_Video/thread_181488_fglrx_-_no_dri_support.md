---
title: "fglrx - no dri support"
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by mich-a on 2006-05-24
Hi,
Im running ubuntu dapper on my notebook Thinkpad t43p.
Once i installed from scratch and added fglrx support using the 
shipped drivers (linux-restricted-modules and xorg-driver-fglrx) everything 
has been working fine 

[INDENT]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FireGL V3200 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.5755 (8.24.8)
[/INDENT]
.
nevertheless i tried to install the drivers from ati. ](*,) but x did not start anymore. 
after this i never managed to get hardware acceleration even when 
removing ati drivers and switching back to the ubuntu shipped  drivers.
[INDENT]fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
[/INDENT]
 
i reinstalled dapper from scratch on another partition and everiting was working fine again. i compared  dmesg and xorg.log 
no errors 
the output is nearly the same on both intallations.
Im using the same xorg.conf on both installations 

i spent so much effort in my *old* installation that i dont wanna loose it.

here the logs of the messed up system
**dmesg | grep fglrx**
[4294699.428000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294699.430000] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[4294699.431000] [fglrx] module loaded - fglrx 8.24.8 [Apr 11 2006] on minor 0
[4294700.733000] [fglrx] free  PCIe = 54804480
[4294700.733000] [fglrx] max   PCIe = 54804480
[4294700.733000] [fglrx] free  LFB = 108908544
[4294700.734000] [fglrx] max   LFB = 108908544
[4294700.734000] [fglrx] free  Inv = 0
[4294700.734000] [fglrx] max   Inv = 0
[4294700.734000] [fglrx] total Inv = 0(II) 

**and the xorg.log is attached **[ATTACH]9966[/ATTACH]

---

