---
title: "Why would lwjgl think nvidia kernel module is different than installed version?"
date: 2012-04-22
forum: Multimedia Software
---

### Post by efflandt on 2012-04-22
64-bit 11.10 w/x-swat repository for nvidia.  I get error below in a java game (minecraft), but the game still works fine.  In an earlier game version OpenGL On used to run faster than OpenGL Off.  Recently OpenGL On runs about 1/10th the speed of having it off (around 15-20 fps vs. 150+ fps).

```
LWJGL Version: 2.6
Error: API mismatch: the NVIDIA kernel module has version 295.33, but this NVIDIA driver component has version 295.40.  Please make sure that the kernel module and all NVIDIA driver components have the same version.
Loading: net.java.games.input.LinuxEnvironmentPlugin
```**uname -a**
Linux XPS-8100-1110 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

**dpkg-query -l nvidia***
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
un  nvidia-173                  <none>                      (no description available)
un  nvidia-180-modaliases       <none>                      (no description available)
un  nvidia-185-modaliases       <none>                      (no description available)
un  nvidia-96                   <none>                      (no description available)
ii  nvidia-common               1:0.2.35                    Find obsolete NVIDIA drivers
ii  nvidia-current              295.40-0ubuntu1~oneiric~xup NVIDIA binary Xorg driver, kernel module and VDPAU library
un  nvidia-current-modaliases   <none>                      (no description available)
un  nvidia-libvdpau             <none>                      (no description available)
un  nvidia-libvdpau-ia32        <none>                      (no description available)
un  nvidia-libvdpau1            <none>                      (no description available)
un  nvidia-libvdpau1-ia32       <none>                      (no description available)
ii  nvidia-settings             295.40-0ubuntu1~oneiric~xup Tool of configuring the NVIDIA graphics driver
un  nvidia-va-driver            <none>                      (no description available)
un  nvidia-vdpau-driver         <none>                      (no description available)
un  nvidia-vdpau-driver-ia32    <none>                      (no description available)
```How would I tell which nvidia kernel module version is actually being used (nomodeset), or where lwjgl gets that 295.33 from, when everything tells me I have nvidia 295.40 installed?

---

