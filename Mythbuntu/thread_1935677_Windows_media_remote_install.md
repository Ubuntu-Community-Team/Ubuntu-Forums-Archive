---
title: "Windows media remote install?"
date: 2012-03-04
forum: Mythbuntu
---

### Post by langner on 2012-03-04
Hi all

I have been trying to install a windows media remote from the manufacture 'aim' version RC118 with a reciver version IR605A. Found here [http://www.maplin.co.uk/windows-media-centre-remote-control-218643?c=froogle&u=218643&t=module]("http://www.maplin.co.uk/windows-media-centre-remote-control-218643?c=froogle&u=218643&t=module")

I have used the the termianl code that lists what ir / usb is atteched and it finds the usb receiver. *lsusb*

I have used the presets from mythtv control centre and installed the 'windows media remote (all)' but im unsure of the setting to use for the receiver. Would this be 'usb direct tv'?

Now this is the part where things go wrong from me.  I did a search on how to install a wmc remote and came up with the following site.


[http://www.mythtv.org/wiki/MCE_Remote]("http://www.mythtv.org/wiki/MCE_Remote") <-weblink

I have been trying to follow the instructions listed in this site, *I have used the 0.8.7 not the pre1 as listed in the text.*

As you can see from my text below I have started to follow the instructions. I did try to do the ./setup.sh which didn't work. So I tried the next bit if it didn't work *the yum bit*.

I have also tried the cvs download but it wouldn't log in but the CVS Sanpshot did work.

I'm not sure if this is what I should be doing but I'm not sure what else I should be doing?

Thanks for your help

Matt

> myth@desktop:~$ cd /usr/src
myth@desktop:/usr/src$ sudo ./configure --prefix=/usr --sysconfdir=/etc/conf.d --with-x --with-driver=all
[sudo] password for myth: 
sudo: ./configure: command not found
myth@desktop:/usr/src$ cd lirc-0.8.7
myth@desktop:/usr/src/lirc-0.8.7$ cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
Logging in to :pserver:anonymous@lirc.cvs.sourceforge.net:2401/cvsroot/lirc
CVS password: 
cvs login: authorization failed: server lirc.cvs.sourceforge.net rejected access to /cvsroot/lirc for user anonymous
myth@desktop:/usr/src/lirc-0.8.7$ sudo./configure --prefix=/usr --sysconfdir=/etc/conf.d --with-x --with-driver=all
bash: sudo./configure: No such file or directory
myth@desktop:/usr/src/lirc-0.8.7$ sudo ./configure --prefix=/usr --sysconfdir=/etc/conf.d --with-x --with-driver=all
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking whether make sets $(MAKE)... (cached) yes
checking for mknod... /bin/mknod
checking for mkfifo... /usr/bin/mkfifo
checking for depmod... /sbin/depmod
checking for libusb-config... no
checking whether ln -s works... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for python... /usr/bin/python
checking for python version... 2.7
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.7/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.7/dist-packages
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for gethostname... yes
checking for gettimeofday... yes
checking for mkfifo... yes
checking for select... yes
checking for socket... yes
checking for strdup... yes
checking for strerror... yes
checking for strtoul... yes
checking for snprintf... yes
checking for strsep... yes
checking for vsyslog... yes
checking for forkpty... no
checking for forkpty in -lutil... yes
checking vga.h usability... no
checking vga.h presence... no
checking for vga.h... no
checking for X... no
checking for getopt_long... yes
checking for mktemp... yes
checking for Linux kernel sources... /lib/modules/3.0.0-16-generic/build/
checking for which drivers can be installed on this system... 
checking for caraca_init in -lcaraca_client... no
checking ftdi.h usability... no
checking ftdi.h presence... no
checking for ftdi.h... no
checking iguanaIR.h usability... no
checking iguanaIR.h presence... no
checking for iguanaIR.h... no
checking for ir_strerror in -lirman... no
checking for ir_strerror in -lirman_sw... no
checking portaudio.h usability... no
checking portaudio.h presence... no
checking for portaudio.h... no
checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... no
checking scsi/sg.h usability... yes
checking scsi/sg.h presence... yes
checking for scsi/sg.h... yes
checking linux/input.h usability... yes
checking linux/input.h presence... yes
checking for linux/input.h... yes
checking linux/types.h usability... yes
checking linux/types.h presence... yes
checking for linux/types.h... yes
checking for linux/hiddev.h... yes
checking for HIDDEV_FLAG_UREF support... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking linux/i2c-dev.h usability... yes
checking linux/i2c-dev.h presence... yes
checking for linux/i2c-dev.h... yes
checking for daemon... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating drivers/Makefile
config.status: creating drivers/lirc_atiusb/Makefile
config.status: creating drivers/lirc_bt829/Makefile
config.status: creating drivers/lirc_ene0100/Makefile
config.status: creating drivers/lirc_dev/Makefile
config.status: creating drivers/lirc_gpio/Makefile
config.status: creating drivers/lirc_i2c/Makefile
config.status: creating drivers/lirc_igorplugusb/Makefile
config.status: creating drivers/lirc_ttusbir/Makefile
config.status: creating drivers/lirc_imon/Makefile
config.status: creating drivers/lirc_it87/Makefile
config.status: creating drivers/lirc_ite8709/Makefile
config.status: creating drivers/lirc_mceusb/Makefile
config.status: creating drivers/lirc_parallel/Makefile
config.status: creating drivers/lirc_sasem/Makefile
config.status: creating drivers/lirc_serial/Makefile
config.status: creating drivers/lirc_sir/Makefile
config.status: creating drivers/lirc_streamzap/Makefile
config.status: creating drivers/lirc_wpc8769l/Makefile
config.status: creating daemons/Makefile
config.status: creating tools/Makefile
config.status: creating doc/Makefile
config.status: creating doc/man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

All kernel modules will be built.

Now enter 'make' and 'make install' to compile and install the package.

myth@desktop:/usr/src/lirc-0.8.7$ sudo make
make  all-recursive
make[1]: Entering directory `/usr/src/lirc-0.8.7'
Making all in drivers
make[2]: Entering directory `/usr/src/lirc-0.8.7/drivers'
Making all in lirc_dev
make[3]: Entering directory `/usr/src/lirc-0.8.7/drivers/lirc_dev'
cp ./../lirc_dev/Module*.symvers .
cp: cannot stat `./../lirc_dev/Module*.symvers': No such file or directory
make[3]: [lirc_dev.o] Error 1 (ignored)
mv Makefile Makefile.automake
cp ./../Makefile.kernel Makefile
CPPFLAGS="" CFLAGS="" LDFLAGS="" \
	make -C /lib/modules/3.0.0-16-generic/build/ SUBDIRS=/usr/src/lirc-0.8.7/drivers/lirc_dev modules \
		KBUILD_VERBOSE=1
make[4]: Entering directory `/usr/src/linux-headers-3.0.0-16-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (	\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /usr/src/lirc-0.8.7/drivers/lirc_dev/.tmp_versions ; rm -f /usr/src/lirc-0.8.7/drivers/lirc_dev/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/src/lirc-0.8.7/drivers/lirc_dev
  gcc -Wp,-MD,/usr/src/lirc-0.8.7/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6.1/include  -I/usr/src/linux-headers-3.0.0-16-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I../.. -I/usr/src/lirc-0.8.7/drivers/lirc_dev/. -I/usr/src/lirc-0.8.7/drivers/lirc_dev/. -I/usr/src/lirc-0.8.7/drivers/lirc_dev/../.. -I/usr/src/lirc-0.8.7/drivers/lirc_dev/../.. -I/lib/modules/3.0.0-16-generic/build//include/ -I/lib/modules/3.0.0-16-generic/build//drivers/media/video/  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -c -o /usr/src/lirc-0.8.7/drivers/lirc_dev/.tmp_lirc_dev.o /usr/src/lirc-0.8.7/drivers/lirc_dev/lirc_dev.c
/usr/src/lirc-0.8.7/drivers/lirc_dev/lirc_dev.c:45:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[5]: *** [/usr/src/lirc-0.8.7/drivers/lirc_dev/lirc_dev.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.8.7/drivers/lirc_dev] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-3.0.0-16-generic'
make[3]: *** [lirc_dev.o] Error 2
make[3]: Leaving directory `/usr/src/lirc-0.8.7/drivers/lirc_dev'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/lirc-0.8.7/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.7'
make: *** [all] Error 2
myth@desktop:/usr/src/lirc-0.8.7$ 

---

### Post by azmyth on 2012-03-04
Just a guess. But I believe you'll need lirc 0.90 for kernel 3.0 and higher.

---

### Post by langner on 2012-03-05
Azmyth

Thanks for getting back to me. I tried it with version 0.9.0 and a simular thing happened with the same errors in the same place. I still couldn't get any further with it. 

I do have some good news, the romte started working but I'm not sure how. So in this case I'm going to leave it there. 

There is a saying "If it aint broke, don't fix it" so that is what I am going to do (or not do in this case).

Thanks
Matt :D

---

