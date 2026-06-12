---
title: "sasc-ng in 64bit mythbuntu"
date: 2010-06-01
forum: Mythbuntu
---

### Post by Saubazi on 2010-06-01
is it a hopeless task?
I followed:
[http://dolot.kipdola.com/wiki/Install_SASC-NG](http://dolot.kipdola.com/wiki/Install_SASC-NG)

everything goes ok until it fails...

# ./configure
Using C++ compiler: g++
Using compile type debug
Processor capabilities: native ( mmx sse sse2 )
Trying various FFdecsa optimizations...
PARALLEL_32_INT: test failed
PARALLEL_64_2INT: 41
PARALLEL_64_LONG: 351
PARALLEL_64_MMX: 347
PARALLEL_128_2LONG: 327
PARALLEL_128_2MMX: 324
PARALLEL_128_SSE: 424
PARALLEL_128_SSE2: 443
Choosing PARALLEL_MODE = PARALLEL_128_SSE2

[COLOR="Red"]
32_INT missing?!?[/COLOR] well maybe it is not relevant

make does not make any unusual remarks
but make module says:
# make module
cd dvbloopback/module && make
make[1]: Entering directory `/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module'
echo "Skipping Modver "
Skipping Modver
./config_dvb.pl "BUILD_DIR=/lib/modules/2.6.32-22-generic/build" "EXTRA_CFLAGS=-Idrivers/media/dvb/dvb-core/ -I/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module"
Found dvbdev.h from 2.6.22 or later
make -C /lib/modules/2.6.32-22-generic/build M=/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
CC [M] /usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.o
/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.c: In function ‘dvblb_fake_ioctl’:
/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.c:281: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.c:281: error: (Each undeclared identifier is reported only once
/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.c:281: error: for each function it appears in.)
/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.c:283: error: implicit declaration of function ‘signal_pending’
/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.c:283: error: implicit declaration of function ‘schedule_timeout’
/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.c:292: error: ‘TASK_UNINTERRUPTIBLE’ undeclared (first use in this function)
/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.c: In function ‘dvblb_open’:
/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.c:408: error: dereferencing pointer to incomplete type
/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.c: In function ‘dvblb_ioctl’:
/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.c:752: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.c:808: error: ‘TASK_NORMAL’ undeclared (first use in this function)
make[3]: *** [/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module/dvb_loopback.o] Error 1
make[2]: *** [_module_/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/local/src/sc/contrib/sasc-ng/dvbloopback/module'
make: *** [module] Error 2 

So is there something I might try (some 32bit lib) or should I just install 32bit mythbuntu instead?

---

