---
title: "about a 3D viewer program on ubuntu"
date: 2011-03-16
forum: Multimedia Software
---

### Post by seawinds on 2011-03-16
Hi all,

[LEFT]I need to run a 3D viewer program on my ubuntu 10.04. It worked for a while, and then crashed. I guess because some update or my graphic driver. When I typed "lspci -v", it gives: 

00:00.0 Host bridge: Intel Corporation 82G35 Express DRAM Controller (rev 03)
    Subsystem: Intel Corporation Device d701
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
    Subsystem: Intel Corporation Device d701
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at e0200000 (32-bit, non-prefetchable) [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 2440 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
    Subsystem: Intel Corporation Device d701
    Flags: bus master, fast devsel, latency 0
    Memory at e0100000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

When I try to open the 3-D viewer program, it gives: 

Info) Multithreading available, 2 CPUs detected.
Info) Free system memory: 3505MB (88%)
Info) No CUDA accelerator devices available.
Warning) Detected X11 'Composite' extension: if incorrect display occurs
Warning) try disabling this optional X server feature.
Xlib:  extension "GLX" missing on display ":0.0".
ERROR) The X server does not support the OpenGL GLX extension.   Exiting ...
Info) VMD for LINUXAMD64, version 1.8.7 (August 1, 2009)
Info) Unable to create OpenGL window.


Since I am new to ubuntu, I tried my best to search on the internet to find ways to solve the problem but failed. Please help me! Thanks a lot!!
[/LEFT]

---

### Post by Claus7 on 2011-03-31
Hello and welcome to the forums!

I had faced a similar issue a long time ago. Hope this:
[http://ubuntuforums.org/showthread.php?t=1098590](http://ubuntuforums.org/showthread.php?t=1098590)

to give you a hint about the opengl problem and how to solve it. It is not an easy task for a beginner though...

Regards!

---

