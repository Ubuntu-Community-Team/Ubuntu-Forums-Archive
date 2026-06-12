---
title: "has anyone gotten the nvidia sound drivers to install correctly?"
date: 2005-12-15
forum: Multimedia &amp; Video
---

### Post by anasazi on 2005-12-15
Well I had working sound through the default install but whenever I loaded up doom3 the sound was all garbled and screwed up, and no changing between OSS and alsa within doom3 would fix it, in fact if I switched to OSS within doom3 then the sound just stopped working.


So I figured I needed to install the NVidia drivers. Did this, no change. Actually, I'm not even sure if I installed it correctly because it seems like the name of every default config file within Ubuntu has been changed, so I'm not sure I changed the right files.


So with no change, I decided to try to install the OSS driver from their website.

Well now I have no sound. When I try to start the OSS driver with the "soundon" command I get:

> anasazi@sazibox:~/Desktop$ sudo /usr/lib/oss/bin/soundon
Kernel and OSS module versions do not match - forcing rebuild.
Building the OSS kernel module - please wait...
It is likely that some important Linux packages are not
installed in your system which makes installing OSS impossible.

The Linux (RPM) packages required before OSS can be installed are
kernel-source, gcc, binutils and make. You can find them from the install CD/DVDor the web/ftp site which you used when installing the Linux distribution.

Please take a look at /usr/lib/oss/logs/soundon.log for more info.



my soundon.log file looks like this:

> OSS version: 3.99.3c
OSS build: 200512022239
Kernel version: Linux sazibox 2.6.12-10-k7-smp #1 SMP Fri Nov 18 13:05:01 UTC 2005 i686 GNU/Linux
Kernel vermagic: 2.6.12-10-k7-smp SMP K7 gcc-3.4
Modutils version: 3.2-pre7
 10:41:32 up 13 min,  2 users,  load average: 0.10, 0.16, 0.09
=== Running /usr/lib/oss/bin/soundon ===
Install directory: /usr/lib/oss
Kernel: "2.6.12-10-k7-smp SMP K7 gcc-3.4 "
OSS: "2.6.12 SMP K7 gcc-4.0 "
Kernel and OSS module versions do not match. Removing the modules.
Will use /usr/bin/ld for linking.
make -C /lib/modules/`uname -r`/source scripts scripts_basic include/linux/version.h
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-k7-smp'
make[1]: Nothing to be done for `scripts_basic'.
  CHK     include/linux/version.h
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-k7-smp'
make -C /lib/modules/`uname -r`/source SUBDIRS=/usr/lib/oss/kbuild CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-k7-smp'
  CC [M]  /usr/lib/oss/kbuild/osslinux.o
  Building modules, stage 2.
  MODPOST
*** Warning: "oss_checksum" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_init_module" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "touch_mixer" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_version_string" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_cardlist" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_cleanup_module" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "num_mididevs" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_mixer_ext" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "mixer_ext_set_enum" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
  CC      /usr/lib/oss/kbuild/osslinux.mod.o
  LD [M]  /usr/lib/oss/kbuild/osslinux.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-k7-smp'
rm -f *.o *.ko *.mod.c
The kbuild method worked OK
/usr/bin/ld -r -o /usr/lib/oss/modules/osslinux /usr/lib/oss/modules/sndshield /usr/lib/oss/modules/soundbase /usr/lib/oss/modules/pnp -L./lib -ldrivers
Loading OSS/Linux module
insmod: error inserting '/usr/lib/oss/modules/osslinux': -1 Invalid module format
insmod: error inserting '/usr/lib/oss/modules/osslinux': -1 Invalid module format
The osslinux module didnt load. Cannot continue.
  echo The osslinux module didnt load. Cannot continue.
[4294701.743000] Bluetooth: L2CAP ver 2.7
[4294701.743000] Bluetooth: L2CAP socket layer initialized
[4294701.772000] Bluetooth: RFCOMM ver 1.5
[4294701.772000] Bluetooth: RFCOMM socket layer initialized
[4294701.772000] Bluetooth: RFCOMM TTY layer initialized
[4294705.158000] eth0: no IPv6 routers present
[4295084.002000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'
[4295084.005000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'
[4295100.316000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'
[4295100.319000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'
[4295112.409000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'
[4295112.411000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'
[4295295.990000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'
[4295295.993000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'
[4295369.349000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'
[4295369.352000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'
[4295383.223000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'
[4295383.225000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'
[4295478.716000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'
[4295478.718000] osslinux: version magic '2.6.12 SMP K7 gcc-4.0' should be '2.6.12-10-k7-smp SMP K7 gcc-3.4'


I ran the "CC=gcc-3.4" command, and the "export CC" command before I attempted to run it.


So is it even possible to get the nvidia drivers to work, and is there any easy way to fix the sound system or should I just reinstall Ubuntu?

---

