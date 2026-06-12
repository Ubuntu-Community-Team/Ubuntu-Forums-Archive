---
title: "Sound Problems Ubuntu 10.04"
date: 2010-06-07
forum: Multimedia Software
---

### Post by Apoorvbarwa on 2010-06-07
After installing Ubuntu 10.04 the sound quality is not that good...... i have tried the following

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

My Kernel and Driver Information:



!Kernel Information
!!------------------

Kernel release:    2.6.32-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.22
Utilities version:  1.0.22


i am getting sound but the quality is very poor ..... also i have downloaded the package(with directory) 

/usr/src/alsa/alsa-driver-1.0.14rc3
/usr/src/alsa/alsa-lib-1.0.14rc3
/usr/src/alsa/alsa-utils-1.0.14rc3


now while running make in folder /usr/src/alsa/ i get the error 

make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.14rc3'
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/usr/src/alsa/alsa-driver-1.0.14rc3  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/usr/src/alsa/alsa-driver-1.0.14rc3/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.14rc3/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.14rc3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [compile] Error 2



And while compiling and running make in alsa-lib-1.0.14rc3 i the below error


make[2]: Entering directory `/usr/src/alsa/alsa-lib-1.0.14rc3/utils'
make[2]: Nothing to be done for `install-exec-am'.



while configuring the alsa-utils-1.0.14rc3 i get the below output

make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14rc2/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14rc2/po'
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14rc2'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14rc2'



PLEASE Have a look and tell me what am i doing wrong and how to fix this problem.

Thanks

---

### Post by mörgæs on 2010-06-08
How was the sound in 9.10?

---

