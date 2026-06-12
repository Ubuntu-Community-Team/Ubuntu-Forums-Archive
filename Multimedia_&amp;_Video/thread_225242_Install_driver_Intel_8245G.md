---
title: "Install driver Intel 8245G"
date: 2006-07-29
forum: Multimedia &amp; Video
---

### Post by Comendante on 2006-07-29
Hallo

I have big problem with install drivers to my graphic card **Intel 8245G**. [I find drivers on this page](http://downloadcenter.intel.com/scripts-df-external/confirm.aspx?httpDown=http://downloadmirror.intel.com/df-support/8203/eng/i915Graphics.tar.gz&agr=&ProductID=865&DwnldId=8203&strOSs=&OSFullName=&lang=eng). This files ar in tar.gz formats.

I unpack files in :
**/home/mateusz/dripkg**

In consol I write :

1. **cd /home/mateusz/dripkg**
2. **./install.sh**

But I have problem , because when Instalation start I see :

> The script will now compile the agpgart module and DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

root@mateusz:/home/mateusz/dripkg

And this is a file dir.log :

> make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/mateusz/dripkg/agpgart-2.0 modules
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.15-26-386'
CC [M] /home/mateusz/dripkg/agpgart-2.0/backend.o
/home/mateusz/dripkg/agpgart-2.0/backend.c:69: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/mateusz/dripkg/agpgart-2.0/backend.c:89: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/mateusz/dripkg/agpgart-2.0/backend.c:220: error: syntax error before ‘drm_agp’
/home/mateusz/dripkg/agpgart-2.0/backend.c:220: warning: type defaults to ‘int’ in declaration of ‘drm_agp’
/home/mateusz/dripkg/agpgart-2.0/backend.c:221: warning: initialization makes integer from pointer without a cast
/home/mateusz/dripkg/agpgart-2.0/backend.c:222: warning: excess elements in scalar initializer
/home/mateusz/dripkg/agpgart-2.0/backend.c:222: warning: (near initialization for ‘drm_agp’)
/home/mateusz/dripkg/agpgart-2.0/backend.c:223: warning: excess elements in scalar initializer
/home/mateusz/dripkg/agpgart-2.0/backend.c:223: warning: (near initialization for ‘drm_agp’)
/home/mateusz/dripkg/agpgart-2.0/backend.c:224: warning: excess elements in scalar initializer
/home/mateusz/dripkg/agpgart-2.0/backend.c:224: warning: (near initialization for ‘drm_agp’)
/home/mateusz/dripkg/agpgart-2.0/backend.c:225: warning: excess elements in scalar initializer
/home/mateusz/dripkg/agpgart-2.0/backend.c:225: warning: (near initialization for ‘drm_agp’)
/home/mateusz/dripkg/agpgart-2.0/backend.c:226: warning: excess elements in scalar initializer
/home/mateusz/dripkg/agpgart-2.0/backend.c:226: warning: (near initialization for ‘drm_agp’)
/home/mateusz/dripkg/agpgart-2.0/backend.c:227: warning: excess elements in scalar initializer
/home/mateusz/dripkg/agpgart-2.0/backend.c:227: warning: (near initialization for ‘drm_agp’)
/home/mateusz/dripkg/agpgart-2.0/backend.c:229: warning: excess elements in scalar initializer
/home/mateusz/dripkg/agpgart-2.0/backend.c:229: warning: (near initialization for ‘drm_agp’)
/home/mateusz/dripkg/agpgart-2.0/backend.c:229: warning: data definition has no type or storage class
/home/mateusz/dripkg/agpgart-2.0/backend.c: In function ‘agp_add_bridge’:
/home/mateusz/dripkg/agpgart-2.0/backend.c:281: warning: ‘inter_module_register’ is deprecated (declared at include/linux/module.h:571)
/home/mateusz/dripkg/agpgart-2.0/backend.c: In function ‘agp_remove_bridge’:
/home/mateusz/dripkg/agpgart-2.0/backend.c:301: warning: ‘inter_module_unregister’ is deprecated (declared at include/linux/module.h:572)
make[2]: *** [/home/mateusz/dripkg/agpgart-2.0/backend.o] B&#322;&#261;d 1
make[1]: *** [_module_/home/mateusz/dripkg/agpgart-2.0] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.15-26-386'
make: *** [default] B&#322;&#261;d 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Wej&#347;cie do katalogu `/home/mateusz/dripkg/drm'
+ ln -s Makefile.linux Makefile
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.15-26-386'
CC [M] /home/mateusz/dripkg/drm/gdg_drv.o
In file included from /home/mateusz/dripkg/drm/gdg_drv.c:12:
/home/mateusz/dripkg/drm/drmP.h:647:5: warning: "__HAVE_VBL_IRQ" is not defined
/home/mateusz/dripkg/drm/drmP.h:750:5: warning: "__HAVE_VBL_IRQ" is not defined
/home/mateusz/dripkg/drm/drmP.h:967:5: warning: "__HAVE_VBL_IRQ" is not defined
/home/mateusz/dripkg/drm/drmP.h:973:5: warning: "__HAVE_IRQ_BH" is not defined
/home/mateusz/dripkg/drm/drmP.h:1021:5: warning: "__HAVE_SG" is not defined
In file included from /home/mateusz/dripkg/drm/gdg_drv.c:17:
/home/mateusz/dripkg/drm/drm_agpsupport.h:47: error: syntax error before ‘*’ token
/home/mateusz/dripkg/drm/drm_agpsupport.h:47: warning: type defaults to ‘int’ in declaration of ‘drm_agp’
/home/mateusz/dripkg/drm/drm_agpsupport.h:47: warning: data definition has no type or storage class
/home/mateusz/dripkg/drm/drm_agpsupport.h: In function ‘gdg_agp_info’:
/home/mateusz/dripkg/drm/drm_agpsupport.h:69: error: request for member ‘copy_info’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h: In function ‘gdg_agp_acquire’:
/home/mateusz/dripkg/drm/drm_agpsupport.h:111: error: request for member ‘acquire’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h:117: error: request for member ‘acquire’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h: In function ‘gdg_agp_release’:
/home/mateusz/dripkg/drm/drm_agpsupport.h:140: error: request for member ‘release’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h:142: error: request for member ‘release’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h: In function ‘gdg_agp_do_release’:
/home/mateusz/dripkg/drm/drm_agpsupport.h:155: error: request for member ‘release’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h:156: error: request for member ‘release’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h: In function ‘gdg_agp_enable’:
/home/mateusz/dripkg/drm/drm_agpsupport.h:178: error: request for member ‘enable’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h:185: error: request for member ‘enable’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h: In function ‘gdg_agp_bind’:
/home/mateusz/dripkg/drm/drm_agpsupport.h:333: error: request for member ‘bind_memory’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h: In function ‘gdg_agp_init’:
/home/mateusz/dripkg/drm/drm_agpsupport.h:407: error: ‘drm_agp_t’ undeclared (first use in this function)
/home/mateusz/dripkg/drm/drm_agpsupport.h:407: error: (Each undeclared identifier is reported only once
/home/mateusz/dripkg/drm/drm_agpsupport.h:407: error: for each function it appears in.)
/home/mateusz/dripkg/drm/drm_agpsupport.h:407: error: syntax error before ‘)’ token
/home/mateusz/dripkg/drm/drm_agpsupport.h:412: error: request for member ‘copy_info’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h: In function ‘gdg_agp_uninit’:
/home/mateusz/dripkg/drm/drm_agpsupport.h:436: warning: ‘inter_module_put’ is deprecated (declared at include/linux/module.h:575)
/home/mateusz/dripkg/drm/drm_agpsupport.h: In function ‘gdg_agp_allocate_memory’:
/home/mateusz/dripkg/drm/drm_agpsupport.h:443: error: request for member ‘allocate_memory’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h:445: error: request for member ‘allocate_memory’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h:446: warning: control reaches end of non-void function
/home/mateusz/dripkg/drm/drm_agpsupport.h: In function ‘gdg_agp_free_memory’:
/home/mateusz/dripkg/drm/drm_agpsupport.h:451: error: request for member ‘free_memory’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h:453: error: request for member ‘free_memory’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h: In function ‘gdg_agp_bind_memory’:
/home/mateusz/dripkg/drm/drm_agpsupport.h:460: error: request for member ‘bind_memory’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h:462: error: request for member ‘bind_memory’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h:463: warning: control reaches end of non-void function
/home/mateusz/dripkg/drm/drm_agpsupport.h: In function ‘gdg_agp_unbind_memory’:
/home/mateusz/dripkg/drm/drm_agpsupport.h:468: error: request for member ‘unbind_memory’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h:470: error: request for member ‘unbind_memory’ in something not a structure or union
/home/mateusz/dripkg/drm/drm_agpsupport.h:471: warning: control reaches end of non-void function
In file included from /home/mateusz/dripkg/drm/gdg_drv.c:22:
/home/mateusz/dripkg/drm/drm_drv.h:246:5: warning: "__HAVE_VBL_IRQ" is not defined
In file included from /home/mateusz/dripkg/drm/gdg_drv.c:25:
/home/mateusz/dripkg/drm/drm_irq.h:137:5: warning: "__HAVE_IRQ_BH" is not defined
/home/mateusz/dripkg/drm/drm_irq.h:148:5: warning: "__HAVE_VBL_IRQ" is not defined
/home/mateusz/dripkg/drm/drm_irq.h:239:5: warning: "__HAVE_VBL_IRQ" is not defined
In file included from /home/mateusz/dripkg/drm/gdg_drv.c:28:
/home/mateusz/dripkg/drm/drm_memory.h: In function ‘drm_follow_page’:
/home/mateusz/dripkg/drm/drm_memory.h:139: warning: passing argument 1 of ‘pmd_offset’ from incompatible pointer type
In file included from /home/mateusz/dripkg/drm/gdg_drv.c:30:
/home/mateusz/dripkg/drm/drm_vm.h:79:5: warning: "__alpha__" is not defined
In file included from /home/mateusz/dripkg/drm/gdg_drv.c:30:
/home/mateusz/dripkg/drm/drm_vm.h: In function ‘gdg_mmap’:
/home/mateusz/dripkg/drm/drm_vm.h:625: warning: implicit declaration of function ‘remap_page_range’
In file included from /home/mateusz/dripkg/drm/gdg_drv.c:31:
/home/mateusz/dripkg/drm/drm_stub.h: In function ‘gdg_stub_putminor’:
/home/mateusz/dripkg/drm/drm_stub.h:145: warning: ‘inter_module_put’ is deprecated (declared at include/linux/module.h:575)
/home/mateusz/dripkg/drm/drm_stub.h:147: warning: ‘inter_module_unregister’ is deprecated (declared at include/linux/module.h:572)
/home/mateusz/dripkg/drm/drm_stub.h: In function ‘gdg_stub_register’:
/home/mateusz/dripkg/drm/drm_stub.h:177: warning: implicit declaration of function ‘inter_module_get’
/home/mateusz/dripkg/drm/drm_stub.h:188: warning: ‘inter_module_register’ is deprecated (declared at include/linux/module.h:571)
make[3]: *** [/home/mateusz/dripkg/drm/gdg_drv.o] B&#322;&#261;d 1
make[2]: *** [_module_/home/mateusz/dripkg/drm] B&#322;&#261;d 2
make[2]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.15-26-386'
make[1]: *** [modules] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/home/mateusz/dripkg/drm'
make: *** [gdg.ko] B&#322;&#261;d 2


I installed **gcc**,**linux-headers** but it still doesn't work.

---

