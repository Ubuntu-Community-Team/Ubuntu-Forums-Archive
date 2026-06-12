---
title: "ndiswrapper won't install!"
date: 2005-01-20
forum: Networking &amp; Wireless
---

### Post by Sepht on 2005-01-20
I'm trying to install ndiswrapper 0.12 on Ubuntu (2.6.8.1-3-386). When I run make deb, I am gettinging the following errors

/home/aemkmmg/ndiswrapper-0.12/driver/ntoskernel.c:744:1: directives may not be used inside a macro argument
/home/aemkmmg/ndiswrapper-0.12/driver/ntoskernel.c:744:1: unterminated argument list invoking macro "kthread_run"
/home/aemkmmg/ndiswrapper-0.12/driver/ntoskernel.c: In function `PsCreateSystemThread':
/home/aemkmmg/ndiswrapper-0.12/driver/ntoskernel.c:747: `kthread_run' undeclared (first use in this function)
/home/aemkmmg/ndiswrapper-0.12/driver/ntoskernel.c:747: (Each undeclared identifier is reported only once
/home/aemkmmg/ndiswrapper-0.12/driver/ntoskernel.c:747: for each function it appears in.)
/home/aemkmmg/ndiswrapper-0.12/driver/ntoskernel.c:747: parse error before string constant
make[5]: *** [/home/aemkmmg/ndiswrapper-0.12/driver/ntoskernel.o] Error 1
make[4]: *** [_module_/home/aemkmmg/ndiswrapper-0.12/driver] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-386'
make[3]: *** [default] Error 2
make[3]: Leaving directory `/home/aemkmmg/ndiswrapper-0.12/driver'
make[2]: *** [build-modules] Error 2
make[2]: Leaving directory `/home/aemkmmg/ndiswrapper-0.12'
make[1]: *** [binary] Error 2
make[1]: Leaving directory `/home/aemkmmg/ndiswrapper-0.12'
make: *** [deb] Error 2

---

