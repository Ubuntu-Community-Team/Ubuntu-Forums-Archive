---
title: "problem with gspca (trying to set up webcam)"
date: 2009-03-25
forum: Multimedia Software
---

### Post by cisneros on 2009-03-25
I am trying to get a logitech webcam to work, and have gathered from other posts that I needed to use module assistant to install a module for gspca, but I get this in the module assistant.  I am very new to ubuntu, and would greatly appreciate simple instructions to try and get it to work.

this is the output from module assistant.

Thank you for any suggestions

dh_testdir                                                                 &#8593; 
   dh_testroot                                                                &#9646; 
   dh_clean                                                                   &#9618; 
   /usr/bin/make -C /usr/src/modules/gspca clean                              &#9618; 
   make[1]: Entering directory `/usr/src/modules/gspca'                       &#9618; 
   rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \                     &#9618; 
           .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \                  &#9618; 
           *.symvers *.err                                                    &#9618; 
   make[1]: Leaving directory `/usr/src/modules/gspca'                        &#9618; 
   /usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules 
   make[1]: Entering directory `/usr/src/modules/gspca'                       &#8593; 
   dh_testdir                                                                 &#9618; 
   dh_testroot                                                                &#9618; 
   dh_clean                                                                   &#9646; 
   /usr/bin/make -C /usr/src/modules/gspca clean                              &#9618; 
   make[2]: Entering directory `/usr/src/modules/gspca'                       &#9618; 
   rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \                     &#9618; 
           .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \                  &#9618; 
           *.symvers *.err                                                    &#9618; 
   make[2]: Leaving directory `/usr/src/modules/gspca'                        &#9618; 
   for templ in ; do \                                                        &#9618; 
       cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27-11-generic/g'` ; \   &#9618; 
     done                                                                     &#9618; 
   for templ in `ls debian/*.modules.in` ; do \                            
     test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in}   
  ${templ%.modules.in}.backup 2>/dev/null || true; \                         &#8593;
      sed -e 's/##KVERS##/2.6.27-11-generic/g                                &#9618;
  ;s/#KVERS#/2.6.27-11-generic/g ; s/_KVERS_/2.6.27-11-generic/g ;           &#9618;
  s/##KDREV##/2.6.27-11.27/g ; s/#KDREV#/2.6.27-11.27/g ;                    &#9618;
  s/_KDREV_/2.6.27-11.27/g  ' < $templ > ${templ%.modules.in}; \             &#9618;
    done                                                                     &#9618;
  dh_testdir                                                                 &#9646;
  dh_testroot                                                                &#9618;
  dh_clean -k                                                                &#9618;
  # Build the module                                                         &#9618;
  /usr/bin/make -C /usr/src/modules/gspca KERNEL_VERSION=2.6.27-11-generic   &#9618;
  KERNELDIR=/usr/src/linux-headers-2.6.27-11-generic                         &#9618;
  make[2]: Entering directory `/usr/src/modules/gspca'                       &#9618;
  /usr/bin/make -C /usr/src/linux-headers-2.6.27-11-generic                  &#9618;
  SUBDIRS=/usr/src/modules/gspca CC=gcc modules 
  make[3]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'     &#8593;
    CC [M]  /usr/src/modules/gspca/gspca_core.o                              &#9618;
  /usr/src/modules/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No      &#9618;
  such file or directory                                                     &#9618;
  /usr/src/modules/gspca/gspca_core.c: In function ‘spca5xx_ioctl’:          &#9618;
  /usr/src/modules/gspca/gspca_core.c:2463: error: implicit declaration of   &#9618;
  function ‘video_usercopy’                                                  &#9618;
  /usr/src/modules/gspca/gspca_core.c: At top level:                         &#9618;
  /usr/src/modules/gspca/gspca_core.c:2609: error: unknown field ‘owner’     &#9618;
  specified in initializer                                                   &#9646;
  /usr/src/modules/gspca/gspca_core.c:2609: warning: initialization from     &#9618;
  incompatible pointer type                                                  &#9618;
  /usr/src/modules/gspca/gspca_core.c:2611: error: unknown field ‘type’      &#9618;
  specified in initializer                                                   &#9618;
  /usr/src/modules/gspca/gspca_core.c: In function ‘spca50x_create_sysfs’:                                                                       &#9474;
  /usr/src/modules/gspca/gspca_core.c:2769: error: implicit declaration of   &#8593;
  function ‘video_device_create_file’                                        &#9618;
  /usr/src/modules/gspca/gspca_core.c:2780: error: implicit declaration of   &#9618;
  function ‘video_device_remove_file’                                        &#9618;
  /usr/src/modules/gspca/gspca_core.c: In function ‘spca5xx_probe’:          &#9618;
  /usr/src/modules/gspca/gspca_core.c:4301: error: incompatible types in     &#9618;
  assignment                                                                 &#9618;
  make[4]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1                 &#9618;
  make[3]: *** [_module_/usr/src/modules/gspca] Error 2                      &#9618;
  make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'      &#9618;
  make[2]: *** [default] Error 2                                             &#9618;
  make[2]: Leaving directory `/usr/src/modules/gspca'                        &#9618;
  make[1]: *** [binary-modules] Error 2                                      &#9618;
  make[1]: Leaving directory `/usr/src/modules/gspca'                        &#9646;
  make: *** [kdist_build] Error 2

---

