---
title: "WUSB54GCv3 drivers?"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by grief -l on 2009-12-02
Hello all -
 
Following instructions in [this]("http://ubuntuforums.org/showthread.php?t=1155941") thread I get to 
 
```
make && make install
```
 
and then Packman spits this out:
 
```
 make && make install
make -C tools
make[1]: Entering directory `/home/gabe/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/gabe/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/gabe/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/gabe/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/gabe/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/gabe/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.o
/home/gabe/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c: In function ‘RTUSBWatchDog’:
/home/gabe/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c:758: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘ULONG’
/home/gabe/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c: At top level:
/home/gabe/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c:1003: error: expected identifier or ‘(’ before ‘{’ token
/home/gabe/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.c:1003: error: expected identifier or ‘(’ before ‘,’ token
make[2]: *** [/home/gabe/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../os/linux/usb_main_dev.o] Error 1
make[1]: *** [_module_/home/gabe/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2
```
 
 
Any and all help will be greatly appreciated.
 
Gabe.

---

### Post by adun153 on 2010-10-30
BUMP

I have the same problem :(

---

