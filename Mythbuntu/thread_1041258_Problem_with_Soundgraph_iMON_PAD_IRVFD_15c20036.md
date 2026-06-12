---
title: "Problem with Soundgraph iMON PAD IR/VFD 15c2:0036"
date: 2009-01-16
forum: Mythbuntu
---

### Post by Freddan101 on 2009-01-16
Hello!

I have run Mythbuntu 7.10 for about a year but never gotten my remote, nor my VFD on my Silverstone LC16MR to work even after a lot of forum reading and testing. The devices didn't even show up under /dev. So I finally gave up and used a wireless keyboard.

When Mythbuntu 8.10 came out I thought it was time to try again so I installed it on a parallel disk. Though, same problem occurred - no devices under /dev. I started to read the forums again and now I found out what could be the problem. The usbhid "steals" the device and loads its driver which makes Ubuntu think it's a keyboard or mouse. 

Therefore I followed a post and forced usbhid to not load the driver. Success! The devices (lirc0, lirc1, lcd0 and lcd1) showed up under /dev and I could load lirc according to the posts. But! I only got the remote to work halfway. Play, pause and so on worked but not the directional buttons, i.e. lirc1 worked but not lirc0. Therefore I thought I should start from scratch and do it properly. 

I reinstalled 8.10, added all official patches and mainly followed [**this post**]("http://www.mythtv.org/wiki/index.php/SilverstoneTek_LC16M") but also [**this**]("http://dolot.kipdola.com/index.php?title=Install_Thermaltake_LIRC") and [**this post**]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html") to figure out which packages to install to be able to compile lirc. But I still can't get it to work. I must do something wrong when compiling lirc. Therefore I thought I should post here and hope that some friendly fellow Myth user with greater knowledge than myself can assist as I feel I'm close to the solution now that usbhid doesn't steal the device. Please, bare with me!

I did the following:

```
mount -t usbfs none /proc/bus/usb

cat /proc/bus/usb/devices 

T:  Bus=03 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  **Vendor=15c2 ProdID=0036** Rev= 0.01
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
```

which shows that usbhid loads the driver. I created /etc/modprobe.d/usbhid and added: 

```
options usbhid quirks=0x15c2:0x0036:0x0004
``` 

to stop usbhid from doing this. I ran below to apply the changes:

```
depmod -ae
update-initramfs -u
```

Uninstalled the default lirc package:

```
sudo apt-get remove lirc
```

Installed packages needed (from what I could read in the posts) to compile lirc:

```
apt-get install cvs
apt-get build-dep lirc
apt-get install libtool automake1.9 autoconf
apt-get install cvs build-essential automake
apt-get install bzr
```

Checked out latest lirc cvs:

```
cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
```

In the lirc folder I ran ./autogen.sh which gave a couple of warnings which I'm not sure are critical:

```
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
```

and then ./setup.sh

```
Driver Configuration > USB Devices > Soundgraph iMON PAD IR/VFD
Save configuration & run configure
```

which gave ok output except below which I'm not sure is critical either.

```
checking for a sed that does not truncate output... ./configure: line 4116: echo: write error: Broken pipe
/bin/sed
```

Then ran make which gave some error and warnings (last portion of the output):

