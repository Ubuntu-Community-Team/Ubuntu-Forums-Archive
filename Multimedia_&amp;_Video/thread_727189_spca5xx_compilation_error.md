---
title: "spca5xx compilation error"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by andrew2325 on 2008-03-17
When I use the module assistant to compile the spca5xx module for my webcam, I get the following output/error:

:
 dh_testdir                                                                 &#8593; 
 &#9474; dh_testroot                                                                
 &#9474; dh_clean                                                                   
 &#9474; /usr/bin/make -C /usr/src/modules/spca5xx clean                             
 &#9474; make[1]: Entering directory `/usr/src/modules/spca5xx'                     
 &#9474; rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \                  
 &#9474;         drivers/usb/.spca5xx.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i       
 &#9474; make[1]: Leaving directory `/usr/src/modules/spca5xx'                      
 &#9474; /usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules     
 &#9474; make[1]: Entering directory `/usr/src/modules/spca5xx'                     
 &#9474; dh_testdir                                                                 
 &#9474; dh_testroot                                                                 
 &#9474; dh_clean                                                                   
 &#9474; /usr/bin/make -C /usr/src/modules/spca5xx clean                             
 &#9474; make[2]: Entering directory `/usr/src/modules/spca5xx' 
 dh_testdir                                                                 
 &#9474; dh_testroot                                                                
 &#9474; dh_clean                                                                   
 &#9474; /usr/bin/make -C /usr/src/modules/spca5xx clean                            
 &#9474; make[2]: Entering directory `/usr/src/modules/spca5xx'                     
 &#9474; rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \                  
 &#9474;         drivers/usb/.spca5xx.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i      
 &#9474; make[2]: Leaving directory `/usr/src/modules/spca5xx'   
 for templ in ; do \                                                        
 &#9474;     cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.22-14-generic/g'` ; \   
 &#9474;   done                                                                     
 &#9474; for templ in `ls debian/*.modules.in` ; do \                               
 &#9474;     test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in}         
 &#9474; ${templ%.modules.in}.backup 2>/dev/null || true; \                         
 &#9474;     sed -e 's/##KVERS##/2.6.22-14-generic/g                                
 &#9474; ;s/#KVERS#/2.6.22-14-generic/g ; s/_KVERS_/2.6.22-14-generic/g ;           
 &#9474; s/##KDREV##/2.6.22-14.52/g ; s/#KDREV#/2.6.22-14.52/g ;                    
 &#9474; s/_KDREV_/2.6.22-14.52/g  ' < $templ > ${templ%.modules.in}; \             
 &#9474;   done                                                                     
 &#9474; dh_testdir             
 for templ in ; do \                                                        &#8593; 
 &#9474;     cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.22-14-generic/g'` ; \   
 &#9474;   done                                                                     
 &#9474; for templ in `ls debian/*.modules.in` ; do \                               
 &#9474;     test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in}         
 &#9474; ${templ%.modules.in}.backup 2>/dev/null || true; \                         
 &#9474;     sed -e 's/##KVERS##/2.6.22-14-generic/g                                
 &#9474; ;s/#KVERS#/2.6.22-14-generic/g ; s/_KVERS_/2.6.22-14-generic/g ;           
 &#9474; s/##KDREV##/2.6.22-14.52/g ; s/#KDREV#/2.6.22-14.52/g ;                    
 &#9474; s/_KDREV_/2.6.22-14.52/g  ' < $templ > ${templ%.modules.in}; \             
 &#9474;   done                                                                     
 &#9474; dh_testdir                                                                 
 &#9474; dh_testroot                                                                
 &#9474; dh_clean -k                                                                
 &#9474; # Build the module    
