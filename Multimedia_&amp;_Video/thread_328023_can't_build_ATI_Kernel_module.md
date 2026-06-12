---
title: "can't build ATI Kernel module"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by usernamebob on 2006-12-30
Hey, I've been trying to get the ATI 6.32.5 drivers working on my system.. (following [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) but when I try and build the Kernel module it fails.. heres my module-assist log.. if anyone could give me a hint it'd be great.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)




 &#9474; dh_testroot                                                                &#8593; 
 &#9474; rm -f configure-stamp                                                      &#9646; 
 &#9474; rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a                               &#9618; 
 &#9474; rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd                        &#9618; 
 &#9474; rm -rf .tmp_versions                                                       &#9618; 
 &#9474; rm -rf patch                                                               &#9618; 
 &#9474; dh_clean                                                                   &#9618; 
 &#9474; rm /usr/src/modules/fglrx/debian/control                                   &#9618; 
 &#9474; rm /usr/src/modules/fglrx/debian/dirs                                      &#9618; 
 &#9474; if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \           &#9618; 
 &#9474;         cat /usr/src/modules/fglrx/debian/control.template >               &#9618; 
 &#9474; /usr/src/modules/fglrx/debian/control; \  
 &#9474;         fi                                                                 &#8593; 
 &#9474; if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \                   &#9618; 
 &#9474;         mv /usr/src/modules/fglrx/debian/postinst                          &#9618; 
 &#9474; /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.19-7-generic.postinst; \    &#9618; 
 &#9474;         fi                                                                 &#9618; 
 &#9474; dh_testdir                                                                 &#9618; 
 &#9474; touch configure-stamp                                                      &#9646; 
 &#9474; dh_testdir                                                                 &#9618; 
 &#9474; /usr/bin/make -C /lib/modules/2.6.19-7-generic/build                       &#9618; 
 &#9474; SUBDIRS=/usr/src/modules/fglrx modules                                     &#9618; 
 &#9474; make[1]: Entering directory `/usr/src/linux-headers-2.6.19-7-generic'      &#9618; 
 &#9474;   CC [M]  /usr/src/modules/fglrx/firegl_public.o                           &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:89:26: error: linux/config.h: No    &#9618; 
 &#9474; such file or directory                                                     &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:456: warning: initialization from 
 &#9474; incompatible pointer type                                                  &#8593; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function ‘firegl_stub_open’:    &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:579: warning: assignment discards   &#9618; 
 &#9474; qualifiers from pointer target type                                        &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_request_irq’:    &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:2568: warning: passing argument 2   &#9618; 
 &#9474; of ‘request_irq’ from incompatible pointer type                            &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function                        &#9618; 
 &#9474; ‘__ke_smp_call_function’:                                                  &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:4008: warning: passing argument 1   &#9618; 
 &#9474; of ‘smp_call_function’ from incompatible pointer type                      &#9618; 
 &#9474; make[2]: *** [/usr/src/modules/fglrx/firegl_public.o] Error 1              &#9618; 
 &#9474; make[1]: *** [_module_/usr/src/modules/fglrx] Error 2                      &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/linux-headers-2.6.19-7-generic'       &#9646; 
 &#9474; make: *** [build] Error 2

---