```

gcc -Wp,-MD,/usr/src/lirc/drivers/lirc_dev/.lirc_dev.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-
gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-9-generic/arch/x86/include -include 
include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -
fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred
-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables 
-mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer 
-fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -
DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I../.. -I/usr/src/lirc/drivers/lirc_dev/. -I/usr/src/lirc/drivers/lirc_dev/. -
I/usr/src/lirc/drivers/lirc_dev/../.. -I/usr/src/lirc/drivers/lirc_dev/../.. -I/lib/modules/2.6.27-9-
generic/build//include/ -I/lib/modules/2.6.27-9-generic/build//drivers/media/video/  -D"KBUILD_STR(s)=#s" -
D"KBUILD_BASENAME=KBUILD_STR(lirc_dev.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -DMODULE -c -o 
/usr/src/lirc/drivers/lirc_dev/lirc_dev.mod.o /usr/src/lirc/drivers/lirc_dev/lirc_dev.mod.c
  ld -r -m elf_i386  --build-id -o /usr/src/lirc/drivers/lirc_dev/lirc_dev.ko 
/usr/src/lirc/drivers/lirc_dev/lirc_dev.o /usr/src/lirc/drivers/lirc_dev/lirc_dev.mod.o
make[4]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
mv Makefile.automake Makefile
make[3]: Leaving directory `/usr/src/lirc/drivers/lirc_dev'
Making all in lirc_imon
make[3]: Entering directory `/usr/src/lirc/drivers/lirc_imon'
cp ./../lirc_dev/Module*.symvers .
mv Makefile Makefile.automake
cp ./../Makefile.kernel Makefile
CPPFLAGS="" CFLAGS="" LDFLAGS="" \
        make -C /lib/modules/2.6.27-9-generic/build/ SUBDIRS=/usr/src/lirc/drivers/lirc_imon modules \
                KBUILD_VERBOSE=1
make[4]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \
echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
echo;                                                           \
        /bin/false)
mkdir -p /usr/src/lirc/drivers/lirc_imon/.tmp_versions ; rm -f /usr/src/lirc/drivers/lirc_imon/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/src/lirc/drivers/lirc_imon
  gcc -Wp,-MD,/usr/src/lirc/drivers/lirc_imon/.lirc_imon.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-
gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-9-generic/arch/x86/include -include 
include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -
fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred
-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables 
-mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer 
-fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -
DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I../.. -I/usr/src/lirc/drivers/lirc_imon/. -I/usr/src/lirc/drivers/lirc_imon/. 
-I/usr/src/lirc/drivers/lirc_imon/../.. -I/usr/src/lirc/drivers/lirc_imon/../.. -I/lib/modules/2.6.27-9-
generic/build//include/ -I/lib/modules/2.6.27-9-generic/build//drivers/media/video/ -DMODULE -D"KBUILD_STR(s)=#s" 
-D"KBUILD_BASENAME=KBUILD_STR(lirc_imon)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_imon)" -c -o 
/usr/src/lirc/drivers/lirc_imon/.tmp_lirc_imon.o /usr/src/lirc/drivers/lirc_imon/lirc_imon.c
(cat /dev/null;   echo kernel//usr/src/lirc/drivers/lirc_imon/lirc_imon.ko;) > 
/usr/src/lirc/drivers/lirc_imon/modules.order
  Building modules, stage 2.
make -f /usr/src/linux-headers-2.6.27-9-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.27-9-generic/Module.symvers -I 
/usr/src/lirc/drivers/lirc_imon/Module.symvers  -o /usr/src/lirc/drivers/lirc_imon/Module.symvers -S -K 

/usr/src/linux-headers-2.6.27-9-generic/Module.markers -M /usr/src/lirc/drivers/lirc_imon/Module.markers -w  -s
  gcc -Wp,-MD,/usr/src/lirc/drivers/lirc_imon/.lirc_imon.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-
gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-9-generic/arch/x86/include -include 
include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -
fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred
-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables 
-mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer 
-fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -
DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I../.. -I/usr/src/lirc/drivers/lirc_imon/. -I/usr/src/lirc/drivers/lirc_imon/. 
-I/usr/src/lirc/drivers/lirc_imon/../.. -I/usr/src/lirc/drivers/lirc_imon/../.. -I/lib/modules/2.6.27-9-
generic/build//include/ -I/lib/modules/2.6.27-9-generic/build//drivers/media/video/  -D"KBUILD_STR(s)=#s" -
D"KBUILD_BASENAME=KBUILD_STR(lirc_imon.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_imon)" -DMODULE -c -o 
/usr/src/lirc/drivers/lirc_imon/lirc_imon.mod.o /usr/src/lirc/drivers/lirc_imon/lirc_imon.mod.c
  ld -r -m elf_i386  --build-id -o /usr/src/lirc/drivers/lirc_imon/lirc_imon.ko 
/usr/src/lirc/drivers/lirc_imon/lirc_imon.o /usr/src/lirc/drivers/lirc_imon/lirc_imon.mod.o
make[4]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
mv Makefile.automake Makefile
make[3]: Leaving directory `/usr/src/lirc/drivers/lirc_imon'
make[3]: Entering directory `/usr/src/lirc/drivers'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/usr/src/lirc/drivers'
make[2]: Leaving directory `/usr/src/lirc/drivers'
Making all in daemons
make[2]: Entering directory `/usr/src/lirc/daemons'
./input_map.sh >input_map.inc
make  all-am
make[3]: Entering directory `/usr/src/lirc/daemons'
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT hw-types.o -MD -MP -MF .deps/hw-types.Tpo -c -o hw-types.o 
hw-types.c
mv -f .deps/hw-types.Tpo .deps/hw-types.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT ir_remote.o -MD -MP -MF .deps/ir_remote.Tpo -c -o ir_remote.o 
ir_remote.c
mv -f .deps/ir_remote.Tpo .deps/ir_remote.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT release.o -MD -MP -MF .deps/release.Tpo -c -o release.o 
release.c
mv -f .deps/release.Tpo .deps/release.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT hw_default.o -MD -MP -MF .deps/hw_default.Tpo -c -o 
hw_default.o hw_default.c
mv -f .deps/hw_default.Tpo .deps/hw_default.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT receive.o -MD -MP -MF .deps/receive.Tpo -c -o receive.o 
receive.c
mv -f .deps/receive.Tpo .deps/receive.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT transmit.o -MD -MP -MF .deps/transmit.Tpo -c -o transmit.o 
transmit.c
mv -f .deps/transmit.Tpo .deps/transmit.Po
rm -f libhw_module.a
ar cru libhw_module.a hw-types.o ir_remote.o release.o hw_default.o receive.o transmit.o
ranlib libhw_module.a
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT irrecord.o -MD -MP -MF .deps/irrecord.Tpo -c -o irrecord.o 
irrecord.c
config_file.h:26: warning: âall_flagsâ defined but not used
irrecord.c: In function âget_repeat_lengthâ:
irrecord.c:2351: warning: âsumâ may be used uninitialized in this function
irrecord.c: In function âget_lead_lengthâ:
irrecord.c:2258: warning: âsumâ may be used uninitialized in this function
irrecord.c: In function âget_trail_lengthâ:
irrecord.c:2235: warning: âsumâ may be used uninitialized in this function
irrecord.c: In function âget_data_lengthâ:
irrecord.c:2452: warning: âsumâ may be used uninitialized in this function
mv -f .deps/irrecord.Tpo .deps/irrecord.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT config_file.o -MD -MP -MF .deps/config_file.Tpo -c -o 
config_file.o config_file.c
mv -f .deps/config_file.Tpo .deps/config_file.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT dump_config.o -MD -MP -MF .deps/dump_config.Tpo -c -o 
dump_config.o dump_config.c
mv -f .deps/dump_config.Tpo .deps/dump_config.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT input_map.o -MD -MP -MF .deps/input_map.Tpo -c -o input_map.o 
input_map.c
mv -f .deps/input_map.Tpo .deps/input_map.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o irrecord irrecord.o config_file.o dump_config.o 
input_map.o libhw_module.a
libtool: link: gcc -O2 -g -Wall -o irrecord irrecord.o config_file.o dump_config.o input_map.o  libhw_module.a
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT lircd.o -MD -MP -MF .deps/lircd.Tpo -c -o lircd.o lircd.c
lircd.c: In function âstart_serverâ:
lircd.c:817: warning: ignoring return value of âftruncateâ, declared with attribute warn_unused_result
lircd.c: In function âdaemonizeâ:
lircd.c:1046: warning: ignoring return value of âftruncateâ, declared with attribute warn_unused_result
lircd.c: At top level:
config_file.h:26: warning: âall_flagsâ defined but not used
mv -f .deps/lircd.Tpo .deps/lircd.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o lircd lircd.o config_file.o input_map.o 
libhw_module.a
libtool: link: gcc -O2 -g -Wall -o lircd lircd.o config_file.o input_map.o  libhw_module.a
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT lircmd.o -MD -MP -MF .deps/lircmd.Tpo -c -o lircmd.o lircmd.c
lircmd.c: In function âmsendâ:
lircmd.c:253: warning: ignoring return value of âwriteâ, declared with attribute warn_unused_result
lircmd.c:270: warning: ignoring return value of âwriteâ, declared with attribute warn_unused_result
lircmd.c:289: warning: ignoring return value of âwriteâ, declared with attribute warn_unused_result
lircmd.c: In function âloopâ:
lircmd.c:694: warning: use of assignment suppression and length modifier together in scanf format
mv -f .deps/lircmd.Tpo .deps/lircmd.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o lircmd lircmd.o
libtool: link: gcc -O2 -g -Wall -o lircmd lircmd.o
make[3]: Leaving directory `/usr/src/lirc/daemons'
make[2]: Leaving directory `/usr/src/lirc/daemons'
Making all in tools
make[2]: Entering directory `/usr/src/lirc/tools'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT lirc_client.lo 
-MD -MP -MF .deps/lirc_client.Tpo -c -o lirc_client.lo lirc_client.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -I.. -O2 -g -Wall -MT lirc_client.lo -MD -MP -MF 
.deps/lirc_client.Tpo -c lirc_client.c  -fPIC -DPIC -o .libs/lirc_client.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -I.. -O2 -g -Wall -MT lirc_client.lo -MD -MP -MF 
.deps/lirc_client.Tpo -c lirc_client.c -o lirc_client.o >/dev/null 2>&1
mv -f .deps/lirc_client.Tpo .deps/lirc_client.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall -version-info 2:1:2  -o liblirc_client.la -rpath 
/usr/local/lib lirc_client.lo
libtool: link: gcc -shared  .libs/lirc_client.o      -Wl,-soname -Wl,liblirc_client.so.0 -o 
.libs/liblirc_client.so.0.2.1
libtool: link: (cd ".libs" && rm -f "liblirc_client.so.0" && ln -s "liblirc_client.so.0.2.1" "liblirc_client.so.0")
libtool: link: (cd ".libs" && rm -f "liblirc_client.so" && ln -s "liblirc_client.so.0.2.1" "liblirc_client.so")
libtool: link: ar cru .libs/liblirc_client.a  lirc_client.o
libtool: link: ranlib .libs/liblirc_client.a
libtool: link: ( cd ".libs" && rm -f "liblirc_client.la" && ln -s "../liblirc_client.la" "liblirc_client.la" )
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT irw.o -MD -MP -MF .deps/irw.Tpo -c -o irw.o irw.c
irw.c: In function âmainâ:
irw.c:99: warning: ignoring return value of âwriteâ, declared with attribute warn_unused_result
mv -f .deps/irw.Tpo .deps/irw.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o irw irw.o
libtool: link: gcc -O2 -g -Wall -o irw irw.o

gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT irpty.o -MD -MP -MF .deps/irpty.Tpo -c -o irpty.o irpty.c
mv -f .deps/irpty.Tpo .deps/irpty.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o irpty irpty.o liblirc_client.la -lutil
libtool: link: gcc -O2 -g -Wall -o .libs/irpty irpty.o  ./.libs/liblirc_client.so -lutil
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT irexec.o -MD -MP -MF .deps/irexec.Tpo -c -o irexec.o irexec.c
irexec.c: In function âmainâ:
irexec.c:111: warning: ignoring return value of âsystemâ, declared with attribute warn_unused_result
mv -f .deps/irexec.Tpo .deps/irexec.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o irexec irexec.o liblirc_client.la
libtool: link: gcc -O2 -g -Wall -o .libs/irexec irexec.o  ./.libs/liblirc_client.so
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT ircat.o -MD -MP -MF .deps/ircat.Tpo -c -o ircat.o ircat.c
mv -f .deps/ircat.Tpo .deps/ircat.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o ircat ircat.o liblirc_client.la
libtool: link: gcc -O2 -g -Wall -o .libs/ircat ircat.o  ./.libs/liblirc_client.so
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT mode2.o -MD -MP -MF .deps/mode2.Tpo -c -o mode2.o mode2.c
mv -f .deps/mode2.Tpo .deps/mode2.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o mode2 mode2.o ../daemons/libhw_module.a
libtool: link: gcc -O2 -g -Wall -o mode2 mode2.o  ../daemons/libhw_module.a
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT irsend.o -MD -MP -MF .deps/irsend.Tpo -c -o irsend.o irsend.c
mv -f .deps/irsend.Tpo .deps/irsend.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o irsend irsend.o
libtool: link: gcc -O2 -g -Wall -o irsend irsend.o
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT lircrcd.o -MD -MP -MF .deps/lircrcd.Tpo -c -o lircrcd.o 
lircrcd.c
lircrcd.c: In function âread_timeoutâ:
lircrcd.c:237: warning: reading through null pointer (argument 3)
lircrcd.c:245: warning: reading through null pointer (argument 3)
lircrcd.c: In function âadd_clientâ:
lircrcd.c:321: warning: pointer targets in passing argument 3 of âacceptâ differ in signedness
lircrcd.c:325: warning: reading through null pointer (argument 3)
lircrcd.c: In function âloopâ:
lircrcd.c:730: warning: reading through null pointer (argument 3)
lircrcd.c: In function âmainâ:
lircrcd.c:991: warning: ignoring return value of âgetcwdâ, declared with attribute warn_unused_result
mv -f .deps/lircrcd.Tpo .deps/lircrcd.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o lircrcd lircrcd.o liblirc_client.la
libtool: link: gcc -O2 -g -Wall -o .libs/lircrcd lircrcd.o  ./.libs/liblirc_client.so
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT irxevent.o -MD -MP -MF .deps/irxevent.Tpo -c -o irxevent.o 
irxevent.c
irxevent.c: In function âfind_sub_sub_windowâ:
irxevent.c:234: warning: pointer targets in passing argument 4 of âXGetGeometryâ differ in signedness
irxevent.c:234: warning: pointer targets in passing argument 5 of âXGetGeometryâ differ in signedness
irxevent.c:243: warning: pointer targets in passing argument 2 of âfind_sub_sub_windowâ differ in signedness
irxevent.c:243: warning: pointer targets in passing argument 3 of âfind_sub_sub_windowâ differ in signedness
irxevent.c: In function âfind_sub_windowâ:
irxevent.c:278: warning: pointer targets in passing argument 4 of âXGetGeometryâ differ in signedness
irxevent.c:278: warning: pointer targets in passing argument 5 of âXGetGeometryâ differ in signedness
irxevent.c:287: warning: pointer targets in passing argument 2 of âfind_sub_sub_windowâ differ in signedness
irxevent.c:287: warning: pointer targets in passing argument 3 of âfind_sub_sub_windowâ differ in signedness
irxevent.c: At top level:
irxevent.c:139: warning: âwâ defined but not used
mv -f .deps/irxevent.Tpo .deps/irxevent.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o irxevent irxevent.o -lSM -lICE -lX11  
liblirc_client.la
libtool: link: gcc -O2 -g -Wall -o .libs/irxevent irxevent.o  -lSM -lICE -lX11 ./.libs/liblirc_client.so
gcc -DHAVE_CONFIG_H -I. -I.. -I..    -O2 -g -Wall -MT xmode2.o -MD -MP -MF .deps/xmode2.Tpo -c -o xmode2.o xmode2.c
xmode2.c: In function âinitscreenâ:
xmode2.c:88: warning: pointer targets in passing argument 2 of âXParseGeometryâ differ in signedness
xmode2.c:88: warning: pointer targets in passing argument 3 of âXParseGeometryâ differ in signedness
mv -f .deps/xmode2.Tpo .deps/xmode2.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o xmode2 xmode2.o -lSM -lICE -lX11
libtool: link: gcc -O2 -g -Wall -o xmode2 xmode2.o  -lSM -lICE -lX11
echo "#! /usr/bin/python" >pronto2lirc
cat pronto2lirc.py >>pronto2lirc
chmod +x pronto2lirc
make[2]: Leaving directory `/usr/src/lirc/tools'
Making all in doc
make[2]: Entering directory `/usr/src/lirc/doc'
Making all in man
make[3]: Entering directory `/usr/src/lirc/doc/man'
(cd .. && make release-man)
make[4]: Entering directory `/usr/src/lirc/doc'
gcc -DHAVE_CONFIG_H -I. -I..     -O2 -g -Wall -MT man2html.o -MD -MP -MF .deps/man2html.Tpo -c -o man2html.o 
man2html.c
man2html.c: In function âmainâ:
man2html.c:3030: warning: format not a string literal and no format arguments
mv -f .deps/man2html.Tpo .deps/man2html.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O2 -g -Wall   -o man2html man2html.o
libtool: link: gcc -O2 -g -Wall -o man2html man2html.o
top_srcdir=".." srcdir="." builddir="." \
                           top_builddir=".." ./release-man.sh
./release-man.sh: 127: help2man: not found
sed: can't read man/irpty.1: No such file or directory
./release-man.sh: 127: help2man: not found
sed: can't read man/irexec.1: No such file or directory
./release-man.sh: 127: help2man: not found
sed: can't read man/ircat.1: No such file or directory
./release-man.sh: 127: help2man: not found
sed: can't read man/irw.1: No such file or directory
./release-man.sh: 127: help2man: not found
sed: can't read man/mode2.1: No such file or directory
./release-man.sh: 127: help2man: not found
sed: can't read man/smode2.1: No such file or directory
./release-man.sh: 127: help2man: not found
sed: can't read man/xmode2.1: No such file or directory
./release-man.sh: 127: help2man: not found
sed: can't read man/irsend.1: No such file or directory
./release-man.sh: 127: help2man: not found
sed: can't read man/irrecord.1: No such file or directory
./release-man.sh: 127: help2man: not found
sed: can't read man/lircd.8: No such file or directory
./release-man.sh: 127: help2man: not found
sed: can't read man/lircmd.8: No such file or directory
./release-man.sh: 127: help2man: not found
sed: can't read man/lircrcd.1: No such file or directory
./release-man.sh: 127: help2man: not found
sed: can't read man/irxevent.1: No such file or directory
make[4]: Leaving directory `/usr/src/lirc/doc'
make[3]: Leaving directory `/usr/src/lirc/doc/man'
make[3]: Entering directory `/usr/src/lirc/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/usr/src/lirc/doc'
make[2]: Leaving directory `/usr/src/lirc/doc'
make[2]: Entering directory `/usr/src/lirc'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/usr/src/lirc'
make[1]: Leaving directory `/usr/src/lirc'
```

