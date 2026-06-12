---
title: "Trouble with drivers FusionHDTV DVB-T Pro"
date: 2008-05-16
forum: Multimedia Software
---

### Post by max littlemore on 2008-05-16
I have a FusionHDTV DVB-T Pro TV tuner card. I had it working great under gutsy, using the instructions/code from [here]("http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/"). Unfortunately the box that I had the card in was made of old junk and some of the junk died.

I put the card into my main PC which is 64bit amd running the 2.6.24-16-rt kernel (rt because I also do home studio work) and now I can't make the drivers. I have tried with the generic kernel and I get the same error:

```
make -C /home/maxl/workspace/ltv/xc-test/xc-test/v4l 
make[1]: Entering directory `/home/maxl/workspace/ltv/xc-test/xc-test/v4l'
creating symbolic links...
Kernel build directory is /lib/modules/2.6.24-16-rt/build
make -C /lib/modules/2.6.24-16-rt/build SUBDIRS=/home/maxl/workspace/ltv/xc-test/xc-test/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-rt'
  CC [M]  /home/maxl/workspace/ltv/xc-test/xc-test/v4l/saa7134-core.o
/home/maxl/workspace/ltv/xc-test/xc-test/v4l/saa7134-core.c: In function 'saa7134_resume':
/home/maxl/workspace/ltv/xc-test/xc-test/v4l/saa7134-core.c:1352: error: size of array 'type name' is negative
/home/maxl/workspace/ltv/xc-test/xc-test/v4l/saa7134-core.c:1352: warning: comparison of distinct pointer types lacks a cast
/home/maxl/workspace/ltv/xc-test/xc-test/v4l/saa7134-core.c:1366: error: size of array 'type name' is negative
/home/maxl/workspace/ltv/xc-test/xc-test/v4l/saa7134-core.c:1366: warning: comparison of distinct pointer types lacks a cast
make[3]: *** [/home/maxl/workspace/ltv/xc-test/xc-test/v4l/saa7134-core.o] Error 1
make[2]: *** [_module_/home/maxl/workspace/ltv/xc-test/xc-test/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-rt'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/maxl/workspace/ltv/xc-test/xc-test/v4l'
make: *** [all] Error 2

```

I cannot get this working under hardy and I don't want to downgrade the main desktop at home just for TV. Can anyone help? It looks like a typing/casting problem in the newer kernel headers vs. drivers but I am not at all confident to go hacking hardware drivers.....

Any help greatly appreciated. Any more info needed, let me know.

---

