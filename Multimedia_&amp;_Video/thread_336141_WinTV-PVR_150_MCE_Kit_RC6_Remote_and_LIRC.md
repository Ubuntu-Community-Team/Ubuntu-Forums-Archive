---
title: "WinTV-PVR 150 MCE Kit RC6 Remote and LIRC"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by CanadianMan on 2007-01-11
I just recently bought this tv tuner card (model 1061) and I have it working fine under dapper.  But for the life of me I can not get the remote it came with to work with LIRC.  The remote has a RC6 printed on the back if that helps.  I've tried a few tutorials and google and nothing has worked.  These are what i've tried or have looked at:

[http://www.mythtv.org/wiki/index.php/PVR150_Remote](http://www.mythtv.org/wiki/index.php/PVR150_Remote)
[http://www.mythtv.org/wiki/index.php/MCE_Remote#The_below_solution_is_no_longer_necessary_since_it_has_been_fixed_in_lirc_0.8.1](http://www.mythtv.org/wiki/index.php/MCE_Remote#The_below_solution_is_no_longer_necessary_since_it_has_been_fixed_in_lirc_0.8.1).

I have gone to a couple of threads on some forums but nothing very specific to my problem. I either get this message when I do:

$ mode2
mode2: error opening /dev/lirc
mode2: No such device

or this when i do:

$ irw
connect: Connection refused

Has anybody gotten this remote to work under Ubuntu Dapper?  I'm mainly going to use this for my htpc and mythtv.  Thank you.

---

### Post by majoridiot on 2007-01-11
do yourself a favor and follow mario's excellent guide (it says for edgy but works for dapper too):

[https://help.ubuntu.com/community/Install_Lirc_Edgy#head-61b516764f233bff0f43ac2ac97bb18db14ad2be](https://help.ubuntu.com/community/Install_Lirc_Edgy#head-61b516764f233bff0f43ac2ac97bb18db14ad2be)

you want to build for/use mceusb2 for that remote.  i have the same remote and it config'd
and works very well in dapper following install from that guide.

---

### Post by CanadianMan on 2007-01-11
Thank you very much for your reply.  I have read the tutorial and am now stuck at this step:

sudo m-a a-i lirc 

I get a screen telling me this:

Build of the package lirc-modules-source failed! How do you wish to prceed?
View
Continue
Stop

I press Continue and continue with the tutorial I get to the command irw and it gives me:

connect: Connection refused

I press Stop and it says:

Package lirc-modules-source was not built successfully, see /var/cache/modass/lirc-modules-source*buildlog* for details!

Here are the contents of the buildlog:

sed -e "s!\$KVERS!`sed -n -e '/UTS_RELEASE/s/^[^"]*"\([^"]*\)".*$/\1/p' /usr/src/linux/include/linux/version.h`!g; s!\$KSRC!/usr/src/linux!; s!\$KARCH!amd64!; s!\$KEMAIL!!; s!\$KMAINT!!; s!\$KDREV!"Custom.1.00"!; s!\$DEBDATE!Thu, 11 Jan 2007 18:18:36 -0500!" debian/control.in > debian/control
/usr/bin/make  -f debian/rules clean
make[1]: Entering directory `/usr/src/modules/lirc'
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[2]: Entering directory `/usr/src/modules/lirc'
/usr/bin/make clean -C drivers SUBDIRS="lirc_serial lirc_parallel lirc_i2c lirc_sir lirc_dev lirc_gpio lirc_it87 lirc_bt829 lirc_atiusb"
make[3]: Entering directory `/usr/src/modules/lirc/drivers'
Making clean in lirc_atiusb
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_atiusb'
test -z "lirc_atiusb.o .lirc_atiusb.o.flags lirc_atiusb.mod.c lirc_atiusb.ko *~" || rm -f lirc_atiusb.o .lirc_atiusb.o.flags lirc_atiusb.mod.c lirc_atiusb.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_atiusb'
Making clean in lirc_bt829
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_bt829'
test -z "lirc_bt829.o .lirc_bt829.o.flags lirc_bt829.mod.c lirc_bt829.ko *~" || rm -f lirc_bt829.o .lirc_bt829.o.flags lirc_bt829.mod.c lirc_bt829.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_bt829'
Making clean in lirc_it87
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_it87'
test -z "lirc_it87.o .lirc_it87.o.flags lirc_it87.mod.c lirc_it87.ko *~" || rm -f lirc_it87.o .lirc_it87.o.flags lirc_it87.mod.c lirc_it87.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_it87'
Making clean in lirc_gpio
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_gpio'
test -z "lirc_gpio.o .lirc_gpio.o.flags lirc_gpio.mod.c lirc_gpio.ko *~" || rm -f lirc_gpio.o .lirc_gpio.o.flags lirc_gpio.mod.c lirc_gpio.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_gpio'
Making clean in lirc_dev
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_dev'
test -z "lirc_dev.o .lirc_dev.o.flags lirc_dev.mod.c lirc_dev.ko *~" || rm -f lirc_dev.o .lirc_dev.o.flags lirc_dev.mod.c lirc_dev.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_dev'
Making clean in lirc_sir
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_sir'
test -z "lirc_sir.o .lirc_sir.o.flags lirc_sir.mod.c lirc_sir.ko *~" || rm -f lirc_sir.o .lirc_sir.o.flags lirc_sir.mod.c lirc_sir.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_sir'
Making clean in lirc_i2c
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_i2c'
test -z "lirc_i2c.o .lirc_i2c.o.flags lirc_i2c.mod.c lirc_i2c.ko *~" || rm -f lirc_i2c.o .lirc_i2c.o.flags lirc_i2c.mod.c lirc_i2c.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_i2c'
Making clean in lirc_parallel
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_parallel'
test -z "lirc_parallel.o .lirc_parallel.o.flags lirc_parallel.mod.c lirc_parallel.ko *~" || rm -f lirc_parallel.o .lirc_parallel.o.flags lirc_parallel.mod.c lirc_parallel.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_parallel'
Making clean in lirc_serial
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_serial'
test -z "lirc_serial.o .lirc_serial.o.flags lirc_serial.mod.c lirc_serial.ko *~" || rm -f lirc_serial.o .lirc_serial.o.flags lirc_serial.mod.c lirc_serial.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_serial'
Making clean in .
make[4]: Entering directory `/usr/src/modules/lirc/drivers'
test -z "*~" || rm -f *~
rm -rf .libs _libs
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers'
make[3]: Leaving directory `/usr/src/modules/lirc/drivers'
rm -rf modules
make[2]: Leaving directory `/usr/src/modules/lirc'
dh_clean
rm -f debian/control
make[1]: Leaving directory `/usr/src/modules/lirc'
/usr/bin/make  -f debian/rules binary-modules
make[1]: Entering directory `/usr/src/modules/lirc'
sed -e "s!\$KVERS!2.6.15-27-amd64-generic!g; s!\$KSRC!/usr/src/linux!; s!\$KARCH!amd64!; s!\$KEMAIL!!; s!\$KMAINT!!; s!\$KDREV!2.6.15-27.50!; s!\$DEBDATE!Thu, 11 Jan 2007 18:18:37 -0500!" debian/control.in > debian/control
dh_testdir
# Add here commands to configure the package.
touch configure-stamp
dh_testdir
# Add here commands to compile the package.
/usr/bin/make debconf
make[2]: Entering directory `/usr/src/modules/lirc'
mkdir modules
/usr/bin/make -C drivers SUBDIRS="lirc_dev"
make[3]: Entering directory `/usr/src/modules/lirc/drivers'
Making all in lirc_dev
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_dev'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/lirc/drivers/lirc_dev modules \
		KBUILD_VERBOSE=1
