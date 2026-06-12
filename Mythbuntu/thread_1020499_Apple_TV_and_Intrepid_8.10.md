---
title: "Apple TV and Intrepid 8.10"
date: 2008-12-24
forum: Mythbuntu
---

### Post by Jim Sahm on 2008-12-24
Hello all,

First let me say that Mythbuntu is awsome... very nicely done!

I'm struggling to find a way to smooth out HD on it.  I've it has the Nvidia 7300 series card in it... One of the items left to do to smooth out XvMC is to underclock the GPU.

I tried to install Nvidia 169.09 driver, but it will not compile a module on Intrepid 8.10 (Mythbuntu 8.10) ... Does anyone have a good Nvidia driver to recommend for 8.10 that will allow underclocking/proper use of the XvMC display options??

Thanks, and Merry Christmas,
Jim


The log file says:

   /tmp/selfgz6573/NVIDIA-Linux-x86-169.09-pkg1/usr/src/nv/nv.c:1286: error: to
   o many arguments to function ‘smp_call_function’
   /tmp/selfgz6573/NVIDIA-Linux-x86-169.09-pkg1/usr/src/nv/nv.c:1293: error: to
   o many arguments to function ‘smp_call_function’
   /tmp/selfgz6573/NVIDIA-Linux-x86-169.09-pkg1/usr/src/nv/nv.c: In function 
   &#65533;nv_kern_vma_nopage’:
   /tmp/selfgz6573/NVIDIA-Linux-x86-169.09-pkg1/usr/src/nv/nv.c:1832: error: 
   &#65533;NOPAGE_SIGBUS’ undeclared (first use in this function)
   /tmp/selfgz6573/NVIDIA-Linux-x86-169.09-pkg1/usr/src/nv/nv.c: At top level:
   /tmp/selfgz6573/NVIDIA-Linux-x86-169.09-pkg1/usr/src/nv/nv.c:1839: error: un
   known field ‘nopage’ specified in initializer
   /tmp/selfgz6573/NVIDIA-Linux-x86-169.09-pkg1/usr/src/nv/nv.c:1839: warning: 
   initialization from incompatible pointer type
   make[3]: *** [/tmp/selfgz6573/NVIDIA-Linux-x86-169.09-pkg1/usr/src/nv/nv.o] 
   Error 1
   make[2]: *** [_module_/tmp/selfgz6573/NVIDIA-Linux-x86-169.09-pkg1/usr/src/n
   v] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.

---

### Post by ian dobson on 2008-12-24
Hi,

I just installed the standard/recommended NVidia driver through the control center and can playback HD (1080i) on my E5200 (2.5GHz Core2Duo) with about 50% load.

I think XvMC is only for MPEG2 I'm not sure if it'll help much for HD as here in Switzerland HD is transmitted as h264.

vdpau should help with hardware assisted decoding of h264 but the NVidia driver is still in beta and the patches for it are only in Myth ver 22, so maybe we need to wait for 9.04.

Regards
Ian Dobson

---