for templ in `ls debian/*.modules.in` ; do \                               &#8593; 
 &#9474;     test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in}         
 &#9474; ${templ%.modules.in}.backup 2>/dev/null || true; \                         
 &#9474;     sed -e 's/##KVERS##/2.6.22-14-generic/g                                
 &#9474; ;s/#KVERS#/2.6.22-14-generic/g ; s/_KVERS_/2.6.22-14-generic/g ;           
 &#9474; s/##KDREV##/2.6.22-14.52/g ; s/#KDREV#/2.6.22-14.52/g ;                     
 &#9474; s/_KDREV_/2.6.22-14.52/g  ' < $templ > ${templ%.modules.in}; \              
 &#9474;   done                                                                      
 &#9474; dh_testdir                                                                 
 &#9474; dh_testroot                                                                
 &#9474; dh_clean -k                                                                
 &#9474; # Build the module                                                         
 &#9474; /usr/bin/make -C /usr/src/modules/spca5xx                                 
 &#9474; KERNEL_VERSION=2.6.22-14-generic                                           
 &#9474; KERNELDIR=/usr/src/linux-headers-2.6.22-14-generic  
     sed -e 's/##KVERS##/2.6.22-14-generic/g                                &#8593; 
 &#9474; ;s/#KVERS#/2.6.22-14-generic/g ; s/_KVERS_/2.6.22-14-generic/g ;           
 &#9474; s/##KDREV##/2.6.22-14.52/g ; s/#KDREV#/2.6.22-14.52/g ;                    
 &#9474; s/_KDREV_/2.6.22-14.52/g  ' < $templ > ${templ%.modules.in}; \             
 &#9474;   done                                                                      
 &#9474; dh_testdir                                                                  
 &#9474; dh_testroot                                                                 
 &#9474; dh_clean -k                                                                
 &#9474; # Build the module                                                          
 &#9474; /usr/bin/make -C /usr/src/modules/spca5xx                                  
 &#9474; KERNEL_VERSION=2.6.22-14-generic                                           
 &#9474; KERNELDIR=/usr/src/linux-headers-2.6.22-14-generic                         
 &#9474; make[2]: Entering directory `/usr/src/modules/spca5xx'                   
 &#9474;    Building SPCA5XX driver for 2.5/2.6 kernel.                             
 &#9474;    Remember: you must have read/write access to your kernel source tree.
 s/_KDREV_/2.6.22-14.52/g  ' < $templ > ${templ%.modules.in}; \             &#8593; 
 &#9474;   done                                                                     
 &#9474; dh_testdir                                                                 
 &#9474; dh_testroot                                                                
 &#9474; dh_clean -k                                                              
 &#9474; # Build the module                                                   
 &#9474; /usr/bin/make -C /usr/src/modules/spca5xx                                
 &#9474; KERNEL_VERSION=2.6.22-14-generic                                           
 &#9474; KERNELDIR=/usr/src/linux-headers-2.6.22-14-generic                        
 &#9474; make[2]: Entering directory `/usr/src/modules/spca5xx'            
 &#9474;    Building SPCA5XX driver for 2.5/2.6 kernel.                           
 &#9474;    Remember: you must have read/write access to your kernel source tree.   
 &#9474; /usr/bin/make -C /usr/src/linux-headers-2.6.22-14-generic                  
 &#9474; SUBDIRS=/usr/src/modules/spca5xx CC=gcc modules                            
 &#9474; make[3]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
 dh_testroot                                                                &#8593; 
 &#9474; dh_clean -k                                                                 
 &#9474; # Build the module                                                         
 &#9474; /usr/bin/make -C /usr/src/modules/spca5xx                                   
 &#9474; KERNEL_VERSION=2.6.22-14-generic                                           
 &#9474; KERNELDIR=/usr/src/linux-headers-2.6.22-14-generic                         
 &#9474; make[2]: Entering directory `/usr/src/modules/spca5xx'                    
 &#9474;    Building SPCA5XX driver for 2.5/2.6 kernel.                           
 &#9474;    Remember: you must have read/write access to your kernel source tree.   
 &#9474; /usr/bin/make -C /usr/src/linux-headers-2.6.22-14-generic                  
 &#9474; SUBDIRS=/usr/src/modules/spca5xx CC=gcc modules                             
 &#9474; make[3]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'      
 &#9474;   CC [M]  /usr/src/modules/spca5xx/drivers/usb/spca5xx.o                    
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26: error:               
 &#9474; linux/config.h: No such file or directory 
 /usr/bin/make -C /usr/src/modules/spca5xx                                  &#8593; 
 &#9474; KERNEL_VERSION=2.6.22-14-generic                                           
 &#9474; KERNELDIR=/usr/src/linux-headers-2.6.22-14-generic                         
 &#9474; make[2]: Entering directory `/usr/src/modules/spca5xx'                     
 &#9474;    Building SPCA5XX driver for 2.5/2.6 kernel.                             
 &#9474;    Remember: you must have read/write access to your kernel source tree.   
 &#9474; /usr/bin/make -C /usr/src/linux-headers-2.6.22-14-generic                   
 &#9474; SUBDIRS=/usr/src/modules/spca5xx CC=gcc modules                            
 &#9474; make[3]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'     
 &#9474;   CC [M]  /usr/src/modules/spca5xx/drivers/usb/spca5xx.o                   
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26: error:               
 &#9474; linux/config.h: No such file or directory                                  
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c: In function                
 &#9474; ‘spca50x_init_isoc’:                                                       
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:1681: warning: assignment  
 make[2]: Entering directory `/usr/src/modules/spca5xx'                     &#8593; 
 &#9474;    Building SPCA5XX driver for 2.5/2.6 kernel.                             
 &#9474;    Remember: you must have read/write access to your kernel source tree.   
 &#9474; /usr/bin/make -C /usr/src/linux-headers-2.6.22-14-generic                  
 &#9474; SUBDIRS=/usr/src/modules/spca5xx CC=gcc modules                             
 &#9474; make[3]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'      
 &#9474;   CC [M]  /usr/src/modules/spca5xx/drivers/usb/spca5xx.o                    
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26: error:                
 &#9474; linux/config.h: No such file or directory                                   
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c: In function                 
 &#9474; ‘spca50x_init_isoc’:                                                        
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:1681: warning: assignment   
 &#9474; from incompatible pointer type                                             
 &#9474; make[4]: *** [/usr/src/modules/spca5xx/drivers/usb/spca5xx.o] Error 1      
 &#9474; make[3]: *** [_module_/usr/src/modules/spca5xx] Error 2     
 /usr/bin/make -C /usr/src/linux-headers-2.6.22-14-generic                  &#8593; 
 &#9474; SUBDIRS=/usr/src/modules/spca5xx CC=gcc modules                            
 &#9474; make[3]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'     
 &#9474;   CC [M]  /usr/src/modules/spca5xx/drivers/usb/spca5xx.o                   
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26: error:               
 &#9474; linux/config.h: No such file or directory                                  
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c: In function                
 &#9474; ‘spca50x_init_isoc’:                                                       
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:1681: warning: assignment    
 &#9474; from incompatible pointer type                                             
 &#9474; make[4]: *** [/usr/src/modules/spca5xx/drivers/usb/spca5xx.o] Error 1      
 &#9474; make[3]: *** [_module_/usr/src/modules/spca5xx] Error 2                     
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'      
 &#9474; make[2]: *** [default] Error 2                                             
 &#9474; make[2]: Leaving directory `/usr/src/modules/spca5xx'  
   CC [M]  /usr/src/modules/spca5xx/drivers/usb/spca5xx.o                   &#8593; 
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26: error:               
 &#9474; linux/config.h: No such file or directory                                  
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c: In function                
 &#9474; ‘spca50x_init_isoc’:                                                       
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:1681: warning: assignment   
 &#9474; from incompatible pointer type                                             
 &#9474; make[4]: *** [/usr/src/modules/spca5xx/drivers/usb/spca5xx.o] Error 1      
 &#9474; make[3]: *** [_module_/usr/src/modules/spca5xx] Error 2                    
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'      
 &#9474; make[2]: *** [default] Error 2                                             
 &#9474; make[2]: Leaving directory `/usr/src/modules/spca5xx'                      
 &#9474; make[1]: *** [binary-modules] Error 2                                      
 &#9474; make[1]: Leaving directory `/usr/src/modules/spca5xx'                      
 &#9474; make: *** [kdist_build] Error 2

---

### Post by arman.haghi on 2008-05-13
> **andrew2325 said:**
> When I use the module assistant to compile the spca5xx module for my webcam, I get the following output/error:

etc etc

Hey mate,

I had the exact same problem, tried everything... was getting the "/dev/video0 doesn't exist etc. etc." even though lsusb and dmesg said it was detected, and m-a was giving me the same errors.

I've now got my antique DSC-350 working!

Check out my post:

[http://ubuntuforums.org/showthread.php?p=4941520](http://ubuntuforums.org/showthread.php?p=4941520)

and let me know if it helps or if you need help.

Cheers,

Arman.

---

