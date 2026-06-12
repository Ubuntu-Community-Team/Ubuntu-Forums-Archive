---
title: "qc-sub-messenger-1.7 not compiling"
date: 2008-06-03
forum: Multimedia Software
---

### Post by WanSheng on 2008-06-03
Hi,

I'm new to Linux and I'm trying to get my webcam working. Reading a lot of posts on this forum, I figured out I need to install the "qc-sub-messenger-1.7" driver since my webcam ID is 08f5 from Logitech. 

```
archi@Bender:~$ lsusb | grep Logitech
Bus 003 Device 002: ID 046d:08f5 Logitech, Inc.
```

I followed the instruction from this old post :
[http://ubuntuforums.org/showthread.php?t=111225&highlight=08f5]("http://ubuntuforums.org/showthread.php?t=111225&highlight=08f5")
and also this one (Ubuntu French forum)
[http://forum.ubuntu-fr.org/viewtopic.php?id=211823]("http://forum.ubuntu-fr.org/viewtopic.php?id=211823")
but I still get an error in the compiling section of the quickcam.sh script. I also tried the patch suggested on the link above. Here's the error :

```
Another round done. Let's now compile the driver, it takes a while.
This step will also clear old unnecessary files from the directory.
Press Ctrl+C to quit, Enter to continue ---> 

rm -f *.o qcset input_read show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
cd testquickcam ; make clean
make[1]: Entering directory `/home/archi/qc-usb-messenger-1.7/testquickcam'
rm -f testquickcam *~ pic.ppm pic.gif
make[1]: Leaving directory `/home/archi/qc-usb-messenger-1.7/testquickcam'
make -C "/lib/modules/2.6.24-17-generic/build" SUBDIRS="/home/archi/qc-usb-messenger-1.7" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /home/archi/qc-usb-messenger-1.7/.tmp_versions ; rm -f /home/archi/qc-usb-messenger-1.7/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/archi/qc-usb-messenger-1.7
  gcc -m32 -Wp,-MD,/home/archi/qc-usb-messenger-1.7/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/archi/qc-usb-messenger-1.7/.tmp_qc-driver.o /home/archi/qc-usb-messenger-1.7/qc-driver.c
/home/archi/qc-usb-messenger-1.7/qc-driver.c: In function ‘qc_usb_init’:
/home/archi/qc-usb-messenger-1.7/qc-driver.c:3667: warning: left shift count >= width of type
  gcc -m32 -Wp,-MD,/home/archi/qc-usb-messenger-1.7/.qc-vv6450.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_vv6450)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/archi/qc-usb-messenger-1.7/.tmp_qc-vv6450.o /home/archi/qc-usb-messenger-1.7/qc-vv6450.c
  gcc -m32 -Wp,-MD,/home/archi/qc-usb-messenger-1.7/.qc-formats.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_formats)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/archi/qc-usb-messenger-1.7/.tmp_qc-formats.o /home/archi/qc-usb-messenger-1.7/qc-formats.c
  gcc -m32 -Wp,-MD,/home/archi/qc-usb-messenger-1.7/.qc-memory.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -DNOKERNEL -DHAVE_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_memory)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/archi/qc-usb-messenger-1.7/.tmp_qc-memory.o /home/archi/qc-usb-messenger-1.7/qc-memory.c
  ld -m elf_i386 -m elf_i386   -r -o /home/archi/qc-usb-messenger-1.7/quickcam.o /home/archi/qc-usb-messenger-1.7/qc-driver.o /home/archi/qc-usb-messenger-1.7/qc-vv6450.o /home/archi/qc-usb-messenger-1.7/qc-formats.o /home/archi/qc-usb-messenger-1.7/qc-memory.o
  Building modules, stage 2.
make -f /usr/src/linux-headers-2.6.24-17-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.24-17-generic/Module.symvers -I /home/archi/qc-usb-messenger-1.7/Module.symvers -o /home/archi/qc-usb-messenger-1.7/Module.symvers -w -s
  gcc -m32 -Wp,-MD,/home/archi/qc-usb-messenger-1.7/.quickcam.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(quickcam.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -DMODULE -c -o /home/archi/qc-usb-messenger-1.7/quickcam.mod.o /home/archi/qc-usb-messenger-1.7/quickcam.mod.c
  ld -m elf_i386 -r -m elf_i386  --build-id -o /home/archi/qc-usb-messenger-1.7/quickcam.ko /home/archi/qc-usb-messenger-1.7/quickcam.o /home/archi/qc-usb-messenger-1.7/quickcam.mod.o
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
gcc -Wall -O2 -s qcset.c -o qcset -lm
qcset.c:26:20: error: string.h: No such file or directory
qcset.c:27:20: error: stdlib.h: No such file or directory
qcset.c:28:19: error: stdio.h: No such file or directory
qcset.c:29:19: error: fcntl.h: No such file or directory
qcset.c:30:19: error: errno.h: No such file or directory
qcset.c:31:20: error: unistd.h: No such file or directory
qcset.c:32:23: error: sys/ioctl.h: No such file or directory
qcset.c:33:23: error: sys/types.h: No such file or directory
qcset.c:34:22: error: sys/stat.h: No such file or directory
qcset.c:35:19: error: ctype.h: No such file or directory
qcset.c:36:18: error: math.h: No such file or directory
In file included from videodev2.h:15,
                 from qcset.c:39:
videodevfix.h:6: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__s8’
videodevfix.h:7: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__u8’
videodevfix.h:8: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__s16’
videodevfix.h:9: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__u16’
videodevfix.h:10: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__s32’
videodevfix.h:11: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__u32’
videodevfix.h:12: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__s64’
videodevfix.h:13: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__u64’
In file included from qcset.c:39:
videodev2.h:34: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘stamp_t’
videodev2.h:52: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:81: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:136: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:147: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:158: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:170: error: expected specifier-qualifier-list before ‘__u8’
videodev2.h:203: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:213: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:219: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:269: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:300: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:314: error: expected specifier-qualifier-list before ‘__u64’
videodev2.h:324: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:338: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:350: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:367: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:375: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:388: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:401: error: expected specifier-qualifier-list before ‘__u8’
videodev2.h:458: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:474: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:494: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:512: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:519: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:535: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:544: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:605: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:619: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:650: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:661: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:683: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:694: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:720: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:735: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:972: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:985: error: expected specifier-qualifier-list before ‘ulong’
videodev2.h:1005: error: expected specifier-qualifier-list before ‘__u16’
videodev2.h:1035: error: expected specifier-qualifier-list before ‘__u16’
videodev2.h:1056: error: expected specifier-qualifier-list before ‘__s32’
videodev2.h:1063: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:1077: error: expected specifier-qualifier-list before ‘__u32’
videodev2.h:1102: error: expected specifier-qualifier-list before ‘__u8’
qcset.c:71: error: ‘NULL’ undeclared here (not in a function)
qcset.c:77: error: initializer element is not constant
qcset.c:77: error: (near initialization for ‘flags_compat[3].name’)
qcset.c:86: error: initializer element is not constant
qcset.c:86: error: (near initialization for ‘flags_quality[6].name’)
qcset.c:91: error: initializer element is not constant
qcset.c:91: error: (near initialization for ‘flags_bool[2].name’)
qcset.c:101: warning: implicit declaration of function ‘_IOR’
qcset.c:101: error: expected expression before ‘int’
qcset.c:101: error: initializer element is not constant
qcset.c:101: error: (near initialization for ‘ioctlinfo[0].get’)
qcset.c:101: warning: implicit declaration of function ‘_IOWR’
qcset.c:101: error: expected expression before ‘int’
qcset.c:101: error: initializer element is not constant
qcset.c:101: error: (near initialization for ‘ioctlinfo[0].set’)
qcset.c:102: error: expected expression before ‘int’
qcset.c:102: error: initializer element is not constant
qcset.c:102: error: (near initialization for ‘ioctlinfo[1].get’)
qcset.c:102: error: expected expression before ‘int’
qcset.c:102: error: initializer element is not constant
qcset.c:102: error: (near initialization for ‘ioctlinfo[1].set’)
qcset.c:103: error: expected expression before ‘int’
qcset.c:103: error: initializer element is not constant
qcset.c:103: error: (near initialization for ‘ioctlinfo[2].get’)
qcset.c:103: error: expected expression before ‘int’
qcset.c:103: error: initializer element is not constant
qcset.c:103: error: (near initialization for ‘ioctlinfo[2].set’)
qcset.c:104: error: expected expression before ‘int’
qcset.c:104: error: initializer element is not constant
qcset.c:104: error: (near initialization for ‘ioctlinfo[3].get’)
qcset.c:104: error: expected expression before ‘int’
qcset.c:104: error: initializer element is not constant
qcset.c:104: error: (near initialization for ‘ioctlinfo[3].set’)
qcset.c:104: error: initializer element is not constant
qcset.c:104: error: (near initialization for ‘ioctlinfo[3].flags’)
qcset.c:105: error: expected expression before ‘int’
qcset.c:105: error: initializer element is not constant
qcset.c:105: error: (near initialization for ‘ioctlinfo[4].get’)
qcset.c:105: error: expected expression before ‘int’
qcset.c:105: error: initializer element is not constant
qcset.c:105: error: (near initialization for ‘ioctlinfo[4].set’)
qcset.c:106: error: expected expression before ‘int’
qcset.c:106: error: initializer element is not constant
qcset.c:106: error: (near initialization for ‘ioctlinfo[5].get’)
qcset.c:106: error: expected expression before ‘int’
qcset.c:106: error: initializer element is not constant
qcset.c:106: error: (near initialization for ‘ioctlinfo[5].set’)
qcset.c:107: error: expected expression before ‘int’
qcset.c:107: error: initializer element is not constant
qcset.c:107: error: (near initialization for ‘ioctlinfo[6].get’)
qcset.c:107: error: expected expression before ‘int’
qcset.c:107: error: initializer element is not constant
qcset.c:107: error: (near initialization for ‘ioctlinfo[6].set’)
qcset.c:107: error: initializer element is not constant
qcset.c:107: error: (near initialization for ‘ioctlinfo[6].flags’)
qcset.c:108: error: expected expression before ‘int’
qcset.c:108: error: initializer element is not constant
qcset.c:108: error: (near initialization for ‘ioctlinfo[7].get’)
qcset.c:108: error: expected expression before ‘int’
qcset.c:108: error: initializer element is not constant
qcset.c:108: error: (near initialization for ‘ioctlinfo[7].set’)
qcset.c:109: error: expected expression before ‘int’
qcset.c:109: error: initializer element is not constant
qcset.c:109: error: (near initialization for ‘ioctlinfo[8].get’)
qcset.c:109: error: expected expression before ‘int’
qcset.c:109: error: initializer element is not constant
qcset.c:109: error: (near initialization for ‘ioctlinfo[8].set’)
qcset.c:110: error: expected expression before ‘int’
qcset.c:110: error: initializer element is not constant
qcset.c:110: error: (near initialization for ‘ioctlinfo[9].get’)
qcset.c:110: error: expected expression before ‘int’
qcset.c:110: error: initializer element is not constant
qcset.c:110: error: (near initialization for ‘ioctlinfo[9].set’)
qcset.c:111: error: expected expression before ‘struct’
qcset.c:111: error: initializer element is not constant
qcset.c:111: error: (near initialization for ‘ioctlinfo[10].get’)
qcset.c:111: error: expected expression before ‘struct’
qcset.c:111: error: initializer element is not constant
qcset.c:111: error: (near initialization for ‘ioctlinfo[10].set’)
qcset.c:112: error: expected expression before ‘int’
qcset.c:112: error: initializer element is not constant
qcset.c:112: error: (near initialization for ‘ioctlinfo[11].get’)
qcset.c:112: error: expected expression before ‘int’
qcset.c:112: error: initializer element is not constant
qcset.c:112: error: (near initialization for ‘ioctlinfo[11].set’)
qcset.c:113: error: expected expression before ‘int’
qcset.c:113: error: initializer element is not constant
qcset.c:113: error: (near initialization for ‘ioctlinfo[12].get’)
qcset.c:113: error: expected expression before ‘int’
qcset.c:113: error: initializer element is not constant
qcset.c:113: error: (near initialization for ‘ioctlinfo[12].set’)
qcset.c:114: error: expected expression before ‘int’
qcset.c:114: error: initializer element is not constant
qcset.c:114: error: (near initialization for ‘ioctlinfo[13].get’)
qcset.c:114: warning: implicit declaration of function ‘_IOW’
qcset.c:114: error: expected expression before ‘int’
qcset.c:114: error: initializer element is not constant
qcset.c:114: error: (near initialization for ‘ioctlinfo[13].set’)
qcset.c:114: error: initializer element is not constant
qcset.c:114: error: (near initialization for ‘ioctlinfo[13].flags’)
qcset.c:115: error: expected expression before ‘int’
qcset.c:115: error: initializer element is not constant
qcset.c:115: error: (near initialization for ‘ioctlinfo[14].get’)
qcset.c:115: error: expected expression before ‘int’
qcset.c:115: error: initializer element is not constant
qcset.c:115: error: (near initialization for ‘ioctlinfo[14].set’)
qcset.c:116: error: expected expression before ‘int’
qcset.c:116: error: initializer element is not constant
qcset.c:116: error: (near initialization for ‘ioctlinfo[15].get’)
qcset.c:116: error: expected expression before ‘int’
qcset.c:116: error: initializer element is not constant
qcset.c:116: error: (near initialization for ‘ioctlinfo[15].set’)
qcset.c:116: error: initializer element is not constant
qcset.c:116: error: (near initialization for ‘ioctlinfo[15].flags’)
qcset.c:117: error: expected expression before ‘int’
qcset.c:117: error: initializer element is not constant
qcset.c:117: error: (near initialization for ‘ioctlinfo[16].get’)
qcset.c:117: error: expected expression before ‘int’
qcset.c:117: error: initializer element is not constant
qcset.c:117: error: (near initialization for ‘ioctlinfo[16].set’)
qcset.c:117: error: initializer element is not constant
qcset.c:117: error: (near initialization for ‘ioctlinfo[16].flags’)
qcset.c: In function ‘print_cap’:
qcset.c:125: warning: implicit declaration of function ‘printf’
qcset.c:125: warning: incompatible implicit declaration of built-in function ‘printf’
qcset.c:145: warning: incompatible implicit declaration of built-in function ‘printf’
qcset.c:145: error: ‘struct video_window’ has no member named ‘x’
qcset.c:145: error: ‘struct video_window’ has no member named ‘y’
qcset.c:146: error: ‘struct video_window’ has no member named ‘width’
qcset.c:146: error: ‘struct video_window’ has no member named ‘height’
qcset.c:146: warning: format ‘%i’ expects type ‘int’, but argument 2 has type ‘const struct ioctlstruct *’
qcset.c:146: warning: format ‘%i’ expects type ‘int’, but argument 3 has type ‘const struct ioctlstruct *’
qcset.c:147: error: ‘struct video_window’ has no member named ‘chromakey’
qcset.c:147: warning: format ‘%i’ expects type ‘int’, but argument 2 has type ‘const struct ioctlstruct *’
qcset.c:149: error: ‘struct video_window’ has no member named ‘flags’
qcset.c:149: error: invalid operands to binary &
qcset.c:150: error: ‘struct video_window’ has no member named ‘flags’
qcset.c:150: error: invalid operands to binary &
qcset.c:155: warning: incompatible implicit declaration of built-in function ‘printf’
qcset.c:159: error: ‘struct video_channel’ has no member named ‘flags’
qcset.c:159: error: invalid operands to binary &
qcset.c:160: error: ‘struct video_channel’ has no member named ‘flags’
qcset.c:160: error: invalid operands to binary &
qcset.c:166: error: ‘struct video_channel’ has no member named ‘type’
qcset.c:171: error: ‘struct video_channel’ has no member named ‘norm’
qcset.c:171: warning: format ‘%i’ expects type ‘int’, but argument 2 has type ‘const struct ioctlstruct *’
qcset.c:175: warning: incompatible implicit declaration of built-in function ‘printf’
qcset.c:175: error: ‘struct video_picture’ has no member named ‘brightness’
qcset.c:175: warning: format ‘%i’ expects type ‘int’, but argument 2 has type ‘const struct ioctlstruct *’
qcset.c:176: error: ‘struct video_picture’ has no member named ‘hue’
qcset.c:176: warning: format ‘%i’ expects type ‘int’, but argument 2 has type ‘const struct ioctlstruct *’
qcset.c:177: error: ‘struct video_picture’ has no member named ‘colour’
qcset.c:177: warning: format ‘%i’ expects type ‘int’, but argument 2 has type ‘const struct ioctlstruct *’
qcset.c:178: error: ‘struct video_picture’ has no member named ‘contrast’
qcset.c:178: warning: format ‘%i’ expects type ‘int’, but argument 2 has type ‘const struct ioctlstruct *’
qcset.c:179: error: ‘struct video_picture’ has no member named ‘whiteness’
qcset.c:179: warning: format ‘%i’ expects type ‘int’, but argument 2 has type ‘const struct ioctlstruct *’
qcset.c:180: error: ‘struct video_picture’ has no member named ‘depth’
qcset.c:180: warning: format ‘%i’ expects type ‘int’, but argument 2 has type ‘const struct ioctlstruct *’
qcset.c:182: error: ‘struct video_picture’ has no member named ‘palette’
qcset.c: In function ‘error’:
qcset.c:212: error: ‘errno’ undeclared (first use in this function)
qcset.c:212: error: (Each undeclared identifier is reported only once
qcset.c:212: error: for each function it appears in.)
qcset.c:212: warning: assignment makes integer from pointer without a cast
qcset.c:214: warning: implicit declaration of function ‘fprintf’
qcset.c:214: warning: incompatible implicit declaration of built-in function ‘fprintf’
qcset.c:214: error: ‘stderr’ undeclared (first use in this function)
qcset.c:214: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type
qcset.c:216: warning: implicit declaration of function ‘vfprintf’
qcset.c:218: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type
qcset.c:219: warning: implicit declaration of function ‘strerror’
qcset.c:219: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type
qcset.c:219: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
qcset.c:220: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type
qcset.c:222: warning: implicit declaration of function ‘exit’
qcset.c:222: warning: incompatible implicit declaration of built-in function ‘exit’
qcset.c: In function ‘help’:
qcset.c:228: warning: incompatible implicit declaration of built-in function ‘printf’
qcset.c:266: warning: comparison of distinct pointer types lacks a cast
qcset.c:273: warning: incompatible implicit declaration of built-in function ‘exit’
qcset.c: In function ‘print_regs’:
qcset.c:292: warning: incompatible implicit declaration of built-in function ‘printf’
qcset.c:297: warning: implicit declaration of function ‘ioctl’
qcset.c:297: error: expected expression before ‘int’
qcset.c:310: warning: implicit declaration of function ‘sleep’
qcset.c:324: error: expected expression before ‘int’
qcset.c: At top level:
qcset.c:345: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
qcset.c: In function ‘pnm_nexttoken’:
qcset.c:351: warning: implicit declaration of function ‘getc’
qcset.c:351: error: ‘pnm_file’ undeclared (first use in this function)
qcset.c:352: error: ‘EOF’ undeclared (first use in this function)
qcset.c:352: warning: comparison between pointer and integer
qcset.c:356: warning: comparison between pointer and integer
qcset.c:360: warning: implicit declaration of function ‘isspace’
qcset.c:361: warning: implicit declaration of function ‘ungetc’
qcset.c: In function ‘pnm_readnum’:
qcset.c:369: error: ‘pnm_file’ undeclared (first use in this function)
qcset.c:370: warning: implicit declaration of function ‘isdigit’
qcset.c: In function ‘pnm_open’:
qcset.c:383: error: ‘pnm_file’ undeclared (first use in this function)
qcset.c:383: warning: implicit declaration of function ‘fopen’
qcset.c:383: warning: statement with no effect
qcset.c: In function ‘pnm_close’:
qcset.c:405: warning: implicit declaration of function ‘fclose’
qcset.c:405: error: ‘pnm_file’ undeclared (first use in this function)
qcset.c:406: warning: statement with no effect
qcset.c: In function ‘pnm_getpixel’:
qcset.c:412: error: ‘pnm_file’ undeclared (first use in this function)
qcset.c: In function ‘compute_lut’:
qcset.c:447: warning: implicit declaration of function ‘pow’
qcset.c:447: warning: incompatible implicit declaration of built-in function ‘pow’
qcset.c:465: warning: incompatible implicit declaration of built-in function ‘pow’
qcset.c: In function ‘main’:
qcset.c:490: warning: implicit declaration of function ‘close’
qcset.c:500: warning: implicit declaration of function ‘open’
qcset.c:500: error: ‘O_RDWR’ undeclared (first use in this function)
qcset.c:501: error: expected expression before ‘struct’
qcset.c:502: error: expected expression before ‘struct’
qcset.c:504: error: expected expression before ‘struct’
qcset.c:505: error: expected expression before ‘struct’
qcset.c:509: warning: assignment from incompatible pointer type
qcset.c:519: warning: implicit declaration of function ‘atoi’
qcset.c:535: error: ‘struct video_picture’ has no member named ‘brightness’
qcset.c:535: warning: statement with no effect
qcset.c:536: error: expected expression before ‘struct’
qcset.c:542: error: ‘struct video_picture’ has no member named ‘hue’
qcset.c:542: warning: statement with no effect
qcset.c:543: error: expected expression before ‘struct’
qcset.c:549: error: ‘struct video_picture’ has no member named ‘colour’
qcset.c:549: warning: statement with no effect
qcset.c:550: error: expected expression before ‘struct’
qcset.c:556: error: ‘struct video_picture’ has no member named ‘contrast’
qcset.c:556: warning: statement with no effect
qcset.c:557: error: expected expression before ‘struct’
qcset.c:563: error: ‘struct video_picture’ has no member named ‘whiteness’
qcset.c:563: warning: statement with no effect
qcset.c:564: error: expected expression before ‘struct’
qcset.c:570: error: expected expression before ‘int’
qcset.c:577: warning: implicit declaration of function ‘memset’
qcset.c:577: warning: incompatible implicit declaration of built-in function ‘memset’
qcset.c:582: error: expected expression before ‘struct’
qcset.c:584: warning: incompatible implicit declaration of built-in function ‘printf’
qcset.c:608: error: expected expression before ‘struct’
qcset.c:620: warning: implicit declaration of function ‘sscanf’
qcset.c:620: warning: incompatible implicit declaration of built-in function ‘sscanf’
qcset.c:627: warning: incompatible implicit declaration of built-in function ‘pow’
qcset.c:632: error: expected expression before ‘struct’
qcset.c:657: error: expected expression before ‘struct’
qcset.c:678: warning: incompatible implicit declaration of built-in function ‘memset’
qcset.c:679: warning: incompatible implicit declaration of built-in function ‘sscanf’
qcset.c:686: warning: incompatible implicit declaration of built-in function ‘pow’
qcset.c:691: warning: incompatible implicit declaration of built-in function ‘printf’
qcset.c:712: warning: incompatible implicit declaration of built-in function ‘exit’
qcset.c:721: warning: implicit declaration of function ‘memcmp’
qcset.c:721: warning: implicit declaration of function ‘strlen’
qcset.c:721: warning: incompatible implicit declaration of built-in function ‘strlen’
qcset.c:725: warning: implicit declaration of function ‘strncmp’
qcset.c:727: warning: incompatible implicit declaration of built-in function ‘sscanf’
qcset.c:728: warning: incompatible implicit declaration of built-in function ‘printf’
qcset.c:732: error: expected expression before ‘int’
qcset.c:736: warning: incompatible implicit declaration of built-in function ‘printf’
qcset.c:737: error: expected expression before ‘int’
qcset.c:748: warning: comparison of distinct pointer types lacks a cast
qcset.c:749: warning: comparison of distinct pointer types lacks a cast
qcset.c:752: warning: incompatible implicit declaration of built-in function ‘printf’
qcset.c:759: warning: incompatible implicit declaration of built-in function ‘printf’
qcset.c:768: warning: comparison of distinct pointer types lacks a cast
qcset.c:769: warning: comparison of distinct pointer types lacks a cast
qcset.c:770: warning: incompatible implicit declaration of built-in function ‘strlen’
qcset.c:785: warning: incompatible implicit declaration of built-in function ‘printf’
make: *** [qcset] Error 1
-rw-r--r-- 1 root root 725551 2008-06-03 20:40 quickcam.ko
[!] Looks like compilation of the utility programs failed.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->
```

Can anyone help ?  I installed Linux last Friday and I like it soo much I'm trying to convince my girlfriend to do the same. I'm in China right now and she's in Canada, so without the webcam working Ubuntu doesn't impress her that much :lolflag:

Thanks

(oh... I also tried the qc-usb-messenger-1.8, I still have the same error)

---

