---
title: "Unable to compile Mixman DM2 driver on 9.10"
date: 2009-12-12
forum: Multimedia Software
---

### Post by kesselwax on 2009-12-12
I more or less followed the solution from the Mixxx forums below (haven't copied the XML file yet as I think it's just MIDI bindings):  [quote=sciamano from Mixxx forums] For using the dm2 with mixxx, copy the MIDI mapping file into the mixxx midi directory:  cp DM2.midi.xml /usr/share/mixxx/midi/  Then of course, in mixxx you'll have to choose the correct device.  Actually, you don't need to build the driver manually, you can just download the deb file, install it with dpkg -i dm2-source_0.9_all.deb and install the modules-assistant package. Then simply run  m-a a-i dm2-source  This will build you a dev package with a driver for your kernel, and automatically install it.  [/quote]    I installed the dm2-source deb file from SourceForge (found at [http://sourceforge.net/projects/dm2linux/](http://sourceforge.net/projects/dm2linux/)), then used module-assistant to try and build the module. The build fails with the following log:    ```
 //Build log  dh_testdir dh_testroot rm -f build-stamp configure-stamp build-arch-stamp build-indep-stamp install-indep-stamp /usr/bin/make clean make[1]: Entering directory `/usr/src/modules/dm2' rm -rf .*.cmd *.o *.ko .tmp* Module.symvers *.mod.c make[1]: Leaving directory `/usr/src/modules/dm2' dh_clean rm -rf debian/dm2-?.?.?* debian/dm2 debian/dm2-module debian/dm2-module-?.?.* debian/*.files /usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules make[1]: Entering directory `/usr/src/modules/dm2' dh_testdir dh_testroot rm -f build-stamp configure-stamp build-arch-stamp build-indep-stamp install-indep-stamp /usr/bin/make clean make[2]: Entering directory `/usr/src/modules/dm2' rm -rf .*.cmd *.o *.ko .tmp* Module.symvers *.mod.c make[2]: Leaving directory `/usr/src/modules/dm2' dh_clean rm -rf debian/dm2-?.?.?* debian/dm2 debian/dm2-module debian/dm2-module-?.?.* debian/*.files for templ in /usr/src/modules/dm2/debian/dm2-module-_KVERS_.postinst /usr/src/modules/dm2/debian/dm2-module-_KVERS_.postinst.backup /usr/src/modules/dm2/debian/dm2-module-_KVERS_.postinst.modules.in; do \     cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.31-16-generic/g'` ; \   done for templ in `ls debian/*.modules.in` ; do \     test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \     sed -e 's/##KVERS##/2.6.31-16-generic/g ;s/#KVERS#/2.6.31-16-generic/g ; s/_KVERS_/2.6.31-16-generic/g ; s/##KDREV##/2.6.31-16.53/g ; s/#KDREV#/2.6.31-16.53/g ; s/_KDREV_/2.6.31-16.53/g  ' < $templ > ${templ%.modules.in}; \   done /usr/bin/make module KERNEL_DIR=/usr/src/linux  KVERSION=2.6.31-16-generic make[2]: Entering directory `/usr/src/modules/dm2' /usr/bin/make -C /lib/modules/2.6.31-16-generic/build SUBDIRS=/usr/src/modules/dm2 modules make[3]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'   CC [M]  /usr/src/modules/dm2/dm2.o /usr/src/modules/dm2/dm2.c:44:26: error: sound/driver.h: No such file or directory /usr/src/modules/dm2/dm2.c: In function ‘dm2_midi_init’: /usr/src/modules/dm2/dm2.c:707: error: implicit declaration of function ‘snd_card_new’ /usr/src/modules/dm2/dm2.c:707: warning: assignment makes pointer from integer without a cast /usr/src/modules/dm2/dm2.c: In function ‘dm2_write’: /usr/src/modules/dm2/dm2.c:839: error: implicit declaration of function ‘info’ make[4]: *** [/usr/src/modules/dm2/dm2.o] Error 1 make[3]: *** [_module_/usr/src/modules/dm2] Error 2 make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic' make[2]: *** [default] Error 2 make[2]: Leaving directory `/usr/src/modules/dm2' make[1]: *** [binary-modules] Error 2 make[1]: Leaving directory `/usr/src/modules/dm2' make: *** [kdist_build] Error 2 
```  Using make fails with the same problem (can't find sound/driver.h). I've already tried installing linux-rt and linux-rt-headers-2.6.31-9 as recommended on the Mixxx forums and received a similar same build failure. I also re-installed linux-headers-2.6.31-16-generic.    Definitely feels like I'm missing something obvious here.

---

### Post by skarychinezeguie on 2010-03-08
having a similar issue myself. running ubuntu 9.1, got my driver from [http://sourceforge.net/projects/dm2linux/](http://sourceforge.net/projects/dm2linux/) and followed this video [http://www.youtube.com/watch?v=e7tonj6_Oik](http://www.youtube.com/watch?v=e7tonj6_Oik)

BTW i'm a total linux noob so go easy on me. I opened terminal, navigated to the dm2 directory, "make" and got errors, but went ahead and did the "sudo make install" and got more errors

```
skary@bobuntu:/$ cd /home/skary/Downloads/dm2
skary@bobuntu:~/Downloads/dm2$ make
make -C /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/skary/Downloads/dm2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/skary/Downloads/dm2/dm2.o
/home/skary/Downloads/dm2/dm2.c:44:26: error: sound/driver.h: No such file or directory
/home/skary/Downloads/dm2/dm2.c: In function ‘dm2_midi_init’:
/home/skary/Downloads/dm2/dm2.c:707: error: implicit declaration of function ‘snd_card_new’
/home/skary/Downloads/dm2/dm2.c:707: warning: assignment makes pointer from integer without a cast
/home/skary/Downloads/dm2/dm2.c: In function ‘dm2_write’:
/home/skary/Downloads/dm2/dm2.c:839: error: implicit declaration of function ‘info’
make[2]: *** [/home/skary/Downloads/dm2/dm2.o] Error 1
make[1]: *** [_module_/home/skary/Downloads/dm2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [default] Error 2
skary@bobuntu:~/Downloads/dm2$ sudo make install
[sudo] password for skary: 
make -C /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/skary/Downloads/dm2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/skary/Downloads/dm2/dm2.o
/home/skary/Downloads/dm2/dm2.c:44:26: error: sound/driver.h: No such file or directory
/home/skary/Downloads/dm2/dm2.c: In function ‘dm2_midi_init’:
/home/skary/Downloads/dm2/dm2.c:707: error: implicit declaration of function ‘snd_card_new’
/home/skary/Downloads/dm2/dm2.c:707: warning: assignment makes pointer from integer without a cast
/home/skary/Downloads/dm2/dm2.c: In function ‘dm2_write’:
/home/skary/Downloads/dm2/dm2.c:839: error: implicit declaration of function ‘info’
make[2]: *** [/home/skary/Downloads/dm2/dm2.o] Error 1
make[1]: *** [_module_/home/skary/Downloads/dm2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [default] Error 2
skary@bobuntu:~/Downloads/dm2$ 

```

idk what i did wrong other than using a different verson of the kernal (2.6.31). any tips or tricks for getting this running?

---

