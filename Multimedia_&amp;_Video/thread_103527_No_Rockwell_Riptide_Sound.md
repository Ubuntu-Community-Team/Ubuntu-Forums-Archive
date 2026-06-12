---
title: "No Rockwell Riptide Sound"
date: 2005-12-14
forum: Multimedia &amp; Video
---

### Post by 3.2.1 Penguins on 2005-12-14
Howdy Y'all,

I just installed Ubuntu a few days ago.  After two days I finally got the display to work!  Now that I'm in Gnome, there is no sound.  Also, internet connection is iffy, but I'll post those problems on the network side of things.  Back to the sound (or lack thereof)

I have an HP Pavilion 8665c (this where you say, "I'm sorry"!) with Pentium III 600, 255 MB RAM, ATI All-In-Wonder Pro, Riptide PCI Audio Legacy by Rockwell.  In Windows device manager, it says the Riptide card has:
Direct Memory Access 01
Input/Output Ranges:
0220-022F
0330-0331
0388-0388

I have no idea what that means, but maybe you do :cool: 

So, are there some things I can try to get the sound going?  Thanx for any help you can give!

MERRY CHRISTMAS!

---

### Post by davesha on 2005-12-16
Go to opensound.com and download the free driver there.  Maybe you'll have better luck installing it.  I've tried to install it and ran into the following problem:

-----------------------------------------------
Couldn't dlopen /tmp/./ui_X.so
libgtk-1.2.so.0: cannot open shared object file: No such file or directory
OSS/Linux kernel module not available. Cannot continue.
It is likely that some important Linux packages are not
installed in your system which makes installing OSS impossible.

The Linux (RPM) packages required before OSS can be installed are
kernel-source, gcc, binutils and make. You can find them from the install CD/DVDor the web/ftp site which you used when installing the Linux distribution.

Please take a look at /usr/lib/oss/logs/soundconf.log for more info.
------------------------------------------------

Does anyone know how I can install kernel-source, gcc, binutils and make?

Thanks...

---

### Post by az on 2005-12-16
I think that the riptide driver made available from Conexant is too old to work.  They do not care about free-libre software.  I think only some of their sound hardware has working native linux drivers for it.

---

### Post by davesha on 2005-12-17
According to OSS, the installation should work for Riptide and Linux 2.6.  I managed to find the packages needed through Synaptic and installed them, and ran the OSS install again and got this:

**********************************
Post install configuration failed.
**********************************

Code=51200
All OSS files have been installed. However there are some problems
with loading the driver module(s).

Please take a look at /usr/lib/oss/logs/soundconf.log for more info.

I took a look at the log and couldn't figure it out.  Any suggestions on why the modules are not loading?  Any help will be appreciated!

Here is the content of the log:

Sat Dec 17 00:45:44 CST 2005
Kernel version: Linux davesha 2.6.12-10-k7 #1 Fri Nov 18 12:46:18 UTC 2005 i686 GNU/Linux
Modutils version: 3.2-pre7
 00:45:44 up  4:27,  2 users,  load average: 0.07, 0.19, 0.25
=== Running ./bin/soundconf ===
Install directory: /usr/lib/oss
Will use /usr/bin/ld for linking.
Will use /usr/bin/X11/ld for linking.
Will use /usr/bin/ld for linking.
make -C /lib/modules/`uname -r`/source scripts scripts_basic include/linux/version.h
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-k7'
make[1]: Nothing to be done for `scripts_basic'.
  CHK     include/linux/version.h
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-k7'
make -C /lib/modules/`uname -r`/source SUBDIRS=/usr/lib/oss/kbuild CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-k7'
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
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-k7'
rm -f *.o *.ko *.mod.c
The kbuild method worked OK
/usr/bin/ld -r -o /usr/lib/oss/modules/osslinux /usr/lib/oss/modules/sndshield /usr/lib/oss/modules/soundbase /usr/lib/oss/modules/pnp /usr/lib/oss/modules/sb /usr/lib/oss/modules/ad1848 /usr/lib/oss/modules/cs4232 /usr/lib/oss/modules/opl3sa -L./lib -ldrivers
Loading OSS/Linux module
insmod: error inserting '/usr/lib/oss/modules/osslinux': -1 Invalid module format
insmod: error inserting '/usr/lib/oss/modules/osslinux': -1 Invalid module format
The osslinux module didnt load. Cannot continue.
  echo The osslinux module didnt load. Cannot continue.
[4310117.548000] osslinux: version magic '2.6.12 K7 gcc-4.0' should be '2.6.12-10-k7 K7 gcc-3.4'
[4310117.561000] osslinux: version magic '2.6.12 K7 gcc-4.0' should be '2.6.12-10-k7 K7 gcc-3.4'
[4310682.062000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4310682.062000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310682.201000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310682.201000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310682.265000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4310682.265000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310682.933000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310682.933000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310682.984000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4310682.984000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310683.694000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310683.694000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310684.096000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4310684.096000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310684.235000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310684.235000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310733.973000] osslinux: version magic '2.6.12 K7 gcc-4.0' should be '2.6.12-10-k7 K7 gcc-3.4'
[4310733.987000] osslinux: version magic '2.6.12 K7 gcc-4.0' should be '2.6.12-10-k7 K7 gcc-3.4'

---

### Post by 3.2.1 Penguins on 2005-12-21
Thanx for all the help.  I ended up getting a Diamond card from a friend at work.  He wasn't using it, so he gave it to me.   I installed it and Ubuntu booted up with beautiful sound!

Merry Christmas All!

---

### Post by varunus on 2005-12-21
There are two sound architectures for linux:  ALSA, the advanced linux sound architecture, and OSS, the open sound system.  ALSA is newer, and replaced OSS a few years ago.

Ubuntu and every other major distro uses ALSA.  However, ALSA drivers are not available for this sound card; you'd have to recompile your kernel with alsa, and install several packages needed for OSS.  Also, you'd pretty much have one sound at a time; two programs couldn't use the sound card without some lag.

So yeah, if you have a Rockwell Riptide, either write a nasty letter to Linuxant/HP, or buy a new $5-20 sound card.

---

### Post by davesha on 2005-12-21
Okay, a new soundcard it is then.

I found the ALSA Soundcard Matrix here:
[http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix)

Has anyone used it?  I should be able to buy any card listed on there and it'll work out of the box with Ubuntu, right?

---