and then make install

```
Making install in drivers
make[1]: Entering directory `/usr/src/lirc/drivers'
Making install in lirc_dev
make[2]: Entering directory `/usr/src/lirc/drivers/lirc_dev'
make[3]: Entering directory `/usr/src/lirc/drivers/lirc_dev'
test -e /dev/lirc || (/bin/bash /usr/src/lirc/install-sh -d /dev && /bin/mknod /dev/lirc c 61 0)
/bin/bash /usr/src/lirc/install-sh -d /lib/modules/2.6.27-9-generic/misc
 /usr/bin/install -c -m 644 lirc_dev.ko /lib/modules/2.6.27-9-generic/misc/lirc_dev.ko
/sbin/depmod -a
make[3]: Leaving directory `/usr/src/lirc/drivers/lirc_dev'
make[2]: Leaving directory `/usr/src/lirc/drivers/lirc_dev'
Making install in lirc_imon
make[2]: Entering directory `/usr/src/lirc/drivers/lirc_imon'
make[3]: Entering directory `/usr/src/lirc/drivers/lirc_imon'
test -e /dev/lirc || (/bin/bash /usr/src/lirc/install-sh -d /dev && /bin/mknod /dev/lirc c 61 0)
/bin/bash /usr/src/lirc/install-sh -d /lib/modules/2.6.27-9-generic/misc
 /usr/bin/install -c -m 644 lirc_imon.ko /lib/modules/2.6.27-9-generic/misc/lirc_imon.ko
