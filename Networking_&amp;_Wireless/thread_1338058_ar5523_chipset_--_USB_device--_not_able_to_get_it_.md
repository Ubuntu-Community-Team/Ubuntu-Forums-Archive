---
title: "ar5523 chipset -- USB device-- not able to get it working in Ubuntu"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by Hatewin7 on 2009-11-26
hi,
 
I am trying to get the above device with an ar5523 chipset working under wubi ubuntu9.10
 
In the first attempt I got to the point where I was told that the ar5523 driver was not 64 bit. 
---------
when I type 
dmesg
tells me:
[ 697.670047] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 697.821707] usb 1-3: configuration #1 chosen from 1 choice
[ 697.950050] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[ 698.103180] ndiswrapper (check_nt_hdr:150): kernel is [URL="http://www.linuxforums.org/forum/#"][COLOR=blue][COLOR=blue! important][FONT=Verdana][COLOR=blue! important][FONT=Verdana]64-bit[/FONT][/FONT][/COLOR][/color][/color]
[COLOR=#003d7d][IMG]http://kona.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG][/COLOR]
[/URL], but Windows driver is not 64-bit;bad magic: 010B
[ 698.103189] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net5523'
[ 698.103705] ndiswrapper (load_wrap_driver:10[IMG]http://www.linuxforums.org/forum/images/smilies/icon_cool.gif[/IMG]: couldn't load driver net5523; check system log for messages from 'loadndisdriver' 
-----------
the next attampt was to switch to a 32 bit Ubuntu version but it seems like the number of problems just increases. Now I cannot get even ndiswrapper working
----------
bichi@ubuntu:~/Documents/ndiswrapper-1.55$ make
make -C driver
make[1]: Entering directory `/home/bichi/Documents/ndiswrapper-1.55/driver'
make -C /usr/src/linux-headers-2.6.31-14-generic M=/home/bichi/Documents/ndiswrapper-1.55/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
LD /home/bichi/Documents/ndiswrapper-1.55/driver/built-in.o
MKEXPORT /home/bichi/Documents/ndiswrapper-1.55/driver/crt_exports.h
MKEXPORT /home/bichi/Documents/ndiswrapper-1.55/driver/hal_exports.h
MKEXPORT /home/bichi/Documents/ndiswrapper-1.55/driver/ndis_exports.h
MKEXPORT /home/bichi/Documents/ndiswrapper-1.55/driver/ntoskernel_exports.h
MKEXPORT /home/bichi/Documents/ndiswrapper-1.55/driver/ntoskernel_io_exports.h
MKEXPORT /home/bichi/Documents/ndiswrapper-1.55/driver/rtl_exports.h
MKEXPORT /home/bichi/Documents/ndiswrapper-1.55/driver/usb_exports.h
CC [M] /home/bichi/Documents/ndiswrapper-1.55/driver/crt.o
In file included from /home/bichi/Documents/ndiswrapper-1.55/driver/crt.c:16:
/home/bichi/Documents/ndiswrapper-1.55/driver/ntoskernel.h: In function â€˜PushEntrySListâ€™:
/home/bichi/Documents/ndiswrapper-1.55/driver/ntoskernel.h:905: error: implicit declaration of function â€˜cmpxchg8bâ€™
make[3]: *** [/home/bichi/Documents/ndiswrapper-1.55/driver/crt.o] Error 1
make[2]: *** [_module_/home/bichi/Documents/ndiswrapper-1.55/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/bichi/Documents/ndiswrapper-1.55/driver'
make: *** [all] Error 2
----------------------
 
If you have any idea please let me know,
I

---