make[5]: Entering directory `/usr/src/linux-source-2.6.15'
mkdir -p /usr/src/modules/lirc/drivers/lirc_dev/.tmp_versions

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

/usr/bin/make -f scripts/Makefile.build obj=/usr/src/modules/lirc/drivers/lirc_dev
  gcc -Wp,-MD,/usr/src/modules/lirc/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.0.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2     -fomit-frame-pointer  -mno-red-zone -mcmodel=kernel -pipe -fno-reorder-blocks	 -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-time -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/src/modules/lirc/drivers/lirc_dev/../.. -I/usr/src/linux/include/  -DMODULE -DKBUILD_BASENAME=lirc_dev -DKBUILD_MODNAME=lirc_dev -c -o /usr/src/modules/lirc/drivers/lirc_dev/.tmp_lirc_dev.o /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c
In file included from <command line>:1:
../../include/linux/autoconf.h:1:35: error: linux/err_kernel_only.h: No such file or directory
In file included from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:35:
include/linux/config.h:6:28: error: linux/autoconf.h: No such file or directory
In file included from include/linux/sched.h:12,
                 from include/linux/module.h:10,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:36:
include/linux/jiffies.h:27:5: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:29:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:31:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:33:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:35:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:37:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:39:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:42:3: error: #error You lose.
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:213:31: error: division by zero in #if
include/linux/jiffies.h:213:46: warning: "SHIFT_HZ" is not defined
include/linux/jiffies.h:257:5: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:44: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:257:46: error: division by zero in #if
include/linux/jiffies.h:259:7: warning: "CONFIG_HZ" is not defined
In file included from include/linux/sched.h:12,
                 from include/linux/module.h:10,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:36:
include/linux/jiffies.h: In function ‘jiffies_to_msecs’:
include/linux/jiffies.h:262: error: ‘CONFIG_HZ’ undeclared (first use in this function)
include/linux/jiffies.h:262: error: (Each undeclared identifier is reported only once
include/linux/jiffies.h:262: error: for each function it appears in.)
include/linux/jiffies.h:268:5: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:268:44: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:268:46: error: division by zero in #if
include/linux/jiffies.h:270:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h: In function ‘jiffies_to_usecs’:
include/linux/jiffies.h:273: error: ‘CONFIG_HZ’ undeclared (first use in this function)
include/linux/jiffies.h:281:5: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:281:44: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:281:46: error: division by zero in #if
include/linux/jiffies.h:283:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h: In function ‘msecs_to_jiffies’:
include/linux/jiffies.h:286: error: ‘CONFIG_HZ’ undeclared (first use in this function)
include/linux/jiffies.h:294:5: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:294:44: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:294:46: error: division by zero in #if
include/linux/jiffies.h:296:7: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h: In function ‘usecs_to_jiffies’:
include/linux/jiffies.h:299: error: ‘CONFIG_HZ’ undeclared (first use in this function)
include/linux/jiffies.h: In function ‘timespec_to_jiffies’:
include/linux/jiffies.h:318: error: ‘CONFIG_HZ’ undeclared (first use in this function)
include/linux/jiffies.h:320: error: ‘SHIFT_HZ’ undeclared (first use in this function)
include/linux/jiffies.h: In function ‘jiffies_to_timespec’:
include/linux/jiffies.h:337: error: ‘CONFIG_HZ’ undeclared (first use in this function)
include/linux/jiffies.h: In function ‘timeval_to_jiffies’:
include/linux/jiffies.h:359: error: ‘SHIFT_HZ’ undeclared (first use in this function)
include/linux/jiffies.h:359: error: ‘CONFIG_HZ’ undeclared (first use in this function)
include/linux/jiffies.h: In function ‘jiffies_to_timeval’:
include/linux/jiffies.h:375: error: ‘CONFIG_HZ’ undeclared (first use in this function)
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:385:6: error: division by zero in #if
include/linux/jiffies.h: In function ‘jiffies_to_clock_t’:
include/linux/jiffies.h:386: error: ‘CONFIG_HZ’ undeclared (first use in this function)
include/linux/jiffies.h:396:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h: In function ‘clock_t_to_jiffies’:
include/linux/jiffies.h:397: error: ‘CONFIG_HZ’ undeclared (first use in this function)
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: warning: "CONFIG_HZ" is not defined
include/linux/jiffies.h:416:6: error: division by zero in #if
include/linux/jiffies.h: In function ‘jiffies_64_to_clock_t’:
include/linux/jiffies.h:417: error: ‘CONFIG_HZ’ undeclared (first use in this function)
In file included from include/linux/prefetch.h:14,
                 from include/linux/list.h:7,
                 from include/linux/wait.h:23,
                 from include/asm/semaphore.h:42,
                 from include/linux/sched.h:20,
                 from include/linux/module.h:10,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:36:
include/asm/processor.h: At top level:
include/asm/processor.h:74: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
include/asm/processor.h:74: error: requested alignment is not a constant
include/asm/processor.h:229: error: requested alignment is not a constant
In file included from include/asm/semaphore.h:43,
                 from include/linux/sched.h:20,
                 from include/linux/module.h:10,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:36:
include/linux/rwsem.h:27:65: error: asm/rwsem.h: No such file or directory
In file included from include/asm/semaphore.h:43,
                 from include/linux/sched.h:20,
                 from include/linux/module.h:10,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:36:
include/linux/rwsem.h: In function ‘down_read’:
include/linux/rwsem.h:45: warning: implicit declaration of function ‘__down_read’
include/linux/rwsem.h: In function ‘down_read_trylock’:
include/linux/rwsem.h:56: warning: implicit declaration of function ‘__down_read_trylock’
include/linux/rwsem.h: In function ‘down_write’:
include/linux/rwsem.h:68: warning: implicit declaration of function ‘__down_write’
include/linux/rwsem.h: In function ‘down_write_trylock’:
include/linux/rwsem.h:79: warning: implicit declaration of function ‘__down_write_trylock’
include/linux/rwsem.h: In function ‘up_read’:
include/linux/rwsem.h:90: warning: implicit declaration of function ‘__up_read’
include/linux/rwsem.h: In function ‘up_write’:
include/linux/rwsem.h:100: warning: implicit declaration of function ‘__up_write’
include/linux/rwsem.h: In function ‘downgrade_write’:
include/linux/rwsem.h:110: warning: implicit declaration of function ‘__downgrade_write’
In file included from include/linux/slab.h:88,
                 from include/linux/percpu.h:4,
                 from include/linux/sched.h:34,
                 from include/linux/module.h:10,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:36:
include/linux/kmalloc_sizes.h:5:5: warning: "CONFIG_X86_L1_CACHE_SHIFT" is not defined
include/linux/kmalloc_sizes.h:9:5: warning: "CONFIG_X86_L1_CACHE_SHIFT" is not defined
In file included from include/linux/module.h:10,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:36:
include/linux/sched.h:252:16: warning: "CONFIG_SPLIT_PTLOCK_CPUS" is not defined
In file included from include/linux/module.h:10,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:36:
include/linux/sched.h: At top level:
include/linux/sched.h:318: error: field ‘mmap_sem’ has incomplete type
In file included from include/linux/module.h:19,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:36:
include/linux/kobject.h:153: error: field ‘rwsem’ has incomplete type
In file included from include/asm/hardirq.h:6,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:11,
                 from include/linux/rcuref.h:36,
                 from include/linux/fs.h:12,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:41:
include/linux/irq.h:83: error: requested alignment is not a constant
In file included from include/linux/fs.h:303,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:41:
include/linux/quota.h:290: error: field ‘dqptr_sem’ has incomplete type
In file included from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:41:
include/linux/fs.h:488: error: field ‘i_alloc_sem’ has incomplete type
In file included from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:41:
include/linux/fs.h:823: error: field ‘s_umount’ has incomplete type
In file included from include/linux/poll.h:11,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:42:
include/linux/mm.h:233:16: warning: "CONFIG_SPLIT_PTLOCK_CPUS" is not defined
In file included from include/linux/poll.h:11,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:42:
include/linux/mm.h: In function ‘lowmem_page_address’:
include/linux/mm.h:512: warning: implicit declaration of function ‘page_to_pfn’
include/linux/mm.h:770:16: warning: "CONFIG_SPLIT_PTLOCK_CPUS" is not defined
In file included from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:53:
/usr/src/modules/lirc/drivers/lirc_dev/../../drivers/kcompat.h:207:2: error: #error "LIRC modules currently require"
/usr/src/modules/lirc/drivers/lirc_dev/../../drivers/kcompat.h:208:2: error: #error "  'Loadable module support  --->  Module unloading'"
/usr/src/modules/lirc/drivers/lirc_dev/../../drivers/kcompat.h:209:2: error: #error "to be enabled in the kernel"
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c: In function ‘lirc_thread’:
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:220: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c: In function ‘lirc_register_plugin’:
/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:279: error: ‘CONFIG_HZ’ undeclared (first use in this function)
make[6]: *** [/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.o] Error 1
make[5]: *** [_module_/usr/src/modules/lirc/drivers/lirc_dev] Error 2
make[5]: Leaving directory `/usr/src/linux-source-2.6.15'
make[4]: *** [lirc_dev.o] Error 2
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_dev'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/usr/src/modules/lirc/drivers'
make[2]: *** [dev] Error 2
make[2]: Leaving directory `/usr/src/modules/lirc'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/lirc'
make: *** [kdist_image] Error 2

Thank you for your help.

---

### Post by CanadianMan on 2007-01-11
I have the 64bit version of dapper does that change anything?

---

### Post by tfmccull on 2007-01-12
I'm having problems getting this remote to work as well. I have had LIRC working great for the past 3 months with the Hauppauge 150 (non-MCE version), but my kids ripped the plug out the card now it's busted. My 2nd tuner is the 150MCE version.

I've tried using Synaptic to install. I've followed the HOW-TO from the Ubuntu community. No joy.

At one point last night, after i had reinstalled LIRC again, after typing modprobe lirc_usbmce2 and trying irw i got it to work. I could see the codes being output by the remote

But after a reboot, it wouldnt work any longer, and the first time i typed "irw" it would drop me back to the shell. If I tried "irw" a second time, i would get a "connection refused" message.

After that, no matter what i tried i couldnt get irw to respond to the remote.

I've checked dmesg and i dont see any errors, it looks like the module is loading and LIRC is starting as a daemon on boot.

I dont get it. If anyone has any insight. PLEASE let me know. I'm getting desperate to get this to work.

---

### Post by CanadianMan on 2007-01-12
Well you've gotten a lot closer than i have.

---

### Post by CanadianMan on 2007-01-13
Any luck on your end tfmccull?

---

### Post by CanadianMan on 2007-01-13
> **majoridiot said:**
> do yourself a favor and follow mario's excellent guide (it says for edgy but works for dapper too):

[https://help.ubuntu.com/community/Install_Lirc_Edgy#head-61b516764f233bff0f43ac2ac97bb18db14ad2be](https://help.ubuntu.com/community/Install_Lirc_Edgy#head-61b516764f233bff0f43ac2ac97bb18db14ad2be)

you want to build for/use mceusb2 for that remote.  i have the same remote and it config'd
and works very well in dapper following install from that guide.


Majoridiot, are you using 32 or 64 bit edition?

---

### Post by tfmccull on 2007-01-13
nope. reinstalled it twice using two different HOW-TOs. I'm ready to give up.

---

### Post by CanadianMan on 2007-01-14
By chance which version are you using of dapper 32 or 64?

---

### Post by majoridiot on 2007-01-14
> **CanadianMan said:**
> Majoridiot, are you using 32 or 64 bit edition?

32 bit.

> **CanadianMan said:**
> sudo m-a a-i lirc

I get a screen telling me this:

Build of the package lirc-modules-source failed! How do you wish to prceed?
View
Continue
Stop

I press Continue...

have you 'Viewed' instead of trying to continue?  you are probably missing out
out important info on why this is failing and leading to-


> **CanadianMan said:**
> ..(buildlog)...WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
is missing; modules will have no dependencies and modversions...(buildlog)...

it's looking for the Module.symvers @ /linux/src/linux-source-2.6.15... have you looked
to see if it's there or somehwere else on the system?

---

### Post by CanadianMan on 2007-01-14
Has anyone tried getting this remote working on the 64bit version on Dapper?  I'm trying to see if that may be the problem for me.  Thanks.

---

### Post by CanadianMan on 2007-01-21
Well saddly i've been working on this for a week and am still having problems.

majoridiot, i did click View but didn't include in my post that I had.  To me what View displayed looked to be the same as the build log that i included.

Dispite all i've done to get mythtv working i've reinstalled dapper to start fresh.  I have gotten passed the error i had before but now when i start LIRC by using:

sudo /etc/init.d/lirc start 

and then use 

irw

i get nothing (just another command prompt) and i've restarted and seen dmesg which gives me this

[   49.241293] lirc_dev: IR Remote Control driver registered, at major 61
[   49.249823] lirc_mceusb2: no version for "lirc_unregister_plugin" found: kernel tainted.
[   49.251759]
[   49.251761] lirc_mceusb2: USB remote driver for LIRC v0.22
[   49.251983] lirc_mceusb2: Martin Blatter <martin_a_blatter@yahoo.com>
[   49.255089] usbcore: registered new driver lirc_mceusb2

i've looked up "lirc_unregisterd_plugin" and that doesn't seem to out of the ordinary.  SO i'm hoping that someone will have the magical answer to my problem because as far as i know i've done all that i can.

Thanks.

---

### Post by majoridiot on 2007-01-22
ok... i'm putting 2 and 2 together here and hopefully getting 4.  reviewing the errors from the
other posts, it looks like the problem is that your kernel has no facility for symbol linkage.

> **CanadianMan said:**
> WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers is missing; modules will have no dependencies and modversions.

which i have seen elsewhere as a problem in other distros... which leads to:

> **CanadianMan said:**
> [ 49.249823] lirc_mceusb2: no version for "lirc_unregister_plugin" found: kernel tainted.

when you build lirc, it is trying to link to the kernel via symbols it would have built, but couldn't build, 
because your kernel was missing Module.symvers.  from what i've seen, there is no way around this 
except to build the kernel with the correct options.  you might try asking around in the 64 bit forum 
about the 64 bit kernel and Module.symvers.  

it might be as simple as apt-getting one that was built correctly for lirc and then updating 
grub, rebuilding your lirc module, video driver, etc.

---

### Post by CanadianMan on 2007-01-22
Ok i've made a post here:

[http://www.ubuntuforums.org/showthread.php?p=2050760#post2050760](http://www.ubuntuforums.org/showthread.php?p=2050760#post2050760)

like i've said i've installed Edgy and still have the same problem/message in dmesg.

---

### Post by CanadianMan on 2007-01-22
Not sure if this helps but when i try to do:

sudo irrecord -d /dev/lirc0 lircd.conf

I get:

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not init hardware (lircd running ? --> close it, check permissions)

I've chmod 777 irrecord and have double checked that lircd is not running and i still get this when i run irrecord.  Does this shed some light on something or other?

Thanks.

---

### Post by CanadianMan on 2007-01-22
Ugh now i'm totally confused.  I clicked on this link:

[http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/)

scrolled down to mceusb and clicked on it and looked at this image of it.

[http://lirc.sourceforge.net/remotes/mceusb/hpmce.jpg](http://lirc.sourceforge.net/remotes/mceusb/hpmce.jpg)

my remote looks nothing like this which could be a very large problem.  I scrolled back up to hauppauge and clicked on both images in there and neither look like the remote i have.  SO i bought my tv tuner card which came with this remote off of newegg here is the link.

[http://www.newegg.com/Product/Product.asp?Item=N82E16815116631](http://www.newegg.com/Product/Product.asp?Item=N82E16815116631)

if you click on the image of contents in the box you'll see the remote i have. . . . . .

I'm guessing that i've miss lead you on the actual remote I have.  But what i wrote in the title for this post is what is exactly on the box so now i don't know what is what.  Right now i'm looking for what the remote i have really is.

---

### Post by majoridiot on 2007-01-22
that is the rc6 and it works with mceusb2... that's what i'm running.  i'm still pretty sure the
problem is your kernel.

---

### Post by CanadianMan on 2007-01-23
ok just checking i'm trying to get my kernel problem fixed now.

---

### Post by CanadianMan on 2007-01-24
Ok i believe i've fixed something, i no longer see:

WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers is missing; modules will have no dependencies and modversions.

However i still get another command prompt line after i do 'irw'.  In 'dmesg' it still says this:

[   47.033028] lirc_dev: IR Remote Control driver registered, at major 61 
[   47.034375] lirc_mceusb2: no version for "lirc_unregister_plugin" found: kernel tainted.
[   47.036408] 
[   47.036410] lirc_mceusb2: USB remote driver for LIRC v0.22
[   47.036413] lirc_mceusb2: Martin Blatter <martin_a_blatter@yahoo.com>
[   47.039985] usbcore: registered new driver lirc_mceusb2

I was on #ubuntu irc channel yesterday afternoon and someone told me to try this command:

sudo lircd -H dev/input -d /dev/input/event0

Then i ran 'irw' and I started getting flooded with newlines (no new command prompt line).  So i pressed some buttons on the remote at the receiver but still nothing came up.  I wish i remember the person's name but all i can remember is that it began with a J.  SO does this mean anything?  

When i type 'mode2' i get:

mode2: error opening /dev/lirc
mode2: No such file or directory

but if i do:

cd /dev
ls -l | grep lirc

i'll get this

srw-rw-rw- 1 root root           0 2007-01-24 08:59 lircd

Is my lirc device named wrong?

Thank you for your help.

---

