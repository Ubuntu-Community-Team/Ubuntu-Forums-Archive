---
title: "Aventail won't install with libssl.0.9.8 in Kubuntu 12.04"
date: 2012-04-11
forum: Networking &amp; Wireless
---

### Post by orezero on 2012-04-11
I cannot install my Aventail client in Kubuntu 12.04 because it does not like 12.04's version of libssl.0.9.8. Although Aventail will install without complaining when 0.9.8o-7ubuntu1 is installed, it's a different story with 0.9.8o-7ubuntu2, the version that 12.04 wants to install. With 0.9.8o-7ubuntu2, I get the following errors:

       ```
 linux-gate.so.1 =>  (0xb77c7000)
        libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xb7798000)
        libssl.so.0.9.7 => not found
        libcrypto.so.0.9.7 => not found
        libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb776b000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb75c5000)
        /lib/ld-linux.so.2 (0xb77c8000)

```

Can anybody help me understand why this might be happening, and what, if anything, I can do about it?

---

### Post by kevdog on 2012-04-12
It look likes your program wants the 0.9.7 version

---