/sbin/depmod -a
make[3]: Leaving directory `/usr/src/lirc/drivers/lirc_imon'
make[2]: Leaving directory `/usr/src/lirc/drivers/lirc_imon'
make[2]: Entering directory `/usr/src/lirc/drivers'
make[3]: Entering directory `/usr/src/lirc/drivers'
test "" = "" || test -L /dev/lirc || (/bin/bash /usr/src/lirc/install-sh -d /dev && cd `dirname ` && ln -s 
`basename ` lirc)
test "imon_pad" != "mediafocusI" || test -c /dev/lirc || (/bin/bash /usr/src/lirc/install-sh -d /dev && /bin/mknod 
/dev/lirc c 61 0)
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/src/lirc/drivers'
make[2]: Leaving directory `/usr/src/lirc/drivers'
make[1]: Leaving directory `/usr/src/lirc/drivers'
Making install in daemons
make[1]: Entering directory `/usr/src/lirc/daemons'
make  install-am
make[2]: Entering directory `/usr/src/lirc/daemons'
make[3]: Entering directory `/usr/src/lirc/daemons'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'irrecord' '/usr/local/bin/irrecord'
libtool: install: /usr/bin/install -c irrecord /usr/local/bin/irrecord
test -e /dev/lircd || (/bin/bash /usr/src/lirc/install-sh -d /dev && /bin/mknod /dev/lircd p)
test -e /dev/lircm || (/bin/bash /usr/src/lirc/install-sh -d /dev && /bin/mknod /dev/lircm p)
test -z "/usr/local/sbin" || /bin/mkdir -p "/usr/local/sbin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'lircd' '/usr/local/sbin/lircd'
libtool: install: /usr/bin/install -c lircd /usr/local/sbin/lircd
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'lircmd' '/usr/local/sbin/lircmd'
libtool: install: /usr/bin/install -c lircmd /usr/local/sbin/lircmd
test "imon/lircd.conf.imon-pad" = ""  || test -e /etc/lircd.conf  || (/bin/bash /usr/src/lirc/install-sh -d /etc && 
/usr/bin/install -c -m 644 ../remotes/imon/lircd.conf.imon-pad /etc/lircd.conf)
test "" = "" || test -e /etc/lircmd.conf || (/bin/bash /usr/src/lirc/install-sh -d /etc && /usr/bin/install -c -m 
644 ../remotes/ /etc/lircmd.conf)
make[3]: Leaving directory `/usr/src/lirc/daemons'
make[2]: Leaving directory `/usr/src/lirc/daemons'
make[1]: Leaving directory `/usr/src/lirc/daemons'
Making install in tools
make[1]: Entering directory `/usr/src/lirc/tools'
make[2]: Entering directory `/usr/src/lirc/tools'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'liblirc_client.la' '/usr/local/lib/liblirc_client.la'
libtool: install: /usr/bin/install -c .libs/liblirc_client.so.0.2.1 /usr/local/lib/liblirc_client.so.0.2.1
libtool: install: (cd /usr/local/lib && { ln -s -f liblirc_client.so.0.2.1 liblirc_client.so.0 || { rm -f 
liblirc_client.so.0 && ln -s liblirc_client.so.0.2.1 liblirc_client.so.0; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f liblirc_client.so.0.2.1 liblirc_client.so || { rm -f 
liblirc_client.so && ln -s liblirc_client.so.0.2.1 liblirc_client.so; }; })
libtool: install: /usr/bin/install -c .libs/liblirc_client.lai /usr/local/lib/liblirc_client.la
libtool: install: /usr/bin/install -c .libs/liblirc_client.a /usr/local/lib/liblirc_client.a
libtool: install: chmod 644 /usr/local/lib/liblirc_client.a
libtool: install: ranlib /usr/local/lib/liblirc_client.a
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig 
-n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'irw' '/usr/local/bin/irw'
libtool: install: /usr/bin/install -c irw /usr/local/bin/irw
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'irpty' '/usr/local/bin/irpty'
libtool: install: /usr/bin/install -c .libs/irpty /usr/local/bin/irpty
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'irexec' '/usr/local/bin/irexec'
libtool: install: /usr/bin/install -c .libs/irexec /usr/local/bin/irexec
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'ircat' '/usr/local/bin/ircat'
libtool: install: /usr/bin/install -c .libs/ircat /usr/local/bin/ircat
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'mode2' '/usr/local/bin/mode2'
libtool: install: /usr/bin/install -c mode2 /usr/local/bin/mode2
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'irsend' '/usr/local/bin/irsend'
libtool: install: /usr/bin/install -c irsend /usr/local/bin/irsend
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'lircrcd' '/usr/local/bin/lircrcd'
libtool: install: /usr/bin/install -c .libs/lircrcd /usr/local/bin/lircrcd
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'irxevent' '/usr/local/bin/irxevent'
libtool: install: /usr/bin/install -c .libs/irxevent /usr/local/bin/irxevent
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'xmode2' '/usr/local/bin/xmode2'
libtool: install: /usr/bin/install -c xmode2 /usr/local/bin/xmode2
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c 'pronto2lirc' '/usr/local/bin/pronto2lirc'
test -z "/usr/local/include/lirc" || /bin/mkdir -p "/usr/local/include/lirc"
 /usr/bin/install -c -m 644 'lirc_client.h' '/usr/local/include/lirc/lirc_client.h'
make[2]: Leaving directory `/usr/src/lirc/tools'
make[1]: Leaving directory `/usr/src/lirc/tools'
Making install in doc
make[1]: Entering directory `/usr/src/lirc/doc'
Making install in man
make[2]: Entering directory `/usr/src/lirc/doc/man'
make[3]: Entering directory `/usr/src/lirc/doc/man'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 './irexec.1' '/usr/local/share/man/man1/irexec.1'
 /usr/bin/install -c -m 644 './ircat.1' '/usr/local/share/man/man1/ircat.1'
 /usr/bin/install -c -m 644 './irpty.1' '/usr/local/share/man/man1/irpty.1'
 /usr/bin/install -c -m 644 './irrecord.1' '/usr/local/share/man/man1/irrecord.1'
 /usr/bin/install -c -m 644 './irw.1' '/usr/local/share/man/man1/irw.1'
 /usr/bin/install -c -m 644 './irxevent.1' '/usr/local/share/man/man1/irxevent.1'
 /usr/bin/install -c -m 644 './lircrcd.1' '/usr/local/share/man/man1/lircrcd.1'
 /usr/bin/install -c -m 644 './mode2.1' '/usr/local/share/man/man1/mode2.1'
 /usr/bin/install -c -m 644 './smode2.1' '/usr/local/share/man/man1/smode2.1'
 /usr/bin/install -c -m 644 './xmode2.1' '/usr/local/share/man/man1/xmode2.1'
 /usr/bin/install -c -m 644 './irsend.1' '/usr/local/share/man/man1/irsend.1'
test -z "/usr/local/share/man/man8" || /bin/mkdir -p "/usr/local/share/man/man8"
 /usr/bin/install -c -m 644 './lircd.8' '/usr/local/share/man/man8/lircd.8'
 /usr/bin/install -c -m 644 './lircmd.8' '/usr/local/share/man/man8/lircmd.8'
make[3]: Leaving directory `/usr/src/lirc/doc/man'
make[2]: Leaving directory `/usr/src/lirc/doc/man'
make[2]: Entering directory `/usr/src/lirc/doc'
make[3]: Entering directory `/usr/src/lirc/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/src/lirc/doc'
make[2]: Leaving directory `/usr/src/lirc/doc'
make[1]: Leaving directory `/usr/src/lirc/doc'
make[1]: Entering directory `/usr/src/lirc'
make[2]: Entering directory `/usr/src/lirc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/lirc'
make[1]: Leaving directory `/usr/src/lirc'
```

Copied the modules to the right folder:

```
sudo cp /lib/modules/`uname -r`/misc/lirc* /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_imon/
```

and added below to /etc/modules

```
lirc_dev 
lirc_imon
```

reboot

Unfortunately nothing seems to work:

```
dmesg |grep lirc
[   14.092364] lirc_dev: IR Remote Control driver registered, major 61
[   14.107773] lirc_imon: Unknown symbol lirc_unregister_driver
[   14.108221] lirc_imon: Unknown symbol lirc_register_driver
```

but at least usbhid doesn't load it's driver for the remote/VFD:

```
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0036 Rev= 0.01
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
```

I would be very greateful if someone had an idea what I'm doing wrong. If there is any other output that can help understanding my problem please let me know. I really would like to start using the remote and VFD to boost the WAF even more! :)

/Fred

---

### Post by Freddan101 on 2009-01-23
*bump*

---

### Post by stalvatero on 2009-01-26
Hi,
i've the same problem...doing the same steps (and probably following the same instructions).
I hope sameone can help us.

---

### Post by Freddan101 on 2009-01-27
I can glady tell you that I now got everything working! :D The process described above is totally right. The problem was that the CVS version I was using contained a bug.

Last Friday night I checked out a new version and compiled. Success! Both lirc0 and lirc1 buttons work. I thereafter installed the LCDProc package and changed to imon drivers in the config file. This made the display work as well.

Before you begin installing the CVS version, be sure to uninstall the lirc package first.

---

### Post by joshoekstra on 2009-01-27
I got it to work downloading only the lirc_imon.c from the drivers folder in Lirc CVS and then using the dpkg-reconfigure lirc-modules-source.
After using the different way to start lirc decribed in one the links above I'm now using the same device for a couple of months now :)

---

### Post by Cuban_Eight on 2009-01-28
Hello guys,

I'm having trouble with this, regardless of how many times I reload the cvs lirc.  I have usbhid leaving the iMON alone now, and dmesg gives me similar output to that in the first post.
```
root@Provider:~# dmesg |grep lirc
[   14.978591] lirc_imon: Unknown symbol lirc_unregister_driver
[   14.979988] lirc_imon: Unknown symbol lirc_register_driver
[   15.223083] lirc_imon: Unknown symbol lirc_unregister_driver
[   15.224516] lirc_imon: Unknown symbol lirc_register_driver
[   19.297895] lirc_dev: IR Remote Control driver registered, major 61 
[   19.316648] lirc_imon: Unknown symbol lirc_unregister_driver
[   19.317536] lirc_imon: Unknown symbol lirc_register_driver
[  744.045219] lirc_imon: Unknown symbol lirc_unregister_driver
[  744.046838] lirc_imon: Unknown symbol lirc_register_driver
[ 3785.962383] lirc_imon: Unknown symbol lirc_unregister_driver
[ 3785.963916] lirc_imon: Unknown symbol lirc_register_driver
[ 4447.506932] lirc_imon: Unknown symbol lirc_unregister_driver
[ 4447.507871] lirc_imon: Unknown symbol lirc_register_driver
[ 4968.016417] lirc_imon: Unknown symbol lirc_unregister_driver
[ 4968.018054] lirc_imon: Unknown symbol lirc_register_driver

```

If I do a modprobe I get..
```
root@Provider:~# modprobe lirc_imon
FATAL: Error inserting lirc_imon (/lib/modules/2.6.27-9-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

I'm using ubuntu 8.10 with the ID15c2:0036 device in a Silverstone LC16m case.  I've been banging away at this all day, its 47 Degress C outside and I think I've fried my brain.  Any help would be most welcome.

---

### Post by yunosh on 2009-01-28
I have lirc from CVS running with this device too for some time, but I'm experience a weird problem. All key presses coming through lirc0, i.e. the black buttons on the PAD, are sent twice. Does anybody else see this or maybe even have a workaround for it?

I filed a bug report for it a few days ago: [https://sourceforge.net/tracker/index.php?func=detail&aid=2529828&group_id=5444&atid=105444](https://sourceforge.net/tracker/index.php?func=detail&aid=2529828&group_id=5444&atid=105444)

---

### Post by Freddan101 on 2009-02-03
> **yunosh said:**
> I have lirc from CVS running with this device too for some time, but I'm experience a weird problem. All key presses coming through lirc0, i.e. the black buttons on the PAD, are sent twice. Does anybody else see this or maybe even have a workaround for it?

I filed a bug report for it a few days ago: [https://sourceforge.net/tracker/index.php?func=detail&aid=2529828&group_id=5444&atid=105444](https://sourceforge.net/tracker/index.php?func=detail&aid=2529828&group_id=5444&atid=105444)
Are you starting lirc like below?

```
/usr/local/sbin/lircd --driver=default --device=/dev/lirc0 --pidfile=/var/run/lirc0.pid --listen=8765
/usr/local/sbin/lircd --driver=default --device=/dev/lirc1 --pidfile=/var/run/lirc1.pid --output=/dev/lircd --connect=localhost:8765
```

---

### Post by yunosh on 2009-02-03
> **Freddan101 said:**
> Are you starting lirc like below?

Basically yes, as you can see from the bug report:

```
/usr/sbin/lircd --device=/dev/lirc0 --listen=8765 --listen
/usr/sbin/lircd --device=/dev/lirc1 --connect=localhost 8765 --output=/dev/lircd --connect=localhost 8765 --pidfile=/var/run/lircd1.pid
```

---

### Post by Freddan101 on 2009-02-03
Well... Now I got problems with the modules again. I got above to work on a test installation with kernel 2.6.27-9-generic. But by the time I reinstalled my original installation a new kernel, 2.6.27-11-generic, had been released.

So I've used the same lirc source, compiled new modules and copied lirc_dev.ko and lirc_imon.ko to /lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon. But they won't load at boot! It seems that some other version of these modules are loaded cause when I rmmod them I then can lsmod the modules and get:

```
[  909.870297] lirc_dev: IR Remote Control driver registered, major 61
[  924.049128] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD, v0.5
[  924.049134] lirc_imon: Venky Raju <dev@venky.ws>
[  924.050045] lirc_imon: imon_probe: found IMON device
[  924.050418] lirc_dev: lirc_register_driver: sample_rate: 0
[  924.050918] lirc_imon: imon_probe: Registered iMON driver(minor:0)
[  924.051401] lirc_imon: imon_probe: iMON device on usb<3:2> initialized
[  924.051877] lirc_imon: imon_probe: found IMON device
[  924.052263] lirc_dev: lirc_register_driver: sample_rate: 0
[  924.052628] lirc_imon: imon_probe: Registered iMON driver(minor:1)
[  924.052663] lirc_imon: imon_probe: iMON device on usb<3:2> initialized
[  924.052680] usbcore: registered new interface driver lirc_imon
[  924.316045] lirc_imon: IR port opened
[  924.528040] lirc_imon: IR port opened
```

I have tried to figure out where Ubuntu now looks for the modules but no luck. Has something changed between sources regarding how modules are loaded? Seems strange I think... 

When I manually have loaded the modules I can get the VFD to work, though I no longer can start lirc. It gives me:

```
lircd: error parsing child file value defined at line 13:
lircd: invalid quoting
lircd: reading of file '/etc/lircd.conf' failed
lircd: reading of config file failed
```

Line 13 is the one that says "include /usr/share/lirc/remotes/imon/lircd.conf.imon-pad" and that file is sure there and I have not messed with it.

---

### Post by yunosh on 2009-02-03
> **Freddan101 said:**
> So I've used the same lirc source, compiled new modules and copied lirc_dev.ko and lirc_imon.ko to /lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon. But they won't load at boot! It seems that some other version of these modules are loaded cause when I rmmod them I then can lsmod the modules and get:

The modules might be in /lib/modules/2.6.27-11-generic/updates/dkms/ after the kernel update.

---

### Post by Kalibur on 2009-02-03
Freddan your CVS in post 1 are wrong today here are the ones that work in order to run setup.sh

cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
cd lirc
./autogen.sh
./setup.sh

I got them from [http://xbmc.org/forum/showthread.php?p=251930](http://xbmc.org/forum/showthread.php?p=251930)

---

### Post by Freddan101 on 2009-02-04
> **Kalibur said:**
> Freddan your CVS in post 1 are wrong today here are the ones that work in order to run setup.sh

cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
cd lirc
./autogen.sh
./setup.sh

I got them from [http://xbmc.org/forum/showthread.php?p=251930](http://xbmc.org/forum/showthread.php?p=251930)
Kalibur, I can't see any difference between the CVS lines you mention and the ones in my post?

---

### Post by Kalibur on 2009-02-04
> **Freddan101 said:**
> Kalibur, I can't see any difference between the CVS lines you mention and the ones in my post?

Sorry seems there is no difference I was using copy and paste so maybe I mistakenly miscopied your cvs.  On what Ubuntu version architecture and kernel did you get this running because I have the 15c9:0038 I have been through gusty to jaunty 64bits and not even a flicker on the LCD screen am now installing win xp just to make sure the hardware works :(.  Am not to bothered about the remote I have a spare usb mce receiver should that become hard.:(

---

### Post by Freddan101 on 2009-02-04
I'm running 32 bit Mythbuntu 8.10 with kernel 2.6.27-11-generic. I got above to work on 2.6.27-09-generic on a parallel disk why I'm a bit confused right now.

I've listed all of the lirc_dev.ko and lirc_imon.ko on my system:

```
$ locate lirc_dev.ko
/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko
/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon/lirc_dev.ko
/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon/new/lirc_dev.ko
/lib/modules/2.6.27-11-generic/misc/lirc_dev.ko
/lib/modules/2.6.27-7-generic/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko
/usr/src/lirc/drivers/lirc_dev/.lirc_dev.ko.cmd
/usr/src/lirc/drivers/lirc_dev/lirc_dev.ko
```

```
$ locate lirc_imon.ko
/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko
/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon/new/lirc_imon.ko
/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon/old/lirc_imon.ko
/lib/modules/2.6.27-11-generic/misc/lirc_imon.ko
/lib/modules/2.6.27-7-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko
/usr/src/lirc/drivers/lirc_imon/.lirc_imon.ko.cmd
/usr/src/lirc/drivers/lirc_imon/lirc_imon.ko

```

Two of these modules are loading but not the "correct" ones which should be the ones located in /lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon/. I know it's not the correct ones as no devices show up under /dev.

```
$lsmod |grep lirc
lirc_imon              23052  0
lirc_dev               20020  1 lirc_imon
usbcore               149360  7 lirc_imon,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
```

```
$dmesg |grep lirc
[   12.870319] lirc_dev: IR Remote Control driver registered, major 61
[   12.892015] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD w/imon pad2keys patch, v0.3p2k
[   12.892019] lirc_imon: Venky Raju <dev@venky.ws>
[   12.892051] usbcore: registered new interface driver lirc_imon

```

If I unload them and load the modules in /lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon/ manually the devices show up under /dev. Though, lirc won't load but's giving me below:

```
lircd: error parsing child file value defined at line 13:
lircd: invalid quoting
lircd: reading of file '/etc/lircd.conf' failed
lircd: reading of config file failed
```

---

### Post by Kalibur on 2009-02-04
[B]Soundgraph iMON PAD IR/VFD(LCD) with MultiDirectionPad remote 15c2:0038
[/B]
So After reaching deep in my box rubbish I found an old hdd and the xp cdrom.  After several encounter with the blue screen of death I managed to install xp after after a sweet full year xp independence, bare with me I had to be sure the hardware was not the problem.  Installed Imedion HD software, imon lcd and the imod remote with the pad mouse control thing.
I can now rule the hardware fault out in fact am back in intrepid 64bt right now and the lcd screen is displaying the time PM 0699 or is it PM 0644 :P.
So why then is it working after an xp driver install!  I think the screen needing some sort of firmware to be installed to get its heart beating.
To everyone who got their LCD VFD screens to display something can you confirm having installed it in MS environment at least once? 
Also maybe some sort of driver wrapper is way to go with the remote pad?

Ok now I will attempt to get in running in Ubuntu.

---

### Post by Freddan101 on 2009-02-04
So after a lot of testing back and forth the mystery is solved once again. Actually it was a couple of things that created the problems.

Lirc_imon.ko was loaded from /lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon/old/ where I had backed up an old version of the file. I deleted this folder and hoped that the module in /lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon/ would load, but no. So I recreated the folder "old" and put the correct file in there. I guess there's an explanation why Ubuntu is looking in that folder but I have no clue so far.

What comes to lirc_dev.ko it loads from /lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_dev/.

The third and final fix was in the /cat/lircd.conf which said

```
include /usr/share/lirc/remotes/imon/lircd.conf.imon-pad
```

but what it should say was

```
include "/usr/share/lirc/remotes/imon/lircd.conf.imon-pad"
```

I also replaced the file above with /usr/src/lirc/remotes/imon/lircd.conf.imon-pad which should be more recent.

Remote and display works like a charm now! I've fixed a startup script in /etc/init.d which loads both lirc commands at startup. 

:popcorn:

---

### Post by Lido on 2009-03-22
I'm not able to get the lirc_imon module loaded either. Any idea?

```
$ sudo modprobe lirc_imon
FATAL: Error inserting lirc_imon (/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

When I look at dmesg, there's nothing:

```
$ tail /var/log/dmesg
[   19.040012] nxt200x: NXT2004 Detected
[   19.048016] tuner-simple 1-0061: creating new instance
[   19.048019] tuner-simple 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   19.048022] DVB: registering new adapter (saa7133[1])
[   19.048025] DVB: registering frontend 1 (Nextwave NXT200X VSB/QAM frontend)...
[   19.060032] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   19.060036] firmware: requesting dvb-fe-nxt2004.fw
[   19.061992] nxt2004: Waiting for firmware upload(2)...
[   19.076478] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.640029] nxt2004: Firmware upload complete

```

Also:```
$ l /dev/lirc*
crw-r--r-- 1 root root 61, 0 2009-03-22 00:41 /dev/lirc
prw-r--r-- 1 root root     0 2009-03-22 00:41 /dev/lircd
prw-r--r-- 1 root root     0 2009-03-22 00:41 /dev/lircm
```

---

### Post by Freddan101 on 2009-03-23
> **Lido said:**
> I'm not able to get the lirc_imon module loaded either. Any idea?

```
$ sudo modprobe lirc_imon
FATAL: Error inserting lirc_imon (/lib/modules/2.6.27-11-generic/kernel/ubuntu/lirc/lirc_imon.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

When I look at dmesg, there's nothing:

```
$ tail /var/log/dmesg
[   19.040012] nxt200x: NXT2004 Detected
[   19.048016] tuner-simple 1-0061: creating new instance
[   19.048019] tuner-simple 1-0061: type set to 68 (Philips TUV1236D ATSC/NTSC dual in)
[   19.048022] DVB: registering new adapter (saa7133[1])
[   19.048025] DVB: registering frontend 1 (Nextwave NXT200X VSB/QAM frontend)...
[   19.060032] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   19.060036] firmware: requesting dvb-fe-nxt2004.fw
[   19.061992] nxt2004: Waiting for firmware upload(2)...
[   19.076478] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.640029] nxt2004: Firmware upload complete

```

Also:```
$ l /dev/lirc*
crw-r--r-- 1 root root 61, 0 2009-03-22 00:41 /dev/lirc
prw-r--r-- 1 root root     0 2009-03-22 00:41 /dev/lircd
prw-r--r-- 1 root root     0 2009-03-22 00:41 /dev/lircm
```
To start with you have to make sure that lirc_dev.ko is loaded before lirc_imon.ko.

---

### Post by Lido on 2009-03-24
Would you mind telling me how to make sure that's happening? I'm getting kind of lost at this point.

---

### Post by Freddan101 on 2009-03-24
> **Lido said:**
> Would you mind telling me how to make sure that's happening? I'm getting kind of lost at this point.
I would start with finding out where the modules loading at boot are located (see my prev post/s above). When neither lirc_dev nor lirc_imon are loaded automatically you can insmod your compiled modules manually and check that they are ok.

---

### Post by Nils Grimsmo on 2009-03-24
Everything seems to load nicely here, but no /dev/lirc or /dev/lirc0 is created. 

```

root@kuken:~# lsb_release -r
Release:	9.04

root@kuken:~# uname -a
Linux kuken 2.6.28-11-generic #37-Ubuntu SMP Mon Mar 23 16:40:00 UTC 2009 x86_64 GNU/Linux

root@kuken:~# apt-cache policy lirc
lirc:
  Installed: 0.8.4a-0ubuntu3

root@kuken:~# cat /etc/modprobe.d/usbhid.conf 
options usbhid quirks=0x15c2:0x0036:0x0004

root@kuken:~# cat /proc/bus/usb/devices
...
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0036 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
...

```

Have run `dpkg-reconfigure lirc` and selected "Soundgraph iMON PAD IR/VFD" for remote, and "None" for IR transmitter (after avoiding a bug in the package installer [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/346468]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/346468") in the package installer.)

```

root@kuken:~# lsmod | grep lirc
lirc_imon              26124  0 
lirc_dev               22088  1 lirc_imon

root@kuken:~# dmesg
...
[ 3142.802664] lirc_dev: IR Remote Control driver registered, major 61 
[ 3142.804273] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD w/imon pad2keys patch, v0.3p2k
[ 3142.804275] lirc_imon: Venky Raju <dev@venky.ws>
[ 3142.804299] usbcore: registered new interface driver lirc_imon

root@kuken:~# ls -l /dev/lirc*
srw-rw-rw- 1 root root 0 2009-03-24 10:56 /dev/lircd

root@kuken:~# ps aux | grep lirc
root     26250  0.0  0.0  18032   596 ?        Ss   11:05   0:00 /usr/sbin/lircd --device=/dev/lirc0

```

/etc/init.d/lirc starts the daemon with `start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- --device=/dev/lirc0`.

Why does LIRC start quietly without complaining, when no /dev/lirc0 is created?  

```

root@kuken:~# lircd -n --device=/dev/lirc0 &
lircd-0.8.4a[31685]: lircd(default) ready

root@kuken:~# ls -l /dev/lirc*
srw-rw-rw- 1 root root 0 2009-03-24 11:12 /dev/lircd

```

Should there have been an error message?  What can I do to get /dev/lirc0?  Do I need LIRC from CVS, even though I have 0.8.4a from Jaunty?

When everything is OK, should I see the remote in /proc/bus/input/devices?


Klem fra Nils

---

### Post by Freddan101 on 2009-03-25
> **Nils Grimsmo said:**
> Everything seems to load nicely here, but no /dev/lirc or /dev/lirc0 is created. 

```

root@kuken:~# lsb_release -r
Release:	9.04

root@kuken:~# uname -a
Linux kuken 2.6.28-11-generic #37-Ubuntu SMP Mon Mar 23 16:40:00 UTC 2009 x86_64 GNU/Linux

root@kuken:~# apt-cache policy lirc
lirc:
  Installed: 0.8.4a-0ubuntu3

root@kuken:~# cat /etc/modprobe.d/usbhid.conf 
options usbhid quirks=0x15c2:0x0036:0x0004

root@kuken:~# cat /proc/bus/usb/devices
...
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0036 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
...

```

Have run `dpkg-reconfigure lirc` and selected "Soundgraph iMON PAD IR/VFD" for remote, and "None" for IR transmitter (after avoiding a bug in the package installer [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/346468]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/346468") in the package installer.)

```

root@kuken:~# lsmod | grep lirc
lirc_imon              26124  0 
lirc_dev               22088  1 lirc_imon

root@kuken:~# dmesg
...
[ 3142.802664] lirc_dev: IR Remote Control driver registered, major 61 
[ 3142.804273] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD w/imon pad2keys patch, v0.3p2k
[ 3142.804275] lirc_imon: Venky Raju <dev@venky.ws>
[ 3142.804299] usbcore: registered new interface driver lirc_imon

root@kuken:~# ls -l /dev/lirc*
srw-rw-rw- 1 root root 0 2009-03-24 10:56 /dev/lircd

root@kuken:~# ps aux | grep lirc
root     26250  0.0  0.0  18032   596 ?        Ss   11:05   0:00 /usr/sbin/lircd --device=/dev/lirc0

```

/etc/init.d/lirc starts the daemon with `start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- --device=/dev/lirc0`.

Why does LIRC start quietly without complaining, when no /dev/lirc0 is created?  

```

root@kuken:~# lircd -n --device=/dev/lirc0 &
lircd-0.8.4a[31685]: lircd(default) ready

root@kuken:~# ls -l /dev/lirc*
srw-rw-rw- 1 root root 0 2009-03-24 11:12 /dev/lircd

```

Should there have been an error message?  What can I do to get /dev/lirc0?  Do I need LIRC from CVS, even though I have 0.8.4a from Jaunty?

When everything is OK, should I see the remote in /proc/bus/input/devices?


Klem fra Nils
When my setup wasn't working lirc didn't give me any errors either. My main problem was that the wrong modules were loading at startup. Once I figured out where Ubuntu was looking I could replace those with my compiled ones.

This is what lsmod | grep gives me:

```
lirc_imon              23816  3
lirc_dev               20164  1 lirc_imon
usbcore               149360  8 lirc_imon,usb_storage,libusual,usbhid,ohci_hcd,ehci_hcd
```
I'm running Mythbuntu 8.10 and lirc 0.8.3. Hopefully someone with the same OS and lirc version as you have can contribute with some more knowledge.

---

### Post by Nils Grimsmo on 2009-03-25
I have now finally managed to get all devices working.  In my previous attempt I used LIRC 0.8.4a from Ubuntu, and the kernel modules from 2.6.28-11-generic.  But now I got LIRC from CVS, compiled, and inserted modules in the right place, and things loaded nicely. 

Tip:  To check what loads:

```

# strace modprobe lirc_imon 2>&1 | grep /lib/modules
open("/lib/modules/2.6.28-11-generic/modules.dep.bin", O_RDONLY) = 3
open("/lib/modules/2.6.28-11-generic/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko", O_RDONLY) = 3
open("/lib/modules/2.6.28-11-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko", O_RDONLY) = 3

```

(These are now symlinks into /lib/modules/2.6.28-11-generic/misc/)

Now everything is in place:

```

# ls -l /dev/lirc*
crw-r--r-- 1 root root 61, 0 2009-03-25 18:21 /dev/lirc
crw-rw---- 1 root root 61, 0 2009-03-25 18:28 /dev/lirc0
crw-rw---- 1 root root 61, 1 2009-03-25 18:28 /dev/lirc1
srw-r--r-- 1 root root     0 2009-03-25 18:40 /dev/lircd
prw-r--r-- 1 root root     0 2009-03-25 18:21 /dev/lircm

```

I started mode2, and got some presses, but then things hung, and gave no more output.

```

root@kuken:/usr/local/src/lirc# mode2 --raw
code: 0x0200001e00000000
code: 0x0200000000000000
code: 0x0200001f00000000
code: 0x0200000000000000
code: 0x0200002000000000
code: 0x0200000000000000
^C
root@kuken:/usr/local/src/lirc# mode2 --raw
^C

```

I have tried removing and re-inserting the kernel modules, rebooting, and even booting windows to check that the remote still worked, but to no avail.  I get nothing more from mode2.

Any ideas?

BTW:  Is there a simple test program to get key presses from lircd, not directly from /dev/lirc, to test that lircd actually works?


Klem fra Nils

---

### Post by Nils Grimsmo on 2009-03-25
BTW: Does anybody know if the 15c2:0036 will work out of the box in Ubuntu 9.04 when it is released?  That would make life a bit easier :popcorn:


Klem fra Nils

---

### Post by fmbrul on 2009-03-31
I have been working on this subject now for several weeks. Unfortunately little result for so many hours. Time to call for some help and sign up at the ubuntu forum.
First: I am running on a 2.6.27-9-generic kernel, ubuntu intrepid.
I am already succesfully running mythtv (backend and frontend on one machine) together with xbmc so I am able to use the streaming script XOTG. I managed to set up lirc for my PVR350 Hauppauge remote. (not really much to it, comes standard out of the box). Next step is to trying to get a 15c2:0038 IR/LCD device working in my Zalman 160 pluse case. (I know, this thread is about the IR/VFD) (as suggested in some posts about hardware failure, my LCD does work, as I have seen it working on a windows xp installation)

I read a lot on this subject, the most helpfull sources beeing:
[http://ubuntuforums.org/archive/index.php/t-1041258.html](http://ubuntuforums.org/archive/index.php/t-1041258.html)
[http://codeka.com/forums/viewtopic.php?f=3&t=57&st=0&sk=t&sd=a&start=10](http://codeka.com/forums/viewtopic.php?f=3&t=57&st=0&sk=t&sd=a&start=10)
[http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html](http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html)
[http://orsolf.blogspot.com/](http://orsolf.blogspot.com/)
[http://ubuntuforums.org/showthread.php?t=915212](http://ubuntuforums.org/showthread.php?t=915212)
[http://codeka.com/forums/viewtopic.php?f=3&p=529](http://codeka.com/forums/viewtopic.php?f=3&p=529)
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/306346](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/306346)

Status thusfar:

From the mythtvblogspot forum I tried to follow the mentioned procedure. Unfortunately the suggested download and build of [http://ronfrazier.net/mythtv/downloads/lirc-cvs.tar.gzip](http://ronfrazier.net/mythtv/downloads/lirc-cvs.tar.gzip) does not work. It gives compilation errors indicating a kernel configuration problem, which I understood has nothing to do with the kernel, but more the source code you are trying to compile.
On [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/306346](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/306346) I found some more info on trying to build lirc. I managed to download the lirc sources from Kenny Millingtons’s PPA. I replaced the lirc_imon.c file and I am able to do a dkms build of lirc without problems. After modprobing:  /dev/lirc0, /dev/lirc1, dev/lcd0 and /dev/lcd1 are visible (huray!) 
But:
When I do perl -e 'print pack "H*", "80000000091e0088"' > /dev/lcd0   (after giving permissions to the device, sudo chmod 777 /dev/lcd0) nothing happens. :( . No error, but nothing on the display either.
When I look at dmesg |grep lirc I see it is opening and closing the lcd device. The driver however is mentioning IR/VFD. My thought is that something still went wrong with loading the driver.
I did try moving around the *.ko files to different locations as mentioned on several of the above posts.

As I understand it the .ko files are the actual drivers. By modprobe –r <drivername> you can unload the driver. With modprobe <drivername> you can load it. Then the point is: from what location does the kernel load the driver (search the system for possible locations). Could it be as easy as obtaining a lirc_imon.ko file from someone who has a similar setup and trying to start that driver? (guess not, bu hey I am learning)

So as a summary, I am looking for the following answers:
1.)	What should the output be of dmesg |grep lirc on a working system, that is an imon 15c2:0038 device.
2.)	What does it mean if perl -e 'print pack "H*", "80000000091e0088"' > /dev/lcd0  does not give any output whatsoever.
3.)	Is it possible to load any compiled .ko file from a similar system


Really hope someone is out there with some answers or directions as I desperately need to boost the WAF! :) So help is appreciated very much!

---

### Post by fastie81 on 2009-04-21
Hi fmbrul

I have got this working on my mythbuntu 8.10 for a long time now..
you can have a look at this, hope it helps
[http://sites.google.com/site/it1stop/Home/linux/mythbuntu---linuxmce/lirc-remote](http://sites.google.com/site/it1stop/Home/linux/mythbuntu---linuxmce/lirc-remote)
There is two pages.. one for the remote and one for the LCD..


I am now looking to see if I can get it working on Mythbuntu 9.04. Just started today so have not got any where yet..
But I will update my website with my results..

Chris

---

### Post by joshoekstra on 2009-05-07
> **fastie81 said:**
> Hi fmbrul

I have got this working on my mythbuntu 8.10 for a long time now..
you can have a look at this, hope it helps
[http://sites.google.com/site/it1stop/Home/linux/mythbuntu---linuxmce/lirc-remote](http://sites.google.com/site/it1stop/Home/linux/mythbuntu---linuxmce/lirc-remote)
There is two pages.. one for the remote and one for the LCD..


I am now looking to see if I can get it working on Mythbuntu 9.04. Just started today so have not got any where yet..
But I will update my website with my results..

Chris
Now it's even easier, still not out-of-the-box but still doable:
apt-get install lirc-modules-source with requisites,

download this [**lirc_imon.c**]("http://lirc.cvs.sourceforge.net/viewvc/*checkout*/lirc/lirc/drivers/lirc_imon/lirc_imon.c?revision=1.33") which is the 1.33 of the imon-driver and place it in /usr/src/lirc-0.8.4a/driver/lirc_imon instead of the original one.

Then try sudo dpkg-reconfigure lirc-modules-source, it will rebuild the modules. After that stop lircd and lcdproc(/etinit.d/lirc[LCDd] stop) and sudo rmmod lirc_imon lirc_dev, reload module with sudo modprobe lirc_imon. Check in dmesg if the version number is 0.5.

*
Sometimes you get an error about dkms not being able to build the driver, then you need to perform these actions and try again:
sudo dkms remove -m lirc -v 0.8.4a --all # removes lirc from dkms
sudo dkms add -m lirc -v 0.8.4a # adds lirc to dkms
sudo dkms build --verbose -m lirc -v 0.8.4a # does a build of modules, not sure if actually required.
*
If your module is loaded you can then use these lirc-files to configure your lirc-client:
[http://www.avenard.org/mythtv/lirc-conf.tar.gz]("http://www.avenard.org/mythtv/lirc-conf.tar.gz")
Then you should be able to start your lirc with that, if lirc complains about modules, you could add the same modulenames to the transmitter-part of hardware.conf, that solved an error for me.
Another reboot helped here as well.

---

### Post by fmbrul on 2009-05-07
Hi,

Thanks for the response, that site refers to the 0.8.3 lirc version. At this moment I have the source of 0.8.4a. Can you confirm this will work on 8.10, kernel 2.6.27?

Since I had trouble installing and compiling I decided to install the 'normal' lirc again from synaptic. This won't run however, not until I manualy remove the 'compiled' driver.
Anyone has a brief explanation on how these things work? Where does ubuntu put these compiled files, how do I tell the operating system to use which drivers on startup etc.? Any link to a website would be helpfull.


Thanks,

---

### Post by joshoekstra on 2009-05-07
I had it working under intrepid with the 0.8.3 version of lirc with the 1.32 driver from lirc CVS, this was with 2.6.27.nn and lirc-modules-source. After upgrade tot jaunty I had to get a newer version and 1.33 seems to work for me now again using lirc-modules source and lirc 0.8.4a with 2.6.28.nn as kernel.
So actually the only thing that changed was the version of lirc, driver and kernel, not the way using lirc-modules-source.

---

### Post by lightpower on 2009-06-07
Have been using Soundgraph imon device (VFD) which came alone with SilverStone LC16M. Got LIRC to work in straight steps as mentioned in the first post here. 

Have been having trouble with corrupt display of VFD until I added two lines to lirc_imon.c file.

Download lirc CVS and edit the file lirc/drivers/lirc_imon/lirc_imon.c

Locate send_packet section and add two lines as below just above return retval


        kfree(control_req);

        set_current_state(TASK_INTERRUPTIBLE);  #<-- Line Added
        schedule_timeout(50);                   #<-- Line Added
        return retval;
}

/**
 * Sends an associate packet to the iMON 2.4G.

Configure, Make and Make install.

After this the VFD started working properly.

Thanks to "http://codeka.com/forums/viewtopic.php?f=3&t=35&start=10#p863" for providing a direction here.

---

### Post by lightpower on 2009-06-14
Figured a problem with irexec part of 0.8.6-CVS. When run it gives "irexec: No such file or directory" error. I have copied irexec alone from 0.8.5-CVS build it works fine now.

---

### Post by haakon on 2009-07-15
Thanks to everyone here, I've now gotten the VFD on my 0036 to work with lcdproc.

The IR remains a problem. In /dev I have lirc0, lirc1 and lircd. To see if the remote works, I use a command like 'mode2 -d /dev/lirc0 --raw'. This mostly does not react to the remote, but on some occasions I am able to get some key presses through (perhaps 4-5 presses), and then it just stops reacting again. I check if the codes correspond to the keys I pressed, and they do. But I also get some codes with lots of zeroes in them, mostly after I have gotten a legitimate keypress through. Does this ring a bell for anyone?

---

### Post by stowaway on 2009-07-17
Excuse my ignorance im a noob to linux.
I have installed Myhtbuntu 9.04 I have IR/VD 15c2:0036.
I choose soundgraph Imon PAD IR/VFD for my remote during install.
I have a fresh install of mythbuntu. no extra programs installed yet

> **joshoekstra said:**
> Now it's even easier, still not out-of-the-box but still doable:
apt-get install lirc-modules-source with requisites,

with requisites?

I did:
apt-get install lirc-modules-source  
i hope that will include requeistes?

> **joshoekstra said:**
> 
download this [**lirc_imon.c**]("http://lirc.cvs.sourceforge.net/viewvc/*checkout*/lirc/lirc/drivers/lirc_imon/lirc_imon.c?revision=1.33") which is the 1.33 of the imon-driver and place it in /usr/src/lirc-0.8.4a/driver/lirc_imon instead of the original one.

done!
sudo cp lirc_imon.c /usr/src/lirc-0.8.4a/driver/lirc_imon

> **joshoekstra said:**
> 
Then try sudo dpkg-reconfigure lirc-modules-source, it will rebuild the modules. 

easy enough?
dpkg-reconfigure lirc-modules-source
done!

> **joshoekstra said:**
> 
After that stop lircd and lcdproc(/etinit.d/lirc[LCDd] stop) 

a bit confused?
michael@MediaPC:/usr/src/lirc-0.8.4a/drivers/lirc_imon$ sudo lircd stop
lircd: there seems to already be a lircd process with pid 2840
lircd: otherwise delete stale lockfile /var/run/lircd.pid

deleted that file..
I dont have lcdproc installed.. dont care about the VFD.. let me know if this is essential?

> **joshoekstra said:**
> 
and sudo rmmod lirc_imon lirc_dev, 

michael@MediaPC:/var/run$ sudo rmmod lirc_imon lirc_dev

(just went to next line. no response)

> **joshoekstra said:**
> 
reload module with sudo modprobe lirc_imon. Check in dmesg if the version number is 0.5.

michael@MediaPC:/var/run$ sudo modprobe lirc_imon
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
michael@MediaPC:/var/run$ 

??

I now seem to have LCD0 LCD1 LIRC0 LIRC1 in my /dev folder so this is good news.
I untared the conf files and copied them to the /etc/init.d and /etc/lirc

Still get no response from my remote in mythtv tho? not sure where to go from here?
i should mention i dont have the original remote. i use a logitech unversal remote. i have loaded antec fusion 480 remote into it tho.. I also loaded mce remote just to test.. 
Any help is much appreciated!

---

### Post by joshoekstra on 2009-07-27
You seem to be close, try if you can run irw and then press all the buttons you can. If your remote is properly configured, it should show keypresses.
But as I understand it, this soundgraph module doesn't support other remotes but if it does with the logitech I'd get one as well.

---

### Post by k-geoir on 2009-07-27
Hello,

    I have a new issue to submit to you :D

   I just download mythbuntu and bought a LC16M case with the famous 15c2:0036 IR/VFD device. (I say famous because I read somuch forum about it that I am think that internet is only talking about it ;) I follow the goog tutorial on [http://www.mythtv.org/wiki/SilverstoneTek_LC16M](http://www.mythtv.org/wiki/SilverstoneTek_LC16M) and had my VFD full working! but I still have some trouble with the remote! My remote is only a mouse: The pad, right click and left click is working but nothing about other button! I only have /dev/lirc0 and not lirc1????????????? when I run cat /dev/lirc0 | xdd I got all button and all number are the same as the lirc.conf. When I am using mode2 on /dev/lirc0 it's working but not with irw (conexion refused)????

   any idea? Thanks

---

