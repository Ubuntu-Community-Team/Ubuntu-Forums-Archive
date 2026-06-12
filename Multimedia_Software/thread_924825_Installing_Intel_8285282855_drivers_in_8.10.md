---
title: "Installing Intel 82852/82855 drivers in 8.10"
date: 2008-09-19
forum: Multimedia Software
---

### Post by devosion on 2008-09-19
I just downloaded the latest graphics drivers for this laptop card from here:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=922&DwnldID=8203&strOSs=39&OSFullName=Linux*&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=922&DwnldID=8203&strOSs=39&OSFullName=Linux*&lang=eng")

Problem is when I run install.sh it tells me:

> 
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


This is what it has in the log file:

> make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/devosion/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/devosion/dripkg/agpgart-2.0/backend.o
/home/devosion/dripkg/agpgart-2.0/backend.c:69: error: conflicting types for &#8216;agp_backend_acquire&#8217;
include/linux/agp_backend.h:110: error: previous declaration of &#8216;agp_backend_acquire&#8217; was here
/home/devosion/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for &#8216;agp_backend_acquire&#8217;
include/linux/agp_backend.h:110: error: previous declaration of &#8216;agp_backend_acquire&#8217; was here
/home/devosion/dripkg/agpgart-2.0/backend.c:89: error: conflicting types for &#8216;agp_backend_release&#8217;
include/linux/agp_backend.h:111: error: previous declaration of &#8216;agp_backend_release&#8217; was here
/home/devosion/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for &#8216;agp_backend_release&#8217;
include/linux/agp_backend.h:111: error: previous declaration of &#8216;agp_backend_release&#8217; was here
/home/devosion/dripkg/agpgart-2.0/backend.c:220: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;drm_agp&#8217;
/home/devosion/dripkg/agpgart-2.0/backend.c: In function &#8216;agp_add_bridge&#8217;:
/home/devosion/dripkg/agpgart-2.0/backend.c:281: error: implicit declaration of function &#8216;inter_module_register&#8217;
/home/devosion/dripkg/agpgart-2.0/backend.c:281: error: &#8216;drm_agp&#8217; undeclared (first use in this function)
/home/devosion/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/devosion/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/devosion/dripkg/agpgart-2.0/backend.c: In function &#8216;agp_remove_bridge&#8217;:
/home/devosion/dripkg/agpgart-2.0/backend.c:301: error: implicit declaration of function &#8216;inter_module_unregister&#8217;
make[2]: *** [/home/devosion/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/devosion/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/devosion/dripkg/drm'
make -C /lib/modules/2.6.24-19-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
rm: cannot remove `/home/devosion/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/devosion/dripkg/drm'
make: *** [gdg.ko] Error 2


And this is after installing the linux headers, linux headers lum, linux restricted modules, and the linux ubuntu modules. What gives? :(

---

### Post by Xyonofcalhoun on 2009-05-02
*bump*

I have the same issue, and no idea how to fix it. I did get it installed once on a previous install, but I have even less idea how that happened.

OpenGL errors are annoying the crap out of me, I'm hoping installing this will fix them. My install errors are identical to OP.

---

