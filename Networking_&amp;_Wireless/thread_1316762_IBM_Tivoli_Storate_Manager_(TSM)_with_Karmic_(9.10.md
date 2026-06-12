---
title: "IBM Tivoli Storate Manager (TSM) with Karmic (9.10)"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by mnagl on 2009-11-06
TSM doesn't work with the usual instructions and karmic because of a missing libstdc++.so.5. It is obvious that this lib is missing in order to run dsmagent:

```
/opt/tivoli/tsm/client/ba/bin# ldd dsmagent 
        linux-gate.so.1 =>  (0xf7728000)                
        libxmlutil-6.1.0.0.so => /opt/tivoli/tsm/client/api/bin/libxmlutil-6.1.0.0.so (0xf7707000)
        libcrypt.so.1 => /lib32/libcrypt.so.1 (0xf76d5000)                                        
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf76bb000)                                    
        libdl.so.2 => /lib32/libdl.so.2 (0xf76b7000)                                              
        libm.so.6 => /lib32/libm.so.6 (0xf7691000)                                                
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf759f000)                                  
        libgpfs.so => /opt/tivoli/tsm/client/api/bin/libgpfs.so (0xf7596000)                      
        libdmapi.so => /opt/tivoli/tsm/client/api/bin/libdmapi.so (0xf758f000)                    
        librt.so.1 => /lib32/librt.so.1 (0xf7586000)                                              
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7568000)                                    
        libc.so.6 => /lib32/libc.so.6 (0xf7424000)                                                
        libtsm610xerces-c1_6_0.so => /usr/lib/libtsm610xerces-c1_6_0.so (0xf71fd000)              
        /lib/ld-linux.so.2 (0xf7729000)                                                           
        libstdc++.so.5 => not found                                                              

/opt/tivoli/tsm/client/ba/bin# dsmagent
dsmagent: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


```

A possible solution is to download this package:
[http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb]("http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb"), extract it using
```
dpkg -x ia32-libs_2.7ubuntu6.1_amd64.deb tmp/
```
and move the missing lib to /usr/lib32.

---

