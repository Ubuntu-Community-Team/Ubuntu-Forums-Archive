---
title: "twinhan dvb-s2 driver, compiling"
date: 2007-10-09
forum: Multimedia &amp; Video
---

### Post by redu on 2007-10-09
For Twinhan dvb-s2-PCI-card (Azurewave tai Digital Rise) there are two linux sources:
1.
[http://www.twinhan.com/download_driver&software.asp](http://www.twinhan.com/download_driver&software.asp)
V1.4.2
AZLinux_v1.4.2_CI_PC6.tar.gz
Ref:
>
There is a binary package at the Twinhan (download page) website which does support the CI but the modules were compiled for the first Fedore Core 6 kernel on a i586 platform.
>
Using this thing in Ubuntu Feisty turns to be too tricky for a newbie.

2.
DigitalRisen www has:
[http://www.digitalrise.biz/support/downloads/index.php?action=file&id=186](http://www.digitalrise.biz/support/downloads/index.php?action=file&id=186)
AZLinux_v1.4.2_no_CI.tar.gz
This seems to be a kind of modified version of the firsyt one. Less CI-section.

But compiling this turned to be too tricky again.
README-instructions:
1) Install Linux DVB API applications and utilities
      $ cd dvb-apps-997424a1799e
      $ make clean
      $ make
      $ make install
      $ cd ..

   2) Install Azurewave card driver
        $ cd linuxdriver
      $ rm v4l/.version
        $ make menuconfig (use default)
      $ make clean
      $ make
      $ make install
       $ make rmmod
       $ make insmod

performing "make menuconfig" fails: “No rule to make target”:

redu@roklotin:/srv/AZLinux_v1.4.2_no_CI/linuxdriver$ make menuconfig
make -C /srv/AZLinux_v1.4.2_no_CI/linuxdriver/v4l menuconfig
make[1]: Entering directory `/srv/AZLinux_v1.4.2_no_CI/linuxdriver/v4l'
No version yet.
scripts/make_makefile.pl /lib/modules/2.6.20-16-generic/build
creating symbolic links...
make -C /lib/modules/2.6.20-16-generic/build -f /srv/AZLinux_v1.4.2_no_CI/linuxdriver/v4l/Makefile.kernel config-targets=1 mixed-targets=0 dot-config=0 v4l-mconf
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
make -f scripts/Makefile.build obj=scripts/kconfig scripts/kconfig/mconf
make[3]: *** No rule to make target `scripts/kconfig/mconf'.  Stop.
make[2]: *** [v4l-mconf] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [/lib/modules/2.6.20-16-generic/build/scripts/kconfig/mconf] Error 2
make[1]: Leaving directory `/srv/AZLinux_v1.4.2_no_CI/linuxdriver/v4l'
make: *** [menuconfig] Error 2

What does this make menuconfig actually? Why it fails?

---

### Post by Darth Arturito on 2008-03-05
Same here. Did you manage to install it?

---

