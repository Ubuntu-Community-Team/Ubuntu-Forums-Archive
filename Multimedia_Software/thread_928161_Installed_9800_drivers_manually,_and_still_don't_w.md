---
title: "Installed 9800 drivers manually, and still don't work"
date: 2008-09-23
forum: Multimedia Software
---

### Post by keres on 2008-09-23
i managed to finally get the NVIDIA-Linux-x86-71.86.06-pkg1 driver installed to my system under "sudo sh NVIDIA* -k $(uname -r)", and it seemed to install properly after i got all of the neccessary runtime files for it.

Anyway, it says

```
installation of the NVIDIA accelerated graphics driver for linux-x86 (version: 71.86.06) is now complete. Please update xf86config or /usr/share/doc/NVIDIA_GLX-1.0/README for details

```

whilst /usr/share/doc/NVIDIA_GLX-1.0/README displays:

```
NVIDIA Accelerated Linux Driver Set README & Installation Guide

Last Updated: $Date: 2007/12/04 $
Most Recent Driver: 71.86.06


The NVIDIA Accelerated Linux Driver Set brings both accelerated 2D
functionality and high performance OpenGL support to Linux x86 with the
use of NVIDIA graphics processing units (GPUs).

These drivers provide optimized hardware acceleration of OpenGL
applications via a direct-rendering X Server and support nearly all
NVIDIA graphics chips (please see APPENDIX A for a complete list of
supported chips).  TwinView, TV-Out and flat panel displays are also
supported.

This README describes how to install, configure, and use the NVIDIA
Accelerated Linux Driver Set.  This file is posted on NVIDIA's web site
(www.nvidia.com), and is installed in /usr/share/doc/NVIDIA_GLX-1.0/.


__________________________________________________________________________

"/usr/share/doc/NVIDIA_GLX-1.0/README" [readonly] 3726L, 165368C


```

so it seems the drivers should be working. right?
wrong.
i go to system->administration->hardware drivers and it lists the nvidia driver as check marked and labeled as "not in use", STILL!

where to go from now? 

if i disable/re-enable it, i have to reset xorg.conf like i have twice already.

please help

thanks
-keres

---

### Post by keres on 2008-09-23
bump for help

---

