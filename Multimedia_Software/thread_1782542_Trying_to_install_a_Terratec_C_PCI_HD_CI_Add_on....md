---
title: "Trying to install a Terratec C PCI HD CI Add on..."
date: 2011-06-14
forum: Multimedia Software
---

### Post by BlackAdderDK on 2011-06-14
Hi 

I'm pretty new to the Ubuntu side of things, and are quite dependent on the forum posts :)

I have installed a 10.02 for use with XBMC with support for PVR, and I have found the following post for installing drivers for the above mentioned TV-tuner...  [http://www.linuxtv.org/wiki/index.php/Mantis_with_DKMS](http://www.linuxtv.org/wiki/index.php/Mantis_with_DKMS)

Everything works fine, until "Step 4" (sudo dkms build -m mantis -v mercurial) as it fails with the following error:

> user@Ubuntu:/usr/src/mantis-mercurial$ sudo dkms build -m mantis -v mercurial

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/mantis/mercurial/build; make KSRC=/lib/modules/2.6.32-32-generic/build KVER=2.6.32-32-generic....

Error!  Build of mantis.ko failed for: 2.6.32-32-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/mantis/mercurial/build/ for more information.
ERROR: binary package for mantis: mercurial not found
user@Ubuntut:/usr/src/mantis-mercurial$ 
The make.log has the following entries:

> DKMS make.log for mantis-mercurial for kernel 2.6.32-32-generic (x86_64)
Wed Jun 15 00:52:17 CEST 2011
make -C /var/lib/dkms/mantis/mercurial/build/v4l 
make[1]: Entering directory `/var/lib/dkms/mantis/mercurial/build/v4l'
scripts/make_makefile.pl
./scripts/make_myconfig.pl
make[1]: Leaving directory `/var/lib/dkms/mantis/mercurial/build/v4l'
make[1]: Entering directory `/var/lib/dkms/mantis/mercurial/build/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.32-32-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/var/lib/dkms/mantis/mercurial/build/v4l/firmware'
make[2]: Leaving directory `/var/lib/dkms/mantis/mercurial/build/v4l/firmware'
make -C firmware
make[2]: Entering directory `/var/lib/dkms/mantis/mercurial/build/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/var/lib/dkms/mantis/mercurial/build/v4l/firmware'
Kernel build directory is /lib/modules/2.6.32-32-generic/build
make -C /lib/modules/2.6.32-32-generic/build SUBDIRS=/var/lib/dkms/mantis/mercurial/build/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-32-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-32-generic'
./scripts/rmmod.pl check
found 0 modules
make[1]: Leaving directory `/var/lib/dkms/mantis/mercurial/build/v4l'
Any ideas?

Regards
'Adder

---

